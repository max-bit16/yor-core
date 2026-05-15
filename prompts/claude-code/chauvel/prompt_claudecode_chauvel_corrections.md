PROMPT CLAUDE CODE — CORRECTIONS POST-CRITIQUE
Étude Chauvel · Design Health Score 28/40 → cible 36/40
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Objectif : corriger l'ensemble des problèmes identifiés
dans le rapport de critique design. Exécuter dans l'ordre
de priorité. Ne touche à aucun élément typographique,
aucune couleur du système de design, aucune structure de
page qui n'est pas explicitement mentionnée ici.

Résumé après chaque étape : ✅ fait / ⚠️ problème / fichier modifié.

━━ P0 — MAP PIN : COULEUR RÉSIDUELLE VIOLET ━━━━━━━━━━━━

Dans pages-core.jsx, autour des lignes 735–740,
le composant MapPlaceholder contient :
  fill="#533afd"
  rgba(83,58,253,0.15)
  rgba(83,58,253,0.3)

Remplace :
  fill="#533afd"            → fill="var(--primary)"
  rgba(83,58,253,0.15)      → rgba(27,45,71,0.15)
  rgba(83,58,253,0.3)       → rgba(27,45,71,0.3)

Trois lignes. Aucun autre changement dans ce fichier
pour cette étape.

━━ P1 — ICON TILES ÉMOTIONNELLEMENT FAUX ━━━━━━━━━━━━━━

Les variantes icon-tile-ruby (rose #ffd1de → #ffb1c5)
et icon-tile-mint (vert #d5f1e3 → #b8e3cd) sont
appliquées à Dommage Corporel et Droit des Étrangers.
Ces couleurs cheerful SaaS sont inappropriées pour des
clients en détresse (blessures corporelles, rétention
immigration).

Étape 1 : Lis ~/.claude/skills/colorize/SKILL.md

Étape 2 : Dans pages-core.jsx et pages-competences.jsx,
repère tous les appels qui utilisent icon-tile-ruby
et icon-tile-mint.

Étape 3 : Remplace icon-tile-ruby par icon-tile (navy
tint, déjà défini dans le système).

Étape 4 : Remplace icon-tile-mint par une nouvelle
variante icon-tile-stone à créer :
  background: rgba(100,90,80,0.08);
  color: var(--ink-secondary);
Ajoute cette variante dans le fichier CSS/Tailwind où
les autres icon-tile-* sont définis.

Étape 5 : Applique icon-tile-stone à Droit des Étrangers
dans tous les composants concernés.

━━ P2 — TÉLÉPHONE HÉRO NON CLIQUABLE ━━━━━━━━━━━━━━━━━━

Dans pages-core.jsx, ligne ~19 :
  <span className="tnum">02.99.66.08.19</span>

Remplace par :
  <a href="tel:0299660819" className="tnum"
     style={{ color: "inherit", textDecoration: "none" }}>
    02.99.66.08.19
  </a>

Vérifie que tous les autres numéros de téléphone dans
le codebase utilisent déjà <a href="tel:">. Si un
<span> contenant un numéro de téléphone est trouvé
ailleurs, applique le même correctif.

━━ P2 — CTA CARD DANS LA GRILLE DES COMPÉTENCES ━━━━━━━

La sixième position de la grille 3×2 de compétences
en homepage est occupée par une card CTA sombre
"Premier rendez-vous". C'est une erreur de catégorie :
un CTA mélangé à du contenu crée de la confusion.

Étape 1 : Lis ~/.claude/skills/layout/SKILL.md

Étape 2 : Dans pages-core.jsx, retire la card CTA sombre
de la grille. La grille doit contenir exactement
5 compétences (ou 6 si une sixième compétence réelle
existe).

Étape 3 : Crée un composant strip full-width indépendant
contenant le même message CTA "Premier rendez-vous",
avec le style card-dark existant.

Étape 4 : Positionne ce strip entre la grille des
compétences et la bande aide juridictionnelle.

La proposition "Premier rendez-vous" est maintenue —
seul son emplacement change.

━━ P2 — MOBILE NAV : ABSENCE DE BOUTON FERMER ━━━━━━━━━

Le menu mobile n'a pas de bouton de fermeture explicite.
L'utilisateur ne peut fermer le menu qu'en cliquant
un lien.

Ajoute un bouton ✕ (icône Lucide X) en haut à droite
du drawer mobile. Au clic : ferme le menu.
Style : même couleur que les liens de nav, 44×44px
zone de tap minimum.

━━ P2 — SIGNAUX D'AUTORITÉ EN HOMEPAGE ━━━━━━━━━━━━━━━━

La homepage ne contient qu'un seul signal d'autorité :
"Depuis 2004". C'est insuffisant pour convertir un
premier visiteur.

Étape 1 : Lis ~/.claude/skills/bolder/SKILL.md

Étape 2 : Ajoute une section autorité entre le hero
et la grille des compétences. Elle doit contenir
exactement 3 éléments :

  · Années d'exercice : calculer dynamiquement depuis
    2004 → new Date().getFullYear() - 2004
    Format : "XX ans de pratique" en Cormorant Garamond
    grand format

  · Affiliation barreau : "Barreau de Rennes"
    avec icône Lucide Scale ou BadgeCheck

  · Domaines : "5 domaines du droit" avec icône
    Lucide BookOpen

Style : bande horizontale sobre, fond var(--surface),
3 colonnes sur desktop, stack sur mobile.
Aucun chiffre inventé. Uniquement des faits vérifiables.

━━ MINOR — CONTRASTES WCAG ━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Dans le nav, le texte "· Avocat" utilise ink-mute
(#647288) sur fond rgba(249,247,242,0.92).
Ratio actuel : 4.3:1 — en dessous du seuil WCAG AA
(4.5:1).

Augmente la valeur de --ink-mute d'un cran :
de #647288 → #5a6577 (ratio ~4.6:1).
Vérifie que ce changement n'affecte pas négativement
d'autres éléments qui utilisent --ink-mute.

━━ MINOR — LIENS FOOTER VERS #/ ━━━━━━━━━━━━━━━━━━━━━━━

Les liens "Mentions légales", "CGV" et "RGPD" dans
le footer pointent tous vers #/ (homepage).
En France, les pages Mentions légales et RGPD sont
obligatoires légalement.

Étape 1 : Crée trois pages minimalistes :
  /mentions-legales
  /cgv
  /rgpd

Contenu minimal requis :
  — Mentions légales : identité éditeur, hébergeur
    (Vercel Inc., San Francisco), avocat responsable
  — RGPD : données collectées (formulaire contact),
    durée conservation, droit d'accès/suppression
  — CGV : peut indiquer "Sur devis, conditions
    communiquées lors du premier rendez-vous"

Étape 2 : Mets à jour les liens footer vers ces routes.

━━ MINOR — CAVEAT AIDE JURIDICTIONNELLE ━━━━━━━━━━━━━━━

Les seuils affichés (≤ 1 007 €, 55%, 25%) changent
chaque année par décret. Ajoute en dessous du tableau :

  <p className="t-caption ink-mute">
    Seuils en vigueur au 1er janvier {new Date().getFullYear()}.
    Ces plafonds sont révisés annuellement par décret.
  </p>

━━ MINOR — SCROLL REVEAL SUR FORMULAIRE CONTACT ━━━━━━━

Les composants .card sur la page Contact peuvent
déclencher le scroll reveal, rendant le formulaire
invisible au chargement initial.

Vérifie si le composant de formulaire et la sidebar
Contact héritent de la classe qui déclenche
l'animation reveal. Si oui : exclure les éléments
du formulaire du scroll reveal (ajouter une exception
dans l'Intersection Observer ou retirer la classe
trigger sur ces éléments spécifiques).

━━ MINOR — COMPTEUR 01/06 ━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Les numéros de section "01 / 06" dans les pages
compétences sont un pattern d'agence créative.
Pour un cabinet d'avocats, ils lisent comme
"regardez notre travail de mise en page".

Retire ces compteurs numériques des pages compétences.
S'ils servent à structurer la navigation visuelle,
remplace par une barre de progression ou un simple
séparateur horizontal.

━━ VALIDATION FINALE ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Après toutes les corrections :

1. Lance le build : npm run build
   → Zéro erreur TypeScript, zéro warning.

2. Vérifie le rendu sur 375px (iPhone SE) :
   · Hero visible sans scroll excessif
   · Téléphone cliquable
   · Nav mobile fermable
   · Grille compétences en colonne unique

3. Produis un rapport final :

   ✅ Corrections appliquées (liste)
   ⚠️ Corrections partielles avec raison
   ❌ Corrections non appliquées avec raison
   Score estimé après corrections : X/40
