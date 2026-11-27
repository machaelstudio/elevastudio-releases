# Restore (highest quality) — setup guide

The **Restore** tool enlarges and restores low-quality or pixelated photos with SeedVR2, a
restoration model that is far too large to ship inside Eleva Studio (3 to 8 GB, and it needs a
graphics card with 8 GB or more of memory). Eleva Studio therefore uses ComfyUI, a separate free
program on the same computer, and drives it for you: you keep working in Eleva Studio, ComfyUI
just has to be open in the background.

This is the one tool that needs a setup. Everything else in Eleva Studio works out of the box.

## What you need

- **Windows**: an NVIDIA graphics card with 8 GB VRAM or more (12 GB or more recommended) and
  about 20 GB of free disk space.
- **Mac**: Apple Silicon with 32 GB or more of unified memory. It works, but expect several
  minutes per photo.
- Internet for the one-time downloads.

## Setup: two steps

1. **Install ComfyUI and leave it open.** In Eleva Studio open **Restore** and press
   **Get ComfyUI**; it opens [comfy.org/download](https://www.comfy.org/download). Install the
   desktop app like any other program (Windows and Mac), open it and let it finish its first
   start. You do not have to do anything inside ComfyUI.
2. **Press Download in Eleva Studio.** Back in **Restore**, press **Check again**: step 1 is
   ticked off and the button now reads **Download (3.9 GB)**. Press it. Eleva Studio downloads
   the Restore component and puts it in the right ComfyUI folder by itself. When the bar
   finishes, the panel shows "Ready · connected to ComfyUI".

That is all: there is nothing to search for, unzip or install inside ComfyUI, and ComfyUI does
not have to be restarted.

Good to know:

- The download can be stopped with **Stop** and continued later; it picks up where it left off.
  The same happens by itself if the connection drops.
- The files are checked after the download, so a damaged download is never used.
- Eleva Studio finds ComfyUI by itself on the usual addresses (`http://127.0.0.1:8000` for the
  desktop app, `http://127.0.0.1:8188` for the portable build). Only if you changed the port do
  you need to type the address under "ComfyUI address (advanced)".
- ComfyUI must be version 0.28 or newer (July 2026). Older versions do not include SeedVR2;
  update ComfyUI and press **Check again**.

## Using it

- **Quality**:
  - *Standard*: fast and fine for most photos. It is the one the setup downloads.
  - *High detail*: the finest detail; slower, and it wants a graphics card with 16 GB or more.
    Choose it in the list and the button turns into **Download this quality (8.2 GB)**; after
    that it is one more entry in the list.
- **Output size**: 2×, 3×, 4×, or **Print**, which computes the pixels your print width needs at
  the chosen dpi (set the width in the Export card).
- Press **Restore image**. Large results are worked in pieces, so the progress counts up; a
  1200 px photo to 4× takes a few minutes on an RTX 3060, longer on smaller cards. If ComfyUI
  runs out of graphics memory Eleva Studio retries once in a low-memory mode (smaller pieces),
  which is slower but usually succeeds.
- The result is a normal step in the history: you can undo it, remove the background, pick a
  background, and export it with the DTF or print options like any other image.

## Problems

- **"ComfyUI was not found on this computer"**: start ComfyUI, wait until its window has
  loaded, press **Check again**. If you changed ComfyUI's port, type the new address under
  "ComfyUI address (advanced)".
- **"This ComfyUI is too old for Restore"**: update ComfyUI (in the desktop app: Help → Check
  for updates), restart it, press **Check again**.
- **The download stops or fails**: press **Download** again; it continues from where it
  stopped. Check the free disk space if it keeps failing.
- **"The component is in place, but ComfyUI does not list it yet"**: restart ComfyUI and press
  **Check again**.
- **Still out of memory after the retry**: use *Standard* quality or a smaller output size, and
  close other programs that use the graphics card.

## Other setups

- **ComfyUI on another computer.** Eleva Studio can use a ComfyUI on your network (type its
  address under "ComfyUI address (advanced)"), but it cannot download into it. Put these files
  from [Comfy-Org/SeedVR2](https://huggingface.co/Comfy-Org/SeedVR2) there yourself:
  `seedvr2_3b_fp8_e4m3fn.safetensors` in `ComfyUI/models/diffusion_models` and
  `seedvr2_ema_vae_fp16.safetensors` in `ComfyUI/models/vae`.
- **You already have SeedVR2 files.** Any SeedVR2 model in `models/diffusion_models` shows up
  in the Quality list under its own name, as long as the VAE file above is in `models/vae`.
- **Installs set up for an earlier Eleva Studio** (the *ComfyUI-SeedVR2_VideoUpscaler* and
  *SeedVR2 Tiling Upscaler* add-ons) keep working as before. To move to the built-in route,
  choose *Standard · download* in the Quality list and press the button; after that the add-ons
  are no longer needed.
