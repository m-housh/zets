# Maintain Custom Homebrew Tap

A gotcha that I found while maintaining a custom homebrew tap is that when
building bottles, you need to specify the root-url in the `bottle do` block,
otherwise it fails to install because it searches `homebrew/core` for
a manifest file.

Another gotcha is that when the tarballs are built they generally will have (2)
`--` in their name, however when a root-url is specified it will use (1) `-` in
the name, so you generally need to rename them when uploading to a release.

