# YOR — Référence Prompts & Templates

## Grand prompt Claude Code SEO (à copier tel quel)

```
Voici mon repo exporté depuis Lovable. Analyse toute la structure
du projet. Puis exécute dans cet ordre :

1. Génère /public/sitemap.xml dynamique avec toutes les pages
2. Crée /public/robots.txt (User-agent: * / Allow: /)
3. Optimise toutes les balises meta (title unique, description 155
   chars max, OpenGraph og:title og:description og:type)
4. Convertis toutes les images en format .webp avec lazy loading
5. Télécharge les polices Google Fonts et héberge-les en local
6. Ajoute un JSON-LD Schema de type LocalBusiness dans le head
7. Vérifie que le build npm run build passe sans erreur

Ne touche pas au design Tailwind ni aux composants UI existants
sans me demander. Montre-moi un résumé de chaque modification.
```

---

## Prompt Lovable — Template élégance YOR

```
Crée un site vitrine professionnel pour [NOM], [SECTEUR] basé(e)
à [VILLE]. Cible : [CIBLE].

CONTRAINTE ABSOLUE : aucune image IA, aucun placeholder,
aucun stock photo. Design basé sur typographie + icônes SVG.

Stack : React + Tailwind CSS + Lucide-React
Polices : Playfair Display (titres) + DM Sans (corps)

Structure HTML sémantique :
— H1 unique : "[SECTEUR] à [VILLE] — [NOM]"
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

Services : [SERVICES]
Différence : [USP]
FAQ : [FAQ]
Meta description : "[META]"
OpenGraph dans le head.
Mobile-first. Pas d'animations lourdes.
```

---

## Prompt Lovable — Préparation repo (à envoyer après validation du design)

> Envoyer ce prompt dans Lovable une fois le design validé, avant l'export GitHub.
> Objectif : nettoyer la structure du code pour que Claude Code, Vercel et GitHub
> travaillent sans friction. Ne touche à rien de visuel.

```
Le design est validé. Maintenant optimise la structure
du projet sans toucher à aucun composant visuel ni au
design Tailwind. Objectif : préparer le repo pour un
export GitHub propre, un déploiement Vercel sans friction
et une optimisation SEO par un agent CLI.

Exécute dans cet ordre :

1. STRUCTURE DES FICHIERS
   — Regroupe toutes les images dans /src/assets/images/
   — Regroupe toutes les polices dans /src/assets/fonts/
   — Un composant = un fichier dans /src/components/
   — Nomme chaque fichier en PascalCase strict

2. INDEX.HTML
   — Toutes les balises <meta> dans le <head> en un seul
     bloc commenté "/* SEO */"
   — Les balises OpenGraph juste après, commentées "/* OG */"
   — Prévoir un emplacement vide commenté
     "<!-- JSON-LD Schema : à injecter -->"
     juste avant </head>
   — Les polices Google Fonts en @import dans un seul
     fichier /src/styles/fonts.css (pas d'appel <link>
     direct dans le HTML — plus facile à remplacer
     en local ensuite)

3. FICHIERS PUBLICS
   — Crée /public/robots.txt avec :
     User-agent: *
     Allow: /
   — Crée /public/sitemap.xml vide avec la structure
     de base xmlns, prêt à être rempli
   — Crée /public/.htaccess vide

4. CONFIGURATION VITE
   — Dans vite.config.ts, ajoute :
     base: '/'
     build.outDir: 'dist'
     build.assetsDir: 'assets'
   — Vérifie que npm run build passe sans erreur
     ni warning

5. VARIABLES D'ENVIRONNEMENT
   — Crée un fichier .env.example avec les variables
     à renseigner : VITE_SITE_URL, VITE_CONTACT_EMAIL,
     VITE_PHONE
   — Remplace toutes les valeurs en dur (email, téléphone,
     URL) par ces variables dans les composants

6. ROUTING
   — Vérifie que React Router est configuré avec
     createBrowserRouter
   — Chaque route pointe vers une page dans /src/pages/
   — Ajoute une page 404 sobre avec lien retour accueil

7. BUILD FINAL
   — Lance npm run build
   — Montre le résumé : taille du bundle, fichiers générés,
     0 erreur, 0 warning

Ne modifie aucun style Tailwind, aucune couleur, aucune
typographie, aucun layout. Uniquement la structure et
la configuration.
```

---

## Prompt correction PageSpeed

```
Voici le rapport PageSpeed Insights de notre site :
[COLLER LE RAPPORT]

Règle chaque point en rouge ou orange dans l'ordre de priorité.
Ne touche pas au design Tailwind ni aux composants existants.
Après chaque correction, explique ce que tu as modifié.
```

---

## Prompt injection balise Search Console

```
Injecte cette balise dans le <head> de index.html juste après
la balise charset, sans toucher à autre chose. Puis git push :

[COLLER LA BALISE GOOGLE]
```

---

## Prompt ajout page/article mensuel (maintenance)

```
Dans le repo, crée une nouvelle page "[TITRE]" avec le même
style et la même structure que les pages existantes.

Contenu : [INFOS]
Mots-clés cibles : [MOTS-CLÉS]
Meta description : [META]

Mets à jour le sitemap.xml pour inclure cette nouvelle page.
Ne touche pas aux autres composants. Git push quand c'est prêt.
```

---

## Prompt sitemap — correction URL

```
Dans public/sitemap.xml, remplace toutes les occurrences de
[ANCIENNE URL] par [NOUVELLE URL]. Puis git push.
```

---

## Checklist livraison YOR

- [ ] H1 unique présent et contient le mot-clé + ville
- [ ] Meta description ≤ 155 caractères
- [ ] Balises OpenGraph présentes (og:title, og:description, og:type)
- [ ] /public/sitemap.xml accessible en ligne
- [ ] /public/robots.txt accessible en ligne
- [ ] JSON-LD LocalBusiness dans le head
- [ ] Images en .webp avec lazy loading
- [ ] Polices hébergées en local (pas d'appel Google Fonts externe)
- [ ] npm run build : 0 erreur, 0 warning
- [ ] Score SEO Lighthouse : 100/100
- [ ] Score Performance bureau : 90+
- [ ] HTTPS actif (cadenas vert)
- [ ] Search Console : propriété vérifiée
- [ ] Sitemap soumis dans Search Console
- [ ] Demande d'indexation envoyée

---

## Tarifs de référence

| Offre | Tarif |
|---|---|
| One-Shot Starter (3–4 pages) | 800–1 200€ |
| One-Shot Standard (5+ pages + contenu) | 1 500–2 500€ |
| Maintenance + hébergement | 29–99€/mois |
| SEO contenu (2 pages/mois) | 200–500€/mois |
| Ticket modification ponctuelle | 50€ |

---

## Contacts & ressources

- Email Max : levysoulamax@yamen-global.com
- Email client Photo Pro : levysoulamax@gmail.com
- Repo Photo Pro : github.com/max-bit16/photo-pros
- Site Photo Pro : https://photo-pros.vercel.app
- PageSpeed : pagespeed.web.dev
- Search Console : search.google.com/search-console
- Vercel : vercel.com
- Netlify Drop (hébergement rapide questionnaire) : netlify.com/drop
