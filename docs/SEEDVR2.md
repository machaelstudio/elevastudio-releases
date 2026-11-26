# Restore (highest quality) — setup guide

The **Restore** tool enlarges and restores low-quality or pixelated photos with SeedVR2, a
restoration model that is far too large to ship inside Eleva Studio (3 to 15 GB per model and a
graphics card with 8 GB or more of memory). Eleva Studio therefore uses a ComfyUI installation on
the same computer and drives it for you: you keep working in Eleva Studio, ComfyUI just has to be
open in the background.

This is the one tool that needs a setup. Everything else in Eleva Studio works out of the box.

## What you need

- **Windows**: an NVIDIA graphics card with 8 GB VRAM or more (12 GB or more recommended) and
  about 20 GB of free disk space. AMD cards work through ComfyUI's ROCm/DirectML builds but are
  slower and less tested.
- **Mac**: Apple Silicon with 32 GB or more of unified memory. It works, but expect several
  minutes per photo.
- Internet for the one-time downloads.

## Install (about 15 minutes, once)

1. **Install ComfyUI.** The simplest route is the official desktop app from
   [comfy.org/download](https://www.comfy.org/download) (Windows and Mac). The portable Windows
   zip from the [ComfyUI GitHub releases](https://github.com/comfyanonymous/ComfyUI/releases) also
   works.
2. **Open ComfyUI** and open the **Manager** (the puzzle-piece button; the desktop app ships
   with it). Choose **Custom Nodes Manager**, search and install:
   - **ComfyUI-SeedVR2_VideoUpscaler** by *numz* (select the **nightly** version when asked).
   - **SeedVR2 Tiling Upscaler** by *moonwhaler* (`comfyui-seedvr2-tilingupscaler`).
   Restart ComfyUI when the Manager asks.
3. **Leave ComfyUI open.** By default it listens on `http://127.0.0.1:8188`.
4. In Eleva Studio open **Restore** and press **Check again**. The steps are ticked off and
   the panel shows "Ready · connected to ComfyUI".

The models are **not** downloaded during the install: the first time you press **Restore image**
ComfyUI downloads the chosen one (the progress is shown in ComfyUI's own window). After that it
is local.

## Using it

- **Quality** lists the SeedVR2 models ComfyUI knows:
  - *3b* models: faster, fine for most photos. `fp8` needs about 8 GB of VRAM, `Q4` GGUF less.
  - *7b* models: the best detail, slower, 16 GB of VRAM or more. `sharp` variants add crispness.
- **Output size**: 2×, 3×, 4×, or **Print**, which computes the pixels your print width needs at
  the chosen dpi (set the width in the Export card).
- Press **Restore image**. A 1200 px photo to 4× takes about a minute on an RTX 3060, longer on
  smaller cards. If ComfyUI runs out of memory Eleva Studio retries once in a low-memory mode
  (smaller tiles, model block swapping, tiled VAE), which is slower but usually succeeds.
- The result is a normal step in the history: you can undo it, remove the background, pick a
  background, and export it with the DTF or print options like any other image.

Settings used (the node author's recommended values): tiles 1024 px with 32 px overlap in
checkerboard order, multi-band blending, LAB colour matching, no anti-aliasing. Low-memory retry
uses 512 px tiles, 16 swapped blocks and tiled VAE.

## Problems

- **"ComfyUI was not found on this computer"**: start ComfyUI, wait until its window has
  loaded, press Check again. If you changed ComfyUI's port, type the new address under
  "ComfyUI address (advanced)".
- **"the two SeedVR2 add-ons are missing"**: finish step 2 and restart ComfyUI.
- **Still out of memory after the retry**: pick a `Q4_K_M` GGUF model, or a smaller output size.
- **ComfyUI shows an error about a missing model**: open ComfyUI's window; the first download
  may have been interrupted. Press Restore again to resume it.
