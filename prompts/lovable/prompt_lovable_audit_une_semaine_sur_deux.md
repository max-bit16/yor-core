# LOVABLE — AUDIT COMPLET
# Une Semaine Sur Deux · Post-build verification

---

Perform a full audit of the current codebase. Do not change any design, any color, any layout, any animation. Fix only what is broken, missing, or non-functional. Report every finding.

---

## 1. ROUTING & NAVIGATION

- Verify all 5 routes exist and render without errors: `/` · `/menu` · `/chef` · `/galerie` · `/reserver`
- Verify the sticky navigation links point to the correct routes
- Verify the "Réserver" CTA in the nav links to `/reserver`
- Verify the "Voir la carte" button on the homepage links to `/menu`
- Verify "Voir la carte complète →" in the plat signature section links to `/menu`
- Verify the footer navigation links are all functional
- Test that the browser back button works correctly on all routes
- Verify there are no 404 pages for any internal link

## 2. ACTION LINKS

Every phone, email, and map link must be verified:

| Element | Expected href |
|---|---|
| "Réserver une table" (hero) | `tel:+33476271375` |
| "Appeler le restaurant" (hours section) | `tel:+33476271375` |
| "Appeler maintenant" (/reserver) | `tel:+33476271375` |
| "Nous écrire →" (/reserver) | `mailto:restaurant1sur2@gmail.com` |
| "Voir sur Google Maps" | `https://maps.google.com/?q=4+Place+Championnet+Grenoble` |
| Instagram link | `https://www.instagram.com/1semainesur2restaurant/` |
| Facebook link | `https://www.facebook.com/1sur2grenoble/` |

Check that all `tel:` and `mailto:` links have the correct `href` attribute — not placeholder text.
Check that all external links have `target="_blank"` and `rel="noopener noreferrer"`.

## 3. IMAGES

- Verify all 8 photos load without 404 error:
  `photo-saint-jacques.jpg` · `photo-pavlova.jpg` · `photo-surf-turf.jpg` · `photo-menu-poulpe.jpg` · `photo-volaille.jpg` · `photo-poisson.jpg` · `photo-legumes.jpg` · `photo-gaultmillau.jpg`
- Verify every `<img>` has a non-empty `alt` attribute
- Verify every `<img>` has `loading="lazy"` (except the first visible image on each page)
- Verify no image has a broken `src` path (check for typos in filenames)
- Verify the Gault & Millau photo renders correctly (object-contain, not cropped)

## 4. FONTS

- Verify Cormorant Garamond loads correctly — check that italic renders as true italic, not faux italic
- Verify DM Sans loads at weight 300 and 400
- Verify fonts are served from `/src/assets/fonts/` (self-hosted), not from Google Fonts CDN
- If fonts are still loading from Google Fonts CDN, move them to local assets immediately

## 5. ANIMATIONS

- Verify Framer Motion is imported from `framer-motion` (not `motion/react`)
- Verify `whileInView` animations trigger correctly on scroll — test fadeUp, stagger, scaleUp
- Verify the scroll-hide navigation works: nav hides on scroll down, reveals on scroll up
- Verify the `AnimatedCounter` (96 and 204) triggers when the social proof section enters the viewport
- Verify the parallax hook `useScroll` / `useTransform` does not cause layout shift (CLS)
- Verify no animation causes horizontal overflow or scroll on mobile

## 6. RESPONSIVE / MOBILE

- Verify the hero typography scales correctly at 375px viewport width (H1 ≤ 52px)
- Verify the hero split-screen stacks vertically on mobile
- Verify the chef page split-screen stacks: photo banner (45vh) then text below
- Verify the photo strip (3 columns) stacks to single column on mobile
- Verify the masonry gallery becomes 2 columns on tablet, 1 column on mobile
- Verify all `rounded-full` buttons are large enough touch targets (min 44px height)
- Verify the sticky nav collapses to a hamburger menu on mobile — and that the hamburger opens/closes correctly
- Verify no text overflows its container at any breakpoint

## 7. SEO & META

Verify the following in `index.html` or the React Head component:

- Homepage `<title>`: "Restaurant Une Semaine Sur Deux à Grenoble — Cuisine Bistronomique · Gault & Millau 2026"
- Homepage `<meta name="description">`: contains "Grenoble", "Gault & Millau", phone number
- Each page has a unique `<title>` and `<meta name="description">`
- `<meta property="og:title">` present on homepage
- `<meta property="og:description">` present on homepage
- `<meta property="og:image">` present and points to `photo-menu-poulpe.jpg`
- `<link rel="canonical">` present on homepage

Verify the JSON-LD Restaurant schema in `index.html`:
```json
{
  "@context": "https://schema.org",
  "@type": "Restaurant",
  "name": "Une Semaine Sur Deux",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "4 Place Championnet",
    "addressLocality": "Grenoble",
    "postalCode": "38000",
    "addressCountry": "FR"
  },
  "telephone": "+33476271375",
  "email": "restaurant1sur2@gmail.com",
  "servesCuisine": "French",
  "openingHours": "Mo-Su 12:00-14:00",
  "url": "https://[deployed-url]"
}
```
If any field is missing or incorrect, fix it.

## 8. CONSOLE ERRORS

Open the browser console on each route and verify:
- Zero JavaScript errors
- Zero failed network requests (404, 500)
- Zero React key warnings
- Zero "Each child in a list should have a unique key" warnings
- Zero missing dependency warnings from useEffect

## 9. CONTENT ACCURACY

Verify the following data is correct everywhere it appears in the site:

| Data | Correct value |
|---|---|
| Address | 4 Place Championnet, 38000 Grenoble |
| Phone | +33 4 76 27 13 75 |
| Email | restaurant1sur2@gmail.com |
| Hours | Ouvert tous les jours · 12h–14h / 19h–21h30 |
| Chef name | Pierrick Vasseur |
| Award | Gault & Millau 2026 · Table Gourmande |
| Social proof | 96% · 204 avis Facebook |
| Instagram handle | @1semainesur2restaurant |
| Signature dish | Poulpe à la crème d'ail noir, risotto de riz vénéré |

Flag any discrepancy — wrong phone number format, wrong address, missing chef name, etc.

## 10. ACCESSIBILITY

- Verify every interactive element (links, buttons) is keyboard-focusable
- Verify focus states are visible (not `outline: none` without replacement)
- Verify the hamburger menu button has an `aria-label`
- Verify all `<img>` have non-empty `alt` (already checked in §3 — double-check here for screen readers)
- Verify color contrast on DM Sans 300 text (#8A7A6A on #1C1814) — flag if contrast ratio < 3:1
- Verify the page has exactly one `<h1>` per route

---

## DELIVERABLE

After the audit, provide a structured report:

```
✅ PASS — item description
⚠️  FIXED — what was broken, what was changed
❌ BLOCKER — what is broken and requires content/asset from client
```

Fix everything in the FIXED category silently in the code.
Flag everything in the BLOCKER category (e.g. missing original photos) with a clear explanation of what the client needs to provide.
Do not change any design decisions, spacing, color, or animation parameters.
