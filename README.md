# Kaleb & Co. — Brand Asset Library

Hosted, versioned image assets for the *Riso Pop on Newsprint* system: torn-paper
dividers and hand-brush underlines. These are alpha silhouettes recolored to the
canonical brand tokens, so they stay crisp at any width and match the palette exactly.

**Why this repo exists:** one maintained home for the assets, with stable public URLs.
The site's CSS points here — so if the site ever moves off Squarespace, nothing about
these assets changes. Update a file here, every surface that uses it updates.

> This repo is **just image files**. It is not connected to Squarespace developer mode
> or any template sync. It's a plain public repo served over a CDN.

## Naming convention

```
hk-{type}--{color}[--{modifier}].png
```

- **type** — `torn`, `brush`
- **color** — a semantic brand token (not a hex): `white`, `newsprint`, `panel-dark`,
  `teal`, `persimmon`, `gold`, `teal-lifted`, `persimmon-lifted`
- **modifier** — optional (e.g. a future `shadow` depth version). Flip is handled in CSS.

Color names are semantic on purpose: if a token's hex is ever adjusted, the filename
stays valid and the file is simply re-cut. `manifest.json` is the source of truth
(token → hex → file → dimensions), mirroring `tokens.json`.

## Hosting / URLs

Served via **jsDelivr** (free CDN, no config beyond a public repo):

```
https://cdn.jsdelivr.net/gh/USERNAME/brand-assets@main/hk-brush--teal.png
```

Alternative: enable **GitHub Pages** for instant-update URLs
(`https://USERNAME.github.io/brand-assets/…`). Do **not** hotlink raw
`githubusercontent.com` URLs — that endpoint is throttled and not a real CDN.

## Use in CSS

Paste `hk-assets.css` (or fold it into your site CSS). Then:

```html
<!-- torn divider at the bottom of a newsprint section -->
<div class="hk-torn hk-torn--newsprint"></div>

<!-- brush underline under a word, in persimmon -->
<span class="hk-brush hk-brush--persimmon">trust it.</span>
```

Default torn is white; default brush is teal. Add a modifier class to switch color.

## Adding a variant

1. Recolor the silhouette to the new token (keep the alpha channel, change RGB only).
2. Save as `hk-{type}--{color}.png`.
3. Add a `--hk-{type}-{color}` variable + modifier class in `hk-assets.css`.
4. Add the entry to `manifest.json`.

## Source / license

Silhouettes are derived from the project's hand-made torn-paper and brush masters.
Internal brand assets for Kaleb & Co. Not for third-party redistribution.
