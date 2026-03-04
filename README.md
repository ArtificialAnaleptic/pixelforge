# ▓▒░ Pixel Forge

A browser-based pixel art converter — drop an image, pick a palette, export.

---

## Inspiration

This project exists entirely because of **[Sora's Pixel Converter](https://pixel-converter.ameniwa.com/)** by [@ameniwa](https://x.com/ameniwa_), which is a genuinely wonderful tool and absolutely worth your time. It's beautifully designed, has a charming Win95-era UI, a mascot character who talks to you, dialog box overlays, and some effects (like animated dithering and afterimage) that go beyond what's in this repo.

**Please go use the original. It's great.**

The reason this fork exists is simple: I love Sora's Pixel Converter and want to use it a **LOT** — and I'd rather not be dependent on whether a third-party site happens to be online when I need it. Since the whole thing runs in the browser anyway and no data ever leaves your machine, a local copy makes sense. This is that.

> ⚠️ **Note on removed features:** The original site includes video export with animated effects (dithering, ghost/afterimage trails). These were removed here for the sake of simplicity — the effect implementations didn't translate cleanly without being able to see and tune them interactively. If you want those features, [use the original](https://pixel-converter.ameniwa.com/).

---

## Usage

No install. No server. No dependencies.

1. Download `index.html`
2. Open it in any modern browser
3. Drop, click, or paste (`Ctrl+V`) an image

That's it.

Or you can access it directly on the github but that sort of defeats the point of the whole endeavour:

https://artificialanaleptic.github.io/pixelforge/

---

## Features

- **4 pixel sizes** — 2px through 5px dot grids
- **20 palettes** across four categories:
  - *Retro Hardware* — Game Boy, NES, CGA, C64, PICO-8
  - *Community Classics* — Sora, DawnBringer 16, Sweetie 16, Endesga 32, Apollo
  - *Mood & Aesthetic* — Vaporwave, Cyber, Horror, Sunset, Sakura
  - *Natural & Tonal* — Ocean, Earth, Arctic, Autumn, Mono
- **3 combinable effects** — Glitch, CRT scanlines, Hue Cycle
- **Brightness / Contrast / Saturation** sliders
- **PNG export** — clean 2× upscaled dot grid, no effects baked in
- **Copy to clipboard** — paste directly into other apps
- **Video export** — WebM capture of the live canvas including active effects
- **Keyboard shortcuts** — `1–4` pixel size, `G` glitch, `C` CRT, `X` cycle, `Ctrl+S` save
- **Paste support** — `Ctrl+V` an image from anywhere
- Entirely client-side — images never leave your browser

---

## How it works

1. The source image is downsampled to a tiny dot-grid canvas (e.g. ~350 dots wide at 2px) using the browser's built-in bicubic averaging
2. Each dot's colour is mapped to the nearest colour in the selected palette using **CIE Lab** distance — perceptually accurate, not just RGB math
3. The dot grid is drawn to the display at container size using nearest-neighbour scaling (`imageSmoothingEnabled = false`), keeping pixels crisp and avoiding moiré banding (**NOTE: some browser rendering produces banding, check the export and it probably isn't there, just in the browser.**)

---

## Credit

Original concept, design, and implementation: **[Sora's Pixel Converter](https://pixel-converter.ameniwa.com/)** by Ameniwa.  
Go see their work. This repo wouldn't exist without it: More: https://lit.link/ameniwa
