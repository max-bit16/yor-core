# YOR — Protocole Entretien Design
> Pour démarrer : dis "nouveau projet YOR" + colle les infos du questionnaire client.
> Claude conduit l'entretien bloc par bloc et génère le prompt Lovable en sortie.

---

## Instructions pour Claude

À chaque nouveau projet YOR, conduire l'entretien dans cet ordre exact.
Poser **une question à la fois**. Attendre la réponse avant de passer à la suivante.
Ne pas proposer de défaut silencieux — toujours demander.
À la fin du Bloc 6, générer le prompt Lovable complet, prêt à coller.

---

## Bloc 1 — Mode & palette (fondation visuelle)

**Q1 — Mode général**
> Quel est le registre visuel du site ?
> A) Sombre (fond noir/anthracite, texte clair) — premium, moderne, impactant
> B) Clair (fond blanc/ivoire, texte sombre) — propre, lisible, rassurant
> C) Mixte (hero sombre, reste clair) — contraste fort en entrée, lecture facile ensuite

**Q2 — Couleur d'accent**
> Propose 4–5 options selon le secteur client (basées sur les infos du brief).
> Exemples : violet profond #6B3FA0 / bleu acier #2D6A9F / vert mousse #4A7C59 /
> terre cuite #C1693A / or chaud #C9A84C / rouge bordeaux #8B2635
> → Quelle couleur reflète le mieux le positionnement du client ?

**Q3 — Fond secondaire / cartes**
> Les blocs et cards auront un fond :
> A) Légèrement plus clair que le fond principal (différenciation subtile)
> B) Bordure fine uniquement, même fond
> C) Glassmorphism léger (effet verre dépoli — backdrop blur)

---

## Bloc 2 — Typographie

**Q4 — Police de titre (H1, H2)**
> A) Playfair Display — serif élégant, éditorial, fort en italic
> B) Cormorant Garamond — serif fin, luxueux, délicat
> C) Fraunces — serif expressif, organique, chaleureux
> D) Syne — sans-serif géométrique, tech, contemporain
> E) DM Serif Display — serif lisible, propre, professionnel

**Q5 — Police de corps (texte courant, labels)**
> A) DM Sans — neutre, très lisible, polyvalent
> B) Inter — technique, propre, standard moderne
> C) Plus Jakarta Sans — légèrement plus personnalisé, humaniste
> D) Outfit — géométrique doux, moderne sans être froid

**Q6 — Style des titres**
> A) Très grands et italics (96px+, Playfair italic en hero)
> B) Grands et droits (72px, impact sans italique)
> C) Moyen, espacé (48–56px, lettres espacées, ton éditorial)

---

## Bloc 3 — Hero section

**Q7 — Format du hero**
> A) Typographique pur — titre géant + sous-titre + CTA, aucune image
> B) Titre + image client (photo fournie ou banque libre) en arrière-plan ou côté droit
> C) Titre + SVG animé en arrière-plan (formes géométriques, particules, code uniquement)
> D) Titre + vidéo loop en fond (à générer avec Nano Banana/Flow ou fournie par le client)

**Q8 — Chiffres clés dans le hero ?**
> Afficher 2–3 stats géantes sous le titre (ex : "48h de livraison", "100% satisfaction", "12 ans d'expérience") ?
> A) Oui — lesquels ? (préciser)
> B) Non

**Q9 — CTA principal**
> Quel est l'objectif de conversion prioritaire ?
> A) Formulaire de contact (scroll vers section contact)
> B) Appel téléphonique direct
> C) Devis en ligne
> D) Prise de rendez-vous
> E) Autre (préciser)

---

## Bloc 4 — Sections & structure

**Q10 — Quelles sections activer ?**
> Cocher tout ce qui s'applique :
> [ ] Services / Prestations
> [ ] À propos / Histoire
> [ ] Équipe
> [ ] Réalisations / Portfolio
> [ ] Témoignages clients
> [ ] Chiffres clés / Stats
> [ ] Processus / Comment ça marche
> [ ] FAQ
> [ ] Blog / Articles
> [ ] Contact / Formulaire
> [ ] Autre (préciser)

**Q11 — Format de présentation des services**
> A) Bento Grid asymétrique (2 grands + 4 petits) — dynamique, moderne
> B) Cards égales en grille (3 ou 4 colonnes) — clair, scannable
> C) Alternance gauche/droite (texte + visuel en miroir) — narratif, détaillé
> D) Liste avec icônes (compact, sans image) — efficace, direct
> E) Accordéon expansible — adapté si beaucoup de services

---

## Bloc 5 — Images & visuels

**Q12 — Stratégie image**
> A) Zéro image — typographie + icônes SVG uniquement (performance maximale)
> B) Photos fournies par le client (upload ou lien)
> C) Banque libre (Unsplash/Pexels) — préciser le style souhaité
> D) Illustrations vectorielles (unDraw, Storyset) — ton doux et moderne
> E) SVG animés générés (formes, icônes en mouvement)
> F) Visuels générés avec Nano Banana Pro (contextualiser au secteur)

**Q13 — Si images présentes : format d'affichage**
> A) Plein écran / fond de section
> B) Vignettes arrondies dans les cards
> C) Galerie / grille photo
> D) Image unique côté droit ou gauche dans les sections
> E) Pas d'image dans les sections — uniquement dans le hero

---

## Bloc 6 — Ambiance & finitions

**Q14 — Mot-clé de vibe**
> En un ou deux mots, quel doit être le ressenti du visiteur en arrivant sur le site ?
> (Exemples : luxueux / artisanal / rassurant / percutant / chaleureux / éditorial / technique / local / haut de gamme / accessible)

**Q15 — Animations**
> A) Aucune animation — performance pure, sobre
> B) Subtiles (fade-in au scroll uniquement)
> C) Présentes (hover sur cards, transitions de sections, quelques effets d'entrée)
> D) Fortes (parallax, révélation de texte, animations marquantes)

**Q16 — Référence visuelle (optionnel)**
> Un site, une marque, une couleur, une image que tu aimerais utiliser comme inspiration ?
> (Si non, passer directement à la génération du prompt)

---

## Sortie — Génération du prompt Lovable

Une fois les 16 questions répondues, Claude génère le prompt Lovable complet dans ce format :

```
Crée un site vitrine professionnel pour [NOM], [SECTEUR] basé(e) à [VILLE].
Cible : [CIBLE]. Objectif principal : [CTA].

CONTRAINTE ABSOLUE : [règle image selon Q12]

Stack : React + Tailwind CSS + Lucide-React
Polices : [Q4] pour les titres · [Q5] pour le corps

Structure HTML sémantique :
— H1 unique : "[MOT-CLÉ SECTEUR] à [VILLE] — [NOM]"
— H2 par section
— aria-label sur chaque icône Lucide

Palette :
— Mode : [Q1]
— Fond : [couleur selon Q1]
— Accent : [Q2]
— Cards/blocs : [Q3]

COHÉRENCE INTER-SECTIONS :
Même border-radius, même palette, même style de bouton, même espacement vertical
dans toutes les sections sans exception.

Hero :
— [Format selon Q7]
— Titre [Q6], police [Q4]
— [Stats selon Q8]
— CTA : [Q9]

Sections (dans l'ordre) :
[Liste des sections selon Q10, avec format selon Q11]

Visuels :
[Stratégie selon Q12 + format selon Q13]

Ambiance : [Q14] — [Q15 pour les animations]
[Référence visuelle si Q16]

Services : [SERVICES du brief]
USP : [DIFFÉRENCIATEUR du brief]
FAQ : [FAQ du brief]
Meta description : "[À générer selon secteur + ville + USP]"
OpenGraph dans le head.
Mobile-first.
```

---

*Ce protocole remplace tout template fixe. Le prompt est construit de zéro à chaque projet.*
*Durée moyenne de l'entretien : 10–15 minutes.*
*Source : workflow YOR — avril 2026*
