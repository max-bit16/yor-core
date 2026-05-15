PROMPT — AUDIT COMPLET + RESTRUCTURATION LAYOUT
Cabinet Maître Olivier Chauvel
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

PHASE 1 : AUDIT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Read ~/.claude/skills/audit/SKILL.md
Read ~/.claude/skills/critique/SKILL.md
Read ~/.claude/skills/colorize/SKILL.md

Audit the full site across three dimensions.
Do not change anything in Phase 1 — observe and report only.

---

A. QUALITÉ

For each page (homepage, 5 competence pages, présentation,
honoraires, publications, contact, mentions légales, rgpd,
cgv), check:

- Spacing consistency: are padding/margin values consistent
  across equivalent elements?
- Alignment: do elements share a visible grid?
- Mobile breakpoints: does each section reflow correctly
  at 390px and 768px?
- Typography: is the Cormorant / DM Sans hierarchy clear
  and consistent across all pages?
- Interactive states: do all buttons, links, and cards have
  :hover and :focus styles?
- Empty states and edge cases: long names, long text,
  missing images — do they break layout?

---

B. COULEURS

Extract the full list of color values currently in use across
all files (CSS variables, inline styles, Tailwind classes).

Then report:
- Colors that appear only once (orphan colors)
- Colors that deviate from the defined token system
  (--primary, --gold, --surface, --ink, --ink-secondary,
  --ink-mute, --cream)
- Sections or components where color usage feels
  inconsistent with the navy/gold/cream editorial palette
- Any color that reads as "off-brand" against the overall
  aesthetic

---

C. ANIMATIONS

List every animation and transition active on the site:
- Scroll reveal (.reveal, .fade-up, IntersectionObserver)
- Page transitions (.page-enter)
- Hover effects (cards, buttons, nav, comp-teaser)
- Nav animations (dropdown stagger, chevron rotation)
- Any other motion present

For each, evaluate:
- Does it serve a purpose or is it decorative noise?
- Is the duration appropriate (too fast / too slow)?
- Is it consistent with other animations on the same page?
- Does it work correctly on mobile?

---

PHASE 1 OUTPUT FORMAT

Produce a structured report with three sections:

QUALITÉ
  [PAGE] [ELEMENT] [ISSUE] [SEVERITY: high/medium/low]

COULEURS
  [LOCATION] [CURRENT VALUE] [ISSUE] [SUGGESTED FIX]

ANIMATIONS
  [NAME] [LOCATION] [ASSESSMENT: keep/adjust/remove]
  [REASON]

End with a Priority List: the 10 most impactful issues
across all three dimensions, ranked by impact.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

PHASE 2 : RESTRUCTURATION LAYOUT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Read ~/.claude/skills/layout/SKILL.md
Read ~/.claude/skills/typeset/SKILL.md
Read ~/.claude/skills/polish/SKILL.md

Based on the Phase 1 findings, apply the following
layout improvements. Use only layouts that already exist
in the codebase or classic proven patterns — no new
design experiments.

Do not change: typography tokens, color tokens, animations
that are marked "keep", any content or copy.

---

1. HOMEPAGE — sections that need restructuring

For each section flagged in Phase 1:
- Identify the closest equivalent layout already used
  elsewhere on the site
- Apply that layout pattern to the flagged section
- If no existing pattern fits, use one of these classic
  patterns:
    · Two-column (text left, visual right) — 1.2fr 1fr
    · Full-width centered text block with max-width 720px
    · Three-column card grid with equal columns
    · Single-column with large left margin (editorial style)

---

2. COMPETENCE PAGES — consistency pass

All 5 competence pages should follow the exact same
section structure and spacing. If any page deviates:
- Identify which page is the most complete/best executed
- Align all other pages to match its structure exactly

---

3. CONTACT PAGE — post-reduction check

The contact hero padding was reduced to 48px 0 40px.
Verify the section above the form still reads as a
deliberate introduction and not as an abrupt start.
If it feels abrupt, add a single centered eyebrow line
in gold above the title (e.g. "Cabinet · Rennes") using
the existing .t-eyebrow class.

---

4. GLOBAL — spacing and rhythm

Identify the 3 sections across the entire site that have
the most inconsistent vertical spacing.
For each: apply the nearest spacing token from the
existing scale to normalize it.

---

5. ANIMATIONS — adjustments from Phase 1

For each animation marked "adjust" in Phase 1:
- Apply the specific fix described in the report
For each animation marked "remove":
- Remove the animation and ensure the element renders
  correctly in its static state

---

PHASE 2 CONSTRAINTS

- Use only existing CSS classes and tokens
- No new color values
- No new font families or sizes outside the existing scale
- No changes to the competence hero background images
  added in the previous session
- No changes to the contact form or validation logic

---

FINAL REPORT

After all changes:

✅ Layout changes applied (section + change description)
✅ Color fixes applied (location + old → new)
✅ Animation adjustments applied (name + change)
⚠️ Partial changes (what remains and why)
❌ Blocked (reason)

Estimated improvement in visual consistency: X/10
