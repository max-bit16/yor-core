# YOR SEO ENGINE — Setup Prompt
# Workflow Yamen Global · Adapté pour sites vitrines clients
# Version 1.0 — Avril 2026
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## COMMENT UTILISER CE FICHIER

1. Place ce fichier à la racine du repo client
2. Ouvre Claude Code
3. Tape : "Read yor-seo-engine-prompt.md and follow all instructions"
4. Réponds aux 5 questions
5. Claude Code construit tout le moteur SEO automatiquement

---

## PROMPT STARTS HERE

Tu es en train de configurer un YOR SEO Engine pour un site
vitrine client produit avec le workflow Yamen Global (YOR).

Ce moteur est optimisé pour :
- Sites vitrines React/Vite/Tailwind/Vercel
- PME, artisans, professions libérales, cabinets
- SEO local (ville + secteur + service)
- Objectif PageSpeed : SEO 100/100 · Performance 90+
- Production de contenu mensuel (2 pages/articles par mois)

Sub-Agent Rule : parallélise les tâches indépendantes.
Si deux tâches ne dépendent pas l'une de l'autre,
lance-les en sous-agents simultanés.

---

## PHASE 1 — AUTO-DÉTECTION DU PROJET

Scanne le repo et détecte automatiquement. Lance en parallèle :

### 1.1 Identité du projet
- Lis package.json → extrait name, description, homepage
- Lis index.html → extrait title, meta description, JSON-LD
- Lis /public/sitemap.xml → liste toutes les pages existantes
- Lis /src/components/ → liste tous les composants
- Identifie : secteur d'activité, ville, services proposés

### 1.2 Structure du site
- Détecte les pages existantes (React Router ou pages statiques)
- Détecte les sections de la page d'accueil (H1, H2, textes)
- Liste toutes les images et leur format
- Vérifie l'existence de : sitemap.xml, robots.txt, vercel.json

### 1.3 État SEO actuel
- Vérifie balises meta (title, description, canonical, OG)
- Vérifie JSON-LD (type, complétude)
- Vérifie lang="fr" et structure HTML sémantique
- Lance npm run build → note les erreurs/warnings éventuels
- Note la taille du bundle JS (objectif < 200kb gzippé)

### 1.4 Contenu existant
- Liste tous les textes visibles par section
- Identifie les mots-clés déjà présents naturellement
- Détecte les mots-clés manquants évidents
- Vérifie la densité des mots-clés (objectif 1-3%)

Stocke TOUT pour la Phase 2 et 3.

---

## PHASE 2 — INTERVIEW RAPIDE (5 questions)

Présente les résultats de la Phase 1 et pose UNIQUEMENT
ces 5 questions dans un seul message :

```
J'ai scanné le repo. Voici ce que j'ai détecté :

🏢 Client : {nom détecté depuis JSON-LD ou package.json}
🌐 Secteur : {secteur détecté}
📍 Ville : {ville détectée}
📄 Pages : {liste des pages}
🔍 SEO actuel : {état résumé — bon/moyen/insuffisant}
📦 Bundle JS : {taille détectée}
⚡ Build : {0 erreur / X erreurs}

Si quelque chose est incorrect, corrige-le dans ta réponse.

J'ai besoin de 5 informations que je ne peux pas détecter :

1. CONCURRENTS — Cite 3 à 5 concurrents directs du client
   (nom + site web si tu le connais)
   Exemple : Studio Photo Martin (studio-martin.fr),
   Photo Pro Paris (photo-pro-paris.com)

2. MOTS-CLÉS PRIORITAIRES — 3 à 5 expressions que le
   client veut absolument ranker
   Exemple : "photographe produit Paris", "shooting
   commercial Paris", "retouche photo professionnelle"

3. ZONE GÉOGRAPHIQUE — Ville principale + zones secondaires ?
   Exemple : Paris 8e, Île-de-France, France entière

4. DIFFÉRENCIATEUR — Qu'est-ce qui rend ce client unique
   vs ses concurrents ? (tarif, délai, spécialisation...)
   Exemple : "Livraison 48h, studio 200m2, équipe dédiée"

5. CIBLE CLIENT — Qui sont ses clients idéaux ?
   Exemple : "Marques e-commerce, agences créatives,
   startups tech"

C'est tout. Je construis le moteur SEO complet ensuite.
```

ATTENDS la réponse. Ne passe pas à la Phase 3 sans.

---

## PHASE 3 — CONSTRUCTION DU MOTEUR

Exécute toutes les étapes. Parallélise ce qui est
indépendant. Ne demande pas de confirmation entre les
étapes.

### Étape 3.1 — Structure des fichiers

Crée exactement cette arborescence :

```
.yor-seo/
├── config.yaml
├── data/
│   ├── keywords.csv
│   ├── competitors.yaml
│   ├── content-map.yaml
│   ├── content-queue.yaml
│   ├── topic-clusters.yaml
│   └── performance-baseline.yaml
├── templates/
│   ├── page-structure.md
│   ├── article-structure.md
│   └── tone-guide.md
├── logs/
│   └── changelog.md
└── GUIDE.md
```

### Étape 3.2 — config.yaml

```yaml
# YOR SEO Engine — Configuration client
# Généré automatiquement. Édite librement.
# Claude Code lit ce fichier avant chaque tâche SEO.

projet:
  nom: "{détecté}"
  secteur: "{détecté}"
  url: "{détecté depuis JSON-LD ou package.json}"
  ville_principale: "{réponse Q3}"
  zones_secondaires: []

client:
  cible: "{réponse Q5}"
  differenciateur: "{réponse Q4}"

contenu:
  auteur: "Yamen Global — YOR"
  ton: "professionnel-direct"
  longueur_min: 600
  longueur_max: 2000
  articles_par_mois: 2
  revue_humaine_requise: true

seo:
  mots_cles_prioritaires: ["{réponses Q2}"]
  zone_geo: "{réponse Q3}"
  langue: "fr"
  schema_type: "{détecté depuis JSON-LD}"
  objectif_pagespeed_seo: 100
  objectif_performance_bureau: 100
  objectif_performance_mobile: 95

concurrents:
  # Depuis réponse Q1
  - nom: "{concurrent 1}"
    url: "{url}"
    id: "comp_1"
  - nom: "{concurrent 2}"
    url: "{url}"
    id: "comp_2"

performance:
  bundle_js_actuel: "{détecté}"
  bundle_js_objectif: "200kb gzippé"
  build_status: "{0 erreur / X erreurs}"
  derniere_mesure: "{date du jour}"
```

### Étape 3.3 — keywords.csv

Génère 25 à 40 mots-clés depuis :
- Les mots-clés prioritaires (réponse Q2)
- La zone géographique (réponse Q3)
- Le secteur et les services détectés
- Les patterns : "{service} {ville}", "{service} pas cher",
  "meilleur {service} {ville}", "{service} professionnel",
  "devis {service} {ville}", "{concurrent} alternative"

```csv
mot_cle,volume_estime,difficulte,intention,etape_funnel,type_contenu,priorite,statut,cluster_id,notes
"{mot-clé}",0,0,"{informationnelle/commerciale/transactionnelle}","{decouverte/consideration/decision}","{page-service/article/landing}","{haute/moyenne/basse}","planifie","{tc_slug}",""
```

Volumes et difficulté à 0 — à remplir avec des données
réelles (Google Search Console, Semrush, Ubersuggest).

Règles d'attribution intention :
- "comment faire X" → informationnelle
- "meilleur X Paris" → commerciale
- "devis X Paris" / "tarif X" → transactionnelle
- "X pas cher" → transactionnelle
- "{concurrent} vs {client}" → commerciale

### Étape 3.4 — competitors.yaml

Pour chaque concurrent (réponse Q1) :

```yaml
derniere_verification: "{date}"

concurrents:
  - id: "comp_1"
    nom: "{nom}"
    url: "{url}"
    points_forts: ""        # À remplir manuellement
    points_faibles: ""      # À remplir manuellement
    tarif_estime: "inconnu"
    notes: "Non encore vérifié."

matrice_services:
  # Pour chaque service détecté sur le site client
  - service: "{service 1}"
    client:
      propose: true
      detail: "{extrait du site}"
    concurrents:
      comp_1:
        propose: null
        detail: ""
        confiance: "non-verifie"
        derniere_verification: ""
      comp_2:
        propose: null
        detail: ""
        confiance: "non-verifie"
        derniere_verification: ""

analyse_mots_cles_concurrents:
  # À remplir via Google : cherche "{concurrent} site:concurrent.fr"
  # et note les mots-clés qui ressortent dans leurs titles/H1
  comp_1:
    mots_cles_detectes: []
    pages_bien_classees: []
  comp_2:
    mots_cles_detectes: []
    pages_bien_classees: []
```

RÈGLE ABSOLUE : ne jamais inventer de données sur les
concurrents. Tout ce qui n'est pas vérifié reste null
avec confiance "non-verifie".

### Étape 3.5 — performance-baseline.yaml

Capture l'état de performance actuel du site :

```yaml
date_mesure: "{date du jour}"
url: "{url de production}"

build:
  bundle_js_principal: "{taille détectée}"
  bundle_css: "{taille détectée}"
  nb_chunks: "{nombre}"
  erreurs: 0
  warnings: 0

seo_technique:
  title_present: true/false
  meta_description_present: true/false
  meta_description_longueur: "{nb caractères}"
  canonical_present: true/false
  og_tags_presents: true/false
  json_ld_present: true/false
  json_ld_type: "{type}"
  lang_fr: true/false
  h1_unique: true/false
  sitemap_xml: true/false
  robots_txt: true/false
  vercel_json: true/false

contenu:
  nb_mots_page_accueil: "{compter les textes visibles}"
  sections_presentes: []
  mots_cles_detectes: []
  densite_mots_cles: {}

points_amelioration:
  priorite_haute: []
  priorite_moyenne: []
  priorite_basse: []

pagespeed_scores:
  # À remplir après le premier audit PageSpeed
  seo: null
  performance_bureau: null
  performance_mobile: null
  accessibilite: null
  bonnes_pratiques: null
  lcp: null
  cls: null
  inp: null
  date_mesure: null
```

### Étape 3.6 — topic-clusters.yaml

Conçois l'architecture pilier/cluster depuis les
mots-clés prioritaires et les services détectés.

```yaml
derniere_mise_a_jour: "{date}"

clusters:
  - cluster_id: "tc_{slug}"
    nom: "{Cluster principal — ex: Photographie Produit Paris}"
    description: "{ce que ce cluster couvre}"
    mot_cle_principal: "{ex: photographe produit Paris}"

    page_pilier:
      titre: "{Titre complet}"
      mot_cle_cible: "{mot-clé large}"
      slug: "{slug}"
      statut: "planifie"
      type: "{page-service/landing/guide}"
      priorite: "haute"

    pages_cluster:
      - titre: "{Page spécifique 1}"
        mot_cle_cible: "{long-tail}"
        slug: "{slug}"
        angle: "{ce qui différencie cette page du pilier}"
        statut: "planifie"
        type: "article"

    regles_maillage:
      - "Chaque page cluster DOIT linker vers la page pilier"
      - "La page pilier DOIT linker vers toutes les pages cluster publiées"
      - "Les pages cluster peuvent se cross-linker si pertinent"
```

Crée 1 cluster par service principal détecté sur le site.
Chaque cluster : 4 à 8 pages planifiées.

AVANT de finaliser une page pilier, demande les données
SERP réelles :

```
Je vais créer la page pilier pour le cluster "{nom}".
Cherche sur Google "{mot-clé pilier}" et donne-moi :
1. Les 5 premiers résultats (titre + URL)
2. Les questions "Les gens demandent aussi"
3. Les recherches associées en bas de page
```

ATTENDS la réponse avant de finaliser la structure du pilier.

### Étape 3.7 — content-queue.yaml

```yaml
derniere_mise_a_jour: "{date}"

file_attente:
  - id: "q_001"
    titre: "{Titre du contenu}"
    type: "{page-service/article-blog/landing-local/faq}"
    cluster_id: "{tc_slug}"
    mots_cles_cibles: []
    angle_unique: "{OBLIGATOIRE — ce qui diffère de ce qui existe}"
    priorite: "{haute/moyenne/basse}"
    raison_priorite: "{pourquoi}"
    statut: "planifie"
    nb_mots_estime: 800
    plan_seo:
      h1: "{proposition de H1}"
      meta_description: "{proposition 120-155 chars}"
      mots_cles_dans_h1: true/false
      mots_cles_dans_intro: true/false
    verification_cannibalisation: "passe"
    notes: ""
```

Génère la file dans cet ordre de priorité :

1. HAUTE — Pages piliers manquantes pour chaque cluster
2. HAUTE — Pages de service non encore créées
3. HAUTE — Landing pages locales (ville + service)
4. MOYENNE — Pages cluster (long-tail spécifiques)
5. MOYENNE — FAQ par service
6. BASSE — Articles blog (tendances, conseils)

Vérification cannibalisation : si deux entrées ciblent
le même mot-clé, fusionne-les ou différencie les angles.

### Étape 3.8 — Templates

**templates/page-structure.md** — Structure d'une page
de service YOR :

```
# Structure Page Service YOR

## HEAD
- title : "{Service} à {Ville} — {Nom Client}" (≤ 60 chars)
- description : "{bénéfice principal} + {différenciateur}
  + {ville}" (120-155 chars)
- canonical : {url}
- JSON-LD LocalBusiness ou ProfessionalService

## STRUCTURE H1 → H2

H1 UNIQUE : "{Service principal} à {Ville} — {Nom Client}"
  → Contient le mot-clé principal + ville
  → 1 seul sur toute la page

H2 Section Services/Expertises
  → Contient variation du mot-clé

H2 Pourquoi choisir {Nom} ?
  → Différenciateur + mots-clés secondaires

H2 Comment ça marche ?
  → Process en étapes numérotées

H2 Ils nous font confiance
  → Témoignages ou secteurs clients

H2 Questions fréquentes
  → FAQ avec questions en langage naturel
  → Réponses courtes et directes
  → Schema FAQPage dans JSON-LD

H2 Contactez-nous / Devis gratuit
  → CTA + coordonnées + ville visible en texte

## RÈGLES CONTENU
- Mot-clé principal dans : H1, 1er paragraphe, 1 H2,
  meta description, URL slug
- Mots-clés secondaires : 1 à 2 occurrences naturelles
- Ville en texte visible au moins 3 fois
- Longueur minimum : 600 mots
- Aucun texte générique type "nous sommes passionnés"
- Chaque phrase doit justifier sa présence
```

**templates/article-structure.md** — Structure article blog :

```
# Structure Article Blog YOR

## Règles générales
- Longueur : 800 à 1500 mots
- Ton : direct, utile, sans jargon
- 1 idée centrale par article
- CTA en bas de page vers le service correspondant

## Structure standard

H1 : "{Question ou affirmation forte}"
  → Contient le mot-clé cible
  → Formule qui donne envie de lire

Introduction (100-150 mots) :
  → Pose le problème du lecteur
  → Annonce ce que l'article apporte
  → Mot-clé dans les 50 premiers mots

H2 : Section 1 — Le problème / Le contexte
H2 : Section 2 — La solution / Les étapes
H2 : Section 3 — Les erreurs à éviter / Les conseils
H2 : Section 4 — FAQ (2-4 questions)
H2 : Section 5 — Conclusion + CTA

## Maillage interne obligatoire
- Lien vers la page pilier du cluster concerné
- Lien vers 1 autre page de service pertinente
- Ancres variées (pas toujours le même texte de lien)
```

**templates/tone-guide.md** :

```
# Guide de Ton — YOR Sites Vitrines

## Ton général
Direct. Concret. Professionnel sans être guindé.
Jamais : "nous sommes fiers", "notre passion",
"à votre écoute", "n'hésitez pas à".
Toujours : bénéfices concrets, chiffres quand possible,
phrases courtes, verbes d'action.

## Par type de contenu

Page service :
→ Ton vendeur sobre. Bénéfices avant caractéristiques.
→ "Livraison en 48h" pas "Nous nous engageons à livrer
   rapidement".

Article blog :
→ Ton expert utile. Donne de la valeur sans vendre.
→ Le CTA final est discret, pas insistant.

FAQ :
→ Ton conversationnel. Répond vraiment à la question.
→ Jamais de réponse vague.

## Règles SEO dans le texte
- Mot-clé principal dans les 100 premiers mots
- H2 contiennent des variations du mot-clé (pas des
  synonymes génériques)
- Densité max 2-3% — au-delà c'est du keyword stuffing
- La ville doit apparaître en texte naturel, pas en liste

## Signaux E-E-A-T (Experience, Expertise, Authority, Trust)
Chaque page/article DOIT contenir au moins un :
- Chiffre concret (années d'expérience, nb clients,
  délai de livraison, note)
- Témoignage ou secteur client cité
- Résultat mesurable ("Score SEO 100/100")
- Référence locale (adresse, quartier, arrondissement)
```

### Étape 3.9 — Initialise le changelog

```markdown
## {date} — Initialisation YOR SEO Engine
**Action :** Setup complet moteur SEO
**Fichiers créés :** config.yaml, keywords.csv,
competitors.yaml, content-map.yaml, content-queue.yaml,
topic-clusters.yaml, performance-baseline.yaml,
3 templates, GUIDE.md
**Résumé :** Moteur initialisé pour {nom client},
{nb} mots-clés générés, {nb} clusters créés,
{nb} contenus en file d'attente.
**Déclenché par :** Setup initial YOR workflow
```

---

## PHASE 4 — RÉSUMÉ

```
✅ YOR SEO Engine initialisé !

📊 Résumé :
- Mots-clés générés : {nb} ({nb} haute priorité)
- Clusters thématiques : {nb} ({nb} pages piliers planifiées)
- Concurrents suivis : {nb}
- Contenus en file d'attente : {nb}
- Cannibalisation détectée : {nb conflits ou "aucun"}
- Bundle JS actuel : {taille}
- Build status : {0 erreur ou X erreurs}

⚠️ Données concurrents non vérifiées — à enrichir
   manuellement depuis leurs sites.

⚠️ Volumes de mots-clés à 0 — à remplir depuis
   Google Search Console ou Ubersuggest.

📂 Tout est dans .yor-seo/ — édite config.yaml
   pour modifier les paramètres.
📖 Lis .yor-seo/GUIDE.md pour toutes les commandes.

🔜 Prochaines étapes :
1. Lance PageSpeed sur {url} et remplis
   performance-baseline.yaml avec les vrais scores
2. Vérifie competitors.yaml et enrichis-le
3. Dis "Écris le prochain contenu" pour démarrer
4. Soumets le sitemap dans Google Search Console
```

---

## PHASE 5 — GUIDE D'UTILISATION

Sauvegarde dans `.yor-seo/GUIDE.md` :

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📖 YOR SEO ENGINE — GUIDE D'UTILISATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Tape ces commandes dans Claude Code.

─── PERFORMANCE ──────────────────────────────────────

"Audit performance"
  → Lance npm run build, analyse la taille du bundle,
    liste tous les points d'amélioration PageSpeed.

"Améliore le score LCP"
  → Analyse et corrige le Largest Contentful Paint.

"Optimise le bundle JS"
  → Analyse les chunks et propose des code-splits.

─── CONTENU ──────────────────────────────────────────

"Écris le prochain contenu"
  → Prend la priorité haute dans content-queue.yaml,
    demande les données SERP, rédige et sauvegarde.

"Écris une page pour [service] à [ville]"
  → Vérifie la cannibalisation, rédige la page.

"Écris un article sur [sujet]"
  → Vérifie la cannibalisation, rédige l'article.

"Approuve [slug]"
  → Marque comme publié après ta relecture.

─── MOTS-CLÉS & CONCURRENTS ─────────────────────────

"Analyse les concurrents"
  → Guide pour enrichir competitors.yaml manuellement.

"Ajoute les mots-clés : [colle tes données]"
  → Importe dans keywords.csv.

"Quels mots-clés me manquent pour [service] ?"
  → Analyse les gaps vs la file d'attente.

─── AUDIT SEO ────────────────────────────────────────

"Audit SEO complet"
  → Vérifie toutes les pages, meta, JSON-LD,
    maillage interne, cannibalisation.

"Quoi écrire ensuite ?"
  → Analyse la file et recommande le contenu
    avec le meilleur ROI SEO.

"Vérifie la cannibalisation"
  → Détecte les pages qui ciblent les mêmes mots-clés.

─── MISE À JOUR ──────────────────────────────────────

"Mets à jour le sitemap"
  → Régénère /public/sitemap.xml avec toutes les pages.

"Nouveau service : [nom]"
  → Crée les mots-clés, le cluster et la file associés.

"Score PageSpeed : SEO {X}, Perf {X}, Mobile {X}"
  → Met à jour performance-baseline.yaml.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

RÈGLE SERP : Claude Code ne cherche JAMAIS les données
SERP lui-même. Il te demande de googler le mot-clé
cible et de lui coller :
1. Les 5 premiers résultats (titre + URL)
2. Les questions "Les gens demandent aussi"
3. Les recherches associées en bas de page

C'est la seule façon d'écrire du contenu qui se classe
vraiment — pas à partir de suppositions de l'IA.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## APPENDICE — RÈGLES CLAUDE CODE (CLAUDE.md)

Ajoute à (ou crée) CLAUDE.md à la racine du repo :

```markdown
## YOR SEO Engine

Le moteur SEO est dans `.yor-seo/`.
Utilise-le pour toutes les tâches SEO, contenu et
performance de ce projet.

**RÈGLE UNIVERSELLE : Pour toute tâche impliquant
du contenu, des mots-clés, des concurrents, le SEO
ou la performance — lis TOUJOURS .yor-seo/config.yaml
et les fichiers data/ pertinents AVANT de répondre.**

### Référence fichiers

| Fichier | Usage | Quand |
|---------|-------|-------|
| config.yaml | Paramètres projet | Avant toute tâche |
| data/keywords.csv | Mots-clés + clusters | Avant écriture |
| data/competitors.yaml | Analyse concurrents | Avant comparaisons |
| data/content-queue.yaml | File priorisée | Pour décider quoi écrire |
| data/topic-clusters.yaml | Architecture pilier/cluster | Avant écriture |
| data/performance-baseline.yaml | Scores actuels | Avant optimisation |
| templates/tone-guide.md | Style + E-E-A-T | Avant écriture |

### Règles fondamentales

1. **Lis avant d'écrire.** Toujours lire config, keywords,
   content-queue, tone-guide avant toute rédaction.

2. **Jamais de données inventées sur les concurrents.**
   Si confiance = "non-verifie" → caveat ou renvoie vers
   le site du concurrent.

3. **Pas de recherche SERP par toi-même.** Demande
   toujours à l'utilisateur de googler et coller les
   vrais résultats. Ta recherche interne donne des
   résultats génériques qui produisent du contenu
   générique.

4. **Vérification cannibalisation obligatoire.** Avant
   chaque nouveau contenu, vérifie keywords.csv et
   content-map.yaml pour les conflits.

5. **Angle unique requis.** "Plus complet" n'est pas
   un angle. Définis ce qui différencie le contenu
   de ce qui existe déjà.

6. **E-E-A-T obligatoire.** Chaque page doit contenir
   au moins : un chiffre concret, un témoignage/secteur
   client, un résultat mesurable, ou une référence locale.

7. **Revue humaine requise.** Sauvegarde tout en statut
   "a-relire". Ne publie jamais automatiquement.

8. **Maillage interne non négociable.** Page cluster →
   linke vers pilier. Pilier → linke vers tous les
   clusters publiés.

9. **Performance = SEO.** Chaque modification du code
   doit maintenir bundle JS < 200kb gzippé et build
   0 erreur / 0 warning.

10. **Log tout** dans logs/changelog.md.

### Workflow rédaction contenu

ÉTAPE 1 — Pré-rédaction
a) Lis config.yaml + keywords.csv + content-queue.yaml
b) Sélectionne la priorité haute suivante
c) Vérification cannibalisation
d) Demande données SERP réelles à l'utilisateur :
   "Cherche '{mot-clé}' sur Google et donne-moi :
   1. Top 5 résultats (titre + URL)
   2. Questions 'Les gens demandent aussi'
   3. Recherches associées en bas de page"
e) ATTENDS la réponse. Ne procède pas sans.
f) Analyse l'intention de recherche depuis les SERP
g) Définis l'angle unique (1 phrase)

ÉTAPE 2 — Rédaction
a) Sélectionne le template approprié
b) Construis le H1 : mot-clé + ville + différenciateur
c) Meta description : bénéfice + mot-clé + ville
   (120-155 chars exactement — vérifie le comptage)
d) Rédige en suivant tone-guide.md
e) Injecte E-E-A-T : chiffre, témoignage ou résultat
f) Ajoute maillage interne (pilier + 1 autre page)
g) Ajoute FAQ depuis les "gens demandent aussi"

ÉTAPE 3 — Post-rédaction
a) Sauvegarde en statut "a-relire"
b) Mets à jour content-map.yaml + content-queue.yaml
c) Si nouvelle page : mets à jour sitemap.xml
d) Log dans changelog.md
e) Alerte :
   "✅ Contenu rédigé : {titre}
    📄 Fichier : {chemin} | Mots : {nb}
    ⚠️ À relire avant publication.
    Dis 'Approuve {slug}' ou donne ton feedback."

### Workflow analyse concurrents

1. Lis competitors.yaml
2. Pour chaque concurrent non vérifié :
   Guide l'utilisateur : "Va sur {url} et note :
   - Leurs services principaux
   - Leurs arguments de vente
   - Leurs mots-clés dans les titles/H1
   - Leur tarification si visible"
3. Met à jour competitors.yaml avec confiance "verifie"
4. Identifie les gaps : services qu'ils ont pas,
   mots-clés qu'ils ciblent pas, angles non couverts
5. Ajoute les opportunités dans content-queue.yaml
6. Log dans changelog.md

### Interprétation intention SERP

Analyse les résultats SERP fournis par l'utilisateur :

Tous les résultats sont des pages de service/produit :
→ Intention TRANSACTIONNELLE
→ La page doit d'abord servir l'intention (CTA,
  formulaire, tarif) puis ajouter du contenu éducatif

Mix guides + pages service :
→ Intention MIXTE
→ Guide complet avec CTA intégré

Tous les résultats sont des guides/articles :
→ Intention INFORMATIONNELLE
→ Rédige un guide complet, CTA discret en fin

Tous les résultats sont des comparatifs/listes :
→ Intention COMMERCIALE
→ Rédige un comparatif ou une liste

RÈGLE : ne combats jamais le SERP. Si Google
affiche des pages de service, ne rédige pas un guide
pur. Si Google affiche des guides, ne rédige pas
une page de vente.
```
