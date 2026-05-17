# YOR — WORKFLOW PROSPECT FIRST
# Yamen Global · Version 1.0 · Avril 2026
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## PRINCIPE

On construit le site avant de contacter le prospect.
Pas de brief, pas de réunion préalable.
Le prospect voit son propre contenu dans un design qu'il
n'aurait jamais pu faire lui-même — avec un score PageSpeed
vérifiable en 30 secondes.

Ce workflow est une approche commerciale, pas un workflow
de production client. L'objectif est la conversion, pas
la perfection. Le polish SEO avancé (mots-clés longue
traîne, contenu rédigé) vient après signature.

---

## VUE D'ENSEMBLE

| Phase | Étape                        | Outil            | Temps réel |
|-------|------------------------------|------------------|------------|
| 1     | Scraping du site prospect    | Chrome MCP       | 20–30 min  |
| 2     | Décision structure           | Claude (chat)    | 5 min      |
| 3     | Direction visuelle           | Google Stitch    | 30–45 min  |
| 4     | Génération prompt Claude Code| Claude (chat)    | 10 min     |
| 5     | Build complet                | Claude Code      | 2–3h       |
| 6     | Deploy                       | GitHub → Vercel  | 5 min      |
| 7     | Audit PageSpeed              | PageSpeed        | 10 min     |
| 8     | Outreach prospect            | Email / LinkedIn | 10 min     |

**Temps total réaliste : une demi-journée.**
Ne pas promettre moins — le build peut boucler.

---

## PHASE 1 — SCRAPING DU SITE PROSPECT (20–30 min)

### Outil
Chrome MCP (`get_page_text`, `javascript_exec`)

### Objectif
Extraire tout le contenu réel du site sans rien inventer.
Ce contenu alimentera directement le build — le prospect
reconnaîtra ses propres mots dans un design supérieur.

### Ce qu'on extrait
- Nom de l'entreprise, secteur, accroche principale
- Liste complète des services (texte exact)
- Adresse, téléphone, email, horaires
- Chiffres clés (années d'expérience, nombre de clients, etc.)
- Témoignages s'ils existent
- Structure de navigation (pages présentes)
- CTA existants (boutons, liens d'action)

### Technique
Les sites Wix / WordPress / Squarespace rendent leur
contenu en JavaScript — `get_page_text` peut être bruité.
Utiliser `javascript_exec` avec `document.body.innerText`
pour les sites dynamiques.

Prévoir une deuxième passe si le résultat est fragmenté.

### Livrable
Fichier texte brut organisé par sections : identité,
services, contact, chiffres, structure.

---

## PHASE 2 — DÉCISION STRUCTURE (5 min)

### Règle
Reproduire la structure existante, pas plus.

| Site actuel              | Décision YOR    |
|--------------------------|-----------------|
| 1 à 3 pages              | Landing page    |
| 4 pages ou plus          | Multipage       |
| Contenu pauvre partout   | Landing page    |
| Contenu dense par page   | Multipage       |

### Pourquoi cette règle
Un prospect sur un site 2 pages ne s'attend pas à
recevoir un site 5 pages. La surprise visuelle suffit —
la surprise structurelle perturbe.

---

## PHASE 3 — DIRECTION VISUELLE STITCH (30–45 min)

### Outil
Google Stitch (stitch.withgoogle.com)

### Objectif
Générer une direction visuelle qui surpasse visuellement
le site actuel tout en restant dans le même univers
sectoriel. Le prospect reconnaît son secteur, pas son
mauvais design.

### Ce qu'on donne à Stitch
- Secteur du client (avocat, restaurant, artisan, etc.)
- Captures d'écran du site actuel → référence de contenu,
  pas de style
- Palette YOR correspondante (voir Dossier 1 — Skins)
- Ambiance cible : sobre, premium, moderne

### Skins YOR par secteur

| Secteur                          | Skin YOR  | Palette principale        |
|----------------------------------|-----------|---------------------------|
| Avocat, notaire, conseil         | PRESTIGE  | Crème #F0EDE6 + Vert #2C4A3E |
| Restaurant gastronomique         | SOFT      | Blanc cassé + Or #C5A059  |
| Artisan, commerce local          | GLOBAL    | Fond #0D0D0D + Violet #6B3FA0 |
| Tech, startup, SaaS              | DARK      | Noir #050505 + Cyan #00F0FF |
| Agence, studio, créatif          | BOLD      | Fort contraste + accent vif |
| Médical, bien-être               | EDITORIAL | Blanc pur + typographie forte |

### Ce qu'on exporte depuis Stitch
- `DESIGN.md` — design system complet avec tokens
- `code.html` par page — source de vérité pour Claude Code
- `screen.png` par page — référence visuelle

### Règle critique
Les URLs d'images générées par Stitch
(`lh3.googleusercontent.com`) ne sont pas pérennes.
Toutes les images seront remplacées par des URLs
Unsplash stables dans le prompt Claude Code.

---

## PHASE 4 — GÉNÉRATION PROMPT CLAUDE CODE (10 min)

### Outil
Claude (ce chat)

### Ce qu'on colle ici
1. Le `DESIGN.md` exporté depuis Stitch
2. Le contenu extrait en Phase 1 (textes exacts)
3. La structure décidée en Phase 2 (landing ou multipage)

### Ce que Claude génère
Un prompt Claude Code complet incluant :

**Stack**
```
Next.js 14 App Router + TypeScript + Tailwind CSS
Aucune librairie d'animation externe
Intersection Observer natif pour les reveals
Images : Unsplash stables uniquement
Icônes : Lucide-React
```

**Contenu injecté**
Textes exacts du prospect, dans l'ordre des sections
Stitch. Aucun placeholder, aucun Lorem ipsum.

**SEO intégré dès le build** (pas en phase séparée)
- `metadata` Next.js par page avec title + description
- JSON-LD LocalBusiness ou LegalService selon secteur
- `sitemap.xml` généré
- `robots.txt`
- Images avec `alt`, `width`, `height`, `fetchPriority`
- Polices hébergées localement (next/font/google)
- `vercel.json` avec headers de sécurité

**Source de vérité design**
Fichiers `code.html` Stitch comme référence absolue
de classes Tailwind et structure de composants.

### Ce qu'on ne fait PAS à cette étape
- Validation de mots-clés (Ubersuggest, Keyword Planner)
- Rédaction de contenu optimisé
- Pages légales
- Google Search Console

Ces éléments viennent après signature — ce site est
un outil commercial, pas le livrable final.

---

## PHASE 5 — BUILD CLAUDE CODE (2–3h)

### Outil
Claude Code (terminal dans le repo)

### Initialisation
```bash
cd ~/Documents/YOR
npx create-next-app@latest [nom-prospect] \
  --typescript --tailwind --eslint --app \
  --no-src-dir --import-alias "@/*"
cd [nom-prospect]
npm install lucide-react
```

### Ordre d'exécution
1. Coller le prompt complet généré en Phase 4
2. Claude Code lit les fichiers Stitch (`code.html`,
   `screen.png`) comme source de vérité
3. Construit les composants page par page
4. Intègre le contenu prospect extrait
5. Génère les fichiers SEO
6. `npm run build` — 0 erreur obligatoire
7. Commit initial

### Si Claude Code boucle
Symptôme le plus fréquent : TypeError au build avec
TypeScript clean en dev. Cause probable : prop optionnelle
non typée, import manquant, ou composant non exporté.

Intervention manuelle : identifier le fichier en erreur
dans le log build, corriger le type, relancer.
Ne pas laisser tourner plus de 15 min sans intervenir.

### Seuils minimum avant de continuer
- Build : 0 erreur, 0 warning TypeScript
- Visuel desktop : cohérent avec les `screen.png` Stitch
- Mobile : responsive validé manuellement

---

## PHASE 6 — DEPLOY GITHUB → VERCEL (5 min)

### Outil
GitHub (`max-bit16`) + Vercel

### Étapes
```bash
# Créer le repo GitHub (sans initialiser)
# Puis dans le terminal :
git remote add origin https://github.com/max-bit16/[nom].git
git push -u origin main
```

Vercel : importer le repo → auto-detect Next.js →
deploy automatique → URL live `[nom].vercel.app`.

### Naming convention
`[secteur]-[ville]-yamen.vercel.app`
ou simplement `[nom-client].vercel.app`

Choisir une URL lisible — le prospect cliquera dessus.

---

## PHASE 7 — AUDIT PAGESPEED (10 min)

### Outil
pagespeed.web.dev

### Seuils minimum avant outreach

| Métrique        | Seuil minimum |
|-----------------|---------------|
| SEO             | 100/100       |
| Performance desktop | 95+/100   |
| Performance mobile  | 90+/100   |
| Bonnes pratiques    | 95+/100   |

**On n'envoie pas si mobile < 90.**

Si mobile bloqué entre 70–89 : vérifier LCP
(image hero sans `fetchPriority="high"`), bundle JS
(manualChunks dans `vite.config` ou Next.js par défaut),
et polices (next/font évite le FOIT).

Si mobile < 70 : le problème est structurel.
Vérifier qu'on est bien sur Next.js App Router avec SSG
(pas de `'use client'` sur les pages statiques).

### Ce qu'on capture
Une screenshot PageSpeed horodatée avec les 4 scores
visibles. Cette capture est la pièce maîtresse de
l'email d'outreach.

---

## PHASE 8 — OUTREACH PROSPECT (10 min)

### Canal
Email professionnel Yamen Global en priorité.
LinkedIn en backup si pas d'email trouvé.

### Message type

**Objet :** Votre site — une question rapide

> Bonjour [Prénom],
>
> J'ai refait votre site. Il est en ligne ici :
> [URL Vercel]
>
> Il score 100 SEO et [score] en performance mobile —
> votre site actuel est à [score Wix/WP].
> Vérifiable en 30 secondes sur pagespeed.web.dev.
>
> Si ça vous convient, on peut parler du reste.
>
> Max
> Yamen Global — yamen-global.com

### Ce qu'on ne dit PAS dans ce premier message
- Le prix
- La stack technique
- Le temps de réalisation
- Les fonctionnalités SEO avancées

Un message court et une preuve. Rien d'autre.

---

## APRÈS CONVERSION — CE QUI RESTE À FAIRE

Une fois le prospect converti en client payant :

**Phase SEO complète**
- Validation volumes Ubersuggest
- Rédaction contenu optimisé par page
- Mots-clés longue traîne
- Pages légales (mentions légales, confidentialité)
- Google Search Console + soumission sitemap

**Domaine custom**
- Migration `[client].vercel.app` → domaine client
- CNAME OVH/Namecheap → Vercel

**Livraison officielle**
- Capture PageSpeed finale horodatée
- Accès repo GitHub transféré au client
- Documentation DESIGN.md archivée

---

## CRITIQUES ET LIMITES DE CE WORKFLOW

**Ce qui peut échouer**

Le prospect peut répondre "c'est pas mon image" — sans
brief préalable, on fait un pari sur ses goûts. Le risque
est limité par le fait qu'on reproduit son contenu exact,
mais il existe.

Le taux de conversion est imprévisible. Ce workflow est
pertinent pour des prospects sur WordPress lent ou Wix —
la comparaison de scores est dévastatrice. Sur un prospect
déjà satisfait de son site, l'argument est plus faible.

**Ce qui prend plus de temps que prévu**

Le scraping sur Wix est souvent bruité — prévoir 30 min,
pas 10. Claude Code peut boucler sur une erreur de build —
prévoir 3h, pas 1h. La migration vers Next.js si on
démarre sur Vite coûte une demi-journée supplémentaire.
C'est pourquoi ce workflow part directement sur Next.js.

**Ce qu'on ne livre pas**

Ce site n'est pas le livrable final — c'est un outil
commercial. Le contenu n'est pas optimisé pour le SEO
longue traîne, les pages internes ne sont pas complètes,
et le Search Console n'est pas configuré. On livre une
preuve de concept de haute qualité, pas un produit fini.

---

## RÉFÉRENCE — PROJET MODÈLE

**Azure Mas** est le cas le plus documenté pour ce
workflow. Prompt complet dans `prompt_claudecode_azure_mas.md`.

**Différences avec ce workflow :**
- Azure Mas utilisait Vite/React (migré vers Next.js après)
- Azure Mas était fictif (pas de scraping)
- Ce workflow part directement sur Next.js 14 App Router

Le prompt Azure Mas reste la référence pour la structure
du build Stitch → Claude Code. Adapter la stack uniquement.

---

*Yamen Global · YOR Workflow Prospect First · Avril 2026*
*Basé sur les retours Azure Mas, Lou Calen, Luciani*
