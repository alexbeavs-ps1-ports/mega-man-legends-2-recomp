<p align="center"><a href="https://alexbeavs-ps1-ports.github.io/psxrecomp-ports/"><img src="https://raw.githubusercontent.com/alexbeavs-ps1-ports/psxrecomp-ports/main/docs/assets/alexbeav-ps1-recomps-banner.png" alt="Alexbeav's PS1 Recomps" width="100%"></a></p>

# Mega Man Legends 2

<!-- retcomm-readme-metrics -->
[![GitHub downloads (all assets, all releases)](https://img.shields.io/github/downloads/Alexbeav/mega-man-legends-2-recomp/total)](https://github.com/Alexbeav/mega-man-legends-2-recomp/releases)
[![GitHub downloads (latest release)](https://img.shields.io/github/downloads/Alexbeav/mega-man-legends-2-recomp/latest/total)](https://github.com/Alexbeav/mega-man-legends-2-recomp/releases/latest)
[![GitHub release](https://img.shields.io/github/v/release/Alexbeav/mega-man-legends-2-recomp)](https://github.com/Alexbeav/mega-man-legends-2-recomp/releases/latest)
<!-- /retcomm-readme-metrics -->

Static recompilation of **Mega Man Legends 2** built on
[psxrecomp](https://github.com/mstan/psxrecomp) and
[recomp-ui](https://github.com/RetroPortingToolKit/recomp-ui).

This is an owned-input setup kit. You supply your own SLES-03556 disc image
and your own SCPH-5552 (Europe) BIOS dump; first-run setup generates and compiles the game on
your machine. The kit and its release archives contain no game disc, retail BIOS,
generated game code, or saved game.

| | |
|---|---|
| Region | Europe |
| Disc serial | SLES-03556 |
| Discs | 1 |
| Supported dump | Redump `Mega Man Legends 2 (Europe).cue` as CUE/BIN or CHD |
| BIOS | SCPH-5552 (Europe), 524288 bytes, SHA-256 `1faaa18fa820a0225e488d9f086296b8e6c46df739666093987ff7d8fd352c09` |

## Setup

1. Download the setup ZIP for your platform from [Releases](https://github.com/Alexbeav/mega-man-legends-2-recomp/releases)
   and extract it into a writable folder.
2. Start `Mega_Man_Legends_2` (`.exe` on Windows).
3. In the setup wizard select your disc image (the Redump CUE, or a CHD of the
   same dump) and your BIOS file.
4. Run Generate & rebuild and wait for the game to start. The first run compiles
   the game and takes several minutes.

On Windows the wizard downloads the portable build tools (cmake-clang-v1) or uses
cmake/ninja already on PATH. On Linux and macOS install CMake, Ninja, Python 3,
and a C/C++ compiler first. Keep a CUE and every file it references together.
Setup produces both a normal and a diagnostic build; see *Diagnostic mode* below.

<!-- retcomm-readme-launcher -->
## Retro Launcher

You can run this title **standalone** (release zip + the built-in recomp-ui
Generate & Build flow), or manage installs, updates, ROM/BIOS wiring, and queued
builds more intuitively with
**[Retro Launcher](https://github.com/RetroPortingToolKit/Retro-Launcher)** —
the Retro Compilation Manager hub for self-compiling recomps.

[Downloads](https://github.com/RetroPortingToolKit/Retro-Launcher/releases) ·
[Full README & features](https://github.com/RetroPortingToolKit/Retro-Launcher#readme)

<p align="center">
  <img src="https://raw.githubusercontent.com/RetroPortingToolKit/Retro-Launcher/main/docs/screenshots/hub-and-game-launcher.png" alt="Retro hub with a background build, next to a title’s recomp-ui launcher" width="720">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/RetroPortingToolKit/Retro-Launcher/main/docs/screenshots/queue-and-background-build.png" alt="Background cmake build with titles queued" width="720">
</p>

Retro checks for updates, rebuilds with existing build data when possible,
shares the portable toolchain used by per-title launchers, and automates
BIOS/ROM/save plumbing so you are not stuck repeating each game’s wizard by hand.
<!-- /retcomm-readme-launcher -->

## Status

Version 0.1.0 release candidate.

- Windows: the exact setup package passed automated clean-extract setup,
  generation, compilation, and a headless start check on the pinned framework.
- Windows play testing on the private build this kit derives from: the first build showed a black window at start. The drive-position query correction is in the pinned framework and was accepted on a test candidate.
- Linux and macOS: packages are built by CI from the same recipe; native setup
  and gameplay have not been verified.

Full-game completion, audio fidelity, and multiplayer are not claimed. Runtime
snapshots from older builds are not qualified compatible; ordinary memory-card
saves are preserved across updates.

## Known issues

- This disc has audio tracks. Select the CUE (or a CHD made from the full dump) so every track is mounted; a Track 01-only BIN fails verification.

## Diagnostic mode

If the game crashes, freezes, or misbehaves, switch to the diagnostic build
that first-run setup already produced (no recompiling): create an empty file
named `diagnostic-mode.txt` next to `Mega_Man_Legends_2.exe` and start the game as
usual, or run `Mega_Man_Legends_2.exe --diagnostic`. Reproduce the problem, quit, then
run `Mega_Man_Legends_2.exe --collect-diagnostics`: it writes `diagnostics-<date>.zip`
next to the exe. Attach that zip to a GitHub issue on this repository with a
short description of what you did. The zip holds only the runtime's report
files, never saves, BIOS, or disc images. Delete `diagnostic-mode.txt` to go
back to normal mode. Details: `psxrecomp/docs/DIAGNOSTIC_MODE.md`.

## Legal

You must own the original game. Disc images under `disc/` are gitignored and
must never be committed. Retail BIOS dumps are not redistributed and OpenBIOS is
not shipped: this title is retail-BIOS-only, so first-run Generate needs your own
legally dumped SCPH-5552 (European) image.

Default app icon: `assets/psxrecomp.ico` (and `.png` / `.svg`) — Retro-themed controller mark from `psxrecomp/assets/`. Windows builds embed it via `APP_ICON`.

Box art is not shipped in this kit or its repository. Redistribution permission for third-party cover images is unresolved, so the launcher runs without one.

## About this project

This project was developed with AI assistance. AI assists with code,
documentation, and investigation; Alex tests the game and makes release
decisions. Validation claims describe only the tests actually performed.

## Credits and licenses

Framework: [psxrecomp](https://github.com/mstan/psxrecomp), built from the
pinned fork commit named by the `psxrecomp` submodule. Launcher:
[recomp-ui](https://github.com/RetroPortingToolKit/recomp-ui), pinned by the
`recomp-ui` submodule. This kit's own files are under [LICENSE](LICENSE); third-party
notices are in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md), and the framework
and launcher licenses remain in their source directories. The original game and its
trademarks belong to their respective owners.

<!-- retcomm-readme-raid -->
---

<p align="center">
  <sub><b>R.A.I.D. — Retro AI Development</b> · a Discord for AI-assisted retro reverse-engineering, decomp &amp; recomp</sub>
</p>

<p align="center">
  <a href="https://discord.gg/Ad9BwSzctP"><img src=".github/raid-discord.png" alt="Join the Retro AI Development (R.A.I.D.) Discord" width="200"></a>
</p>
<!-- /retcomm-readme-raid -->
