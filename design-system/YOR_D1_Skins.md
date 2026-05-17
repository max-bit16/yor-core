# YOR — DOSSIER 1 : SKINS
# Yamen Global · Version 1.0 · Avril 2026
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## COMMENT UTILISER CE FICHIER

Chaque skin est un prompt Lovable complet, prêt à copier-coller.
Remplace les variables entre crochets par les infos du brief client.
Les buzzwords en tête de prompt définissent l'ambiance globale —
Lovable les interprète comme une direction esthétique.

Ne modifie jamais les contraintes absolues (zéro image IA, Lucide
uniquement, mobile-first). Elles sont non-négociables pour les
scores PageSpeed YOR.

---

## TABLEAU RÉCAPITULATIF

| Skin | Ambiance | Palette dominante | Pour qui |
|------|----------|-------------------|----------|
| 01 DARK | Premium sombre | Noir / Violet / Ivoire | Studios, photographes, agences |
| 02 PRESTIGE | Institutionnel sobre | Crème / Vert forêt | Avocats, notaires, cabinets |
| 03 GLOBAL | Aéré corporate | Blanc cassé / Or | Consultants, stratèges |
| 04 BOLD | Brutal impactant | Noir / Blanc / Accent vif | Artisans, commerçants |
| 05 SOFT | Chaleureux humain | Pêche / Sauge | Bien-être, soin, coaching |
| 06 EDITORIAL | Magazine raffiné | Blanc pur / Or pâle | Intellectuels, chercheurs |

---

## SKIN 01 — DARK

**Ambiance :** Studio, premium, typographie dominante.
**Cas client :** Photo Pro — photo-pros.vercel.app
**Pour qui :** Photographes, studios créatifs, agences BtoB, profils premium.

**Buzzwords :**
`cinematic, typographic dominance, deep contrast, editorial dark,
serif italic, bento grid, premium dark, moody`

```
Crée un site vitrine professionnel pour [NOM], [SECTEUR]
basé(e) à [VILLE]. Cible : [CIBLE].

STYLE : cinematic, typographic dominance, deep contrast,
editorial dark, serif italic, bento grid, premium dark, moody.

CONTRAINTE ABSOLUE : aucune image IA, aucun placeholder,
aucun stock photo. Design basé sur typographie + icônes SVG.

Stack : React + Tailwind CSS + Lucide-React
Polices : Playfair Display (titres) + DM Sans (corps)

Palette :
— Fond : #0D0D0D
— Accent : #6B3FA0 (violet profond)
— Texte : #F5F0EB (ivoire)
— Secondaire : #1A1A1A (cards)

Structure HTML sémantique :
— H1 unique : "[MOT-CLÉ] à [VILLE] — [NOM]"
— H2 par section

Sections dans l'ordre :
1. Hero plein écran — Playfair 96px italic, stats géantes
2. Bento Grid services — 6 blocs asymétriques, icônes Lucide
3. Section confiance — secteurs clients en ligne
4. FAQ accordéon — ChevronDown Lucide
5. Contact — formulaire 3 champs + infos

Services : [SERVICES]
USP : [DIFFÉRENCIATEUR]
Chiffres clés : [CHIFFRES]
FAQ : [FAQ]
Meta description : "[META 155 chars max]"
OpenGraph dans le head. Mobile-first. Pas d'animations lourdes.
```

---

## SKIN 02 — PRESTIGE

**Ambiance :** Cabinet, institution, serif dominant.
**Cas client :** Renaud Voss — prestige-legal.vercel.app
**Pour qui :** Avocats, notaires, experts-comptables, architectes, cabinets de conseil.

**Buzzwords :**
`serif luxury, cream editorial, old-money, dense layout,
tactile, institutional, understated elegance, law firm`

```
Crée un site vitrine professionnel pour [NOM], [SECTEUR]
basé(e) à [VILLE]. Cible : [CIBLE].

STYLE : serif luxury, cream editorial, old-money, dense layout,
tactile, institutional, understated elegance.

CONTRAINTE ABSOLUE : aucune image IA, aucun placeholder,
aucun stock photo. Design basé sur typographie + icônes SVG.

Stack : React + Tailwind CSS + Lucide-React
Polices : Playfair Display (titres) + DM Sans (corps)

Palette :
— Fond : #F0EDE6 (crème chaud)
— Texte principal : #1C1C1C (noir profond)
— Accent : #2C4A3E (vert forêt)
— Cards : #FAFAF7
— Bordures : #E0DBD3

Structure HTML sémantique :
— H1 unique : "[MOT-CLÉ] à [VILLE] — [NOM]"
— H2 par section

Sections dans l'ordre :
1. Hero sobre — Playfair 72px, fond crème, pas de plein écran
2. Philosophie — 2 colonnes texte, citation Playfair italic
3. Services — grille 2x3 cards bordurées, icônes Lucide
4. Équipe / À propos — layout horizontal sobre
5. Témoignages — cards minimalistes fond #FAFAF7
6. Contact — formulaire sobre + adresse + téléphone

Services : [SERVICES]
USP : [DIFFÉRENCIATEUR]
Chiffres clés : [CHIFFRES]
FAQ : [FAQ]
Meta description : "[META 155 chars max]"
OpenGraph dans le head. Mobile-first. Pas d'animations lourdes.
```

---

## SKIN 03 — GLOBAL

**Ambiance :** Conseil, international, aéré.
**Cas client :** Yamen Global — yamen-global.com
**Pour qui :** Consultants stratégiques, cabinets de conseil, profils internationaux.

**Buzzwords :**
`clean corporate, airy layout, confident spacing, international,
minimal icons, strategic, world-class, editorial white`

```
Crée un site vitrine professionnel pour [NOM], [SECTEUR]
basé(e) à [VILLE]. Cible : [CIBLE].

STYLE : clean corporate, airy layout, confident spacing,
international, minimal icons, strategic, editorial white.

CONTRAINTE ABSOLUE : aucune image IA, aucun placeholder,
aucun stock photo. Design basé sur typographie + icônes SVG.

Stack : React + Tailwind CSS + Lucide-React
Polices : Playfair Display (titres) + DM Sans (corps)

Palette :
— Fond : #FAFAF8 (blanc cassé)
— Texte principal : #111111 (noir profond)
— Accent chaud : #C8965A (or discret)
— Sections alternées : #F2EFE9
— Bordures : #E5E0D8

Structure HTML sémantique :
— H1 unique : "[MOT-CLÉ] à [VILLE] — [NOM]"
— H2 par section

Sections dans l'ordre :
1. Hero aéré — Playfair 80px, espace blanc généreux
2. Services — grid 2 colonnes, titres Playfair, icônes Lucide
3. Process — 4 étapes numérotées Playfair, layout vertical
4. Chiffres clés — 3 stats géantes Playfair, fond alterné
5. Manifeste / À propos — texte long, typographie seule
6. Contact — minimaliste, formulaire + email direct

Services : [SERVICES]
USP : [DIFFÉRENCIATEUR]
Chiffres clés : [CHIFFRES]
Meta description : "[META 155 chars max]"
OpenGraph dans le head. Mobile-first. Pas d'animations lourdes.
```

---

## SKIN 04 — BOLD

**Ambiance :** Impact immédiat, contraste brutal, typographie XXL.
**Cas client :** —
**Pour qui :** Artisans, commerçants, métiers manuels, marques jeunes.

**Buzzwords :**
`brutalist, raw typography, oversized headlines, stark contrast,
grid-heavy, bold disruptive, high-impact, black and white`

```
Crée un site vitrine professionnel pour [NOM], [SECTEUR]
basé(e) à [VILLE]. Cible : [CIBLE].

STYLE : brutalist, raw typography, oversized headlines,
stark contrast, grid-heavy, bold disruptive, high-impact.

CONTRAINTE ABSOLUE : aucune image IA, aucun placeholder,
aucun stock photo. Design basé sur typographie + icônes SVG.

Stack : React + Tailwind CSS + Lucide-React
Polices : Playfair Display (titres très grands) + DM Sans (corps)

Palette :
— Fond : #FFFFFF (blanc pur)
— Texte : #0A0A0A (noir)
— Accent unique : [AU CHOIX — #E63329 rouge / #F5A623 orange / #1DB954 vert]
— Blocs alternés : #0A0A0A (fond noir pour sections clés)

Structure HTML sémantique :
— H1 unique : "[MOT-CLÉ] à [VILLE] — [NOM]"
— H2 par section

Sections dans l'ordre :
1. Hero fullscreen — Playfair 110px bold, fond noir,
   une accroche, CTA en accent
2. Services — grille rigide, cards bordure épaisse noire,
   titres grands, icônes Lucide
3. Différenciateur — grande stat Playfair, fond accent
4. Process — 3 étapes numérotées très grandes
5. Contact — fond noir, texte blanc, formulaire simple

Services : [SERVICES]
USP : [DIFFÉRENCIATEUR]
Chiffres clés : [CHIFFRES]
Meta description : "[META 155 chars max]"
OpenGraph dans le head. Mobile-first. Pas d'animations lourdes.
```

---

## SKIN 05 — SOFT

**Ambiance :** Chaleureux, accessible, humain.
**Cas client :** —
**Pour qui :** Thérapeutes, coachs, kinés, naturopathes, professions du bien-être.

**Buzzwords :**
`soft gradients, rounded corners, muted earth tones, cozy layout,
gentle microinteractions, wellness, warm, approachable, human`

```
Crée un site vitrine professionnel pour [NOM], [SECTEUR]
basé(e) à [VILLE]. Cible : [CIBLE].

STYLE : soft gradients, rounded corners, muted earth tones,
cozy layout, wellness, warm, approachable, human.

CONTRAINTE ABSOLUE : aucune image IA, aucun placeholder,
aucun stock photo. Design basé sur typographie + icônes SVG.

Stack : React + Tailwind CSS + Lucide-React
Polices : Playfair Display (titres) + DM Sans (corps)

Palette :
— Fond : #FDF8F3 (blanc pêche très doux)
— Texte : #3D2B1F (brun doux)
— Accent principal : #D4856A (terre cuite rosée)
— Accent secondaire : #7EB5A6 (sauge)
— Cards : #FFFFFF avec ombre très légère
— Border-radius : 2xl sur tous les éléments

Structure HTML sémantique :
— H1 unique : "[MOT-CLÉ] à [VILLE] — [NOM]"
— H2 par section

Sections dans l'ordre :
1. Hero centré — Playfair 72px, fond dégradé pêche → blanc
2. Services — 3 cards rondes, icônes Lucide couleur accent
3. À propos — texte chaleureux, mise en avant de l'humain
4. Témoignages — 2 cards minimalistes fond blanc
5. Tarifs — 2 ou 3 formules, cards arrondies
6. Contact — fond accent doux, formulaire simple + tél

Services : [SERVICES]
USP : [DIFFÉRENCIATEUR]
Chiffres clés : [CHIFFRES]
FAQ : [FAQ]
Meta description : "[META 155 chars max]"
OpenGraph dans le head. Mobile-first. Pas d'animations lourdes.
```

---

## SKIN 06 — EDITORIAL

**Ambiance :** Magazine, intellectuel, grille asymétrique.
**Cas client :** —
**Pour qui :** Avocats haut de gamme, architectes, chercheurs, journalistes, think tanks.

**Buzzwords :**
`magazine grid, asymmetric columns, thin serif, white space,
intellectual, editorial, refined, long-form, newspaper`

```
Crée un site vitrine professionnel pour [NOM], [SECTEUR]
basé(e) à [VILLE]. Cible : [CIBLE].

STYLE : magazine grid, asymmetric columns, thin serif,
white space, intellectual, editorial, refined, newspaper.

CONTRAINTE ABSOLUE : aucune image IA, aucun placeholder,
aucun stock photo. Design basé sur typographie + icônes SVG.

Stack : React + Tailwind CSS + Lucide-React
Polices : Playfair Display weight-300 (titres fins) + DM Sans (corps léger)

Palette :
— Fond : #FFFFFF (blanc pur)
— Texte : #1A1A1A
— Accent ligne : #C0A882 (or pâle)
— Séparateurs : lignes fines 1px #DDDDDD
— Aucun fond de section coloré — tout en blanc

Structure HTML sémantique :
— H1 unique : "[MOT-CLÉ] à [VILLE] — [NOM]"
— H2 par section

Sections dans l'ordre :
1. Hero éditorial — Playfair 88px weight-300, sous-titre DM Sans
   petit, ligne séparatrice fine, pas de couleur de fond
2. Services — grille 2 colonnes asymétriques (60/40),
   numérotation Playfair, descriptions longues
3. Expertise — texte seul, longues colonnes, citations italiques
4. Références / Publications — liste typographique sobre
5. Contact — minimaliste absolu, email + adresse, pas de formulaire

Services : [SERVICES]
USP : [DIFFÉRENCIATEUR]
Meta description : "[META 155 chars max]"
OpenGraph dans le head. Mobile-first. Pas d'animations lourdes.
```

---

## NOTES DE VERSION

v1.0 — Avril 2026
- 6 skins initiaux créés
- DARK et PRESTIGE et GLOBAL validés sur cas clients réels
- BOLD, SOFT, EDITORIAL à valider sur prochain client

## À FAIRE (prochaines versions)
- [ ] Ajouter un cas client de référence pour BOLD, SOFT, EDITORIAL
- [ ] Tester les buzzwords sur Lovable et noter les résultats
- [ ] Ajouter variantes de palette pour BOLD (rouge / orange / vert)
- [ ] Créer un skin 07 — LIQUID GLASS (tendance 2026)
- [ ] Intégrer les DESIGN.md correspondants (Dossier 4)
