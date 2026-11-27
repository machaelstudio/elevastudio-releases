# Changelog

All notable changes to Eleva Studio are listed here. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and the project uses
[Semantic Versioning](https://semver.org/).

## [1.1.2] - 2026-11-26

### Fixed

- **Restore now finds the ComfyUI desktop app.** Eleva Studio only looked for ComfyUI on port
  8188, the address of the portable build, so an installed and running ComfyUI desktop app
  (port 8000) was reported as "not found". The app now checks the usual local addresses by
  itself and remembers the one that answers.
- **The Quality list in Restore is filled in.** With the current SeedVR2 add-on the list stayed
  empty, so Restore could not be started even though ComfyUI was connected. The low-memory retry
  now also reaches the add-on's memory options, which it silently skipped before.
- **The setup guide matches current ComfyUI.** The Manager is now called Manage Extensions, and
  the SeedVR2 Tiling Upscaler add-on is not offered there, so the old instructions could not be
  completed. The guide, in English and Spanish, now explains where to find Manage Extensions,
  how to add the second add-on by hand, and how to enable the extension manager in the portable
  build.

### Changed

- **Restore says which part is missing.** The setup steps are ticked off separately for
  ComfyUI, the SeedVR2 add-on and the tiling add-on, and the message below names the one that
  is still missing instead of a general "add-ons are missing".

## [1.1.1] - 2026-11-25

### Changed

- **Faster processing.** On Apple Silicon the Precise cut-out is about four times faster and
  Enlarge about 1.7 times faster. Precise now uses the accelerated path on Mac instead of the
  processor alone.
- **Smaller Enlarge components.** The download is about half the size (34 MB for photos, 9 MB
  for logos and art) with no visible change in the result. After updating, Precise and Enlarge
  download their new components once; the old files are removed automatically.

- **Restore explains its setup.** Until ComfyUI and its two add-ons are installed, the Restore
  tab shows the setup steps in place, ticks them off as they are completed, and keeps its
  controls greyed out under "Available after setup", with a pointer to Enlarge, which needs no
  setup. The tool rail shows "Setup needed" or "Connected". A Spanish setup guide was added.

### Fixed

- **Maximum quality on Mac** took more than six minutes to start on every launch. It now starts
  at once and takes about ten seconds per photo.

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

[1.1.2]: https://github.com/machaelstudio/elevastudio-releases/releases/tag/v1.1.2
[1.1.1]: https://github.com/machaelstudio/elevastudio-releases/releases/tag/v1.1.1
[1.1.0]: https://github.com/machaelstudio/elevastudio-releases/releases/tag/v1.1.0
[1.0.0]: https://github.com/machaelstudio/elevastudio-releases/releases/tag/v1.0.0
