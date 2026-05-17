# Assets YOR

Ressources visuelles réutilisables par projet.
Toutes les images doivent être en .webp avant utilisation.
Conversion : sharp (jamais sips).

## Structure

assets/
├── photos/     ← photos de fond, heroes, ambiance par secteur
├── videos/     ← vidéos de fond (MP4, max 5MB)
└── ui/         ← icônes, logos, éléments graphiques

## Sources autorisées
- Unsplash : images.unsplash.com (pas source.unsplash.com)
- Pexels CDN
- Photos client fournies directement

## Règles
- Format : .webp uniquement en production
- Nommage : [secteur]-[description]-[id].webp
  ex: avocat-bureau-01.webp, restaurant-salle-02.webp
- Dimensions hero : 1920x1080 minimum
- og:image : 1200x630 exactement
