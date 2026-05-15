# LOVABLE — REMPLACEMENT PHOTOS PAR PEXELS CDN
# Une Semaine Sur Deux · Photos temporaires haute qualité
# Objectif : présenter le site au restaurant avec des photos
# professionnelles en attendant leurs originaux

---

## CONTEXTE

The current photos come from Instagram and are heavily compressed.
Replace them with high-quality Pexels CDN images that match
each dish and section of the site.

Do NOT replace `photo-gaultmillau` — it is the real Gault & Millau
2026 plaque and must stay.

Use the Pexels CDN URLs directly as `src` attributes —
no download needed.

Pexels CDN URL format:
`https://images.pexels.com/photos/{ID}/pexels-photo-{ID}.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1`

---

## PHOTO REPLACEMENTS — 7 PHOTOS

### 1. Hero background — `hero-grenoble`
**Section:** Homepage hero (full-screen, text overlay)
**Replace with:** Pexels ID `3534750`
**URL:** `https://images.pexels.com/photos/3534750/pexels-photo-3534750.jpeg?auto=compress&cs=tinysrgb&w=1920&h=1080&dpr=1`
**Description:** Elegant restaurant interior with warm lighting and table settings.
**Alt:** `"Salle du restaurant Une Semaine Sur Deux — bistronomie à Grenoble"`
**Note:** Use `w=1920&h=1080` for the hero (larger viewport). Add `object-position: center 40%`.

---

### 2. Plat signature — `photo-menu-poulpe`
**Section:** Homepage cinematic full-bleed section (65vh, dark overlay, text bottom-left)
**Replace with:** Pexels ID `14885388`
**URL:** `https://images.pexels.com/photos/14885388/pexels-photo-14885388.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1`
**Description:** Close-up gourmet octopus dish with rich orange sauce on patterned plate — dark background, fine dining.
**Alt:** `"Poulpe à la crème d'ail noir — plat signature du Chef Pierrick Vasseur"`
**Note:** This replaces the poulpe/menu cover photo. Perfect match for the signature dish section.

---

### 3. Photo strip — left column — `photo-volaille`
**Section:** Homepage photo strip (3 equal columns, 340px height)
**Caption:** "Viandes & volailles"
**Replace with:** Pexels ID `769289`
**URL:** `https://images.pexels.com/photos/769289/pexels-photo-769289.jpeg?auto=compress&cs=tinysrgb&w=800&h=800&dpr=1`
**Description:** Gourmet steak with vegetables and peppercorn sauce on dark background — fine dining style.
**Alt:** `"Viande et légumes de saison — Une Semaine Sur Deux"`
**Note:** Use `w=800&h=800` for the square strip columns.

---

### 4. Photo strip — center column — `photo-poisson`
**Section:** Homepage photo strip (3 equal columns, 340px height)
**Caption:** "Poissons & saison"
**Replace with:** Pexels ID `20802561`
**URL:** `https://images.pexels.com/photos/20802561/pexels-photo-20802561.jpeg?auto=compress&cs=tinysrgb&w=800&h=800&dpr=1`
**Description:** Elegant fish dish with mushrooms and flower on dark rustic plate — minimal fine dining.
**Alt:** `"Poisson et légumes frais de saison — bistronomie Grenoble"`
**Note:** Exceptional match — dark background, elegant plating, very close to the restaurant's actual style.

---

### 5. Photo strip — right column — `photo-surf-turf`
**Section:** Homepage photo strip (3 equal columns, 340px height)
**Caption:** "Plats du moment"
**Replace with:** Pexels ID `4553378`
**URL:** `https://images.pexels.com/photos/4553378/pexels-photo-4553378.jpeg?auto=compress&cs=tinysrgb&w=800&h=800&dpr=1`
**Description:** Delicious lobster with white wine in an elegant setting — luxury gourmet presentation.
**Alt:** `"Homard et vins au restaurant Une Semaine Sur Deux"`
**Note:** Use `object-position: center 30%` to favor the plated lobster.

---

### 6. Menu page header — `photo-legumes`
**Section:** /menu page header (45vh, text overlay)
**Replace with:** Pexels ID `32615777`
**URL:** `https://images.pexels.com/photos/32615777/pexels-photo-32615777.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1`
**Description:** Bustling French village market with fresh figs and local produce — stone archway, France.
**Alt:** `"Produits frais du marché — Une Semaine Sur Deux cuisine de saison"`
**Note:** This is a FRENCH MARKET photo (Occitanie/Pyrénées-Orientales). Perfect for "produits frais, circuit court, de saison."

---

### 7. Menu page break — `photo-pavlova`
**Section:** /menu page cinematic break (after the dish list, 40vh)
**Replace with:** Pexels ID `3740177`
**URL:** `https://images.pexels.com/photos/3740177/pexels-photo-3740177.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1`
**Description:** Elegant chocolate cake with white meringue icing on square plate — refined dessert presentation.
**Alt:** `"Desserts faits maison — mousse au chocolat Valrhona, crème brûlée"`
**Note:** The menu lists "Mousse au chocolat Valrhona" and "Crème brûlée" — this photo represents the dessert course beautifully.

---

## IMPLEMENTATION

For each photo replacement:

1. Find the `<img>` (or `<motion.img>` or `<picture><source>`) that references the old filename
2. Replace the `src` attribute with the new Pexels CDN URL above
3. Update the `alt` attribute with the new alt text above
4. If a `<picture><source>` wrapper exists, update the `srcSet` to the same Pexels URL
5. Keep all existing CSS classes, animations, and object-fit/object-position unchanged

Example:
```tsx
// BEFORE
<img
  src="/src/assets/photos/photo-menu-poulpe.jpg"
  alt="Le plat signature poulpe à la crème d'ail noir"
  className="w-full h-full object-cover"
/>

// AFTER
<img
  src="https://images.pexels.com/photos/14885388/pexels-photo-14885388.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
  alt="Poulpe à la crème d'ail noir — plat signature du Chef Pierrick Vasseur"
  className="w-full h-full object-cover"
/>
```

---

## DO NOT TOUCH

- `photo-gaultmillau` — real restaurant asset, keep exactly as-is
- All CSS classes, Tailwind utilities, Framer Motion variants
- All text content, section layout, colors, typography
- Any other asset not listed above

---

## AFTER REPLACEMENT

Add this comment block in the component where photos are imported,
so the next developer knows:

```tsx
{/*
  PHOTOS TEMPORAIRES — Pexels CDN (libre de droits)
  Ces photos sont des substituts haute qualité.
  Remplacer par les photos originales du restaurant
  une fois reçues en format RAW ou JPEG non compressé.
  Contact : restaurant1sur2@gmail.com
  Date de remplacement prévue : à confirmer avec le client
*/}
```
