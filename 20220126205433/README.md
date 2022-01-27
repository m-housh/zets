# Building Homebrew Bottles with Github Action

So I've been working on pre-built binaries distributed through a custom
homebrew tap.  With Github actions it seems that I can build them for big-sur
on intel.  It seemed to fail when building a universal binary, but that was
a path error in the build command in the `Makefile`. I also am not sure if
`brew` allows universal binaries or not, some older threads indicated that they
don't.

The action that builds the binary also updates the homebrew tap, which if a
build exits in an error can leave the tap in an invalid / incomplete state, the
action does state that it's archived (or WIP), so I should explore a different
action.

My work-around so far has been to build the binary that I can then build for
monterey on my machines and upload the binary to the release.  Which actually
requires building on 2 different machines (one `arm64` and the other `x86_64`).
This could potentially be my lack of understanding of how to distribute and
build the binaries.

