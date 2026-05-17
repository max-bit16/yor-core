# Azur Mas

## Infos
- **Secteur** : Restaurant gastronomique (demo Méditerranéen)
- **Ville** : —
- **Structure** : Site vitrine demo YOR — cuisine méditerranéenne fictive

## Repo & Deploy
- **GitHub** : https://github.com/max-bit16/azur-mas-next
- **Vercel** : https://azur-mas-next.vercel.app
- **Domaine** : —

## Stack
- **Chemin** : Claude Design (Stitch) → Claude Code
- **Framework** : Next.js 14 App Router + output: 'export' (SSG)
- **Skin** : Mediterranean Luxury (Cinzel + Manrope)
- **Palette** : Azure #005D90 · Gold #C5A059 · Blanc

## Scores PageSpeed
- **Mobile** : 93
- **Desktop** : 91
- **SEO** : 100
- **Best Practices** : 100

## Statut
- [x] Design (Stitch export)
- [x] Claude Code
- [x] Migration Vite → Next.js SSG
- [x] Vercel
- [x] GSC vérifié + sitemap soumis
- [ ] Images WebP trackées dans git
- [ ] Domaine connecté

## Notes
- Premier cas Stitch → Claude Code documenté
- Migration Vite → Next.js output:'export' pour PageSpeed mobile 57 → 93
- app/sitemap.ts incompatible avec output:'export' → public/sitemap.xml statique
- Material Symbols : preload async pattern (non blocking)
- vercel.json pour headers CDN (output:'export' ignore next.config.ts headers)
- 5 animations natives : useReveal, useScrollProgress, useTilt, useMagneticZoom, gold shimmer
