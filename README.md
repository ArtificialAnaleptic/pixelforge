# ▓▒░ Pixel Forge Suite
A browser-based suite of pixel art tools — drop an image, pick your settings, and export.
---
## Inspiration
This project originally started as a fork of **[Sora's Pixel Converter](https://pixel-converter.ameniwa.com/)** by [@ameniwa](https://x.com/ameniwa_), which is a genuinely wonderful tool and absolutely worth your time. It's beautifully designed, has a charming Win95-era UI, a mascot character who talks to you, dialog box overlays, and some effects (like animated dithering and afterimage) that go beyond what's in this repo.
**Please go use the original. It's great.**
The suite now also includes a recreation of the **[GB Dot Converter](https://deepblizzard.itch.io/gb-dot-converter)** by DeepBlizzard ([@mao_DBmiyuki](https://x.com/mao_DBmiyuki)). This tool allows for highly customizable conversion of images specifically into the classic 4-color Game Boy palette. I highly recommend checking out DeepBlizzard's original work and their other tools on Itch.io!
The reason this project exists is simple: I love these tools and want to use them a **LOT**. But I'd rather not be dependent on whether a third-party site happens to be online when I need it. Since the whole thing runs in the browser anyway and no data ever leaves your machine, a local copy makes sense. This is that.
> ⚠️ **Note on removed features:** The original Pixel Converter site includes video export with animated effects (dithering, ghost/afterimage trails). These were removed from the Pixel Forge tool here for the sake of simplicity — the effect implementations didn't translate cleanly without being able to see and tune them interactively. If you want those features, [use the original](https://pixel-converter.ameniwa.com/).
---
## Usage
No install. No server. No dependencies.
1. Download `index.html`
2. Open it in any modern browser
3. Select a tool from the Home Screen or upper-left App Switcher menu
4. Drop, click, or paste (`Ctrl+V`) an image
That's it.
Or you can access it directly on github but that sort of defeats the point of the whole endeavour:
https://artificialanaleptic.github.io/pixelforge/
---
## Tools Included
### 🎨 Pixel Forge
A general-purpose pixel art converter.
- **4 pixel sizes** — 2px through 5px dot grids
- **20 palettes** across four categories: Game Boy, NES, Vaporwave, Earth, etc.
- **3 combinable effects** — Glitch, CRT scanlines, Hue Cycle
- **Brightness / Contrast / Saturation** sliders
- **PNG export** — clean 2× upscaled dot grid, no effects baked in
- **Video export** — WebM capture of the live canvas including active effects
- **Keyboard shortcuts** — `1–4` pixel size, `G` glitch, `C` CRT, `X` cycle, `Ctrl+S` save
- **Paste support** — `Ctrl+V` an image from anywhere
### 🟩 GB Dot Converter
A specialized tool for converting photos and illustrations into Game Boy-compatible pixel art.
- **Crop / Resize** — Custom pan, zoom, and aspect ratios
- **Photo Pre-Correction** — Live brightness, contrast, gamma, and blur adjustments
- **Quantize / Dither** — Bayer 4x4, Floyd-Steinberg, or solid thresholding
- **GB Studio Validation** — Checks the final output against GB Studio's strict grid rules (8x8 tiles, max 192 unique tiles)
- **Export Options** — Save as Game Boy standard PNG, upscaled PNG for social media, or GB Paint JSON
---
## How it works
1. The source image is downsampled to a tiny dot-grid canvas (e.g. ~350 dots wide at 2px) using the browser's built-in bicubic averaging.
2. Each dot's colour is mapped to the nearest colour in the selected palette using **CIE Lab** distance — perceptually accurate, not just RGB math.
3. The dot grid is drawn to the display at container size using nearest-neighbour scaling (`imageSmoothingEnabled = false`), keeping pixels crisp and avoiding moiré banding (**NOTE: some browser rendering produces banding, check the export and it probably isn't there, just in the browser.**).
4. Everything happens entirely client-side — your images never leave your browser.
---
## Credit
*   **Pixel Forge** original concept, design, and implementation: **[Sora's Pixel Converter](https://pixel-converter.ameniwa.com/)** by Ameniwa. [More: lit.link/ameniwa](https://lit.link/ameniwa)
*   **GB Dot Converter** original concept, design, and implementation: **[GB Dot Converter](https://deepblizzard.itch.io/gb-dot-converter)** by DeepBlizzard (@mao_DBmiyuki).
Go see their work! This repo wouldn't exist without them.
