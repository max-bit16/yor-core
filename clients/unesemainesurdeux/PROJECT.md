# Une Semaine Sur Deux

## Infos
- **Secteur** : Restaurant gastronomique
- **Ville** : Grenoble (4 Place Championnet, 38000)
- **Structure** : Chef Pierrick Vasseur — Gault & Millau 2026 "Table Gourmande"
- **Contact** : +33 4 76 27 13 75 · restaurant1sur2@gmail.com
- **Social** : @1semainesur2restaurant (Instagram) · facebook.com/1sur2grenoble

## Repo & Deploy
- **GitHub** : https://github.com/max-bit16/unesemainesurdeux
- **Vercel** : https://unesemainesurdeux.vercel.app
- **Domaine** : restaurant1sur2.fr (à connecter)

## Stack
- **Chemin** : Lovable → Claude Code
- **Framework** : TanStack Start + Tailwind (Lovable lock)
- **Skin** : Editorial Light (Cormorant Garamond + DM Sans)
- **Palette** : Forest green #2C4A3E · Gold #C8965A · Cream

## Scores PageSpeed
- **Mobile** : 77 (objectif 90+ après fix images)
- **Desktop** : —
- **SEO** : 92
- **Best Practices** : 100

## Statut
- [x] Design (Lovable v3)
- [x] Claude Code
- [x] Vercel
- [ ] DNS restaurant1sur2.fr configuré
- [ ] VITE_SITE_URL env var mise à jour
- [ ] GSC configuré
- [ ] Node.js 20.19+ dans Vercel settings
- [ ] Performance mobile 90+ (images locales .webp)

## Notes
- 15 images JPEG → webp (20–95% réduction)
- Cloudflare → Vercel migration (suppression @lovable.dev/vite-tanstack-config)
- AnimatedCounter : mount → IntersectionObserver (fix CLS)
- Radix UI 43 packages supprimés
- SSH ed25519 recommandé (levysoulamax@gmail.com) pour remplacer PAT
