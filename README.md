# MachFox

A modern web browser for **Mac OS X 10.4 Tiger** on **PowerPC** (G3/G4/G5).

Built on the [UXP](https://github.com/ArcticFoxie/ArcticFox)/[Basilisk](https://www.basilisk-browser.org/) engine, cross-compiled from Linux using GCC 15 + ld64.

## Features

- **GPU-accelerated compositing** via CompositorOGL (OpenGL 1.5)
- **OMTC (Off-Main-Thread Compositing)** for smoother UI
- **GLSL 1.05 compatible shaders** with constant-index workarounds
- **Non-NPOT GPU fixes** — buffer rotation and FBO workarounds for vintage GPUs
- **G3/G4/G5 compatible** — runs on any PowerPC Mac with Tiger
- Modern web standards on vintage hardware

## Download

**[Latest release](https://github.com/danupsher/machfox-browser/releases)** — DMG and tarball available.

## Hardware Tested

| Spec | Value |
|------|-------|
| Machine | iMac G5 (PowerMac8,2) |
| CPU | PowerPC G5 2.0 GHz |
| RAM | 1 GB |
| GPU | ATI Radeon 9600, 128 MB VRAM |
| Display | 1680x1050 |
| OS | Mac OS X 10.4.11 Tiger |

## What is different from upstream

- Targets `powerpc-apple-darwin8` (Tiger) instead of Leopard/Snow Leopard
- Cross-compiled from Linux using GCC 15.2.0 with ld64-linux linker
- GPU compositing fixes for GLSL 1.05 / OpenGL 1.5 (Radeon 9600)
- Buffer rotation disabled for non-NPOT GPUs (fixes scroll black bars)
- FBO intermediate surfaces disabled (fixes Y-flip / inverted content)
- GL context view attachment timing fix for Tiger compositor thread
- Opaque GL surface for Tiger (no rounded window corners)
- Cairo font rendering fixes for Tiger
- Smooth scrolling disabled by default (better performance on slow hardware)
- MachFox branding with OpenMoji globe icon
- 10.4 universal SDK, `-force_cpusubtype_ALL` for G3/G4/G5 compatibility

## Building

Cross-compiled from Linux — requires:
- [GCC 15 + ld64 cross-compiler](https://github.com/danupsher/tiger-ppc-builds/releases/tag/gcc15-xcompiler-1.3) targeting `powerpc-apple-darwin8`
- cctools-port (assembler, ar, ranlib)
- MacOSX10.4u.sdk

See `mozconfig` on the `tiger-ppc` branch for build configuration.

## Credits

- [Jazzzny](https://github.com/Jazzzny) for PowerFox (Leopard/Snow Leopard)
- Basilisk and UXP teams for the browser engine
- TenFourFox for legacy Mac OS X support inspiration
- [OpenMoji](https://openmoji.org/) for the globe icon (CC BY-SA 4.0)
