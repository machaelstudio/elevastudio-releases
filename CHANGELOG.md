# Changelog

All notable changes to Eleva Studio are listed here. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and the project uses
[Semantic Versioning](https://semver.org/).

## [1.1.0] - 2026-11-18

### Added

- **Export for print and DTF.** A "Use" selector (Screen, Print, DTF) in the new Export tab.
  Print and DTF files carry a resolution tag from 150 to 600 dpi. The DTF preset applies the
  clean-up transfer RIPs need: solid edges, stray-speck removal, a one-pixel edge shrink against
  white halos, margin trimming and an optional mirror.
- **Print width check.** Enter the final print width and the app shows the resolution the image
  reaches at that size, with a one-click enlarge to the target.
- **TIFF export.** 8-bit, lossless LZW compression, transparency preserved when present.
- **Logo / art cut-out.** A fifth cut-out mode that removes a flat background colour exactly,
  including enclosed areas such as the insides of letters, and cleans the colour fringe from
  edges. It needs no download, runs in a fraction of a second and is preselected automatically
  for flat artwork.
- **Restore.** A third tool for the highest-quality enlargement and restoration of low-quality
  images, run through a ComfyUI installation on the same computer (SeedVR2). One-time setup;
  see the [Restore setup guide](docs/SEEDVR2.md).
- **File size and destination before saving.** The action bar shows the size of the file that
  will be written and where it will go.
- **Save location setting.** Ask every time, save next to the original, or use a fixed folder.
  Existing files are never overwritten.
- **Spanish interface.** English is now the default language; Spanish is available in Settings.
- Canvas zoom, keyboard shortcuts (Ctrl/Cmd+O, Z, S), elapsed time per step, and a Settings
  panel with storage use and a shortcut to the components folder.
- macOS installer window with drag-to-Applications instructions.

### Changed

- **New interface.** A labelled tool rail (Cutout, Enlarge, Restore, Export), a panel that shows
  only the active step, and an action bar that keeps file size, destination, Undo and Save
  visible at all times. File names are shown in the filmstrip.
- Images opened through the Open dialog or dropped on the window keep their original location,
  which the "save next to the original" option uses.
- Error and progress messages follow the selected language.

### Fixed

- The After side of the comparison view showed the original image through transparent areas, so
  a removed background appeared to be still there.

## [1.0.0] - 2026-11-18

First release as a native application for Windows and macOS.

### Added

- **Background removal** in four qualities (Fast, Precise, Maximum, People) with a fine-edges
  option for hair and fur.
- **New background**: transparent, solid colour, your own image or the blurred original, with an
  optional soft shadow and margin.
- **Enlarge** 2×, 3× or 4× in Photo or Logo / art mode, accelerated by the graphics card
  (DirectML on Windows, Core ML on macOS).
- Batch processing, before/after comparison, undo, and export to PNG, JPG or a ZIP of all images.
- Signed Windows installer, signed and notarized macOS app, and automatic updates.

[1.1.0]: https://github.com/machaelstudio/elevastudio-releases/releases/tag/v1.1.0
[1.0.0]: https://github.com/machaelstudio/elevastudio-releases/releases/tag/v1.0.0
