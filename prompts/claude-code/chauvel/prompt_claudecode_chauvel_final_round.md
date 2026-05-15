Fix the remaining open issues — accessibility, SEO, and legal pages.
Do not touch design, layout, or any element not listed here.
Report after each section: ✅ done / ⚠️ partial / ❌ blocked + reason.

━━ A11Y — PREFERS-REDUCED-MOTION ━━━━━━━━━━━━━━━━━━━━━━

Check if styles.css already contains a prefers-reduced-motion
media query. If it does not, add at the very end of the file:

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
  .card:hover,
  .comp-teaser:hover {
    transform: translateY(-2px);
    transition: none;
  }
}

━━ A11Y — NAV DROPDOWN TRIGGERS ━━━━━━━━━━━━━━━━━━━━━━━

In the nav component, find all <span role="button"> elements
used as dropdown triggers.

For each one:
1. Replace <span role="button"> with <button type="button">
   Preserve all existing className, onClick, onKeyDown handlers.
2. Add a unique id: id="nav-trigger-[slug]"
   (e.g. nav-trigger-famille, nav-trigger-penal, etc.)
3. On the corresponding .nav-dropdown-menu div, add a matching
   id: id="nav-menu-[slug]"
4. Add to the trigger button:
   aria-controls="nav-menu-[slug]"
   aria-expanded={isOpen} (use the existing open state variable)

━━ A11Y — FOCUS TRAP MOBILE MENU ━━━━━━━━━━━━━━━━━━━━━━

When the mobile nav panel is open, keyboard focus must be
trapped inside it. Tab and Shift+Tab should cycle only through
focusable elements inside the panel.

Implement using the following pattern:
- On panel open: store the previously focused element, move
  focus to the first focusable element inside the panel
- On Tab keydown: if focus is on last focusable element,
  move to first
- On Shift+Tab keydown: if focus is on first focusable element,
  move to last
- On panel close: return focus to the element that opened it

Focusable elements: all <a>, <button> inside the panel.
Do not use any external library — implement with vanilla JS
inside the existing component.

━━ SEO — ARTICLE PAGE TITLES ━━━━━━━━━━━━━━━━━━━━━━━━━━

In app.jsx, find PAGE_TITLES.
First, list all route slugs defined in the router for
/publications/* to confirm the exact paths.

Then add one entry per article route:

"/publications/[exact-slug]": "[Article title] · Maître Olivier Chauvel"

Use the actual article headline from the page content as the
title — do not invent titles. If the slug or title is
uncertain, read the relevant component file first.

Result: every article page must have a unique <title>.

━━ SEO — OG:IMAGE ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

In index.html, after the existing og:url meta tag, add:

<meta property="og:image" content="https://olivierchauvel-avocat.fr/og-cover.jpg" />
<meta property="og:image:width" content="1200" />
<meta property="og:image:height" content="630" />
<meta property="og:image:alt" content="Cabinet Maître Olivier Chauvel — Avocat à Rennes" />

Then check if /public/og-cover.jpg exists.
- If yes: done.
- If no: find the highest-resolution image in /public/ or
  /src/assets/, copy it to /public/og-cover.jpg.

━━ SEO — JSON-LD ARTICLE SCHEMA ━━━━━━━━━━━━━━━━━━━━━━━

For each of the 6 article pages, inject an Article JSON-LD
block using the same pattern as the existing LegalService
schema.

Schema per article:
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "[article title from page content]",
  "author": {
    "@type": "Person",
    "name": "Maître Olivier Chauvel"
  },
  "publisher": {
    "@type": "LegalService",
    "name": "Cabinet Maître Olivier Chauvel"
  },
  "datePublished": "[date from article content, or omit if unavailable]",
  "url": "https://olivierchauvel-avocat.fr/publications/[slug]"
}

━━ LÉGAL — PAGES MENTIONS / RGPD / CGV ━━━━━━━━━━━━━━━━

Footer links to /mentions-legales, /rgpd, /cgv currently
point to #/. These pages are legally required in France.

Create three minimal pages with the following content:

/mentions-legales
  Éditeur : Maître Olivier Chauvel, Avocat au Barreau de Rennes
  Adresse : [use address already in the codebase]
  Email : [use email already in the codebase]
  Téléphone : [use phone already in the codebase]
  Hébergeur : Vercel Inc., 340 Pine Street Suite 701,
              San Francisco, CA 94104, États-Unis
              https://vercel.com

/rgpd
  Responsable du traitement : Maître Olivier Chauvel
  Données collectées : nom, téléphone, email, message
    (via le formulaire de contact)
  Finalité : réponse aux demandes de contact uniquement
  Durée de conservation : 3 ans à compter du dernier contact
  Droits : accès, rectification, suppression sur demande
    à [use email already in the codebase]
  Pas de transfert de données à des tiers

/cgv
  Les honoraires sont fixés par convention entre le client
  et Maître Olivier Chauvel, conformément à l'article 10
  de la loi du 31 décembre 1971. Les conditions détaillées
  sont remises lors du premier rendez-vous.

Style: use the existing page layout and typography tokens.
No hero section needed — these are utility pages.
Add these three routes to the router in app.jsx.
Update the footer links to point to the correct routes.

━━ FINAL CHECK ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Run: npm run build
→ Zero TypeScript errors, zero warnings.

Verify:
- Tab through the mobile nav when open — focus stays inside
- Each article page has a unique <title> in the browser tab
- /mentions-legales, /rgpd, /cgv render without 404
- Footer links point to correct routes

Final report:
✅ Fixed (list each item)
⚠️ Partial (what was done, what remains)
❌ Blocked (reason)
