# DESIGN LUCIANI — Analyse & Prompt Claude Code
# Yamen Global / YOR · 25 avril 2026
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## ANALYSE DU DESIGN STITCH (MLS Law)

### Ce que tu as choisi

Le design Stitch est un **skin DARK premium** — pas le PRESTIGE crème.
C'est un choix fort et cohérent pour un avocat luxembourgeois qui veut
se démarquer radicalement de la concurrence locale (tous sur des
templates Wix/WordPress beige-bleu).

**Caractéristiques visuelles :**

| Élément | Stitch MLS Law | YOR PRESTIGE (Renaud Voss) |
|---------|---------------|---------------------------|
| Mode | Dark #111111 | Crème #F0EDE6 |
| Accent | Cyan #00F0FF | Vert forêt #2C4A3E |
| Police titres | Inter 600 uppercase | Playfair Display italic |
| Police corps | Inter | DM Sans |
| Cards | Glass shell (gradient border) | Bordurées simples |
| Ambiance | Technique · Premium sombre | Institutionnel · Old-money |

### Ce qu'on garde

- Fond `#111111` avec ambient glow cyan/bleu subtil
- Navbar fixe, backdrop-blur, navigation uppercase tracking-widest
- Hero full-bleed, titre uppercase Inter 72px letter-spacing -0.05em
- Label au-dessus du titre : `· LUXEMBOURG · BARREAU DEPUIS 2007`
- Bento grid pour les domaines avec glass shell (gradient border)
- Section biographie : layout split image-texte + stats géantes
- CTA primaire cyan rempli + CTA ghost bordure blanche
- Footer 4 colonnes sombre

### Ce qu'on adapte (contraintes YOR performance)

**1. GSAP ScrollTrigger → Intersection Observer natif**
Stitch génère du GSAP dans la V3 animation. On ne l'utilise pas.
Zéro bibliothèque d'animation externe. GPU-composited transforms
avec Intersection Observer = zéro impact PageSpeed.

**2. Material Symbols → Lucide React**
Material Symbols = police d'icônes Google (appel réseau).
On les remplace par Lucide React (bundlé, zéro requête externe).

**3. Fluid motion background → CSS only**
Le background animé de la V2 utilise canvas ou WebGL.
On le remplace par un radial-gradient CSS animé en `@keyframes`
sur la propriété `opacity` uniquement — GPU-composited, zéro JS.

**4. Pas de formulaire**
Le "Secure Portal Access" et le formulaire de contact Stitch
→ remplacés par `tel:` et `mailto:` directs (règle YOR).

**5. Images Stitch**
Stitch utilise une photo de façade en noir/blanc ("LUX" typographie).
→ On la remplace par du texte typographique seul (zéro image IA).
Pas d'image = pas de LCP image = score performance maximal.

---

## PROMPT CLAUDE CODE — ÉTUDE LUCIANI

> Coller directement dans Claude Code depuis la racine du repo.
> Le CLAUDE.md du repo chargera automatiquement le YOR SEO Engine.

---

```
Tu vas développer le site vitrine complet de l'Étude LUCIANI,
cabinet d'avocats à Dudelange (Luxembourg).

Stack : Next.js 14 App Router + Tailwind CSS + TypeScript + Lucide React
Hébergement cible : Vercel
Repo : etude-luciani (max-bit16)

━━ DESIGN SYSTEM ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Palette exacte :
  --bg:           #111111
  --bg-surface:   #1C1B1B
  --bg-card:      #201F1F
  --bg-card-high: #2A2A2A
  --text:         #FFFFFF
  --text-muted:   #E5E2E1
  --text-dim:     #B9CABB
  --accent:       #00F0FF
  --accent-blue:  #0A45FF
  --border:       rgba(255,255,255,0.1)
  --border-glow:  rgba(255,255,255,0.2)

Typographie :
  Police unique : Inter (Google Fonts, preload)
  Display hero  : 72px · weight 600 · letter-spacing -0.05em · uppercase
  Headline      : 32px · weight 600 · letter-spacing -0.02em · uppercase
  Label         : 12px · weight 500 · letter-spacing 1.2px · uppercase
  Body          : 16px · weight 400 · line-height 1.6

Glass Shell (traitement carte premium) :
  Outer wrapper : padding 1px, background linear-gradient(135deg,
                  rgba(255,255,255,0.2) 0%, rgba(255,255,255,0.02) 100%)
  Inner surface : background #111111 ou #1C1B1B

Ambient glow (hero background) :
  Deux div absolues pointer-events-none opacity-20 :
  · top-1/4 left-1/4 : 500px×500px bg rgba(0,240,255,0.1) blur-[120px]
  · bottom-1/4 right-1/4 : 400px×400px bg rgba(10,69,255,0.05) blur-[100px]
  CSS-only, zéro JS, zéro bibliothèque d'animation.

Icônes : Lucide React uniquement (pas de Material Symbols)
Animations : Intersection Observer natif, GPU-composited transforms
             (opacity + translateY uniquement), zéro GSAP, zéro Framer Motion
Mobile-first, zéro image IA, zéro placeholder

━━ ARCHITECTURE — 4 PAGES ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

app/
  layout.tsx          → RootLayout : meta, fonts, nav, footer
  page.tsx            → Accueil
  domaines/page.tsx   → Domaines d'intervention
  presentation/page.tsx → Présentation de l'avocat
  contact/page.tsx    → Contact & Localisation

━━ COMPOSANTS GLOBAUX ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Navigation (fixe, backdrop-blur-xl, border-b border-white/10) :
  Logo gauche : "ÉTUDE LUCIANI" — Inter weight 800 tracking-tighter uppercase white
  Liens centre : Domaines · Présentation · Contact
                 DM Sans 11px tracking-widest uppercase #B9CABB hover:#FFFFFF
  CTA droit    : "Prendre rendez-vous" — border-b border-cyan-400 text-cyan-400
                 href="tel:+35220331456"
  Mobile : hamburger Menu (Lucide), fond #111111, liens centrés

Footer (4 colonnes, fond #0E0E0E) :
  Col 1 : "ÉTUDE LUCIANI" + tagline "Cabinet d'avocats · Dudelange · Luxembourg"
  Col 2 : Navigation rapide (Domaines · Présentation · Contact)
  Col 3 : Légal (Mentions légales · Confidentialité)
  Col 4 : Coordonnées (adresse · tél · email si disponible)
  Copyright : "© 2025 Étude LUCIANI · Tous droits réservés"
  Mention : "Membre du Barreau de Luxembourg depuis 2007"

━━ PAGE ACCUEIL (/) ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Section 1 — Hero
  Fond : #111111 + ambient glow (voir design system)
  Label (au-dessus du titre) :
    Puce cyan 4×4px + texte uppercase label-md text-accent-cyan :
    "· DUDELANGE · LUXEMBOURG · BARREAU DEPUIS 2007"
  H1 (72px Inter 600 -0.05em tracking, uppercase, blanc) :
    "AVOCAT À LA COUR
     À DUDELANGE
     LUXEMBOURG"
  Sous-titre (32px Inter 600, text-on-surface-variant, max-w-2xl) :
    "Conseil juridique personnalisé en droit civil, pénal,
     commercial et administratif.
     Consultations en français, luxembourgeois, allemand et anglais."
  CTA primaire : bg-accent-cyan text-neutral-950 uppercase tracking-widest
                 "PRENDRE RENDEZ-VOUS" → tel:+35220331456
  CTA secondaire : border border-white/20 text-white
                   "NOS DOMAINES" → /domaines
  Scroll indicator : "DÉFILER POUR EXPLORER" + ligne verticale cyan dégradée

Section 2 — Domaines (bento grid)
  Header section :
    H2 "DOMAINES D'INTERVENTION"
    Sous-titre label : "Droit civil · Droit pénal · Droit commercial · Droit administratif"
    Compteur droit : "01 / 04"
  Bento grid 4 colonnes, gap-1 :

  Card DROIT CIVIL (col-span-2, row-span-2) — glass-shell taille XL :
    Icône Lucide : <Users /> cyan
    H3 "DROIT CIVIL"
    Texte : "Famille, successions, divorce, garde d'enfants, bail à loyer,
             responsabilité civile, droit du travail."
    Lien : "VOIR LES DÉTAILS →" cyan

  Card DROIT PÉNAL (col-span-2) — glass-shell :
    Icône Lucide : <Shield /> cyan
    H3 "DROIT PÉNAL"
    Sous-label : "Défense · Procédure · Exécution des peines"
    Numéro : "02" text-neutral-700

  Card DROIT COMMERCIAL (col-span-1) — glass-shell :
    Icône Lucide : <Briefcase />
    H3 "COMMERCIAL"

  Card DROIT ADMINISTRATIF (col-span-1) — glass-shell :
    Icône Lucide : <Building2 />
    H3 "ADMINISTRATIF"

Section 3 — Profil (split layout)
  Gauche : Bloc typographique sombre fond #1C1B1B
    Grande lettre "L" en Playfair Display 200px italic opacity-10
    Sur fond : stats empilées
    "2007" — label "BARREAU DE LUXEMBOURG"
    "4"    — label "LANGUES DE CONSULTATION"
    "2014" — label "CRÉATION DE L'ÉTUDE À DUDELANGE"
  Droite :
    Accent line cyan 48px hauteur 2px
    H2 "MAÎTRE TOM LUCIANI"
    Texte DM Sans 16px text-on-surface-variant :
      "Inscrit au Barreau de Luxembourg depuis le 24 mai 2007,
       Tom Luciani cumule plus de 17 ans d'expérience en
       contentieux et conseil.
       Titulaire d'une maîtrise en Droit Privé et Études
       Européennes de l'Université Robert Schumann à Strasbourg,
       il accompagne particuliers et entreprises dans tous les
       domaines du droit luxembourgeois."
    Lien "PRÉSENTATION COMPLÈTE →" → /presentation

Section 4 — Langues (différenciateur)
  Fond #0E0E0E
  H2 "VOTRE AVOCAT PARLE VOTRE LANGUE"
  4 cards glass-shell horizontal :
    🇫🇷 FRANÇAIS · 🇱🇺 LUXEMBOURGEOIS · 🇩🇪 ALLEMAND · 🇬🇧 ANGLAIS
  Sous-texte : "Consultations disponibles dans les quatre langues."

Section 5 — Contact rapide
  Fond glass-shell pleine largeur
  Gauche : H2 "PRENDRE RENDEZ-VOUS"
           Texte : "Disponible lundi–vendredi 9h–19h.
                    Consultations sur rendez-vous uniquement."
           Adresse : 40, rue du Commerce · L-3450 Dudelange
           Tél : 20 33 14 56 (disponible 14h–18h)
  Droite : 2 boutons empilés
    Primaire : "APPELER" → tel:+35220331456 (fond cyan)
    Secondaire : "ITINÉRAIRE" → Google Maps (bordure blanche)

━━ PAGE DOMAINES (/domaines) ━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Mini-hero sobre :
  Label "DOMAINES D'INTERVENTION"
  H1 "DROIT CIVIL · PÉNAL · COMMERCIAL · ADMINISTRATIF"
  Sous-titre : "Représentation et conseil dans tous les domaines
               du droit luxembourgeois."

Section Droit Civil (layout 2 colonnes) :
  Gauche : Icône <Users /> 48px cyan + H2 + description complète
  Droite : Liste structurée des sous-domaines avec séparateurs

  Contenu détaillé :
  DROIT DES PERSONNES ET DE LA FAMILLE
  · État civil, capacité, filiation (recherche / contestation de paternité)
  · Adoption, protection de la jeunesse
  · Divorce, garde d'enfants, droit de visite et d'hébergement
  · Pensions alimentaires, successions

  DROIT DU TRAVAIL
  · Contrat de travail, licenciement, réintégration
  · Demande et défense devant le tribunal du travail
  · Chômage, référé-travail

  RESPONSABILITÉ CIVILE
  · Responsabilité délictuelle et contractuelle
  · Accidents de la circulation

  DROIT DES IMMEUBLES ET BAIL À LOYER
  · Rédaction de contrats, compromis de vente
  · Clause pénale, indemnité d'occupation
  · Indemnité de relocation, sursis

Section Droit Pénal :
  Icône <Shield /> + H2 "DROIT PÉNAL"
  Sous-domaines :
  · Conduite en état d'ivresse (Alkohol um Steier)
  · Infractions contre les personnes / les propriétés / stupéfiants
  · Procédure pénale, plainte pénale, citation directe, partie civile
  · Restitution permis de conduire et véhicule
  · Mainlevée interdiction de conduire
  · Demande de mise en liberté, exécution des peines, bracelet électronique

Section Droit Commercial :
  Icône <Briefcase /> + H2 "DROIT COMMERCIAL"
  · Sociétés, contrats, faillites, liquidations
  · Demande et défense devant le tribunal de commerce
  · Bail commercial, recouvrements

Section Droit Administratif :
  Icône <Building2 /> + H2 "DROIT ADMINISTRATIF"
  · Recours gracieux et contentieux
  · Décision individuelle, autorisations communales
  · Immigration, réfugiés

━━ PAGE PRÉSENTATION (/presentation) ━━━━━━━━━━━━━━━━━━━━

Mini-hero :
  Label "L'ÉTUDE"
  H1 "MAÎTRE TOM LUCIANI — AVOCAT À LA COUR"
  Sous-titre : "Inscrit au Barreau de Luxembourg depuis le 24 mai 2007."

Section biographie complète :
  Reprendre exactement le texte extrait du site actuel :
  "Né le 7 septembre 1980 à Esch-sur-Alzette, de nationalité
   luxembourgeoise, il est inscrit au Barreau de Luxembourg
   depuis le 24 mai 2007 et exerce la profession d'avocat
   depuis cette même date. [...]"

  Parcours chronologique (timeline verticale) :
  2007 → Inscription au Barreau de Luxembourg
  2009 → Étude MAJERUS, Esch-sur-Alzette
  2014 → Création de l'Étude LUCIANI, Dudelange

  Formation :
  Maîtrise en Droit Privé et Études Européennes
  Université Robert Schumann · Strasbourg

  Collaboration :
  "L'Étude opère en collaboration avec l'Étude MAJERUS
   à Esch-sur-Alzette pour les juridictions du tribunal
   d'Esch."

  Langues (4 cards) :
  Français · Luxembourgeois · Allemand · Anglais

━━ PAGE CONTACT (/contact) ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

H1 "PRENDRE RENDEZ-VOUS"

Pas de formulaire (règle YOR).
Liens directs uniquement.

Carte d'informations (glass-shell) :
  📍 40, rue du Commerce · L-3450 Dudelange · Luxembourg
  📞 20 33 14 56 (disponible 14h00 – 18h00)
     → href="tel:+35220331456"
  ⏰ Lundi – Vendredi · 9h00 – 19h00 · Sur rendez-vous
  🅿️ Parking public en face du cabinet

Collaboration :
  "En collaboration avec l'Étude MAJERUS à Esch-sur-Alzette."

Embed Google Maps :
  Iframe Google Maps pour "40 rue du Commerce, Dudelange, Luxembourg"
  Fond sombre (filtre CSS grayscale + invert pour cohérence dark mode)

━━ SEO TECHNIQUE ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Générer dans l'ordre :

1. Meta tags par page (title + description) :

   / (accueil) :
   title → "Avocat à Dudelange — Étude LUCIANI | Luxembourg"
   description → "Étude LUCIANI, cabinet d'avocats à Dudelange.
   Maître Tom Luciani vous conseille en droit civil, pénal,
   commercial et administratif. 4 langues : fr · lb · de · en."

   /domaines :
   title → "Domaines d'intervention — Droit civil, pénal, commercial | Étude LUCIANI"
   description → "Droit de la famille, successions, droit pénal, travail,
   droit commercial — Étude LUCIANI, avocat à Dudelange, Luxembourg."

   /presentation :
   title → "Maître Tom LUCIANI — Avocat à la Cour | Dudelange Luxembourg"
   description → "Maître Tom LUCIANI, inscrit au Barreau de Luxembourg
   depuis 2007. Étude créée en 2014 à Dudelange. Maîtrise Droit Privé,
   Université de Strasbourg."

   /contact :
   title → "Contact — Prendre rendez-vous | Étude LUCIANI Dudelange"
   description → "Prendre rendez-vous avec Maître LUCIANI, avocat à
   Dudelange. Lundi–vendredi 9h–19h. 40 rue du Commerce, L-3450
   Dudelange. Tél : 20 33 14 56."

2. JSON-LD LegalService (dans layout.tsx, <head>) :
   {
     "@context": "https://schema.org",
     "@type": "LegalService",
     "name": "Étude LUCIANI",
     "description": "Cabinet d'avocats généraliste à Dudelange, Luxembourg.",
     "url": "https://[DOMAINE]",
     "telephone": "+35220331456",
     "address": {
       "@type": "PostalAddress",
       "streetAddress": "40, rue du Commerce",
       "addressLocality": "Dudelange",
       "postalCode": "L-3450",
       "addressCountry": "LU"
     },
     "openingHours": "Mo-Fr 09:00-19:00",
     "areaServed": ["Dudelange", "Luxembourg", "Esch-sur-Alzette"],
     "founder": {
       "@type": "Person",
       "name": "Tom LUCIANI",
       "jobTitle": "Avocat à la Cour",
       "knowsLanguage": ["fr", "lb", "de", "en"]
     }
   }

3. sitemap.xml (4 URLs, priority 1.0 pour /, 0.8 pour les autres)

4. robots.txt :
   User-agent: *
   Allow: /
   Sitemap: https://[DOMAINE]/sitemap.xml

5. vercel.json (security headers) :
   X-Content-Type-Options: nosniff
   X-Frame-Options: DENY
   X-XSS-Protection: 1; mode=block
   Referrer-Policy: strict-origin-when-cross-origin
   Permissions-Policy: camera=(), microphone=(), geolocation=()

6. lang="fr" sur la balise <html> (corriger l'erreur du site actuel)

7. Polices en local (Inter) : télécharger et servir depuis /public/fonts/
   Ne pas appeler Google Fonts en production.

━━ PERFORMANCE (objectif 98+ mobile) ━━━━━━━━━━━━━━━━━━━━

- next/font/local pour Inter (zéro render-blocking)
- Zéro bibliothèque d'animation externe
- Ambient glow = div CSS blur uniquement (pas de canvas)
- Images : aucune image dans le build (pas de LCP image)
- Tailwind CSS purge activé (production build)
- Vercel Edge Network (auto via déploiement Vercel)

━━ CONTRAINTES ABSOLUES ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

- Ne jamais créer de formulaire de contact
- Ne jamais utiliser d'image IA ou de placeholder
- Ne jamais utiliser GSAP, Framer Motion, ou toute bibliothèque d'animation
- Ne jamais appeler Google Fonts en production (local uniquement)
- Toujours utiliser Lucide React pour les icônes
- Liens de contact : tel: et mailto: uniquement
- lang="fr" sur <html>
```

---

## PROCHAINES ÉTAPES

1. Créer repo GitHub `etude-luciani` sur `max-bit16`
2. Init Next.js 14 : `npx create-next-app@latest etude-luciani --typescript --tailwind --app`
3. Coller le prompt Claude Code ci-dessus
4. Run PageSpeed après build
5. Deploy Vercel → lien live
6. Email à Tom Luciani

---

_Dossier design Yamen Global — Workflow YOR · Avril 2026_
