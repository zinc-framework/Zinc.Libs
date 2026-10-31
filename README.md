# Zinc.Libs

These libs are built out of the [Zinc.Bootstrapper](https://github.com/zinc-framework/Zinc.Bootstrapper) repo and are nested as a submodule in that repo as well as [Zinc.Core](https://github.com/zinc-framework/Zinc.Core)

Every native lib comes in two builds, chosen by the game's build configuration (see `ZincNativeLibFlavor` in Zinc.csproj):

| Folder | zig build | What it's for |
|---|---|---|
| `runtimes/<rid>/native/` | `ReleaseFast` | What ships: optimized, no sokol validation or asserts |
| `runtimes-debug/<rid>/native/` | `Debug` | Development: sokol validation and asserts, UBSan, the D3D11 debug layer where Graphics Tools are installed |

Both are built for a baseline CPU (x86-64-v2 on Windows, Apple M1 on macOS), not for the machine that built them. `build.ps1 <lib>:build` in the Bootstrapper builds both flavors; macOS ones can only be built on a Mac. Until a platform has a Release build, Release games fall back to its Debug one (osx-arm64 and browser-wasm, as of Oct 2026).
