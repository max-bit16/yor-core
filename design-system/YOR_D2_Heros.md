# YOR — DOSSIER 2 : BIBLIOTHÈQUE DE HÉROS
# Yamen Global · Version 1.0 · Avril 2026
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## COMMENT UTILISER CE FICHIER

Le hero est la section la plus importante d'un site vitrine.
C'est ce qui décide en 3 secondes si le visiteur reste ou part.

Chaque prompt ici est autonome — il génère uniquement la section
hero. À coller dans Lovable APRÈS avoir posé la structure globale
avec le prompt du Dossier 1 (Skins), ou en remplacement du hero
par défaut si le résultat initial ne convient pas.

RÈGLE PAGESPEED : aucune animation lourde, pas de vidéo autoplay,
pas de librairie tierce (Framer Motion, GSAP). Tout doit être
réalisable en CSS Tailwind natif. Les transitions légères (fade,
slide 0.3s) sont acceptées. Les animations complexes doivent être
testées sur PageSpeed avant livraison.

RAPPEL : aucune image IA, aucun placeholder, aucun stock photo.

---

## TABLEAU RÉCAPITULATIF

| Hero | Ambiance | Poids performance | Skin compatible |
|------|----------|-------------------|-----------------|
| 01 TYPOGRAPHIQUE | Typographie seule, aucun effet | ✅ Ultra léger | Tous |
| 02 GRADIENT ANIMÉ | Fond dégradé CSS animé | ✅ Léger | DARK, GLOBAL |
| 03 STATS GÉANTES | Chiffres XXL, impact immédiat | ✅ Ultra léger | DARK, BOLD |
| 04 SPLIT SCREEN | 2 colonnes texte / visuel | ✅ Léger | PRESTIGE, GLOBAL |
| 05 EDITORIAL | Layout magazine, colonnes | ✅ Ultra léger | EDITORIAL, PRESTIGE |
| 06 PLEIN ÉCRAN SOMBRE | Fond noir, texte centré | ✅ Léger | DARK, BOLD |
| 07 LIQUID GLASS | Glassmorphism, fond flou | ⚠️ Tester PageSpeed | DARK, GLOBAL |
| 08 MINIMAL CENTRÉ | Maximal épure, tout en blanc | ✅ Ultra léger | SOFT, EDITORIAL |

---

## HERO 01 — TYPOGRAPHIQUE

**Ambiance :** La typographie EST le design. Rien d'autre.
**Compatible :** Tous les skins YOR.
**Performance :** Ultra léger — zéro effet, zéro ressource externe.

```
Remplace uniquement la section hero existante par celle-ci.
Garde tout le reste du site intact.

HERO TYPOGRAPHIQUE :
— Plein écran (min-h-screen)
— Centré verticalement et horizontalement
— Fond : [COULEUR FOND DU SKIN]
— Pas d'image, pas d'icône, pas de fond décoratif

Contenu dans l'ordre (centré) :
1. Label uppercase très petit (tracking-widest, text-xs,
   couleur accent) : "[SECTEUR] · [VILLE]"
2. H1 Playfair Display italic, 88px desktop / 52px mobile,
   couleur texte principal : "[ACCROCHE PRINCIPALE]"
3. Sous-titre DM Sans, 18px, couleur texte secondaire,
   max-w-lg centré : "[DESCRIPTION COURTE]"
4. 2 boutons inline : CTA principal (fond accent, texte blanc)
   + CTA secondaire (outline, bordure accent)
5. Ligne séparatrice fine (1px, couleur bordure), width 80px,
   centrée, mt-8

Aucune animation. Aucun effet hover sur le fond.
Transitions légères uniquement sur les boutons (0.2s ease).
Mobile-first — empiler verticalement sous 768px.
```

---

## HERO 02 — GRADIENT ANIMÉ

**Ambiance :** Fond en mouvement doux, premium sans lourdeur.
**Compatible :** Skins DARK, GLOBAL.
**Performance :** Léger si limité à CSS — animation keyframes pure.

```
Remplace uniquement la section hero existante par celle-ci.
Garde tout le reste du site intact.

HERO GRADIENT ANIMÉ :
— Plein écran (min-h-screen)
— Fond : dégradé radial animé en CSS pur (keyframes Tailwind)
  Couleurs pour DARK : de #0D0D0D vers #1a0533 vers #0D0D0D
  Couleurs pour GLOBAL : de #FAFAF8 vers #F2EFE9 vers #FAFAF8
— Animation : 8s ease infinite alternate (très lente, subtile)
— Implémentation en CSS pur uniquement — pas de Framer Motion,
  pas de canvas, pas de WebGL

Contenu dans l'ordre :
1. Label uppercase tracking-widest text-xs couleur accent :
   "[SECTEUR] · [VILLE]"
2. H1 Playfair Display italic, 96px desktop / 56px mobile :
   "[ACCROCHE]"
3. Sous-titre DM Sans 18px max-w-xl : "[DESCRIPTION]"
4. 3 stats en ligne (flex gap-12, mt-10) :
   — Chiffre en Playfair 48px + label DM Sans 12px uppercase
   — "[CHIFFRE 1]" / "[CHIFFRE 2]" / "[CHIFFRE 3]"
5. CTA principal bouton (fond accent)

IMPORTANT : tester le score PageSpeed après intégration.
Si Performance < 95 sur mobile, supprimer l'animation keyframes
et garder le dégradé statique.
```

---

## HERO 03 — STATS GÉANTES

**Ambiance :** Les chiffres parlent. Impact immédiat, confiance instantanée.
**Compatible :** Skins DARK, BOLD, GLOBAL.
**Performance :** Ultra léger — chiffres en pur HTML/CSS.

```
Remplace uniquement la section hero existante par celle-ci.
Garde tout le reste du site intact.

HERO STATS GÉANTES :
— Plein écran (min-h-screen)
— Layout : 2 colonnes sur desktop (60% texte / 40% stats)
  Empilé sur mobile (texte en haut, stats en bas)
— Fond : [COULEUR FOND DU SKIN]

Colonne gauche :
1. Label uppercase text-xs tracking-widest couleur accent
2. H1 Playfair italic 80px desktop / 48px mobile
3. Description DM Sans 16px max-w-sm
4. CTA bouton fond accent

Colonne droite — grille 2x2 de stats :
Chaque stat :
— Chiffre Playfair Display 72px bold couleur accent
— Label DM Sans 12px uppercase tracking-wide couleur secondaire
— Séparateur fin en dessous

Stats à remplir : [STAT 1] / [STAT 2] / [STAT 3] / [STAT 4]
(ex : "12 ans" / "+200 clients" / "48h" / "100% satisfaits")

Aucune animation. Aucun compteur JavaScript.
Chiffres statiques uniquement — indispensable pour PageSpeed.
```

---

## HERO 04 — SPLIT SCREEN

**Ambiance :** Professionnel, structuré, deux zones distinctes.
**Compatible :** Skins PRESTIGE, GLOBAL, EDITORIAL.
**Performance :** Léger.

```
Remplace uniquement la section hero existante par celle-ci.
Garde tout le reste du site intact.

HERO SPLIT SCREEN :
— Plein écran (min-h-screen)
— Layout : 2 colonnes 50/50 sur desktop, empilées sur mobile
— Pas de gap entre les colonnes — collées

Colonne gauche (fond [COULEUR FOND SKIN]) :
— Padding généreux (px-16 py-24)
— Label uppercase text-xs tracking-widest couleur accent
— H1 Playfair italic 72px
— Description DM Sans 16px max-w-sm mt-6
— CTA bouton mt-8

Colonne droite (fond légèrement différent — 5% plus sombre) :
— Padding identique
— 4 à 5 éléments de confiance en liste verticale :
  chaque élément = icône Lucide (Check ou ArrowRight)
  couleur accent + texte DM Sans 15px
  (ex : "Livraison en 48h", "Certifié XYZ", etc.)
— En bas : mention courte DM Sans italic 13px couleur secondaire

Ligne de séparation entre les deux colonnes :
— 1px vertical couleur bordure (pas de box-shadow)

Mobile : colonne gauche d'abord, droite dessous, fond unifié.
```

---

## HERO 05 — EDITORIAL

**Ambiance :** Magazine, grille asymétrique, lecture longue.
**Compatible :** Skins EDITORIAL, PRESTIGE.
**Performance :** Ultra léger.

```
Remplace uniquement la section hero existante par celle-ci.
Garde tout le reste du site intact.

HERO EDITORIAL :
— Hauteur : auto (pas de plein écran) — py-32 md:py-44
— Fond blanc pur ou crème selon le skin
— Grid asymétrique : 3 colonnes (2fr 1px 1fr)
  — Colonne 1 (grande) : contenu principal
  — Colonne 2 : séparateur vertical 1px couleur bordure
  — Colonne 3 : méta-information

Colonne principale :
— Label éditorial uppercase text-xs tracking-[4px] couleur accent
  format : "N°01 — [SECTEUR]"
— H1 Playfair weight-300 italic, 96px desktop / 52px mobile,
  line-height très serré (leading-none)
— Sous-titre DM Sans 15px max-w-sm mt-8 couleur secondaire

Colonne méta (visible desktop uniquement) :
— 3 à 4 informations courtes en liste verticale
  format : label uppercase 10px + valeur DM Sans 13px
  (ex : "LOCALISATION / Paris 8e", "FONDÉ / 2011")
— En bas : CTA texte seul (pas de bouton) avec ArrowRight Lucide

Pas d'animation. Pas de fond décoratif.
Tout repose sur la typographie et l'espacement.
```

---

## HERO 06 — PLEIN ÉCRAN SOMBRE

**Ambiance :** Cinématique, dramatique, fond noir total.
**Compatible :** Skins DARK, BOLD.
**Performance :** Léger.

```
Remplace uniquement la section hero existante par celle-ci.
Garde tout le reste du site intact.

HERO PLEIN ÉCRAN SOMBRE :
— Plein écran strict (h-screen overflow-hidden)
— Fond : #0A0A0A (noir profond)
— Contenu centré verticalement et horizontalement

Contenu dans l'ordre :
1. Badge centré : fond #1A1A1A, texte DM Sans 11px uppercase
   tracking-widest couleur accent, padding px-4 py-1.5 rounded-full
   texte : "[SECTEUR] · [VILLE]"
2. H1 Playfair italic 110px desktop / 56px mobile, blanc pur,
   line-height 1, max-w-4xl centré
3. Sous-titre DM Sans 17px couleur #888888, max-w-md centré, mt-6
4. Bouton CTA centré mt-10 : fond accent #6B3FA0, texte blanc,
   px-8 py-4 rounded-full, texte DM Sans 14px

En bas de l'écran (absolute bottom-8 left-0 right-0) :
— Flex row space-between px-12
— Gauche : texte DM Sans 11px uppercase tracking-wide #444444
  "[NOM ENTREPRISE]"
— Centre : scroll indicator — petit texte "Scroll" + trait 1px
  vertical animé (CSS only, hauteur 24px, keyframes opacity)
— Droite : texte DM Sans 11px #444444 "[ANNÉE]"

Scroll indicator : CSS keyframes uniquement.
Vérifier PageSpeed si animé.
```

---

## HERO 07 — LIQUID GLASS

**Ambiance :** Glassmorphism, moderne, profondeur visuelle.
**Compatible :** Skins DARK, GLOBAL.
**Performance :** ⚠️ À tester impérativement sur PageSpeed.
**Note :** backdrop-filter peut impacter les performances mobile.
Désactiver sur mobile si score < 90.

```
Remplace uniquement la section hero existante par celle-ci.
Garde tout le reste du site intact.

HERO LIQUID GLASS :
— Plein écran (min-h-screen)
— Fond : dégradé statique (pas animé)
  DARK : linear-gradient(135deg, #0D0D0D 0%, #1a0533 100%)
  GLOBAL : linear-gradient(135deg, #FAFAF8 0%, #EDE8E0 100%)

Carte centrale glassmorphism (max-w-2xl centré, my-auto mx-auto) :
— background: rgba(255,255,255,0.05) pour DARK
  background: rgba(255,255,255,0.7) pour GLOBAL
— backdrop-filter: blur(12px) — désactiver sur mobile
— border: 1px solid rgba(255,255,255,0.1)
— border-radius: 24px
— padding: p-12 md:p-16

Contenu dans la carte :
1. Label uppercase text-xs tracking-widest couleur accent
2. H1 Playfair italic 80px desktop / 44px mobile
3. Description DM Sans 16px max-w-md
4. Bouton CTA fond accent

En dehors de la carte (position absolute, coins) :
— 2 à 3 petits badges DM Sans 11px glassmorphism léger
  contenant les chiffres clés
  (backdrop-filter uniquement sur desktop)

CRITIQUE : tester pagespeed.web.dev avant livraison.
Si Performance mobile < 90 → passer en HERO 01 TYPOGRAPHIQUE.
```

---

## HERO 08 — MINIMAL CENTRÉ

**Ambiance :** Épure absolue, maximalisme du vide.
**Compatible :** Skins SOFT, EDITORIAL.
**Performance :** Ultra léger.

```
Remplace uniquement la section hero existante par celle-ci.
Garde tout le reste du site intact.

HERO MINIMAL CENTRÉ :
— Hauteur : min-h-[80vh]
— Fond : blanc pur ou fond très doux du skin
— Tout centré, beaucoup d'espace blanc

Contenu dans l'ordre (centré, max-w-lg) :
1. Icône Lucide centrée, taille w-8 h-8, couleur accent,
   mb-8 (choisir selon le secteur : Heart, Leaf, Star, Sparkles)
2. H1 Playfair italic 64px desktop / 40px mobile,
   couleur texte, line-height serré
3. Description DM Sans 16px couleur secondaire, mt-4
4. Séparateur horizontal fin (1px, 40px de large, centré, mt-8)
5. CTA texte seul (pas de bouton) + icône ArrowRight Lucide
   couleur accent, mt-6, DM Sans 14px

Aucune décoration, aucun fond coloré, aucun badge.
L'espace blanc est le design.
Transitions légères uniquement sur le CTA (underline au hover).
```

---

## RÈGLES GÉNÉRALES POUR LES HÉROS YOR

### Performance
- Aucune librairie d'animation externe (Framer Motion, GSAP, AOS)
- Les keyframes CSS Tailwind sont autorisées si elles ne bloquent pas le rendu
- backdrop-filter uniquement sur desktop, désactivé sur mobile
- Aucune image en fond — uniquement CSS (couleurs, dégradés)
- Tester systématiquement sur pagespeed.web.dev avant livraison

### Typographie
- H1 toujours en Playfair Display italic
- Sous-titres toujours en DM Sans
- Taille minimum H1 mobile : 40px
- Taille maximum H1 desktop : 110px

### Structure HTML
- Un seul H1 par page
- Le H1 doit contenir le mot-clé principal et la ville
- Les stats et chiffres sont des éléments <p> ou <span> — jamais des H2
- CTA principal = balise <a> avec href vers #contact ou page contact

### Combinaisons recommandées (Skin + Hero)

| Skin | Hero recommandé | Hero alternatif |
|------|-----------------|-----------------|
| DARK | 06 PLEIN ÉCRAN SOMBRE | 02 GRADIENT ANIMÉ |
| PRESTIGE | 04 SPLIT SCREEN | 05 EDITORIAL |
| GLOBAL | 03 STATS GÉANTES | 02 GRADIENT ANIMÉ |
| BOLD | 06 PLEIN ÉCRAN SOMBRE | 03 STATS GÉANTES |
| SOFT | 08 MINIMAL CENTRÉ | 01 TYPOGRAPHIQUE |
| EDITORIAL | 05 EDITORIAL | 08 MINIMAL CENTRÉ |

---

## NOTES DE VERSION

v1.0 — Avril 2026
- 8 héros initiaux créés
- Basés sur : MotionSites, Awwwards, Lovable Buzzwords,
  Lovable Prompting Bible, 0xminds hero guide
- Tous adaptés aux contraintes PageSpeed YOR
- Hero 07 LIQUID GLASS à valider sur cas client réel

## À FAIRE (prochaines versions)
- [ ] Tester chaque hero sur PageSpeed et noter les scores
- [ ] Ajouter un hero BENTO (hero = grille bento complète)
- [ ] Ajouter un hero avec Shader Gradient CSS (Dossier ressources)
- [ ] Documenter les héros des 3 cas clients réels (Photo Pro,
      Renaud Voss, Yamen Global) comme références
- [ ] Créer un hero 09 — HORIZONTAL SCROLL (tendance 2026)
