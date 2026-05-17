# YOR — WORKFLOW COMPLET
# Yamen Global · Version 2.0 · Avril 2026
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## VUE D'ENSEMBLE

| Phase | Étape | Outil | Jour |
|-------|-------|-------|------|
| 1 | Brief client | Google Forms / HTML | J0 |
| 2 | Arborescence & mots-clés | Claude (chat) | J0 |
| 3 | Validation volumes | Claude in Chrome | J0–J1 |
| 4 | Génération du site | Lovable | J1–J6 |
| 5 | Préparation repo | Lovable | J6 |
| 6 | Export GitHub | GitHub | J7 |
| 7 | Optimisation SEO | Claude Code | J8–J9 |
| 8 | Moteur SEO | Claude Code | J9 |
| 9 | Déploiement | Vercel | J10 |
| 10 | Audit PageSpeed | PageSpeed Insights | J10 |
| 11 | Search Console | Google | J10 |

Délai total garanti : **10 jours ouvrés.**
On ne livre pas si SEO < 100 ou Performance < 90.

---

## PHASE 1 — BRIEF CLIENT (J0)

### Outil
Google Forms ou questionnaire HTML (Netlify Drop)

### Objectif
Collecter toutes les informations nécessaires pour générer
le prompt Lovable et initialiser le moteur SEO. Rien ne
démarre sans ce brief complet.

### Les 5 informations critiques
1. **Concurrents** — 3 à 5 concurrents directs (nom + URL)
2. **Mots-clés** — 3 à 5 expressions cibles prioritaires
3. **Zone géographique** — Ville principale + zones secondaires
4. **Différenciateur** — Ce qui rend le client unique (tarif,
   délai, spécialisation, certifications)
5. **Cible client** — Profil des clients idéaux

### Autres informations à collecter
- Nom de l'entreprise, secteur, adresse
- Services proposés (liste exhaustive)
- Chiffres clés (années d'expérience, nb clients, délais)
- Témoignages ou références clients
- Palette de couleurs souhaitée (ou laisser YOR décider)
- Pages souhaitées (Accueil, Services, À propos, Contact...)
- Nom de domaine existant ou à acheter

### Livrable
Brief client complet → alimente directement les phases 2, 3, 4.

---

## PHASE 2 — ARBORESCENCE & MOTS-CLÉS (J0)

### Outil
Claude (ce chat)

### Objectif
Définir l'architecture du site avant de toucher à Lovable.
Une page = un mot-clé cible = une intention de recherche.
Jamais deux pages sur le même mot-clé.

### Instructions pour Claude
Colle les réponses du brief et demande :

```
Sur la base de ce brief, propose-moi :
1. L'arborescence complète du site (pages + slugs)
2. Pour chaque page : le mot-clé cible principal
3. Le H1 suggéré pour chaque page
4. Les mots-clés secondaires à intégrer
5. Les 25 à 40 mots-clés à valider (pour la phase suivante)

Client : [NOM]
Secteur : [SECTEUR]
Ville : [VILLE]
Services : [SERVICES]
Mots-clés donnés par le client : [MOTS-CLÉS]
Concurrents : [CONCURRENTS]
```

### Règles d'arborescence
- Page d'accueil → mot-clé large (ex: "photographe Paris")
- Page par service → mot-clé transactionnel (ex: "shooting
  produit Paris")
- Page locale si multi-zones → (ex: "photographe Lyon")
- Pas plus de 7 pages pour un Starter, pas de limite pour
  un Standard

### Livrable
- Arborescence validée avec slugs
- Liste de 25 à 40 mots-clés à passer en phase 3

---

## PHASE 3 — VALIDATION VOLUMES MOTS-CLÉS (J0–J1)

### Outil
**Claude in Chrome** (navigateur)

### Objectif
Vérifier que les mots-clés ciblés ont un volume de recherche
réel avant de construire les pages. Évite de produire du
contenu pour personne.

### Règle
Ne jamais construire un site multi-pages sans avoir validé
les volumes. Un mot-clé à 10 recherches/mois ne justifie
pas une page dédiée.

### Prompt Claude in Chrome

```
# YOR — VALIDATION VOLUMES MOTS-CLÉS
# Prompt Claude in Chrome · Étape post-arborescence
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Tu vas valider les volumes de recherche des mots-clés
définis pour un site client YOR.

## LISTE DES MOTS-CLÉS À VALIDER

[COLLE ICI LA LISTE GÉNÉRÉE EN PHASE 2]

## INSTRUCTIONS

### Étape 1 — Connexion Google Keyword Planner

1. Va sur https://ads.google.com/intl/fr_fr/home/tools/keyword-planner/
2. Connecte-toi avec le compte Google si nécessaire
3. Clique sur "Obtenir le volume de recherche et les prévisions"
4. Si demande de créer une campagne : cherche le lien
   "Passer à la version Expert" en bas de page — clique dessus

### Étape 2 — Saisie des mots-clés

1. Colle TOUS les mots-clés (un par ligne) dans le champ
2. Langue : Français / Zone : France (ou zone client si locale)
3. Clique sur "Commencer"

### Étape 3 — Extraction des résultats

Pour chaque mot-clé, note :
- Volume mensuel moyen
- Niveau de concurrence (Faible / Moyen / Élevé)
- Enchère suggérée haut de page (proxy valeur commerciale)

Si Google affiche des fourchettes (100–1 000), note la
fourchette complète. Si volume affiché "—", marque "< 10".

### Étape 4 — Retour structuré

Retourne ce tableau CSV :

mot_cle,volume_mensuel,fourchette,concurrence_ads,enchere_haute,recommandation
"[mot-clé]","[volume]","[fourchette]","[niveau]","[enchère]","[GARDER/ÉCARTER/SURVEILLER]"

Règles de recommandation :
- GARDER → volume > 100 + intention commerciale claire
- SURVEILLER → volume 10–100 ou long-tail utile
- ÉCARTER → volume < 10 ou trop générique/concurrentiel
- RISQUÉ → volume fort mais concurrence agence impossible

### Étape 5 — Synthèse finale

Après le tableau, fournis :

MOTS-CLÉS PRIORITAIRES (à construire en premier) :
→ Top 5 à 10 avec volume + intention

MOTS-CLÉS À ÉCARTER :
→ Liste + raison courte

OPPORTUNITÉS DÉTECTÉES :
→ Variantes suggérées par Google avec bon volume
   non présentes dans la liste initiale

## RÈGLES

- Ne remplis jamais les volumes avec des estimations
- Si Keyword Planner inaccessible → essaie
  https://app.ubersuggest.com (même format de retour)
- Si les deux sont inaccessibles → liste les mots-clés
  avec statut "volume-non-verifie" et préviens-moi
- Lecture seule — ne crée aucune campagne Google Ads
```

### Après la validation
Mets à jour l'arborescence en phase 2 si certains mots-clés
sont écartés. Ajuste le nombre de pages en conséquence.

### Livrable
- Liste de mots-clés validés avec volumes réels
- Arborescence finale confirmée
- Opportunités détectées à intégrer dans le moteur SEO

---

## PHASE 4 — GÉNÉRATION DU SITE (J1–J6)

### Outil
**Lovable** (lovable.dev)

### Objectif
Générer le site React/Tailwind avec le design system YOR.
Aucune image IA, aucun placeholder, zéro stock photo.

### Design system YOR
- Stack : React + Vite + Tailwind CSS + Lucide-React
- Polices : Playfair Display (titres) + DM Sans (corps)
- Palette : fond #0D0D0D · accent #6B3FA0 · ivoire #F5F0EB
- Hero : typographie 80–96px italic, Playfair
- Services : Bento Grid asymétrique, icônes Lucide uniquement
- Chiffres clés : Playfair Display très grand
- Aucune animation lourde, mobile-first

### Prompt Lovable principal

```
Crée un site vitrine professionnel pour [NOM], [SECTEUR]
basé(e) à [VILLE]. Cible : [CIBLE].

CONTRAINTE ABSOLUE : aucune image IA, aucun placeholder,
aucun stock photo. Design basé sur typographie + icônes SVG.

Stack : React + Tailwind CSS + Lucide-React
Polices : Playfair Display (titres) + DM Sans (corps)

Structure HTML sémantique :
— H1 unique : "[MOT-CLÉ PRINCIPAL] à [VILLE] — [NOM]"
— H2 par section de service
— aria-label sur chaque icône Lucide

Palette :
— Fond : #0D0D0D
— Accent : #6B3FA0 (violet profond)
— Texte clair : #F5F0EB

Sections :
1. Hero plein écran — titre Playfair 96px italic + stats géantes
2. Bento Grid services — 6 blocs asymétriques avec icônes Lucide
3. Section confiance — secteurs clients en ligne
4. FAQ accordéon — 4 questions avec ChevronDown
5. Contact — formulaire 3 champs + infos

Pages à créer : [LISTE DES PAGES + SLUGS VALIDÉS EN PHASE 2]
Services : [SERVICES]
Différence : [USP]
Chiffres clés : [CHIFFRES]
FAQ : [FAQ]
Meta description page d'accueil : "[META]"
OpenGraph dans le head.
Mobile-first. Pas d'animations lourdes.
```

### Itérations J1–J6
Affine le design dans Lovable par prompts successifs.
Ne jamais modifier le code directement dans Lovable —
tout passe par des prompts.

Vérifier avant de passer à la phase 5 :
- [ ] H1 unique sur chaque page contenant le mot-clé + ville
- [ ] Structure de navigation correcte
- [ ] Toutes les pages de l'arborescence présentes
- [ ] Mobile responsive validé manuellement
- [ ] Aucun placeholder visible

---

## PHASE 5 — PRÉPARATION REPO (J6)

### Outil
**Lovable** (avant l'export GitHub)

### Objectif
Nettoyer la structure du code sans toucher au design.
Cette étape évite les problèmes lors de l'optimisation
Claude Code.

### Prompt Lovable préparation

```
Le design est validé. Maintenant optimise la structure
du projet sans toucher à aucun composant visuel ni au
design Tailwind. Objectif : préparer le repo pour un
export GitHub propre et un déploiement Vercel sans friction.

Exécute dans cet ordre :

1. STRUCTURE DES FICHIERS
   — Regroupe toutes les images dans /src/assets/images/
   — Regroupe toutes les polices dans /src/assets/fonts/
   — Un composant = un fichier dans /src/components/
   — Nomme chaque fichier en PascalCase strict

2. FICHIERS DE CONFIG
   — Vérifie vite.config.ts : base = "/", build.outDir = "dist"
   — Crée vercel.json à la racine :
     { "rewrites": [{ "source": "/(.*)", "destination": "/index.html" }] }
   — Crée .gitignore propre : node_modules, dist, .env

3. NETTOYAGE CODE
   — Supprime tous les console.log
   — Supprime les composants non utilisés
   — Vérifie qu'il n'y a pas de TODO ou FIXME

4. BUILD DE VÉRIFICATION
   — Lance npm run build
   — Le build doit passer 0 erreur / 0 warning
   — Affiche la taille du bundle JS (objectif < 200kb gzippé)
```

### Livrable
Repo propre, build validé, prêt pour l'export GitHub.

---

## PHASE 6 — EXPORT GITHUB (J7)

### Outil
**GitHub** (github.com)

### Objectif
Créer le coffre-fort du code. À partir de ce moment,
`git checkout .` = filet de sécurité total.

### Étapes
1. Dans Lovable → "Export to GitHub" → créer un nouveau repo
2. Nommer le repo : `[nom-client]-site` (ex: photo-pros)
3. Vérifier que le repo est **privé** par défaut
4. Cloner en local si modifications CLI prévues :
   `git clone https://github.com/[user]/[repo].git`

### Règle d'or
**Jamais de modification directe sur la branche main.**
Toutes les modifications de Claude Code passent par des
commits clairs avec message descriptif.

### Livrable
Repo GitHub créé, code en ligne, clone local prêt.

---

## PHASE 7 — OPTIMISATION SEO (J8–J9)

### Outil
**Claude Code** (terminal)

### Objectif
Les 7 optimisations techniques SEO dans l'ordre.
Ne touche jamais au design Tailwind sans permission explicite.

### Prompt Claude Code SEO

```
Voici mon repo exporté depuis Lovable. Analyse toute la
structure du projet. Puis exécute dans cet ordre :

1. Génère /public/sitemap.xml dynamique avec toutes les pages
2. Crée /public/robots.txt (User-agent: * / Allow: /)
3. Optimise toutes les balises meta (title unique,
   description 155 chars max, OpenGraph og:title
   og:description og:type)
4. Convertis toutes les images en format .webp avec lazy loading
5. Télécharge les polices Google Fonts et héberge-les en local
6. Ajoute un JSON-LD Schema de type LocalBusiness dans le head
7. Vérifie que le build npm run build passe sans erreur

Ne touche pas au design Tailwind ni aux composants UI existants
sans me demander. Montre-moi un résumé de chaque modification.
Après chaque étape, git add + git commit avec message clair.
```

### Vérifications manuelles après Claude Code
- [ ] sitemap.xml accessible sur /sitemap.xml en prod
- [ ] robots.txt accessible sur /robots.txt
- [ ] Meta description ≤ 155 chars sur chaque page
- [ ] H1 unique contient mot-clé + ville
- [ ] JSON-LD valide (tester sur schema.org/validator)
- [ ] Images en .webp avec attribut alt non vide
- [ ] Polices en local (0 appel Google Fonts externe)
- [ ] Build : 0 erreur, 0 warning
- [ ] Bundle JS < 200kb gzippé

### Prompt correction PageSpeed (si scores insuffisants)

```
Voici le rapport PageSpeed Insights de notre site :
[COLLER LE RAPPORT]

Règle chaque point en rouge ou orange dans l'ordre de priorité.
Ne touche pas au design Tailwind ni aux composants existants.
Après chaque correction, explique ce que tu as modifié.
```

---

## PHASE 8 — MOTEUR SEO (J9)

### Outil
**Claude Code** (terminal)

### Objectif
Initialiser le YOR SEO Engine dans le repo pour la
production de contenu mensuel post-livraison.
S'applique uniquement aux offres Standard et aux
clients avec abonnement SEO contenu.

### Instructions
1. Place `yor-seo-engine-prompt.md` à la racine du repo
2. Ouvre Claude Code
3. Tape : `Read yor-seo-engine-prompt.md and follow all instructions`
4. Réponds aux 5 questions (Claude Code a détecté le reste)
5. Claude Code construit le moteur complet dans `.yor-seo/`

### Ce que le moteur génère automatiquement
- `config.yaml` — paramètres client
- `keywords.csv` — 25 à 40 mots-clés (volumes à remplir
  depuis la phase 3)
- `competitors.yaml` — matrice concurrents
- `content-map.yaml` — cartographie contenu existant
- `content-queue.yaml` — file de contenu priorisée
- `topic-clusters.yaml` — architecture pilier/cluster
- `performance-baseline.yaml` — scores actuels
- 3 templates rédaction (page service, article, guide ton)
- `GUIDE.md` — commandes disponibles

### Mise à jour keywords.csv avec les volumes validés
Après initialisation, colle les données de la phase 3 :

```
Mets à jour .yor-seo/data/keywords.csv avec ces données
de volume réelles. Réordonne les priorités en conséquence
et mets à jour content-queue.yaml.

[COLLE LE CSV RETOURNÉ PAR CLAUDE IN CHROME EN PHASE 3]
```

---

## PHASE 9 — DÉPLOIEMENT VERCEL (J10)

### Outil
**Vercel** (vercel.com)

### Objectif
Mise en ligne du site avec HTTPS automatique et CDN mondial.
Auto-deploy sur chaque push GitHub.

### Étapes
1. vercel.com → "Add New Project"
2. Connecter le repo GitHub du client
3. Framework : Vite (détecté automatiquement)
4. Build command : `npm run build`
5. Output directory : `dist`
6. Deploy

### Domaine custom
1. Acheter domaine sur OVH ou Namecheap (~12€/an)
2. Dans Vercel → Settings → Domains → ajouter le domaine
3. Ajouter CNAME chez le registrar :
   `www` → `cname.vercel-dns.com`
4. Attendre propagation DNS (5 min à 24h)
5. HTTPS activé automatiquement par Vercel

### Livrable
Site en ligne sur URL de production avec HTTPS actif.
Vercel deploy timestamp = preuve de délai J+10.

---

## PHASE 10 — AUDIT PAGESPEED (J10)

### Outil
**PageSpeed Insights** (pagespeed.web.dev)

### Objectif
Valider les scores avant livraison. On ne livre pas
en dessous des seuils garantis.

### Seuils de livraison YOR
| Métrique | Seuil minimum | Objectif |
|----------|---------------|---------|
| SEO | 100/100 | 100/100 |
| Performance bureau | 90/100 | 100/100 |
| Performance mobile | 90/100 | 95/100 |
| Bonnes pratiques | 95/100 | 100/100 |

### Procédure
1. Aller sur https://pagespeed.web.dev
2. Tester l'URL de production (pas localhost)
3. Tester bureau ET mobile
4. Capturer les scores (screenshot horodaté)
5. Si score insuffisant → retour phase 7 avec prompt correction

### Livrable
- Capture PageSpeed bureau + mobile horodatée
- URL PageSpeed publique à partager avec le client
- Les scores sont vérifiables par n'importe qui

---

## PHASE 11 — GOOGLE SEARCH CONSOLE (J10)

### Outil
**Google Search Console** (search.google.com/search-console)

### Objectif
Déclarer le site à Google, soumettre le sitemap,
demander l'indexation. Indexation garantie en < 7 jours.

### Étapes dans l'ordre
1. Search Console → Ajouter une propriété → URL
2. Méthode de vérification : balise HTML meta
3. Copier la balise de vérification
4. Injecter dans le head via Claude Code :

```
Injecte cette balise dans le <head> de index.html
juste après la balise charset, sans toucher à autre chose.
Puis git push :

[COLLER LA BALISE GOOGLE]
```

5. Vercel redéploie automatiquement (2 min)
6. Retour Search Console → Vérifier
7. Sitemap → Soumettre : `https://[domaine]/sitemap.xml`
8. Inspection d'URL → Demander l'indexation sur la page d'accueil

### Livrable
- Propriété Search Console vérifiée (capture)
- Sitemap soumis
- Demande d'indexation envoyée

---

## CHECKLIST DE LIVRAISON YOR

### Technique
- [ ] H1 unique présent et contient le mot-clé + ville
- [ ] Meta description ≤ 155 caractères sur chaque page
- [ ] Balises OpenGraph présentes (og:title, og:description, og:type)
- [ ] /sitemap.xml accessible en production
- [ ] /robots.txt accessible en production
- [ ] JSON-LD LocalBusiness dans le head
- [ ] Images en .webp avec lazy loading et attribut alt
- [ ] Polices hébergées en local (0 appel Google Fonts externe)
- [ ] npm run build : 0 erreur, 0 warning
- [ ] Bundle JS < 200kb gzippé
- [ ] vercel.json présent à la racine

### Performance
- [ ] Score SEO Lighthouse : 100/100
- [ ] Performance bureau : 90+ (objectif 100)
- [ ] Performance mobile : 90+ (objectif 95)
- [ ] HTTPS actif (cadenas vert)
- [ ] Capture PageSpeed horodatée

### Déploiement
- [ ] Site en ligne sur URL de production
- [ ] Domaine custom configuré (si applicable)
- [ ] Search Console : propriété vérifiée
- [ ] Sitemap soumis dans Search Console
- [ ] Demande d'indexation envoyée
- [ ] Repo GitHub livré au client (ou accès transmis)

---

## PERFORMANCES GARANTIES À LA LIVRAISON

| Métrique | Garanti | Preuve |
|----------|---------|--------|
| Score SEO Lighthouse | 100/100 | Capture PageSpeed |
| Performance bureau | 100/100 | URL PageSpeed publique |
| Performance mobile | 95/100 | Vérifiable par le client |
| Site en ligne | J+10 | Vercel deploy timestamp |
| Indexation Google | < 7 jours | Search Console |
| Propriété du code | Totale | Repo GitHub livré |

**Non garanti :** position précise sur Google, maintien
du score si le client ajoute des scripts tiers après livraison.

---

## APRÈS LA LIVRAISON — OFFRES RÉCURRENTES

### Maintenance (29–99€/mois)
- Hébergement Vercel
- Monitoring uptime
- 1 modification mensuelle
- Rapport Search Console mensuel

### SEO Contenu (350–600€/mois)
- 2 pages ou articles par mois
- Basé sur le moteur YOR SEO Engine (.yor-seo/)
- Processus : sélection mot-clé → données SERP → rédaction
  → relecture humaine → publication → mise à jour sitemap
- Commande Claude Code : "Écris le prochain contenu"

### Modification ponctuelle
- 80–120€ par ticket
- Délai : 48–72h
- Prompt Claude Code → git push → Vercel auto-deploy

---

## OUTILS & RESSOURCES

| Outil | Usage | URL |
|-------|-------|-----|
| Lovable | Génération site | lovable.dev |
| GitHub | Versioning | github.com |
| Claude Code | Optimisation SEO | Terminal |
| Claude in Chrome | Validation mots-clés | Navigateur |
| Vercel | Hébergement | vercel.com |
| PageSpeed | Audit performance | pagespeed.web.dev |
| Search Console | Indexation | search.google.com/search-console |
| Google Keyword Planner | Volumes mots-clés | ads.google.com |
| Ubersuggest | Backup volumes | app.ubersuggest.com |
| OVH / Namecheap | Domaine (~12€/an) | ovh.com |
| Schema Validator | Vérif JSON-LD | validator.schema.org |
```
