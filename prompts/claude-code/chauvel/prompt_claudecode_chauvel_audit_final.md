Fix all issues from the production audit below. Execute in priority order.
Do not touch design, colors, or layout unless explicitly stated.
Report after each fix: ✅ file modified / ⚠️ partial / ❌ blocked + reason.

━━ CRITICAL ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. prefers-reduced-motion

Add at the very end of styles.css:

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}

Exception: do NOT zero out translateY hover lifts on cards —
these communicate affordance and should remain without transition.
Implement by adding a carve-out after the global rule:

@media (prefers-reduced-motion: reduce) {
  .card:hover, .comp-teaser:hover {
    transform: translateY(-2px);
    transition: none;
  }
}

---

2. Article page titles

In app.jsx, locate PAGE_TITLES.
Add the 6 missing article routes with specific titles:

"/publications/les-juridictions": "Les juridictions compétentes · Maître Olivier Chauvel",
"/publications/la-procedure-penale": "La procédure pénale · Maître Olivier Chauvel",
"/publications/le-divorce": "Le divorce · Maître Olivier Chauvel",
"/publications/lindemnisation-du-dommage-corporel": "L'indemnisation du dommage corporel · Maître Olivier Chauvel",
"/publications/le-droit-des-etrangers": "Le droit des étrangers · Maître Olivier Chauvel",
"/publications/la-chasse-et-le-droit": "La chasse et le droit · Maître Olivier Chauvel"

Verify the actual route slugs match what is defined in the router before adding.
Correct any slug mismatch.

---

3. og:image

In index.html, after the existing og:url meta tag, add:

<meta property="og:image" content="https://olivierchauvel-avocat.fr/og-cover.jpg" />
<meta property="og:image:width" content="1200" />
<meta property="og:image:height" content="630" />
<meta property="og:image:alt" content="Cabinet Maître Olivier Chauvel — Avocat à Rennes" />

Then check if /public/og-cover.jpg exists.
If it does not exist: find the hero building photo in /public/ or /src/assets/,
copy it to /public/og-cover.jpg.
If no building photo exists: use the highest-resolution image available in the project.

━━ HIGH ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

4. Competences ordering

Canonical order: Famille → Corporel → Chasse → Étrangers → Pénal
(matches the nav dropdown).

Find the CompTeaser grid in pages-core.jsx and reorder the 5 competence entries
to match: Famille → Corporel → Chasse → Étrangers → Pénal.
Do not change the nav dropdown — it is already correct.

---

5. Nav dropdown accessibility

In the nav component, locate all <span role="button"> elements
used as dropdown triggers.

Replace each with <button type="button">.
Preserve all existing className, onClick, onKeyDown handlers exactly.

Then for each dropdown trigger:
- Add a unique id to the trigger button: id="nav-trigger-[competence-slug]"
- Add a matching id to its .nav-dropdown-menu div: id="nav-menu-[competence-slug]"
- Add aria-controls="nav-menu-[competence-slug]" to the trigger button
- Add aria-expanded={isOpen} to the trigger button

━━ MEDIUM ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

6. sidePhoto decoding attribute

Find the hero-photo-side <img> element.
Add decoding="async" alongside the existing loading="lazy".

---

7. Contact grid breakpoint

In styles.css, find the .contact-grid rule.
Add a breakpoint at 900px that stacks the grid to a single column:

@media (max-width: 900px) {
  .contact-grid {
    grid-template-columns: 1fr;
  }
}

---

8. aria-hidden on mobile panel

Find the mobile nav panel component.
Replace aria-hidden={!mobileOpen} with:
aria-hidden={mobileOpen ? undefined : "true"}

━━ LOW ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

9. Article JSON-LD

For each of the 6 article pages, add an Article JSON-LD block in the <head>:

{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "[article title]",
  "author": {
    "@type": "Person",
    "name": "Maître Olivier Chauvel"
  },
  "publisher": {
    "@type": "LegalService",
    "name": "Cabinet Maître Olivier Chauvel"
  },
  "datePublished": "[use the date visible in the article content, or 2024-01-01 as fallback]",
  "url": "https://olivierchauvel-avocat.fr/publications/[slug]"
}

Implement via the same pattern used for the existing LegalService JSON-LD.

---

10. Footer layout on mobile

In styles.css, find the footer-grid mobile rule (@media max-width: 768px).
Update it so the about column is full-width on its own row:

@media (max-width: 768px) {
  .footer-grid {
    grid-template-columns: 1fr;
  }
}

━━ FINAL CHECK ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Run: npm run build
→ Zero TypeScript errors, zero warnings.

Then produce a final report:

✅ Fixed (list each item)
⚠️ Partial (what was done, what remains)
❌ Blocked (reason)

Estimate the new audit score out of 40 after all fixes.
