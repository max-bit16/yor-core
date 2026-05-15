Fix all issues from the design critique below. Execute in priority order.
Do not change typography, color tokens, or any element not explicitly mentioned.
Report after each section: ✅ done / ⚠️ partial / ❌ blocked + reason.

━━ P1 — CONTACT PAGE: FORM ABOVE THE FOLD ━━━━━━━━━━━━━

The contact hero padding (130px 0 108px) pushes the form
below the fold. The form is the only purpose of this page.

Read ~/.claude/skills/layout/SKILL.md

Then apply one of these two fixes — choose whichever
requires fewer component changes:

Option A (minimal change):
Reduce contact hero padding to 48px 0 40px.
This should bring the form into view on most viewports.

Option B (structural):
Remove the contact hero section entirely.
Replace with a two-column above-fold layout:
  - Left column (1.4fr): page title + subtitle + contact info
    (address, phone as <a href="tel:">, email)
  - Right column (1fr): the existing contact form
No hero image, no gradient mesh on this page.

Verify on 390px mobile that the form is visible without
scrolling after the fix. If it is not, reduce padding further.

━━ P1 — HOMEPAGE ARCHITECTURE ━━━━━━━━━━━━━━━━━━━━━━━━━

Current order: Hero → authority strip → 5 competences →
dark CTA card → legal aid → CTA strip.

Problem: 3 conversion asks before any trust is built.

Read ~/.claude/skills/layout/SKILL.md

Reorder the homepage sections to:
1. Hero (keep as-is)
2. Authority strip (keep as-is)
3. Philosophy/approach section (see below)
4. 3 competence teasers (reduce from 5 to 3 — keep:
   Famille, Corporel, Pénal — the highest-volume areas)
5. Single CTA strip
6. Legal aid band (move here, at the bottom)

Philosophy section to add (between authority strip and
competences):
A two-column row: left side a pull quote in Cormorant
Garamond italic large — something like "Disponible,
rigoureux, transparent sur les honoraires." Right side
2–3 short sentences about the approach. Keep existing
copy if available in the codebase; do not invent new copy.

━━ P1 — CTA REPETITION ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Read ~/.claude/skills/distill/SKILL.md

"Prendre rendez-vous" currently appears 6 times on the
homepage (nav, hero, competences, dark CTA card, bottom
strip, footer).

Keep: nav pill CTA + one primary CTA after the new
philosophy section.

Change:
- Competence card buttons: change label to "En savoir plus"
  (may already be the case — verify)
- Dark CTA card: remove entirely if the single CTA strip
  is kept; if the dark CTA card is kept, remove the strip
- Footer CTA: change to a plain text link or remove

Result: max 2 instances of "Prendre rendez-vous" on the
full homepage.

━━ P2 — COMPETENCE PAGE MOCKUPS ━━━━━━━━━━━━━━━━━━━━━━━

Read ~/.claude/skills/clarify/SKILL.md

The SideComposition panels (phase trackers, damage
assessment dashboards, "Suivi en temps réel" UI) imply
software functionality that does not exist in a solo
practice. This creates a trust gap.

Replace each SideComposition panel with a process timeline:

Format for each competence:
- Title: "La procédure en [N] étapes"
- 3–5 numbered steps with a short label + one-sentence
  description each
- Style: vertical timeline, left-aligned, using existing
  token system (no new colors)
- No fake case numbers, no fake monetary amounts,
  no fake status indicators

Use only the competence content already in the codebase
for step descriptions. Do not invent new claims.

Apply to all competence pages that currently show a
SideComposition panel.

━━ P2 — FORM VALIDATION & UX ━━━━━━━━━━━━━━━━━━━━━━━━━━

Read ~/.claude/skills/harden/SKILL.md

1. Field-level validation on blur:
   - All required fields: show red border + "Ce champ est
     requis." if empty on blur
   - Phone field: validate format on blur
     (accepts: 0X XX XX XX XX or +33X XX XX XX XX)
     error message: "Format invalide. Ex: 06 12 34 56 78"
   - Email field: ensure type="email" is set + onBlur
     validation with message: "Adresse email invalide."

2. Submit button loading state:
   - On click: disable button, replace label with a spinner
     (Lucide Loader2 with animate-spin) + "Envoi en cours…"
   - On success: show ✓ icon + "Message envoyé"
   - On error: re-enable button, show inline error above
     the button: "Une erreur est survenue. Veuillez réessayer
     ou nous appeler directement."

3. Success state:
   Add below the confirmation message:
   "Nous vous répondons sous 24h ouvrées."

4. Autocomplete attributes:
   Add to each form field:
   - Name field: autocomplete="name"
   - Phone field: autocomplete="tel"
   - Email field: autocomplete="email"
   - Message field: autocomplete="off"

━━ P3 — MINOR FIXES ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

5. Form label font size:
   Change form field labels from 13px to 14px.

6. Footer domain list:
   Add "droit des étrangers" and "droit de la chasse"
   to the footer description to match the 5 competences
   listed on the site.

7. Publications date:
   Remove the "Publiés le 04/09/2018" timestamp from the
   article list view. Keep dates on individual article
   pages only if they are accurate.

8. Mobile nav close button:
   Increase the close button tap target to minimum 44×44px.
   Ensure it is reachable with one hand (top-right is fine,
   but increase the padding around the icon).

9. btn-secondary visibility on photo background:
   On the hero "Découvrir le cabinet" button, add a
   semi-transparent background on mobile:
   background: rgba(15, 30, 50, 0.35) on screens < 768px.
   This prevents the border from disappearing against
   the hero photo.

10. Contact page image:
    The Rennes photo behind the contact hero is never
    visible as intentional content.
    If Option A (reduced padding) is applied: keep it as
    subtle background, ensure it has a dark scrim overlay
    of rgba(15,30,50,0.55) so text remains readable.
    If Option B (no hero) is applied: remove the image
    entirely from the contact page.

━━ FINAL CHECK ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Run: npm run build
→ Zero TypeScript errors, zero warnings.

Check on 390px mobile:
- Contact form visible without scrolling ✓
- Nav close button reachable one-handed ✓
- Form fields trigger iOS autocomplete ✓
- Submit button shows loading state on tap ✓

Final report:
✅ Fixed (list each item by number)
⚠️ Partial (what was done, what remains)
❌ Blocked (reason)
Estimated new Design Health Score: X/40
