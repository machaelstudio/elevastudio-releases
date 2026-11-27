# Eleva Studio

Background removal, enlargement and print-ready export for photos and artwork, on your own
computer. Eleva Studio is free, works offline once set up, and never uploads your images.

**[Download the latest version](https://github.com/machaelstudio/elevastudio-releases/releases/latest)**

| Platform | Requirements | Installer |
|---|---|---|
| Windows | Windows 10 or 11, 64-bit | `ElevaStudio-<version>-windows-x64-setup.exe` |
| macOS | macOS 14 or later, Apple Silicon | `ElevaStudio-<version>-macos-arm64.dmg` |

## Features

- **Cutout.** Remove the background from product photos and portraits in four qualities, with a
  fine-edges option for hair and fur. A dedicated Logo / art mode removes flat background colours
  exactly.
- **New background.** Transparent, a solid colour, your own image or the blurred original, with
  an optional soft shadow and margin.
- **Enlarge.** 2×, 3× or 4×, for photos or for logos and flat art, using the graphics card when
  one is available.
- **Vectorize.** Traces logos, lettering and flat artwork into clean SVG shapes for CorelDRAW,
  Illustrator and cutting software.
- **Restore.** Highest-quality restoration of low-quality images through ComfyUI, a free
  program on the same computer. Optional, set up in two steps; see the
  [setup guide](docs/SEEDVR2.md).
- **Export for print and DTF.** PNG, JPG and TIFF with a resolution tag, a print-width
  resolution check, and DTF clean-up: solid edges, speck removal, edge shrink, trim and mirror.
- **Batch work.** Process several images at once and save them together.
- English and Spanish interface.

## Installing

**Windows.** Run the installer. It is signed by Machael Studio LLC and installs for the current
user, so it needs no administrator rights.

**macOS.** Open the disk image and drag Eleva Studio to the Applications folder. The app is
signed with a Developer ID and notarized by Apple.

The first time you use a tool, Eleva Studio downloads the component it needs: about 170 MB for
Cutout (930 MB for the Maximum quality) and 34 MB for Enlarge. After that it works offline.

## Updates

Eleva Studio checks for a new version when it starts and offers to install it. Every release is
listed on the [Releases page](https://github.com/machaelstudio/elevastudio-releases/releases)
with its installers and SHA-256 checksums, and described in the [changelog](CHANGELOG.md).

## Documentation

- [User guide](docs/GUIDE.md)
- [Guía de uso en español](docs/LEEME.md)
- [Restore setup guide](docs/SEEDVR2.md) · [en español](docs/SEEDVR2-ES.md)
- [Changelog](CHANGELOG.md)

## Privacy

Images are processed on your computer and are never uploaded. The app connects to the internet
only to download components on first use and to check for updates, both from this repository.

## Components

The [`models-1`](https://github.com/machaelstudio/elevastudio-releases/releases/tag/models-1)
release holds the processing components the app downloads on first use. They are ONNX builds of
U²-Net, IS-Net and BiRefNet as distributed by [rembg](https://github.com/danielgatis/rembg), and
of [Real-ESRGAN](https://github.com/xinntao/Real-ESRGAN). All are published under open licences
that permit commercial use.

## Support

Found a problem or have a request? Open an
[issue](https://github.com/machaelstudio/elevastudio-releases/issues) and include the version
shown in Settings and your operating system.

Published by Machael Studio LLC.
