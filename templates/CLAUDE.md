# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

MLS Law — demo law firm site (Paris) produced by Yamen Global via the YOR workflow. Single-file static site deployed on Vercel. No build step, no package manager, no framework.

## Deployment

- Open `index.html` directly in a browser to preview locally
- **Vercel config**: `vercel.json` — sets security headers only (`X-Content-Type-Options`, `X-Frame-Options`, `Referrer-Policy`)
- No build command required; output is the repo root

## Architecture

Everything lives in `index.html` — styles, markup, and JS are co-located in one file:

1. **CSS custom properties** (`:root`) — full design token system using `oklch()` color space. All colors must use these tokens; never hardcode hex/rgb.
2. **Sections** (in order): intro overlay → nav → hero → band (marquee) → expertise → approche → chiffres → secteurs → contact → footer
3. **Vanilla JS** (bottom of `<body>`): no libraries. Modules:
   - Intro overlay (timed fade, 1400ms)
   - Custom cursor (rAF lerp loop — dot + ring)
   - Scroll progress bar
   - Animated canvas background (`lines` / `dots` modes, togglable via Tweaks panel)
   - Nav scroll-spy + sticky shrink on scroll > 60px
   - Hero parallax (passive scroll, `will-change: transform` on `.hero-img-frame`)
   - Scroll reveals via `IntersectionObserver` (`.reveal`, `.reveal-clip → .visible`)
   - Animated counters (easeOutCubic, triggers once on viewport entry)
   - Magnetic buttons (mousemove offset on `.btn-dark`, `.nav-cta`)
   - **Tweaks panel** — hidden dev panel, activated by `postMessage({ type: '__activate_edit_mode' })`. Exposes accent color picker, hero background selector, canvas animation switcher.

## Design tokens

```
--white / --off / --green-xl / --green-l / --grey   backgrounds
--mid                                                 secondary text
--green / --green-d / --ink                          primary text & nav
--gold / --gold-l / --gold-f / --gold-line           accent (oklch 62% 0.10 82)
```

## Animation rules

- GPU-composited only: `transform` + `opacity`. Never animate `width`, `height`, `top`, `left`.
- All reveals: `IntersectionObserver`, threshold `0.1`, unobserve after trigger.
- Parallax: passive scroll listener + direct style mutation (no rAF needed here).
- Custom cursor: rAF lerp loop — do not replace with CSS transitions.

## Images

Stored in `uploads/`. Three photos used (hero, approche, contact) — `object-fit: cover`, absolutely positioned within their containers.

## Typography

- `Cormorant Garamond` (300–600, italic) — Google Fonts — all headings
- `DM Sans` (300–500) — Google Fonts — body, UI, buttons

## Adapting for a new client

1. Replace `--gold` value in `:root` (or use Tweaks panel at runtime)
2. Update firm name, attorney name, address, phone, email throughout the HTML
3. Swap images in `uploads/`
4. Update `<title>`, meta description, and JSON-LD if present
