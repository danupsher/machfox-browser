# PowerFox Tiger

A port of [PowerFox](https://github.com/Jazzzny/powerfox-browser) to **Mac OS X 10.4 Tiger** on **PowerPC G5**.

PowerFox is a modern, open-source web browser based on the UXP engine and Basilisk browser. The original targets 10.5 Leopard and 10.6 Snow Leopard — this fork brings it to Tiger with full GPU-accelerated compositing.

## Features

- **GPU-accelerated compositing** via CompositorOGL on the ATI Radeon 9600 (OpenGL 1.5)
- **OMTC (Off-Main-Thread Compositing)** — compositing runs on a separate thread, freeing the CPU for JavaScript, layout, and video decode
- **GLSL 1.05 compatible shaders** — constant-index workarounds for variable array indexing limitations
- **Non-NPOT GPU fixes** — buffer rotation disabled to prevent scroll black bars on GPUs without non-power-of-two texture support; FBO intermediate surfaces disabled to prevent Y-flip artifacts
- Modern web browsing on vintage Tiger PPC hardware

## Download

**[Latest release: v1.3](https://github.com/danupsher/powerfox-tiger/releases/tag/v1.3)** — DMG and tarball available.

## Hardware Tested

| Spec | Value |
|------|-------|
| Machine | iMac G5 (PowerMac8,2) |
| CPU | PowerPC G5 2.0 GHz |
| RAM | 1 GB |
| GPU | ATI Radeon 9600, 128 MB VRAM |
| Display | 1680x1050 |
| OS | Mac OS X 10.4.11 Tiger |

## Release History

| Version | Date | Highlights |
|---------|------|-----------|
| **v1.3** | 2026-03-03 | Fixed tab text showing middle of title instead of beginning |
| **v1.2** | 2026-03-03 | Fixed scroll black bars (buffer rotation + NPOT padding), fixed FBO Y-flip on YouTube |
| **v1.1** | 2026-03-03 | GPU-accelerated compositing (CompositorOGL + OMTC), GLSL 1.05 shaders, opaque GL surface |
| **v1.0** | 2026-03-02 | Initial Tiger port — Cairo fonts, CSS fixes, PowerFox branding |

## What is different from upstream

- Targets `powerpc-apple-darwin8` (Tiger) instead of Leopard/Snow Leopard
- Cross-compiled from Linux using GCC 15 with ld64-linux linker
- GPU compositing fixes for GLSL 1.05 / OpenGL 1.5 (Radeon 9600)
- Buffer rotation disabled for non-NPOT GPUs (fixes scroll black bars)
- FBO intermediate surfaces disabled (fixes Y-flip on video content)
- GL context view attachment timing fix for Tiger compositor thread
- Opaque GL surface for Tiger (no rounded window corners)
- Cairo font rendering fixes for Tiger
- 10.4 universal SDK

## Building

Cross-compiled from Linux — requires:
- [GCC 15 cross-compiler](https://github.com/danupsher/tiger-ppc-builds) targeting `powerpc-apple-darwin8`
- ld64-linux (Mach-O linker for Linux)
- cctools-port (assembler, ar, ranlib)
- MacOSX10.4u.sdk

See `mozconfig` on the `tiger-ppc` branch for build configuration.

## Credits

- [Jazzzny](https://github.com/Jazzzny) for PowerFox
- Basilisk and UXP teams for the browser engine
- TenFourFox for legacy Mac OS X support inspiration
