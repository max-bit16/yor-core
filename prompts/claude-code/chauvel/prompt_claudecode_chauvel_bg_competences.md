Add a background photo to the hero section of each competence page.
Do not change typography, colors, spacing, or any content.
Report after each step: ✅ done / ⚠️ partial / ❌ blocked + reason.

━━ STEP 1 — COPY IMAGES TO PROJECT ━━━━━━━━━━━━━━━━━━━━

The 5 source images are already on disk in the Downloads
folder or the Desktop. Locate them by their Unsplash
filename pattern, then copy to /public/images/competences/:

cp ~/Desktop/jane-utochkina-0GrtD_9WnPU-unsplash.jpg   ./public/images/competences/bg-famille.jpg
cp ~/Desktop/pawel-czerwinski-g0eRErPBoTA-unsplash.jpg  ./public/images/competences/bg-corporel.jpg
cp ~/Desktop/shridhar-thorat-6AKLKt-KmdY-unsplash.jpg  ./public/images/competences/bg-penal.jpg
cp ~/Desktop/antoine-rault-IhWRrZx4-kk-unsplash.jpg    ./public/images/competences/bg-etrangers.jpg
cp ~/Desktop/krzysztof-kowalik-2pnozU26QBo-unsplash.jpg ./public/images/competences/bg-chasse.jpg

If any file is not found, run: ls ~/Desktop/*unsplash* to
list available filenames and adapt the cp command accordingly.

━━ STEP 2 — CONVERT TO WEBP ━━━━━━━━━━━━━━━━━━━━━━━━━━━

Convert each jpg to webp using sharp (NOT sips):

node -e "
const sharp = require('sharp');
const files = [
  'bg-famille','bg-corporel','bg-penal','bg-etrangers','bg-chasse'
];
files.forEach(f => {
  sharp('./public/images/competences/' + f + '.jpg')
    .webp({ quality: 82 })
    .toFile('./public/images/competences/' + f + '.webp')
    .then(() => console.log('✅ ' + f + '.webp'))
    .catch(e => console.error('❌ ' + f, e.message));
});
"

If sharp is not installed: npm install sharp --save-dev
After conversion, keep the .jpg files as fallback.

━━ STEP 3 — ADD CSS CLASS ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

In styles.css, add a reusable hero background pattern.
Find where .hero-mesh or .page-hero is defined and add
after it:

.comp-hero-bg {
  position: relative;
  overflow: hidden;
}

.comp-hero-bg::before {
  content: '';
  position: absolute;
  inset: 0;
  background-image: var(--hero-bg-image);
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  opacity: 0.18;
  z-index: 0;
  pointer-events: none;
}

.comp-hero-bg > * {
  position: relative;
  z-index: 1;
}

Opacity 0.18 keeps the image subtle — text remains fully
readable without any additional scrim overlay. The image
adds depth without competing with the Cormorant Garamond
headline.

━━ STEP 4 — APPLY TO EACH COMPETENCE PAGE ━━━━━━━━━━━━━

In pages-competences.jsx (or wherever each competence
hero section is rendered), find the hero/header element
for each competence.

For each competence, add:
1. The class comp-hero-bg to the hero container element
2. An inline style: style={{ '--hero-bg-image': 'url(/images/competences/bg-[slug].webp)' }}

Mapping:
- Droit de la famille  → bg-famille.webp
- Dommage corporel     → bg-corporel.webp
- Droit pénal          → bg-penal.webp
- Droit des étrangers  → bg-etrangers.webp
- Droit de la chasse   → bg-chasse.webp

If the competences share a single CompetenceLayout component
with a slug or id prop, add a bgImage prop instead and pass
the correct filename per competence. This is cleaner than
adding inline styles in 5 separate places.

━━ STEP 5 — VERIFY ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Open each competence page and confirm:
- Background image is visible but not dominant
- Headline text is fully readable (white on dark hero)
- No layout shift or overflow on mobile (390px)
- Images load as webp (check Network tab)

If the opacity feels too low (image barely visible), increase
to 0.22. If it competes with the text, reduce to 0.14.
Do not go above 0.25 — above that, a dark scrim overlay
becomes necessary to maintain WCAG contrast.

━━ FINAL REPORT ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ Files copied and converted (list each)
✅ CSS added
✅ Applied to competences (list each with filename used)
⚠️ / ❌ Any issue with reason
