# Turning Point Studio — Brand Identity Guide

**Version:** v2.0 · 2026-06-03
**Status:** canonical for the electric-utility / EA site. Supersedes the v1 paper/Fraunces aesthetic still live on `index.html` and `community.html`, and the v1.0 geometric-arc mark direction.
**Owner:** Mira Tanaka (Web/Digital Director)

This guide codifies the visual identity for the engineering audience: electric-utility solution architects and enterprise architects. The brief is credibility through high contrast and restraint, not warmth. Everything here is build-first-safe — positioning and craft, not selling.

## The look in one line

High-contrast IDE-dark. The real hand-brushed ensō — the studio's actual logo mark — rendered light on true dark, paired with a monospaced wordmark. It should read like a confident technical document, not a wellness brand. The mark carries the studio's heritage; the dark surface, mono type, and cool accent carry the engineering credibility.

## The mark — real brush ensō

The mark is the studio's existing hand-brushed sumi ensō, taken from the original logo artwork (`TPS Cover.png`), not a redrawn geometric ring. Its character lives in the brush texture, the dry-brush striations, the double-contour where the bristles split, and the overlap where the stroke closes at the lower right. That texture is the brand — do not smooth it into a clean vector circle, and do not reduce it to a thin even-weight arc.

For the dark site the ink is recolored to light (`--text`, `#e6edf3`) so it reads at full contrast on `--bg`; the original ink version is preserved for light surfaces. Because the texture must survive, the mark ships as a high-resolution transparent **PNG**, not an SVG. `enso-mark.png` is the light mark on transparent; `enso-mark-dark.png` is the ink version for light backgrounds.

Rules: always high contrast (light mark on true dark, or ink on paper) — never a muted mid-tone, never terracotta, never on a low-contrast surface. Keep the brush texture. Don't outline, fill, or recolor it to an accent hue.

## Wordmark

The wordmark is monospaced — **JetBrains Mono** on the web (falling back to `'Fira Code', ui-monospace, Menlo, monospace`). "Turning Point" is set in `--text`; "Studio" in the cool accent `--cool`. This is deliberately *not* the inscriptional serif from the original stacked logo and *not* an italic warm treatment — the serif/paper lockup belongs to the studio's heritage/woodworking identity; the electric-utility site speaks in the engineering register. `wordmark-lockup.png` carries the horizontal mark-plus-wordmark arrangement for docs, decks, and email; in HTML, build the lockup live (mark `<img>` + mono text) so it inherits page fonts.

Per the founder-obfuscation rule, the mark and wordmark are the brand's public face — no personal name, no founder bio. The studio is the entity.

## Color tokens

Mirror `sku/styles.css`. Use the variable names verbatim when extending the CSS.

| Token | Hex | Role |
|---|---|---|
| `--bg` | `#0d1117` | Page background (GitHub-dark) |
| `--surface` | `#161b22` | Cards, header, the favicon tile |
| `--surface-2` | `#1c2128` | Nested surfaces |
| `--rule` | `#30363d` | Borders / dividers |
| `--rule-soft` | `#21262d` | Subtle dividers |
| `--text` | `#e6edf3` | Primary text, headings, **the mark** |
| `--text-2` | `#b1bac4` | Body / secondary |
| `--muted` | `#7d8590` | Captions, eyebrows, breadcrumbs |
| `--cool` | `#58a6ff` | Primary action / links / "Studio" accent |
| `--cool-bright` | `#79c0ff` | Brighter cool for large display text |
| `--ok` | `#3fb950` | Success / green-light status |
| `--warn` | `#d29922` | Caution / yellow-light status |

Terracotta is retired from this site's palette. It read as warmth/wellness and worked against the engineering signal. The single accent is the cool blue. (Terracotta and warmth remain available to the studio's heritage/woodworking identity, which is a separate brand.)

## Typography & register

Headings and machine text (nav, breadcrumbs, SKU IDs, the draft banner) are **JetBrains Mono** (500). Body is **Inter** (300–600). Two register conventions carry the engineering voice: section headings and eyebrows are prefixed `// ` (code-comment), and the wordmark and command-like callouts such as the footer domain are prefixed `$ ` (shell prompt).

## Wiring the favicon + social card

Add to the `<head>` of every page (paths assume root pages referencing `brand/`):

```html
<link rel="icon" type="image/png" sizes="32x32" href="/brand/favicon-32.png">
<link rel="alternate icon" href="/brand/favicon.ico">
<link rel="apple-touch-icon" href="/brand/apple-touch-icon.png">
<meta property="og:title" content="Turning Point Studio">
<meta property="og:description" content="Reference architectures and NERC CIP-aware compliance patterns for the electric utility industry.">
<meta property="og:image" content="https://turningpointstudio.net/brand/og-image.png">
<meta property="og:url" content="https://turningpointstudio.net">
<meta property="og:type" content="website">
<meta name="twitter:card" content="summary_large_image">
```

## Asset inventory

`enso-mark.png` (light brush mark, transparent) · `enso-mark-dark.png` (ink mark for light surfaces) · `favicon.ico` (16/32/48) · `favicon-32.png` · `apple-touch-icon.png` (180) · `icon-512.png` (PWA/large) · `og-image.png` (1200×630 social card) · `wordmark-lockup.png` (horizontal lockup) · `mark-directions.png` (the rejected exploration sheet, kept for the record) · this guide.

Source artwork: `../TPS Cover.png` (the original stacked logo). Keep it — every raster asset here derives from it.

## Open reconciliation — the homepage is still v1

`index.html` and `community.html` were never moved off the original Fraunces/paper aesthetic, so dark technical SKU pages currently hang off a light homepage. Recommended next step: reskin those two pages onto this token system (lift `sku/styles.css` to a shared root stylesheet, place the ensō-plus-mono lockup in the header, wire the favicon/OG head block above). Pure visual work — no copy or positioning changes, so it stays clear of the unresolved audience/funnel questions and the build-first gate.

## Production note

The mark and layout in `og-image.png` and `wordmark-lockup.png` are exact. Their wordmark text was rasterized with DejaVu Sans Mono as a stand-in because JetBrains Mono wasn't available in the build environment — only the social-card letterforms differ slightly from the live site's JetBrains Mono. Regenerate with JetBrains Mono installed for a perfect match; the build script is reusable.
