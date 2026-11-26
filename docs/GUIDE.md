# Eleva Studio — user guide

Photo cutouts and upscaling on your own computer. Nothing is uploaded, there is no subscription,
and the app is in English by default (Spanish is available in Settings).

## Install

Download the latest version from
[github.com/machaelstudio/elevastudio-releases/releases/latest](https://github.com/machaelstudio/elevastudio-releases/releases/latest):

- **Windows 10 / 11 (64-bit)**: run `ElevaStudio-<version>-windows-x64-setup.exe`. The installer is
  signed, so Windows and Smart App Control accept it without warnings. No administrator rights needed.
- **Mac (Apple Silicon, macOS 14 or newer)**: open `ElevaStudio-<version>-macos-arm64.dmg` and drag
  Eleva Studio to Applications. The app is signed and notarized by Apple.

When a new version exists the app offers to update itself on launch.

## Tools

- **Cutout** (remove background): four qualities (Fast, Precise, Maximum, People) and a **Fine edges**
  switch for hair and fur. Then choose a new background: transparent, a color, your own image or the
  blurred photo, with an optional soft shadow and margin.
- **Enlarge**: 2×, 3× or 4×, in Photo or Logo / art mode. Made for large-format printing.
- **Restore**: the highest-quality enlargement and restoration (SeedVR2). It needs a one-time
  setup of ComfyUI on the same computer; see [SEEDVR2.md](SEEDVR2.md). Everything else works
  without it.
- **Batch**: open several photos and switch on "Apply to all images".
- **Before / after** slider, zoom, undo (Ctrl+Z), save (Ctrl+S), open (Ctrl+O).

The first time you use each tool it downloads a component (internet needed only then): about
170 MB for Cutout (930 MB for Maximum) and 34 MB for Enlarge. Settings shows how much is stored
and opens the folder.

## Export for print and DTF

The Export card has a **Use** selector:

- **Screen**: plain PNG or JPG, no resolution tag.
- **Print**: files carry a resolution tag (300 dpi by default; 150 to 600 available), so CorelDRAW,
  Illustrator and Photoshop open them at the right physical size. TIFF is 8-bit, LZW (lossless),
  with transparency when there is any.
- **DTF transfer**: PNG with transparency plus the clean-up that DTF RIPs need, because the RIP
  prints white ink under every pixel that is not fully transparent:
  - **Solid edges**: no semi-transparent pixels (otherwise soft edges print as a white fringe).
  - **Remove stray specks**: isolated dots left by the cutout, which would print as white dots.
  - **Shrink edges 1 px**: pulls the artwork back by one pixel so the white underbase never shows.
  - **Trim transparent margins**: crops to the artwork, handy for gang sheets.
  - **Mirror horizontally**: off by default. Most RIP programs mirror the design themselves; turn it
    on only if yours does not.

**File size and destination**: under the format you see the size of the file that will be written
("File size: 12.4 MB · 4800 × 3600 px") and where it goes. Settings → **Save to** chooses between
asking every time, the same folder as the original photo, or a fixed folder; files are never
overwritten (a -2, -3 suffix is added).

**Print width**: type the final width (inches or cm) and the hint tells you the resolution the current
image reaches at that size. If it is below the target, one click enlarges it by the scale needed
(up to 4×). Example: a 1200 px photo printed 12 in wide is 100 dpi; "Enlarge 3×" takes it to 300 dpi.

## Graphics card

The app uses the graphics card when it can: DirectML on Windows (most NVIDIA, AMD and Intel GPUs of
the last few years) and CoreML on Mac. The status at the top right shows which is active, for
example "Ready · GPU (DirectML)". With "CPU" everything still works, only slower.

## Limits and tips

- Maximum result size when enlarging: 16,000 px per side. Use 2× for very large photos.
- Hard cases (loose hair, glass, jewelry): Maximum quality with Fine edges.
- For transparency use PNG or TIFF; JPG is flattened on white.
- JPG is fine for screens and photo prints; for transfers always use PNG.
