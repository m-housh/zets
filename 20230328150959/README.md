# API Call for TCA Example

Define what you would like to return from the api.

## Model

```swift
struct User: Codable, Equatable, Identifiable {
  let id: UUID
  let email: String
}

extension User {
  static let mock = Self(id: UUID(uuidString: "deadbeef-dead-beef-dead-beefdeadbeef"), email: "blob@example.com")
}
```

## Dependency to load a `User`

Define a struct that abstracts / can load data from an external source.

```swift
struct UserLoader {
  var load: () async throws -> User

  init(_ load: @escaping () async throws -> User) {
    self.load = load
  }
}

extension UserLoader: DependencyKey {
  var liveValue = Self {
    // do work here, URLSession, etc.
    let request = URLRequest(url: URL(string: "http://mysite.com/user/deadbeef-dead-beef-dead-beefdeadbeef")!)
    try await URLSession.shared.data(for: request)
  }

  var testValue = Self {
    return User.mock
  }

  var previewValue: Self { .testValue }
}

extension DependencyValues {
  public var userLoader: UserLoader {
    get { self[UserLoader.self] }
    set { self[UserLoader.self = newValue }
  }
}
```

## Use the Dependency in a TCA View

Create a view and feature in the `TCA` style, that needs the dependency defined above.

```swift
struct UserFeature: ReducerProtocol
  @Dependency(\.userLoader) var userLoader

  struct State: Equatable {
    var user: User?
  }

  struct Action: Equatable {
    case viewDidAppear
    case recieveUser(TaskResult<User>)
  }

  var body: some ReducerOf<Self> {
    Reduce { state, action in
      switch action {
        case .viewDidAppear:
          return .task {
            await TaskResult {
              try await userLoader.load()
            }
          }
        case .recieveUser(.success(let user)):
          state.user = user
          return .none
        case .recieveUser(.failure(let error)):
          // handle error
          print("ERROR: \(error)")
          return .none
    }
  }
}

struct UserView: View {
  let store: StoreOf<UserFeature>

  var body: some View {
    // Should really us an `IfLetStore`, but for example purposes.
    WithViewStore(store, observe: { $0 }) { viewStore in
      Text(viewStore.user?.email ?? "")
        .onAppear { viewStore.send(.viewDidAppear) }
    }
  }
}
```

