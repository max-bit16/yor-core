# LOVABLE PROMPT — UNE SEMAINE SUR DEUX
# Version 2.0 — Design cinématographique · Photos réelles · Framer Motion
# Restaurant gastronomique · Grenoble · Gault & Millau 2026

---

## RESTAURANT DATA
- Name: Une Semaine Sur Deux
- Address: 4 Place Championnet, 38000 Grenoble, France
- Phone: +33 4 76 27 13 75 · tel:+33476271375
- Email: restaurant1sur2@gmail.com
- Instagram: @1semainesur2restaurant · https://www.instagram.com/1semainesur2restaurant/
- Facebook: https://www.facebook.com/1sur2grenoble/
- Social proof: 96% recommended · 204 avis Facebook
- Chef: Pierrick Vasseur · Gault & Millau Table Gourmande 2026

---

## PHOTO ASSETS — UPLOAD INSTRUCTIONS

Upload these 8 photos to `/src/assets/photos/` and name them exactly:

| Filename | What it shows |
|---|---|
| `photo-saint-jacques.jpg` | Scallops + mussels + purple rice on white plate, stone wall behind |
| `photo-pavlova.jpg` | Pavlova with mango and meringue on black plate, stone wall behind |
| `photo-surf-turf.jpg` | Meat + lobster + cream sauce, wine rack in background |
| `photo-menu-poulpe.jpg` | Green menu cover + poulpe dish on white plate |
| `photo-volaille.jpg` | Chicken / mushrooms / cream sauce, aerial view |
| `photo-poisson.jpg` | Fish fillet with colorful root vegetables, aerial view |
| `photo-legumes.jpg` | Vegetable plate with mushrooms and cherry tomatoes, moody light |
| `photo-gaultmillau.jpg` | Gault & Millau 2026 "Table Gourmande" yellow award plaque |

Reference them as: `import photoSaintJacques from '@/assets/photos/photo-saint-jacques.jpg'` etc.

---

## TECH STACK
- React + Vite + TypeScript
- Tailwind CSS
- Framer Motion (animations — see ANIMATION SYSTEM below)
- Lucide-React icons ONLY
- Fonts: Cormorant Garamond (headings) + DM Sans (body) — self-hosted in /src/assets/fonts/
- No AI images, no Unsplash, no placeholder images
- No contact forms — direct action links only (tel:, mailto:, Google Maps)
- Mobile-first

---

## COLOR PALETTE
```
background:    #1A1714   warm dark stone
surface:       #252118   cards and panels
surface-alt:   #1F1C18   alternate sections
text-primary:  #F5EFE0   warm ivory
text-muted:    #9E9080   secondary text
green:         #2C4A3E   forest green (menu cover color)
green-hover:   #3A5F52
gold:          #C8965A   plate rim gold
gold-dim:      rgba(200,150,90,0.15)
border:        #2E2A24
overlay:       rgba(26,23,20,0.72)   photo overlays
```

---

## TYPOGRAPHY
- H1: Cormorant Garamond, italic, font-weight 400, 96px desktop / 56px mobile
- H2: Cormorant Garamond, italic, font-weight 400, 52px desktop / 38px mobile
- H3: Cormorant Garamond, font-weight 500, 26px
- Body: DM Sans, 16px, line-height 1.85
- Labels: DM Sans, 11px, letter-spacing 0.22em, uppercase, color #9E9080
- Label format: "N°01 — SECTION TITLE"
- Pull quotes: Cormorant Garamond italic, 1.4rem, color #F5EFE0

---

## ANIMATION SYSTEM

### Install
Framer Motion is already available in Lovable. Import:
```tsx
import { motion, useScroll, useTransform, useMotionValue, useSpring, animate } from 'framer-motion'
```

### Easing curves
```tsx
const ease = [0.22, 1, 0.36, 1]         // smooth deceleration
const easeIn = [0.4, 0, 1, 1]
const spring = { type: 'spring', stiffness: 60, damping: 20 }
```

### Reusable variants (define once, use everywhere)

```tsx
// Fade up — single element
const fadeUp = {
  hidden: { opacity: 0, y: 40 },
  visible: { opacity: 1, y: 0, transition: { duration: 0.9, ease } }
}

// Stagger container
const staggerContainer = {
  hidden: {},
  visible: { transition: { staggerChildren: 0.12, delayChildren: 0.1 } }
}

// Stagger child (used inside staggerContainer)
const staggerChild = {
  hidden: { opacity: 0, y: 30 },
  visible: { opacity: 1, y: 0, transition: { duration: 0.7, ease } }
}

// Fade in only
const fadeIn = {
  hidden: { opacity: 0 },
  visible: { opacity: 1, transition: { duration: 1 } }
}

// Scale up from center
const scaleUp = {
  hidden: { opacity: 0, scale: 0.92 },
  visible: { opacity: 1, scale: 1, transition: { duration: 0.8, ease } }
}
```

### Scroll trigger wrapper
Apply `whileInView="visible" initial="hidden" viewport={{ once: true, margin: "-80px" }}` to all sections.

### Parallax hook (use in Hero and full-bleed photo sections)
```tsx
const { scrollY } = useScroll()
const y = useTransform(scrollY, [0, 600], [0, -80])
// Apply <motion.img style={{ y }} ... />
```

### Counter animation (for stats: 96 and 204)
```tsx
function AnimatedCounter({ target }: { target: number }) {
  const count = useMotionValue(0)
  const rounded = useTransform(count, (v) => Math.round(v))
  useEffect(() => {
    const controls = animate(count, target, { duration: 2, ease: 'easeOut' })
    return controls.stop
  }, [])
  return <motion.span>{rounded}</motion.span>
}
```
Trigger only when the social proof section enters viewport using IntersectionObserver.

### Navigation scroll behavior
```tsx
// Hide nav on scroll down, reveal on scroll up
const [visible, setVisible] = useState(true)
const [lastY, setLastY] = useState(0)
useEffect(() => {
  const handleScroll = () => {
    setVisible(window.scrollY < lastY || window.scrollY < 80)
    setLastY(window.scrollY)
  }
  window.addEventListener('scroll', handleScroll)
  return () => window.removeEventListener('scroll', handleScroll)
}, [lastY])
// Apply: <motion.nav animate={{ y: visible ? 0 : -80 }} transition={{ duration: 0.3 }}>
```

### Photo hover effect (gallery cards)
```tsx
<motion.div
  className="overflow-hidden rounded-xl"
  whileHover="hovered"
>
  <motion.img
    variants={{ hovered: { scale: 1.07, transition: { duration: 0.6, ease } } }}
    className="w-full h-full object-cover"
  />
  <motion.div
    className="absolute inset-0 bg-overlay flex items-end p-6"
    variants={{ hovered: { opacity: 1 }, initial: { opacity: 0 } }}
    initial="initial"
  >
    <p className="text-ivory font-dm-sans text-sm uppercase tracking-widest">Nom du plat</p>
  </motion.div>
</motion.div>
```

### CTA button micro-interaction
```tsx
<motion.a
  whileHover={{ scale: 1.03 }}
  whileTap={{ scale: 0.97 }}
  transition={{ duration: 0.2 }}
>
```

### Menu item hover (left gold bar appears)
```tsx
<motion.div
  className="relative pl-5 py-4 cursor-default"
  whileHover="hovered"
>
  <motion.div
    className="absolute left-0 top-0 h-full w-0.5 bg-gold"
    variants={{ hovered: { scaleY: 1, opacity: 1 }, initial: { scaleY: 0, opacity: 0 } }}
    initial="initial"
    style={{ originY: 0 }}
    transition={{ duration: 0.25 }}
  />
  <span className="text-ivory">Nom du plat</span>
</motion.div>
```

---

## PAGES

---

### PAGE 1 — HOME (index)

#### NAVIGATION
Sticky. Transparent on top, transitions to `background: #1A1714CC` (backdrop-blur-md) on scroll.
Logo left: "Une Semaine Sur Deux" — Cormorant Garamond italic, 20px, #F5EFE0.
Links center: Menu · Le Chef · Galerie · Réserver.
CTA right: "Réserver" — bg #2C4A3E, text white, px-5 py-2.5, rounded-sm.
Hide/show on scroll direction (see animation system above).
Enter animation: `fadeIn` variant on mount.

---

#### HERO — SPLIT SCREEN (100vh)
Full-screen, two columns side by side.

**Left column (55%) — Typography**
Background: #1A1714 with very subtle radial gradient from #252118 at center.
Padding: pl-16 desktop, centered mobile.
Stagger container wrapping all children.
- Stagger child 1: label "N°01 — GASTRONOMIE GRENOBLOISE"
- Stagger child 2: H1 in two lines, Cormorant italic 96px:
  *"Cuisine vivante,*
  *saisons intactes."*
- Stagger child 3: DM Sans 17px #9E9080: "Restaurant gastronomique · Grenoble · Toque Gault & Millau 2026"
- Stagger child 4: Two buttons side by side:
  - Primary: "Réserver une table" → tel:+33476271375, bg #2C4A3E, rounded-sm
  - Secondary: "Voir la carte" → /menu, border 1px #C8965A, text #C8965A, rounded-sm
- Stagger child 5 (delayed 0.6s): Thin horizontal divider, 80px wide, color #C8965A opacity-40

**Right column (45%) — Photo**
Image: `photo-saint-jacques.jpg` — fills full column height.
`object-fit: cover`, `object-position: center`.
Parallax: `<motion.img style={{ y }}>` using useScroll hook (image moves -80px as page scrolls 600px).
Subtle dark gradient overlay on left edge of the photo (to blend into the left column):
`background: linear-gradient(to right, #1A1714, transparent)`
applied as an absolute overlay on the left 30% of the image column.

Mobile: stack vertically. Photo becomes a 50vw tall banner above the text.

---

#### GAULT & MILLAU BANNER (full-width, bg #252118, py-14)
`whileInView fadeIn` on the whole section.
Three-column layout (equal widths):
- Left col: `<img src={photoGaultMillau} />` — rounded-xl, max-h-32, object-contain. **This is the actual Gault & Millau 2026 yellow plaque photo.**
- Center col (text, centered):
  - Gold label: "DISTINCTION · 2026"
  - Cormorant italic 2.5rem: *"Table Gourmande"*
  - DM Sans 15px #9E9080: "Attribuée au Chef Pierrick Vasseur pour la qualité de sa cuisine bistronomique à Grenoble."
- Right col: Lucide Award icon #C8965A 40px + Lucide Star icon #C8965A 28px, centered.

Mobile: stacked. Photo on top, text below.

---

#### FULL-BLEED CINEMATIC SECTION — PLAT SIGNATURE
Full-width, height 70vh.
Background image: `photo-menu-poulpe.jpg` — `object-fit: cover`.
Dark overlay: `rgba(26,23,20,0.65)`.
Content centered absolutely over the overlay:
- Label: "N°02 — PLAT SIGNATURE"
- H2 Cormorant italic 64px white: *"Le Poulpe à la crème d'ail noir,*
  *risotto de riz vénéré."*
- DM Sans 17px #9E9080: "Le plat qui revient dans tous les avis. Cuisson parfaite, produits de saison, fait maison."
- CTA text link: "Voir la carte complète →" in gold, ArrowRight icon

Animation: `scaleUp` variant on the image (scale 1.0 → visible).
Parallax on image: slow vertical drift as section scrolls through viewport.
Text children: `staggerContainer` + `staggerChild`.

---

#### BENTO GRID — L'ESPRIT DU LIEU (bg #1F1C18, py-28)
Label: "N°03 — L'ESPRIT DU LIEU"
`staggerContainer` wrapping all cards.

**Grid: 3 columns, 2 rows** (CSS grid, auto rows)

- **Card A** (cols 1–2, row 1) — Large photo card
  Background image: `photo-pavlova.jpg`, `object-cover`, rounded-2xl, overflow-hidden.
  Dark overlay. Text bottom-left:
  - Label "DESSERTS" uppercase
  - H3 italic: *"Bistronomie"*
  - Body: "Une carte courte, renouvelée au fil des saisons."
  Photo hover: `scale(1.05)` zoom on the background image (motion.div with whileHover).

- **Card B** (col 3, row 1) — Dark stat card
  bg #252118, border 1px #2E2A24, rounded-2xl, p-8.
  Lucide MapPin #C8965A + "Produits locaux" H3.
  Body: "Produits frais, circuit court, de saison."

- **Card C** (col 1, row 2) — Dark card
  bg #252118, border 1px #2E2A24, rounded-2xl, p-8.
  Lucide Wine #C8965A + "Cave personnelle".
  Body: "Sélection viticole du chef à prix justes."

- **Card D** (col 2, row 2) — Dark card
  bg #252118, border 1px #2E2A24, rounded-2xl, p-8.
  Lucide Users #C8965A + "Privatisation".
  Body: "Le restaurant peut accueillir vos événements privés."

- **Card E** (col 3, row 2) — Testimonial pull card
  bg #2C4A3E (green), rounded-2xl, p-8.
  Cormorant italic 1.3rem #F5EFE0:
  *"On se régale du début à la fin. Le poulpe était incroyable."*
  DM Sans 13px #9E9080 below: "— E. Bagdassarian ★★★★★"

Card hover: `whileHover={{ y: -4, borderColor: '#C8965A' }}` on dark cards.

---

#### PHOTO STRIP — 3 HORIZONTAL PHOTOS (py-0, no padding)
Full-width, 3 equal columns, height 380px.
Each column: one photo, `object-cover`, no gap.
Photos: `photo-volaille.jpg` · `photo-poisson.jpg` · `photo-surf-turf.jpg`
On hover each photo: `scale(1.04)` zoom + gold overlay appears with dish category text:
- "Viandes & volailles" / "Poissons & fruits de mer" / "Plats du moment"
Caption: DM Sans 12px uppercase white, centered bottom.
Animation: `staggerContainer` on the three columns (they enter left-to-right with 0.15s stagger).

---

#### SOCIAL PROOF BAR (bg #252118, py-14)
3 stats, equal columns, vertical dividers 1px #2E2A24.
`whileInView` triggers the counter animations.

- Col 1: AnimatedCounter target={96} in Cormorant 4.5rem #C8965A + "%" + label "RECOMMANDENT CE RESTAURANT"
- Col 2: AnimatedCounter target={204} in Cormorant 4.5rem #C8965A + label "AVIS FACEBOOK"
- Col 3: Lucide Award 36px #2C4A3E + label "TABLE GOURMANDE · GAULT & MILLAU 2026"

---

#### HOURS & RESERVATION (py-24)
Two columns.
Left: `fadeUp` on scroll.
- H3: "Nous retrouver"
- Hours table, DM Sans:
  Tous les jours · 12h–14h / 19h–21h30
- Map address: Lucide MapPin + "4 Place Championnet, Grenoble"
- Phone: Lucide Phone + "+33 4 76 27 13 75"

Right: CTA card — bg #252118, border 1px #2C4A3E, rounded-xl, p-10.
`scaleUp` on scroll.
- H3: "Réserver votre table"
- Body: "Sur place ou par téléphone. Confirmation immédiate."
- Button primary: "Appeler le restaurant" → tel:+33476271375, bg #2C4A3E
- Text link below: "Voir sur Google Maps →" #C8965A, ArrowRight icon

---

#### FOOTER (bg #0E0C09, py-16)
Logo centered top: "Une Semaine Sur Deux" Cormorant italic 22px.
3 cols below: Adresse · Horaires · Navigation links.
Thin gold separator (1px #C8965A, opacity-20, full-width) above footer.
Bottom bar: "© 2026 Une Semaine Sur Deux · Grenoble · Site réalisé par Yamen Global"

---

---

### PAGE 2 — MENU (/menu)

#### HEADER (py-24, centered)
Background: `photo-legumes.jpg` full-width 40vh, object-cover, dark overlay rgba(26,23,20,0.75).
Text over photo:
- Label: "N°01 — LA CARTE"
- H1 Cormorant italic: *"Une carte courte,*
  *qui dit l'essentiel."*
- Body: "Renouvelée au fil des saisons. Tout est fait maison."
Animation: text staggered entrance, photo parallax.

#### MENU SECTIONS (bg #1A1714, py-20, max-w-4xl centered)
3 sections, each as an open card (not accordion — always visible).
Card: bg #252118, border-b 1px #2E2A24, rounded-none on top card, rounded-2xl on bottom.

Each dish row uses menu item hover animation (gold left bar on hover, see animation system).
**ENTRÉES:**
- Foie gras mi-cuit au bœuf séché, chutney de coing
- Gravlax de saumon Bömlo
- Tartare de thon
- Œuf poché à la crème d'olives noires, risotto noir

**PLATS:**
- Poulpe à la crème d'ail noir, risotto de riz vénéré — badge right: "SIGNATURE" bg #2C4A3E text white DM Sans 9px uppercase px-2 py-0.5 rounded-sm
- Souris d'agneau fondante
- Truite, légumes frais de saison
- Suprême de pintade fermière, crème de chorizo
- Porc ibérique, réduction romarin, purée façon Robuchon

**DESSERTS:**
- Mousse au chocolat Valrhona
- Crème brûlée au limoncello
- Pavlova mangue, sphères glacées
- Palet breton

#### PHOTO BREAK — full-width 50vh
Image: `photo-pavlova.jpg`, object-cover, parallax.
Overlay: rgba(26,23,20,0.5).
Centered text: Cormorant italic 2rem: *"Tout est fait maison, jusqu'aux desserts."*

#### PRICE SECTION (bg #1F1C18, py-16)
3 cards, `staggerContainer`:
- Plat du jour · **13,50 €** · Lucide Utensils #C8965A
- Menu adulte · **À partir de 39 €** · Lucide ChefHat #C8965A
- Menu enfant · **15 €** · Lucide Users #C8965A
Price in Cormorant 3rem #F5EFE0, label DM Sans uppercase #9E9080.

---

---

### PAGE 3 — LE CHEF (/chef)

#### HERO — ASYMMETRIC SPLIT (100vh)
Left (45%): `photo-menu-poulpe.jpg`, object-cover, full height.
Subtle right-edge gradient (transparent → #1A1714) to blend into right column.
Right (55%): bg #1A1714, padding px-16, centered vertically.
Text staggered:
- Label: "N°01 — DERRIÈRE LES FOURNEAUX"
- H1: *"Pierrick Vasseur,*
  *cuisiner avec intention."*
- Body: "Depuis l'ouverture, Pierrick Vasseur défend une cuisine bistronomique ancrée dans la saison et le territoire. Pas de carte longue — une sélection courte, renouvelée, où chaque plat est travaillé jusqu'à l'essentiel."
- Second paragraph: "Distingué par une toque Gault & Millau 2026, il s'appuie sur des produits en circuit court et une sélection viticole personnelle à prix justes."
- Two badges: Lucide Award + "Toque Gault & Millau 2026" · Lucide Leaf + "Circuit court"

#### PULL QUOTE SECTION (bg #252118, py-20, centered)
`scaleUp` on scroll.
Cormorant italic 2.2rem #F5EFE0, max-w-3xl:
*"Tout est fait maison, jusqu'aux desserts."*
DM Sans below: "— Chef Pierrick Vasseur"
Thin gold line (80px) above and below the quote.

#### VALUES — 3 CARDS (bg #1F1C18, py-20)
`staggerContainer`, 3 equal columns:
- Lucide Sprout #C8965A + "Produits frais" + "Fruits, légumes et viandes sourcés localement."
- Lucide Sun #C8965A + "Saisons respectées" + "La carte change quand les saisons changent."
- Lucide ChefHat #C8965A + "Fait maison" + "Chaque plat, chaque dessert, préparé sur place."

---

---

### PAGE 4 — GALERIE (/galerie)

#### HEADER (py-20, centered)
Label: "N°01 — DANS L'ASSIETTE"
H1: *"Un régal pour les yeux aussi."*
DM Sans #9E9080: "Photographies · Une Semaine Sur Deux · Grenoble"

#### MASONRY GRID (3 columns, gap-3, px-6 md:px-12)
8 photos in masonry layout using CSS columns or a grid with specific row-spans.
Each photo: rounded-xl, overflow-hidden, cursor-default.

**Photo placement:**
- Slot 1 (tall, row-span-2): `photo-saint-jacques.jpg` — "Saint-Jacques, riz noir vénéré"
- Slot 2: `photo-pavlova.jpg` — "Pavlova mangue, sphères glacées"
- Slot 3: `photo-surf-turf.jpg` — "Viande, homard, sauce crémée"
- Slot 4 (tall, row-span-2): `photo-poisson.jpg` — "Truite, légumes frais de saison"
- Slot 5: `photo-volaille.jpg` — "Volaille, champignons, sauce"
- Slot 6: `photo-menu-poulpe.jpg` — "Le menu · Plat signature"
- Slot 7: `photo-legumes.jpg` — "Légumes du marché, champignons"
- Slot 8: `photo-gaultmillau.jpg` — "Toque Gault & Millau 2026"

Each slot: photo hover animation (scale + overlay caption, see animation system).
Caption: DM Sans 11px uppercase #F5EFE0 tracking-widest, centered bottom.

`staggerContainer` on the grid: photos appear one by one as the page loads (0.08s stagger).

#### CTA STRIP (py-16, bg #252118, centered)
"Retrouvez-nous sur Instagram"
Link: @1semainesur2restaurant → Instagram URL, Lucide Instagram-style icon, gold color.

---

---

### PAGE 5 — RÉSERVER (/reserver)

#### HEADER PHOTO (40vh)
Background: `photo-surf-turf.jpg`, object-cover, overlay rgba(26,23,20,0.7).
Centered text:
- Label: "N°01 — VENEZ NOUS VOIR"
- H1: *"Réservez votre table."*

#### CONTACT SPLIT (py-24)
Two columns.
Left — Info card (bg #252118, border 1px #2E2A24, rounded-2xl, p-10):
`fadeUp` on scroll.
- Lucide MapPin #C8965A + "4 Place Championnet, 38000 Grenoble"
- Lucide Phone #C8965A + "+33 4 76 27 13 75"
- Lucide Mail #C8965A + "restaurant1sur2@gmail.com"
- Lucide Clock #C8965A + "Ouvert tous les jours · 12h–14h / 19h–21h30"
- Button: "Voir sur Google Maps" → bg #2C4A3E, href https://maps.google.com/?q=4+Place+Championnet+Grenoble

Right — Reservation card (bg #252118, border 1px #2C4A3E, rounded-2xl, p-10):
`fadeUp` on scroll, delay 0.15s.
- H3: "Par téléphone"
- Body: "La meilleure façon de réserver. Nous confirmons immédiatement."
- Large CTA button: "Appeler maintenant" → tel:+33476271375, bg #2C4A3E, py-4 px-8, full-width
- Separator 1px #2E2A24
- H3: "Événements privés"
- Body: "Le restaurant peut être privatisé pour vos événements professionnels ou familiaux."
- Text link: "Nous écrire →" → mailto:restaurant1sur2@gmail.com, #C8965A

#### TESTIMONIALS (bg #1F1C18, py-24)
Label: "N°02 — ILS EN PARLENT"
3-column grid. `staggerContainer`.
Each card: bg #252118, border 1px #2E2A24, rounded-2xl, p-8.
Card hover: `whileHover={{ y: -6, borderColor: '#C8965A' }}`.
- Card 1: *"Le poulpe était incroyable : cuisson parfaite, tendre, bien assaisonné. Et la souris d'agneau, fondante, pleine de goût."* — E. Bagdassarian ★★★★★
- Card 2: *"La mousse au chocolat est sans doute la meilleure que j'ai pu manger. De loin ma plus belle expérience culinaire à Grenoble."* — G. Cascone ★★★★★
- Card 3: *"Les plats, à la fois croquants et fondants, sont un vrai régal. L'ambiance allie modernité et raffinement."* — Ozzy Makeo ★★★★★

Below: centered — "96% des clients recommandent ce restaurant · 204 avis Facebook" — DM Sans 14px #9E9080

#### SOCIAL (py-16, centered)
Instagram link → @1semainesur2restaurant
Facebook link → Une Semaine sur Deux

---

## ABSOLUTE RULES
1. No AI images, no Unsplash, no placeholder images — use the 8 photos listed above
2. No contact forms anywhere — direct action links only (tel:, mailto:, Google Maps)
3. Self-host Cormorant Garamond + DM Sans in /src/assets/fonts/
4. Single H1 per page, containing "restaurant" + "Grenoble" on homepage
5. All icons: Lucide-React exclusively
6. Buttons: rounded-sm (slightly squared — prestige feel, never rounded-full)
7. Framer Motion: GPU-composited transforms only (opacity + transform). No layout animations. No width/height animations.
8. Images: always with `loading="lazy"` and descriptive `alt` attributes
9. Mobile-first: hero split becomes stacked, bento grid becomes 1 column, photo strip becomes vertical scroll
10. Photo strip and full-bleed sections: always `object-cover`, always with dark overlay for text legibility

## SEO
- Homepage title: "Restaurant Une Semaine Sur Deux à Grenoble — Cuisine Bistronomique · Gault & Millau 2026"
- Meta description: "Restaurant bistronomique à Grenoble. Produits frais, circuit court, fait maison. Toque Gault & Millau 2026. Chef Pierrick Vasseur. ☎ 04 76 27 13 75"
- JSON-LD type Restaurant in index.html — include name, address, telephone, email, openingHours, servesCuisine: "French"
- OG:image → photo-saint-jacques.jpg (most visually striking)
- Each page has unique title and description
- All images: .webp format (convert before upload), alt non-empty
