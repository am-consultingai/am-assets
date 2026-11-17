# am-assets

AM Consulting brand assets and shared CSS, served over a CDN so every page references
one hosted copy instead of embedding images and re-declaring the same 200 lines of CSS.

**Consume it via jsDelivr, always pinned to a tag:**

```
https://cdn.jsdelivr.net/gh/am-consultingai/am-assets@v3/<path>
```

---

## Contents

```
brand.css                     tokens, base type, shared components
brand-tokens.json             source of truth for colours, fonts, identity
logo/
  rook-tilt.svg               tilted rook mark, vector, transparent — PRIMARY mark (v3)
  rook-tilt-dark.svg          same mark on its own dark field
  rook-tilt.png               master, 1198 × 2048 RGBA
  rook-tilt-512.png           299 × 512
  rook-tilt-256.png           150 × 256 — email and documents
  rook-tilt-128.png           75 × 128
  favicon/                    favicon.svg, favicon.ico, favicon-16/32/48x48.png,
                              apple-touch-icon.png (180), icon-192.png, icon-512.png
  am-logo.png                 legacy: master, 2528 × 683 RGBA — blue wordmark (older rook)
  am-logo-600.png             legacy: 600 × 162, blue — for light backgrounds
  am-logo-white.png           legacy: master, 2243 × 605 RGBA — white Daytona variant
  am-logo-white-600.png       legacy: 600 × 162, white — raster lockup on dark
  am-favicon.png              legacy: 128 × 128, the older rook
portrait/
  avishay.png                 master, 2208 × 1952
  avishay-400.png             400 × 400, bio blocks and speaker cards
  avishay-200.png             200 × 200, web default for small avatars
misc/
  rook-blue-network.png       371 × 666, decorative texture
```

Masters are committed alongside the resized versions — masters for print and future
crops, resized ones for pages to reference.

---

## Usage

```html
<head>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Space+Grotesk:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500;600&display=swap">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/am-consultingai/am-assets@v3/brand.css">
  <link rel="icon" type="image/svg+xml" href="https://cdn.jsdelivr.net/gh/am-consultingai/am-assets@v3/logo/favicon/favicon.svg">
  <link rel="icon" sizes="32x32" href="https://cdn.jsdelivr.net/gh/am-consultingai/am-assets@v3/logo/favicon/favicon-32x32.png">
  <link rel="apple-touch-icon" href="https://cdn.jsdelivr.net/gh/am-consultingai/am-assets@v3/logo/favicon/apple-touch-icon.png">
</head>
```

Nav logo — the tilted rook mark plus a live-text wordmark (crisp at any size, and the
text inherits the page's contrast):

```html
<a class="wordmark" href="/">
  <img class="nav-mark" src="https://cdn.jsdelivr.net/gh/am-consultingai/am-assets@v3/logo/rook-tilt.svg" alt="">
  <span class="nm">AM Consulting</span>
</a>
```

The SVG is about 435 KB (a detailed network mesh with glow filters). Use it at nav and
hero sizes on web pages; use `rook-tilt-256.png` in email and documents.

Avatar:

```html
<img class="av" width="200" height="200"
     src="https://cdn.jsdelivr.net/gh/am-consultingai/am-assets@v3/portrait/avishay-200.png"
     alt="Avishay Meron">
```

The font import must come **before** `brand.css`. Load the fonts even if you only use
some of the CSS — the tokens name the families but do not fetch them.

---

## Rules

- **No Git LFS.** jsDelivr and raw GitHub serve the LFS *pointer file* rather than the
  image, so every `<img>` silently breaks. Plain committed binaries only.
- **Brand-level assets only.** No per-page imagery — hero shots, screenshots, diagrams
  for individual workshop pages. Those belong with their page. This repo stays small
  precisely because it changes about once a year; per-page assets would grow it without
  bound and Git would become the wrong tool fast.
- **No client material, ever.** If an asset names a customer, it belongs with that page.
  This repo is public; only the client pages are sensitive, and keeping them apart is
  what makes public hosting safe here.
- **Always pin a tag** in consuming pages. `@v3` is immutable and cached permanently at
  the edge. `@main` is cached for hours and produces the classic "I updated the logo and
  half my pages still show the old one".
- **Cut a new tag on change**, so pages opt in deliberately rather than changing
  underneath. Bump the tag in a page when you want the new asset.

## Fallback

GitHub Pages serves the same files if jsDelivr is ever unavailable:

```
https://am-consultingai.github.io/am-assets/logo/am-logo-white-600.png
```

---

## Brand quick reference

Full values live in `brand-tokens.json`; `brand.css` exposes them as CSS custom properties.

```
Backgrounds   #0b0f19 base · #070b13 deep · #0d1321 card · #0b101c tile
Text          #f3f4f6 primary · #dde4ee / #b9c4d3 / #9aa6b8 secondary (15.0 / 10.9 / 7.8 : 1 on --bg)
Accent        #22d3ee cyan · #38bdf8 sky · #818cf8 indigo
Gradient      linear-gradient(to right, #22d3ee, #38bdf8, #818cf8)
Status        #10b981 good · #ef4444 bad

Display       Space Grotesk  400,500,600,700
Body          Inter          300,400,500,600,700
Mono/labels   JetBrains Mono 400,500,600
```

**Convention:** uppercase, letter-spaced JetBrains Mono for eyebrows and metric captions;
Space Grotesk for headlines; Inter for paragraphs.

**Logo usage:** the tilted rook (`logo/rook-tilt.svg`) is the primary mark. It sits on dark
backgrounds; keep the transparent padding and never place it on busy imagery. The older
raster wordmarks are legacy — if you must use one on dark, use the white variant.

**Contrast and size (v3):** every text colour at 4.5:1 or better against its background;
never #334155 or darker for text. Mono labels and eyebrows 12px minimum, secondary body
text 14px minimum, body weight 400 (Inter Light at 300 reads too thin on the dark
background). No letter-spacing on Hebrew or other non-Latin text.

**Tagline:** *"The model is rarely the hard part — the system around it is."*

**Identity:** Avishay Meron, CEO & Founder, AM Consulting ·
[amconsultingai.com](https://www.amconsultingai.com) · office@amconsultingai.com ·
[LinkedIn](https://www.linkedin.com/in/avishay-meron/)

**Credentials:** 10+ AI patents · 10+ years taming AI · CEO & Founder, AM Consulting

**Tone:** confident, technical, no-hype. Peer-to-peer with senior engineers and
architects. Concrete numbers over buzzwords.
