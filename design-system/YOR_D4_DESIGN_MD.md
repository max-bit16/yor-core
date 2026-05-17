# YOR — DOSSIER 4 : DESIGN.md
# Yamen Global · Version 1.0 · Avril 2026
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QU'EST-CE QU'UN DESIGN.md ?

Concept introduit par Google Stitch. Un fichier markdown plain-text
qui décrit le design system complet d'un projet. Claude Code,
Stitch, et tout agent IA le lit pour générer une UI cohérente sans
avoir à répéter les instructions à chaque session.

Format : un seul fichier markdown à la racine du repo client.
Nom : DESIGN.md

Avantage pour YOR : au lieu de réécrire le skin dans chaque prompt
Claude Code, on place le DESIGN.md une fois dans le repo, et
Claude Code s'y réfère automatiquement pour toutes les modifications
futures (maintenance, ajout de pages, corrections SEO).

RÈGLE : Claude Code ne modifie jamais le design system décrit dans
DESIGN.md sans permission explicite.

---

## COMMENT UTILISER CE FICHIER

1. Identifier le skin du projet (Dossier 1)
2. Copier le DESIGN.md correspondant ci-dessous
3. Remplacer les variables [entre crochets]
4. Placer le fichier à la racine du repo GitHub
5. Dans Claude Code, commencer chaque session par :
   "Read DESIGN.md before making any changes to this project."

---

## DESIGN.md — SKIN 01 DARK

```markdown
# DESIGN.md — [NOM CLIENT]
# YOR Skin: DARK
# Généré par Yamen Global — yamen-global.com

## Identité du projet
- Client : [NOM]
- Secteur : [SECTEUR]
- Ville : [VILLE]
- URL production : [URL]
- Skin YOR : DARK

## Stack technique
- Framework : React + Vite
- Styling : Tailwind CSS
- Icônes : Lucide-React (UNIQUEMENT)
- Polices : Playfair Display + DM Sans (hébergées en local)
- Hébergement : Vercel
- Versioning : GitHub

## Couleurs
- Fond principal : #0D0D0D
- Fond cards : #1A1A1A
- Fond sections alternées : #111111
- Texte principal : #F5F0EB
- Texte secondaire : #888888
- Accent principal : #6B3FA0
- Accent hover : #7B4FB0
- Bordures : #2A2A2A
- Séparateurs : 1px solid #2A2A2A

## Typographie
- Titres (H1, H2, H3) : Playfair Display, italic, variable weight
- Corps : DM Sans, regular/medium
- Labels uppercase : DM Sans, 0.75rem, letter-spacing 0.15em
- H1 : 6rem desktop / 3.5rem mobile, italic
- H2 : 2.5rem desktop / 2rem mobile
- H3 : 1.5rem
- Corps : 1rem / line-height 1.7
- Petits labels : 0.75rem

## Espacements
- Section padding vertical : py-24 md:py-32
- Container max-width : max-w-7xl mx-auto px-6 md:px-12
- Gap cards : gap-6
- Border-radius cards : rounded-2xl
- Border-radius boutons : rounded-full

## Composants

### Bouton principal
- Fond : #6B3FA0
- Texte : #FFFFFF, DM Sans 14px
- Padding : px-8 py-4
- Border-radius : rounded-full
- Hover : bg-[#7B4FB0] transition-colors duration-200

### Bouton secondaire
- Fond : transparent
- Bordure : 1px solid #6B3FA0
- Texte : #F5F0EB
- Hover : bg-[#6B3FA0]/10

### Cards services (Bento Grid)
- Fond : #1A1A1A
- Bordure : 1px solid #2A2A2A
- Padding : p-8
- Border-radius : rounded-2xl
- Hover : border-color #6B3FA0, transition 0.2s

### Stats / Chiffres clés
- Chiffre : Playfair Display, 4rem+, #F5F0EB
- Label : DM Sans uppercase, 0.75rem, #888888

### Badge / Label éditorial
- Fond : #1A1A1A
- Texte : DM Sans uppercase, 0.7rem, letter-spacing 0.2em, #6B3FA0
- Padding : px-4 py-1.5
- Border-radius : rounded-full

## Règles absolues
- JAMAIS d'image IA, de placeholder Unsplash ou stock photo
- JAMAIS d'icône autre que Lucide-React
- JAMAIS de font chargée depuis Google Fonts en production
  (toutes les polices sont en local dans /src/assets/fonts/)
- Un seul H1 par page, contenant le mot-clé principal + ville
- Meta description ≤ 155 caractères
- Pas d'animation lourde (pas de Framer Motion, GSAP, AOS)
- Transitions CSS légères uniquement (duration-200 à duration-300)
- Mobile-first strict

## SEO
- H1 : "[MOT-CLÉ PRINCIPAL] à [VILLE] — [NOM]"
- Meta description : "[META]"
- JSON-LD LocalBusiness dans le head
- Sitemap : /public/sitemap.xml
- Robots : /public/robots.txt
- Images : format .webp, attribut alt non vide, lazy loading
- Bundle JS cible : < 200kb gzippé
```

---

## DESIGN.md — SKIN 02 PRESTIGE

```markdown
# DESIGN.md — [NOM CLIENT]
# YOR Skin: PRESTIGE
# Généré par Yamen Global — yamen-global.com

## Identité du projet
- Client : [NOM]
- Secteur : [SECTEUR]
- Ville : [VILLE]
- URL production : [URL]
- Skin YOR : PRESTIGE

## Stack technique
- Framework : React + Vite
- Styling : Tailwind CSS
- Icônes : Lucide-React (UNIQUEMENT)
- Polices : Playfair Display + DM Sans (hébergées en local)
- Hébergement : Vercel
- Versioning : GitHub

## Couleurs
- Fond principal : #F0EDE6
- Fond cards : #FAFAF7
- Fond sections alternées : #EAE6DE
- Texte principal : #1C1C1C
- Texte secondaire : #666666
- Accent principal : #2C4A3E
- Accent hover : #3A5F52
- Bordures : #E0DBD3
- Séparateurs : 1px solid #E0DBD3

## Typographie
- Titres : Playfair Display, italic, variable weight
- Corps : DM Sans, regular
- Labels uppercase : DM Sans, 0.75rem, letter-spacing 0.15em
- H1 : 4.5rem desktop / 3rem mobile, italic
- H2 : 2rem desktop / 1.75rem mobile
- Corps : 1rem / line-height 1.8
- Citations : Playfair Display italic, 1.25rem, couleur #2C4A3E

## Espacements
- Section padding vertical : py-24 md:py-36
- Container : max-w-6xl mx-auto px-8 md:px-16
- Gap cards : gap-4
- Border-radius cards : rounded-xl
- Border-radius boutons : rounded-sm (sobre, presque carré)

## Composants

### Bouton principal
- Fond : #2C4A3E
- Texte : #FFFFFF, DM Sans 13px, letter-spacing 0.05em
- Padding : px-8 py-3.5
- Border-radius : rounded-sm
- Hover : bg-[#3A5F52]

### Bouton secondaire
- Fond : transparent
- Bordure : 1px solid #2C4A3E
- Texte : #2C4A3E
- Hover : bg-[#2C4A3E]/5

### Cards services
- Fond : #FAFAF7
- Bordure : 1px solid #E0DBD3
- Padding : p-8
- Border-radius : rounded-xl
- Hover : border-color #2C4A3E, transition 0.2s

### Citation / Quote
- Fond : transparent
- Bordure gauche : 3px solid #2C4A3E
- Padding gauche : pl-6
- Texte : Playfair italic 1.2rem #1C1C1C

### Badge secteur client
- Fond : transparent
- Bordure : 1px solid #E0DBD3
- Texte : DM Sans uppercase 0.65rem letter-spacing 0.2em #666666
- Padding : px-3 py-1

## Règles absolues
- JAMAIS d'image IA, placeholder, stock photo
- JAMAIS d'icône autre que Lucide-React
- JAMAIS de font externe en production
- Un seul H1 par page
- Pas d'animation — ce skin est intentionnellement statique
- Mobile-first strict

## SEO
- H1 : "[MOT-CLÉ] à [VILLE] — [NOM]"
- Meta description : "[META]"
- JSON-LD LocalBusiness
- Sitemap, robots.txt, images .webp, alt non vide
```

---

## DESIGN.md — SKIN 03 GLOBAL

```markdown
# DESIGN.md — [NOM CLIENT]
# YOR Skin: GLOBAL
# Généré par Yamen Global — yamen-global.com

## Identité du projet
- Client : [NOM]
- Secteur : [SECTEUR]
- Ville : [VILLE]
- URL production : [URL]
- Skin YOR : GLOBAL

## Stack technique
- Framework : React + Vite
- Styling : Tailwind CSS
- Icônes : Lucide-React (UNIQUEMENT)
- Polices : Playfair Display + DM Sans (hébergées en local)
- Hébergement : Vercel
- Versioning : GitHub

## Couleurs
- Fond principal : #FAFAF8
- Fond sections alternées : #F2EFE9
- Texte principal : #111111
- Texte secondaire : #777777
- Accent principal : #C8965A
- Accent hover : #B8854A
- Bordures : #E5E0D8
- Séparateurs : 1px solid #E5E0D8

## Typographie
- Titres : Playfair Display, italic
- Corps : DM Sans, regular/light
- Labels : DM Sans uppercase 0.7rem letter-spacing 0.2em
- H1 : 5rem desktop / 3rem mobile
- H2 : 2.25rem desktop / 1.75rem mobile
- Corps : 1rem / line-height 1.8
- Très large espace blanc entre les sections

## Espacements
- Section padding : py-28 md:py-44 (très aéré)
- Container : max-w-6xl mx-auto px-8 md:px-16
- Gap : gap-8 à gap-16 selon contexte
- Border-radius : rounded-2xl
- Marges internes larges : padding minimum p-10

## Composants

### Bouton principal
- Fond : #C8965A
- Texte : #FFFFFF DM Sans 14px
- Padding : px-8 py-4
- Border-radius : rounded-full
- Hover : bg-[#B8854A]

### Stats géantes
- Chiffre : Playfair Display 5rem, #111111
- Label : DM Sans uppercase 0.7rem #777777
- Séparateur entre stats : 1px vertical #E5E0D8

### Process step
- Numéro : Playfair Display 5rem, opacity-15, #111111
- Titre : DM Sans 1rem bold #111111
- Description : DM Sans 0.9rem #777777

### Badges secteurs
- Fond : #F2EFE9
- Texte : DM Sans uppercase 0.7rem #777777
- Padding : px-4 py-2
- Border-radius : rounded-full

## Règles absolues
- L'espace blanc EST le design — ne pas compresser les sections
- JAMAIS d'image IA, placeholder, stock photo
- JAMAIS d'icône autre que Lucide-React
- JAMAIS de font externe en production
- Transitions légères uniquement (200ms)
- Mobile-first strict

## SEO
- H1 : "[MOT-CLÉ] à [VILLE] — [NOM]"
- Meta description : "[META]"
- JSON-LD LocalBusiness
- Sitemap, robots.txt, images .webp, alt non vide
```

---

## DESIGN.md — SKIN 04 BOLD

```markdown
# DESIGN.md — [NOM CLIENT]
# YOR Skin: BOLD
# Généré par Yamen Global — yamen-global.com

## Identité du projet
- Client : [NOM]
- Secteur : [SECTEUR]
- Ville : [VILLE]
- URL production : [URL]
- Skin YOR : BOLD
- Couleur accent choisie : [#E63329 / #F5A623 / #1DB954 / AUTRE]

## Stack technique
- Framework : React + Vite
- Styling : Tailwind CSS
- Icônes : Lucide-React (UNIQUEMENT)
- Polices : Playfair Display + DM Sans (hébergées en local)
- Hébergement : Vercel
- Versioning : GitHub

## Couleurs
- Fond principal : #FFFFFF
- Fond sections sombres : #0A0A0A
- Texte sur fond blanc : #0A0A0A
- Texte sur fond noir : #FFFFFF
- Accent : [COULEUR CHOISIE]
- Accent hover : [COULEUR CHOISIE -10% luminosité]
- Bordures fond blanc : 2px solid #0A0A0A (épaisse, brutalist)
- Bordures fond noir : 2px solid [ACCENT]

## Typographie
- Titres : Playfair Display, bold (pas italic pour ce skin)
- Corps : DM Sans, medium
- H1 : 7rem desktop / 3.5rem mobile, bold
- H2 : 3rem desktop / 2rem mobile
- Corps : 1rem / line-height 1.6
- Tout en majuscules pour les labels : uppercase tracking-widest

## Espacements
- Section padding : py-20 md:py-28
- Container : max-w-7xl mx-auto px-6 md:px-12
- Gap cards : gap-0 (cards collées, grille stricte)
- Border-radius : rounded-none (0) ou rounded-sm (2px) maximum
- Pas de border-radius généreux — esthétique brutalist

## Composants

### Bouton principal
- Fond : [ACCENT]
- Texte : #FFFFFF DM Sans 14px bold uppercase
- Padding : px-10 py-4
- Border-radius : rounded-none
- Border : 2px solid [ACCENT]
- Hover : fond #0A0A0A border #0A0A0A

### Réassurance badges
- Fond : [ACCENT]
- Texte : #FFFFFF DM Sans bold uppercase 0.8rem
- Padding : px-6 py-3
- Border-radius : rounded-none

### Cards services
- Fond : #FFFFFF
- Bordure : 2px solid #0A0A0A
- Padding : p-8
- Border-radius : rounded-none
- Hover : fond #0A0A0A texte #FFFFFF bordure #0A0A0A

### Section sombre (alternée)
- Fond : #0A0A0A
- Texte : #FFFFFF
- Accent visible : [COULEUR CHOISIE]

## Règles absolues
- Esthétique brutalist — angles droits, contrastes forts
- JAMAIS d'image IA, placeholder, stock photo
- JAMAIS d'icône autre que Lucide-React
- JAMAIS de font externe en production
- Pas d'animation — ce skin est intentionnellement brut
- Mobile-first strict

## SEO
- H1 : "[MOT-CLÉ] à [VILLE] — [NOM]"
- Meta description : "[META]"
- JSON-LD LocalBusiness
- Sitemap, robots.txt, images .webp, alt non vide
```

---

## DESIGN.md — SKIN 05 SOFT

```markdown
# DESIGN.md — [NOM CLIENT]
# YOR Skin: SOFT
# Généré par Yamen Global — yamen-global.com

## Identité du projet
- Client : [NOM]
- Secteur : [SECTEUR]
- Ville : [VILLE]
- URL production : [URL]
- Skin YOR : SOFT

## Stack technique
- Framework : React + Vite
- Styling : Tailwind CSS
- Icônes : Lucide-React (UNIQUEMENT)
- Polices : Playfair Display + DM Sans (hébergées en local)
- Hébergement : Vercel
- Versioning : GitHub

## Couleurs
- Fond principal : #FDF8F3
- Fond cards : #FFFFFF
- Fond sections alternées : #F0F7F5
- Texte principal : #3D2B1F
- Texte secondaire : #8A7060
- Accent terre cuite : #D4856A
- Accent sauge : #7EB5A6
- Bordures : #EDE3D8
- Séparateurs : 1px solid #EDE3D8

## Typographie
- Titres : Playfair Display italic, doux
- Corps : DM Sans regular
- H1 : 4.5rem desktop / 2.75rem mobile, italic
- H2 : 2rem desktop / 1.5rem mobile
- Corps : 1rem / line-height 1.9 (aéré, lisible)
- Labels : DM Sans 0.75rem, couleur secondaire

## Espacements
- Section padding : py-20 md:py-32
- Container : max-w-5xl mx-auto px-8 md:px-12
- Gap : gap-6
- Border-radius : rounded-2xl partout (généreux, doux)
- Ombres : shadow-sm uniquement (légères, chaudes)

## Composants

### Bouton principal
- Fond : #D4856A
- Texte : #FFFFFF DM Sans 14px
- Padding : px-8 py-4
- Border-radius : rounded-full
- Hover : bg-[#C4755A]

### Bouton secondaire
- Fond : transparent
- Bordure : 1px solid #D4856A
- Texte : #D4856A
- Border-radius : rounded-full

### Cards soins / services
- Fond : #FFFFFF
- Ombre : shadow-sm
- Padding : p-8
- Border-radius : rounded-2xl
- Icône Lucide : couleur #7EB5A6

### Icône décorative centrale (hero)
- Taille : w-10 h-10
- Couleur : #D4856A
- Position : mb-8, centrée

### Section témoignage
- Fond : #F0F7F5
- Citation : Playfair italic 1.1rem #3D2B1F
- Auteur : DM Sans 0.85rem #8A7060

## Règles absolues
- Tout doit inspirer calme et confiance
- JAMAIS d'image IA, placeholder, stock photo
- JAMAIS d'icône autre que Lucide-React
- JAMAIS de font externe en production
- Border-radius toujours généreux (min rounded-xl)
- Transitions douces uniquement (300ms ease)
- Mobile-first strict

## SEO
- H1 : "[MOT-CLÉ] à [VILLE] — [NOM]"
- Meta description : "[META]"
- JSON-LD LocalBusiness
- Sitemap, robots.txt, images .webp, alt non vide
```

---

## DESIGN.md — SKIN 06 EDITORIAL

```markdown
# DESIGN.md — [NOM CLIENT]
# YOR Skin: EDITORIAL
# Généré par Yamen Global — yamen-global.com

## Identité du projet
- Client : [NOM]
- Secteur : [SECTEUR]
- Ville : [VILLE]
- URL production : [URL]
- Skin YOR : EDITORIAL

## Stack technique
- Framework : React + Vite
- Styling : Tailwind CSS
- Icônes : Lucide-React (UNIQUEMENT)
- Polices : Playfair Display + DM Sans (hébergées en local)
- Hébergement : Vercel
- Versioning : GitHub

## Couleurs
- Fond : #FFFFFF (blanc pur — jamais de fond coloré)
- Texte principal : #1A1A1A
- Texte secondaire : #888888
- Accent ligne : #C0A882
- Séparateurs : 1px solid #DDDDDD
- Aucune couleur de fond sur les sections — tout blanc

## Typographie
- Titres : Playfair Display weight-300 italic (fin, élégant)
- Corps : DM Sans weight-300 (léger)
- H1 : 5.5rem desktop / 3rem mobile, weight-300 italic
- H2 : 2.25rem desktop / 1.75rem mobile, weight-300
- Corps : 1rem / line-height 2 (très aéré)
- Labels : DM Sans 0.65rem uppercase letter-spacing 0.3em #888888
  format "[N°01 — CATÉGORIE]"
- Citations longues : Playfair 1.1rem italic, indentées

## Espacements
- Sections : py-32 md:py-48 (très grand — l'espace est le design)
- Container : max-w-6xl mx-auto px-8 md:px-20
- Colonnes : grid asymétrique 2fr/1fr ou 3fr/1fr selon contexte
- Séparateurs horizontaux : border-b 1px #DDDDDD entre sections
- Pas de cards, pas de fond coloré, pas de border-radius

## Composants

### Séparateur de section
- border-b 1px solid #DDDDDD
- mb-16 ou mt-16

### Label éditorial
- DM Sans uppercase 0.65rem letter-spacing 0.3em
- Couleur : #888888
- Format : "N°01 — TITRE DE SECTION"
- mb-6

### Numérotation service
- Playfair Display 3.5rem opacity-20 #1A1A1A
- Position relative, flottant à gauche du titre

### Méta colonne (hero)
- DM Sans 0.8rem #888888
- Format label/valeur empilés
- Séparé du contenu principal par 1px vertical #DDDDDD

### CTA éditorial (pas de bouton)
- Texte lien DM Sans 14px #1A1A1A
- Icône ArrowRight Lucide inline
- Underline au hover
- Pas de bouton avec fond coloré

## Règles absolues
- Ce skin n'a PAS de boutons colorés — uniquement des liens texte
- JAMAIS de fond de section coloré
- JAMAIS d'image IA, placeholder, stock photo
- JAMAIS d'icône autre que Lucide-React
- JAMAIS de font externe en production
- Pas d'animation
- Mobile-first strict

## SEO
- H1 : "[MOT-CLÉ] à [VILLE] — [NOM]"
- Meta description : "[META]"
- JSON-LD LocalBusiness
- Sitemap, robots.txt, images .webp, alt non vide
```

---

## PROMPT CLAUDE CODE — LECTURE DU DESIGN.md

À coller dans Claude Code au début de chaque session sur un projet
YOR qui a un DESIGN.md à la racine :

```
Read DESIGN.md at the root of this project before doing anything.
Respect all design tokens, colors, typography, and absolute rules
defined in DESIGN.md for every change you make.

If a requested change would break the design system defined in
DESIGN.md (wrong color, wrong font, wrong border-radius, adding
an image), warn me before proceeding.

Do not modify DESIGN.md unless I explicitly ask you to update it.
```

---

## COMMENT METTRE À JOUR UN DESIGN.md

Quand le design system évolue (nouveau cas client, nouvelle
décision de palette, nouveau composant), mettre à jour le
DESIGN.md correspondant dans ce dossier ET dans le repo client.

Format de mise à jour :
- Incrémenter la version en commentaire en tête de fichier
- Documenter le changement dans la section CHANGELOG en bas

Exemple d'ajout dans le repo client :
```
# CHANGELOG DESIGN.md
v1.1 — [DATE] : Ajout couleur accent secondaire #XXX pour badges
v1.0 — [DATE] : Création initiale
```

---

## NOTES DE VERSION

v1.0 — Avril 2026
- 6 DESIGN.md créés, un par skin YOR
- DARK, PRESTIGE, GLOBAL validés sur cas clients réels
- BOLD, SOFT, EDITORIAL à valider sur prochains projets
- Prompt Claude Code de lecture inclus

## À FAIRE (prochaines versions)
- [ ] Tester le DESIGN.md DARK sur un nouveau projet
      et noter ce que Claude Code interprète bien / mal
- [ ] Ajouter section "Composants Lovable" dans chaque DESIGN.md
      (noms exacts des composants générés par Lovable)
- [ ] Créer script d'extraction DESIGN.md depuis Google Stitch
      (pointer Stitch sur yamen-global.com pour extraire le GLOBAL)
- [ ] Synchroniser DESIGN.md avec le Dossier 1 Skins à chaque
      mise à jour de palette
