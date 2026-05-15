# LOVABLE — PRÉPARATION PHASE SEO / CLAUDE CODE
# Une Semaine Sur Deux · Pre-handoff optimization
# Objectif : rendre le codebase propre, structuré et prêt
# pour la phase Claude Code (SEO technique + PageSpeed)

---

The next step after Lovable is Claude Code, which will handle
all technical SEO, performance optimization, and Google Search
Console setup. Your job here is to prepare the cleanest possible
handoff. Claude Code cannot fix what Lovable never built correctly.

Do not change any design, colors, animations, or copy.
Only improve the technical structure.

---

## 1. HTML SEMANTICS — Structure every page correctly

For each of the 5 routes (/ · /menu · /chef · /galerie · /reserver):

### Heading hierarchy
- Verify exactly ONE `<h1>` per page — no more, no less
- Verify all section titles use `<h2>` (not `<div>` with large font)
- Verify sub-items within sections use `<h3>`
- Never skip levels: h1 → h2 → h3, no jumps
- The h1 on the homepage MUST contain the words "Grenoble" and "restaurant"

### Semantic HTML elements
Replace any `<div>` used as a structural landmark with the correct element:
- Site header → `<header>`
- Main navigation → `<nav aria-label="Navigation principale">`
- Main content area → `<main>`
- Each page section → `<section aria-labelledby="[section-h2-id]">`
- Footer → `<footer>`
- The menu items list → `<ul>` + `<li>`
- Address information → `<address>`

### `<head>` completeness — verify each page has:
```html
<html lang="fr">
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#1C1814">
<title>[Unique title per page]</title>
<meta name="description" content="[Unique description, 120–155 chars]">
<link rel="canonical" href="https://[domain]/[path]">
<meta property="og:title" content="...">
<meta property="og:description" content="...">
<meta property="og:type" content="website">
<meta property="og:image" content="...">
<meta name="twitter:card" content="summary_large_image">
```

---

## 2. JSON-LD — Verify and complete the Restaurant schema

The JSON-LD must be in the `<head>` of index.html (not in a React component).
Verify it matches this structure exactly:

```json
{
  "@context": "https://schema.org",
  "@type": "Restaurant",
  "name": "Une Semaine Sur Deux",
  "description": "Restaurant bistronomique à Grenoble. Cuisine faite maison, produits frais en circuit court. Toque Gault & Millau 2026.",
  "url": "https://[DOMAIN]/",
  "telephone": "+33476271375",
  "email": "restaurant1sur2@gmail.com",
  "servesCuisine": ["French", "Bistronomique"],
  "priceRange": "€€",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "4 Place Championnet",
    "addressLocality": "Grenoble",
    "postalCode": "38000",
    "addressCountry": "FR"
  },
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": 45.1857,
    "longitude": 5.7224
  },
  "openingHoursSpecification": [
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Monday","Tuesday","Wednesday","Thursday","Friday","Saturday","Sunday"],
      "opens": "12:00",
      "closes": "14:00"
    },
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Monday","Tuesday","Wednesday","Thursday","Friday","Saturday","Sunday"],
      "opens": "19:00",
      "closes": "21:30"
    }
  ],
  "sameAs": [
    "https://www.instagram.com/1semainesur2restaurant/",
    "https://www.facebook.com/1sur2grenoble/"
  ],
  "award": "Table Gourmande · Gault & Millau 2026"
}
```

If any field is missing, add it. If the JSON is malformed, fix it.

---

## 3. IMAGE OPTIMIZATION — Prepare for Claude Code webp conversion

Claude Code will convert all images to `.webp` after export.
Prepare the codebase so this conversion is seamless:

### Every `<img>` must have:
- `alt="[descriptive text in French]"` — non-empty, descriptive
- `width` and `height` attributes matching the intrinsic dimensions — prevents CLS
- `loading="lazy"` on all images except the first visible one per page
- `loading="eager"` + `fetchPriority="high"` on the first visible image per page (LCP)
- `decoding="async"` on all lazy images

### Expected alt attributes per photo:
| File | Alt text |
|---|---|
| photo-saint-jacques.jpg | "Saint-Jacques, riz noir vénéré et moule — Une Semaine Sur Deux" |
| photo-pavlova.jpg | "Pavlova mangue et sphères glacées — Une Semaine Sur Deux Grenoble" |
| photo-surf-turf.jpg | "Plat viande et homard sauce crémée — restaurant Une Semaine Sur Deux" |
| photo-menu-poulpe.jpg | "Menu et poulpe signature du Chef Pierrick Vasseur" |
| photo-volaille.jpg | "Volaille aux champignons sauce crémée — bistronomie Grenoble" |
| photo-poisson.jpg | "Truite aux légumes frais de saison — Une Semaine Sur Deux" |
| photo-legumes.jpg | "Légumes du marché et champignons — cuisine de saison Grenoble" |
| photo-gaultmillau.jpg | "Plaque Table Gourmande Gault & Millau 2026 — Une Semaine Sur Deux" |

### Add `<picture>` wrapper ready for webp:
Wrap each `<img>` in a `<picture>` element with a `.webp` source:
```html
<picture>
  <source srcSet="/src/assets/photos/photo-saint-jacques.webp" type="image/webp" />
  <img
    src="/src/assets/photos/photo-saint-jacques.jpg"
    alt="Saint-Jacques, riz noir vénéré et moule — Une Semaine Sur Deux"
    width="1080"
    height="1080"
    loading="lazy"
    decoding="async"
  />
</picture>
```
Claude Code will generate the `.webp` files. The `<source>` tag is ready to use the moment they exist.

---

## 4. ROUTING — Verify React Router is production-ready

- All internal `<a href="/...">` must be `<Link to="/...">` from React Router
- Add a `/404` catch-all route that renders a simple 404 page with:
  - H1: "Page introuvable"
  - Body: "La page que vous cherchez n'existe pas."
  - Link back to homepage: "Retour à l'accueil"
- Verify `vercel.json` exists at the root with the SPA rewrite:
```json
{
  "rewrites": [{ "source": "/(.*)", "destination": "/index.html" }]
}
```
If `vercel.json` is missing, create it.

---

## 5. SITEMAP — Create or verify `/public/sitemap.xml`

Create `/public/sitemap.xml` with all 5 routes:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://[DOMAIN]/</loc>
    <lastmod>2026-04-29</lastmod>
    <changefreq>monthly</changefreq>
    <priority>1.0</priority>
  </url>
  <url>
    <loc>https://[DOMAIN]/menu</loc>
    <lastmod>2026-04-29</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.9</priority>
  </url>
  <url>
    <loc>https://[DOMAIN]/chef</loc>
    <lastmod>2026-04-29</lastmod>
    <changefreq>yearly</changefreq>
    <priority>0.7</priority>
  </url>
  <url>
    <loc>https://[DOMAIN]/galerie</loc>
    <lastmod>2026-04-29</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.6</priority>
  </url>
  <url>
    <loc>https://[DOMAIN]/reserver</loc>
    <lastmod>2026-04-29</lastmod>
    <changefreq>yearly</changefreq>
    <priority>0.8</priority>
  </url>
</urlset>
```
Replace `[DOMAIN]` with the placeholder `restaurant1sur2.fr` — Claude Code will update it after deployment.

---

## 6. ROBOTS.TXT — Create `/public/robots.txt`

```
User-agent: *
Allow: /

Sitemap: https://restaurant1sur2.fr/sitemap.xml
```

If it already exists, verify it does NOT contain any `Disallow` lines that block crawlers.

---

## 7. PERFORMANCE — Remove everything that slows the build

### Google Fonts
- Confirm zero `@import url('https://fonts.googleapis.com/...')` in any CSS file
- Confirm zero `<link href="https://fonts.googleapis.com/...">` in index.html
- Confirm `font-display: swap` is set on every `@font-face` declaration

### Framer Motion tree-shaking
Verify all Framer Motion imports are named (not wildcard):
```tsx
// ✅ correct
import { motion, useScroll, useTransform } from 'framer-motion'

// ❌ wrong — imports entire library
import * as motion from 'framer-motion'
```

### Dead code
- Remove any `console.log`, `console.warn`, `console.error` from production code
- Remove any commented-out code blocks (<!-- --> or // blocks)
- Remove any unused imports at the top of components

### `will-change` — use sparingly
Audit all CSS and Tailwind classes. Remove `will-change` from any element that is:
- Not currently being animated
- A static container

Keep `will-change: transform` only on elements with active Framer Motion animations.

---

## 8. ACCESSIBILITY — Minimum viable score

- Every Lucide-React icon used decoratively: add `aria-hidden="true"`
- Every Lucide-React icon that conveys meaning: add `aria-label="[description]"`
- Every button with only an icon: add `aria-label="[action]"`
- The mobile hamburger button: `aria-label="Ouvrir le menu"` when closed, `aria-label="Fermer le menu"` when open
- All interactive elements must have visible `:focus-visible` styles — do not remove the outline without adding a replacement
- Verify the color contrast of muted text (#8A7A6A on #1C1814):
  If contrast ratio < 3:1, lighten #8A7A6A to #9A8A7A

---

## 9. META TITLES AND DESCRIPTIONS — Unique per page

Set these exactly:

**Homepage /**
- Title: `Restaurant Une Semaine Sur Deux à Grenoble — Cuisine Bistronomique · Gault & Millau 2026`
- Description: `Restaurant bistronomique à Grenoble. Produits frais, circuit court, cuisine faite maison. Toque Gault & Millau 2026. Chef Pierrick Vasseur. ☎ 04 76 27 13 75`

**Menu /menu**
- Title: `Carte du restaurant Une Semaine Sur Deux — Grenoble · Bistronomie de saison`
- Description: `Découvrez la carte du restaurant Une Semaine Sur Deux à Grenoble. Entrées, plats, desserts faits maison. Poulpe signature, truite, mousse au chocolat Valrhona.`

**Chef /chef**
- Title: `Chef Pierrick Vasseur — Restaurant Une Semaine Sur Deux · Grenoble`
- Description: `Pierrick Vasseur, chef du restaurant Une Semaine Sur Deux à Grenoble. Cuisine bistronomique, produits locaux et de saison. Toque Gault & Millau 2026.`

**Galerie /galerie**
- Title: `Galerie — Restaurant Une Semaine Sur Deux · Grenoble`
- Description: `Photos des plats et de l'ambiance du restaurant Une Semaine Sur Deux à Grenoble. Cuisine bistronomique, dressage soigné, produits frais.`

**Réserver /reserver**
- Title: `Réserver une table — Restaurant Une Semaine Sur Deux · Grenoble`
- Description: `Réservez votre table au restaurant Une Semaine Sur Deux, 4 Place Championnet, Grenoble. ☎ 04 76 27 13 75. Ouvert tous les jours.`

---

## 10. LEGAL PAGE — Create `/mentions-legales`

Add a 6th route `/mentions-legales` with the following content:

```
Mentions légales

Éditeur du site
Une Semaine Sur Deux
4 Place Championnet
38000 Grenoble
Téléphone : 04 76 27 13 75
Email : restaurant1sur2@gmail.com

Directeur de publication
Pierrick Vasseur

Hébergeur
Vercel Inc.
340 Pine Street, Suite 701
San Francisco, CA 94104, USA
https://vercel.com

Conception et réalisation
Yamen Global — yamen-global.com
```

Add a discreet footer link: "Mentions légales" → `/mentions-legales`
Use `<Link>` from React Router, DM Sans 12px #5A4E44.
Add this route to `sitemap.xml` with `priority: 0.1`.

---

## FINAL VERIFICATION — Run before export to GitHub

Run `npm run build` and confirm:
- ✅ 0 TypeScript errors
- ✅ 0 ESLint errors
- ✅ sitemap.xml in `/public/`
- ✅ robots.txt in `/public/`
- ✅ vercel.json at root
- ✅ fonts in `/src/assets/fonts/` (no Google CDN calls)
- ✅ All images have alt, width, height, loading attributes
- ✅ `<picture>` wrappers in place for webp readiness
- ✅ JSON-LD Restaurant complete in `<head>`
- ✅ Unique title + description on all 6 pages
- ✅ Canonical on all 6 pages
- ✅ 0 console.log in source

Do not push to GitHub. Export is handled manually.
Report every fix applied and every item that requires a real domain to be confirmed.
