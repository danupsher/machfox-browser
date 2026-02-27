# PowerFox for Tiger

A port of [PowerFox](https://github.com/Jazzzny/powerfox-browser) to **Mac OS X 10.4 Tiger** on **PowerPC G5**.

PowerFox is a modern, open-source web browser based on the UXP engine and Basilisk browser. The original targets 10.5 Leopard and 10.6 Snow Leopard — this fork aims to bring it to Tiger.

## Status

**Work in progress.** The build compiles but is not yet producing a working browser.

## What's different from upstream

- Targets `powerpc-apple-darwin8` (Tiger) instead of Leopard/Snow Leopard
- Cross-compiled from Linux using GCC 7.5.0 with a custom toolchain:
  - Assembly fixup pipeline for Darwin PPC compatibility
  - SSH-proxied linking on a real Tiger Mac
  - 10.4 universal SDK
- See `mozconfig` on the `tiger-ppc` branch for build configuration

## Building

This is cross-compiled from Linux — it cannot be built natively on Tiger. Requires:
- GCC 7.5.0 cross-compiler targeting `powerpc-apple-darwin8`
- cctools-port (assembler, ar, ranlib)
- MacOSX10.4u.sdk
- A Tiger Mac accessible via SSH (for native linking)

## Credits

- [Jazzzny](https://github.com/Jazzzny) for PowerFox
- Basilisk and UXP teams for the browser engine
- TenFourFox for legacy Mac OS X support code
