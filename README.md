# am-assets

AM Consulting brand assets and shared CSS, served over a CDN so every page references
one hosted copy instead of embedding images and re-declaring the same 200 lines of CSS.

**Consume it via jsDelivr, always pinned to a tag:**

```
https://cdn.jsdelivr.net/gh/am-consultingai/am-assets@v2/<path>
```

---

## Contents

```
brand.css                     tokens, base type, shared components
brand-tokens.json             source of truth for colours, fonts, identity
logo/
  am-logo.png                 master, 2528 × 683 RGBA — blue wordmark
  am-logo-600.png             600 × 162, blue — for light backgrounds
  am-logo-white.png           master, 2243 × 605 RGBA — white Daytona variant
  am-logo-white-600.png       600 × 162, white — web default on dark nav bars
  am-favicon.png              128 × 128, the rook mark
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
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/am-consultingai/am-assets@v2/brand.css">
  <link rel="icon" href="https://cdn.jsdelivr.net/gh/am-consultingai/am-assets@v2/logo/am-favicon.png">
</head>
```

Nav logo — on the dark brand background, use the **white** variant:

```html
<img class="nav-logo"
     src="https://cdn.jsdelivr.net/gh/am-consultingai/am-assets@v2/logo/am-logo-white-600.png"
     alt="AM Consulting">
```

Avatar:

```html
<img class="av" width="200" height="200"
     src="https://cdn.jsdelivr.net/gh/am-consultingai/am-assets@v2/portrait/avishay-200.png"
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
- **Always pin a tag** in consuming pages. `@v2` is immutable and cached permanently at
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
Text          #f3f4f6 primary · #cbd5e1 / #94a3b8 / #64748b secondary
Accent        #22d3ee cyan · #38bdf8 sky · #818cf8 indigo
Gradient      linear-gradient(to right, #22d3ee, #38bdf8, #818cf8)
Status        #10b981 good · #ef4444 bad

Display       Space Grotesk  400,500,600,700
Body          Inter          300,400,500,600,700
Mono/labels   JetBrains Mono 400,500,600
```

**Convention:** uppercase, letter-spaced JetBrains Mono for eyebrows and metric captions;
Space Grotesk for headlines; Inter for paragraphs.

**Logo usage:** sits on dark backgrounds, keep the transparent padding, never place it on
busy imagery. On dark, reach for the white variant — the blue wordmark does not carry
enough contrast against `--bg` or `--deep`.

**Tagline:** *"The model is rarely the hard part — the system around it is."*

**Identity:** Avishay Meron, CEO & Founder, AM Consulting ·
[amconsultingai.com](https://www.amconsultingai.com) · office@amconsultingai.com ·
[LinkedIn](https://www.linkedin.com/in/avishay-meron/)

**Credentials:** 10+ AI patents · 10+ years taming AI · CEO & Founder, AM Consulting

**Tone:** confident, technical, no-hype. Peer-to-peer with senior engineers and
architects. Concrete numbers over buzzwords.
