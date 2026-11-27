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

1. **Install ComfyUI and open it.** The simplest route is the official desktop app from
   [comfy.org/download](https://www.comfy.org/download) (Windows and Mac). The portable Windows
   zip from the [ComfyUI GitHub releases](https://github.com/comfyanonymous/ComfyUI/releases) also
   works; see "Portable build" below.
2. **Install the first add-on from inside ComfyUI.** Open **Manage Extensions**: the
   puzzle-piece icon in the top bar, or **Help → Manage Extensions**. Search for `SeedVR2` and
   install **ComfyUI-SeedVR2_VideoUpscaler** (by *numz* / AInVFX).
3. **Add the second add-on by hand.** *SeedVR2 Tiling Upscaler* (by *moonwhaler*) is not in
   that list, so it will not show up in the search:
   1. Download it as a zip: [comfyui-seedvr2-tilingupscaler](https://github.com/moonwhaler/comfyui-seedvr2-tilingupscaler/archive/refs/heads/main.zip).
   2. Unzip it into ComfyUI's `custom_nodes` folder. With the desktop app that is
      `Documents/ComfyUI/custom_nodes`; with the portable build it is
      `ComfyUI_windows_portable\ComfyUI\custom_nodes`.
   3. Check the result: `custom_nodes/comfyui-seedvr2-tilingupscaler-main/` must contain the
      add-on's files (`__init__.py`, `upscaler.py`, …) directly, not another folder of the same
      name.
   4. Restart ComfyUI.
4. **Leave ComfyUI open.** In Eleva Studio open **Restore** and press **Check again**. The
   steps are ticked off one by one, so you can see which part is still missing, and the panel
   then shows "Ready · connected to ComfyUI".

Eleva Studio finds ComfyUI by itself on the usual addresses (`http://127.0.0.1:8188`, and
`http://127.0.0.1:8000` for the desktop app). Only if you changed the port do you need to type
the address under "ComfyUI address (advanced)".

Recent versions of ComfyUI also ship their own SeedVR2 workflows. Those are separate: Eleva
Studio uses the two add-ons above, because the tiling add-on is what makes large print sizes fit
in memory.

### Portable build: turning on Manage Extensions

In the portable build the extension manager is switched off until you enable it once:

1. Open the `ComfyUI_windows_portable` folder, type `cmd` in the address bar and press Enter.
2. Run `.\python_embeded\python.exe -m pip install -r ComfyUI\manager_requirements.txt`
   (if that file does not exist, run `update\update_comfyui.bat` first).
3. Make a copy of `run_nvidia_gpu.bat`, open the copy in Notepad and add ` --enable-manager` to
   the end of the line that starts with `.\python_embeded\python.exe`.
4. Start ComfyUI with that copy from now on.

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
- **An add-on is reported missing after you installed it**: restart ComfyUI; add-ons are only
  loaded at start. If *SeedVR2 Tiling Upscaler* is still missing, open its folder in
  `custom_nodes` and make sure the files are not one folder too deep (step 3).
- **You cannot find the Manager**: it is now called **Manage Extensions** (puzzle-piece icon or
  the Help menu). In the portable build it has to be enabled first, see above.
- **Still out of memory after the retry**: pick a `Q4_K_M` GGUF model, or a smaller output size.
- **ComfyUI shows an error about a missing model**: open ComfyUI's window; the first download
  may have been interrupted. Press Restore again to resume it.
