# Étude Chauvel

## Infos
- **Secteur** : Avocat
- **Ville** : Rennes
- **Structure** : Cabinet solo — Maître Olivier Chauvel
- **Domaines** : Famille, Dommage corporel, Pénal, Étrangers, Chasse

## Repo & Deploy
- **GitHub** : https://github.com/max-bit16/olivier-chauvel-avocat
- **Vercel** : https://olivier-chauvel-avocat.vercel.app
- **Domaine** : olivierchauvel-avocat.fr (à connecter)

## Stack
- **Chemin** : Claude Code (Babel-standalone static)
- **Framework** : JSX Babel runtime (sans bundler)
- **Skin** : Editorial Luxury (Cormorant Garamond + DM Sans)
- **Palette** : Navy #1B2D47 · Gold #9A7332 · Cream #F9F7F2

## Scores PageSpeed
- **Mobile** : à mesurer après migration Vite
- **Desktop** : à mesurer après migration Vite
- **SEO** : 100
- **Design Health** : 25 → 28 → 33+/40

## Statut
- [x] Design
- [x] Claude Code
- [x] Vercel
- [ ] Migration Babel → Vite (recommandée)
- [ ] Domaine connecté
- [ ] GSC configuré
- [ ] Livré client

## Notes
- Design critique score 28/40 → corrections P0/P1/P2 appliquées
- Floating pill nav + frosted glass backdrop
- Pages légales FR créées (mentions, RGPD, CGV)
- Focus trap mobile menu implémenté
- Formulaire contact avec validation onBlur + loading state
- Photos de fond compétences : webp via sharp (opacity 0.35 + scrim)
- Babel-standalone bloque Performance 90+ — migration Vite prioritaire avant livraison
