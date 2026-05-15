# PrescriTech — Prompt Claude Code MVP

## Contexte projet

Tu es un développeur senior fullstack. Tu dois créer le MVP d'une plateforme web appelée **PrescriTech** : un outil de prescription technique intelligente destiné aux **architectes et bureaux d'études** du secteur de la construction.

## Stack technique

- **Framework** : Next.js 14 avec App Router (TypeScript)
- **ORM** : Prisma
- **Base de données** : PostgreSQL (utilise le fichier `schema.sql` fourni)
- **Styling** : Tailwind CSS
- **IA** : OpenAI API (modèle `gpt-4o-mini`) pour l'analyse sémantique du besoin
- **Données initiales** : `mock_data.json` fourni à charger via un script de seed Prisma

---

## Périmètre MVP (étapes 1, 3 et 4 uniquement)

### Étape 1 — Saisie du besoin
- Page d'accueil avec un grand champ de saisie en langage naturel
- Placeholder guidant l'utilisateur : "Décrivez votre besoin technique : type d'espace, performances attendues, contexte du projet…"
- Bouton "Analyser mon besoin"
- Optionnel : quelques suggestions de questions rapides (chips cliquables) comme "Isolation façade RT2020", "Acoustique bureau open space", "Vitrage passif"

### Étape 2 (simplifiée) — Analyse sémantique (interne, pas d'UI dédiée)
- Appel à l'API OpenAI pour extraire depuis le texte brut :
  - `type_projet` (neuf | rénovation)
  - `type_usage` (résidentiel | tertiaire | ERP | data_center)
  - `type_espace` (ex: façade_extérieure, bureau, combles…)
  - `normes_requises` (ex: RE2020, ACERMI, NF S31-080…)
  - `contraintes_tags` (ex: acoustique, thermique, feu, humidité…)
- Retourner ces paramètres en JSON structuré
- Enregistrer le besoin en base (table `besoins`)

### Étape 3 — Filtrage produits
- Requête Prisma sur la table `produits` en croisant :
  - `conditions_usage` contient `type_usage`
  - `type_espace` contient le type d'espace extrait
  - `normes_conformes` contient au moins une des normes requises (si précisées)
- Score de pertinence calculé côté serveur :
  - +30 points si le type_espace correspond exactement
  - +25 points par norme correspondante
  - +20 points si conditions_usage correspond
  - +10 points si fabricant actif avec zone_geo compatible
  - +15 points bonus si le produit apparaît dans des projets similaires

### Étape 4 — Page de résultats / recommandations
- Afficher les produits recommandés triés par score décroissant (max 6)
- Chaque carte produit doit afficher :
  - Nom, catégorie, sous-catégorie
  - Logo fabricant
  - Performances clés (2-3 métriques extraites du champ JSONB `performances`)
  - Normes conformes (badges)
  - Prix indicatif HT
  - Bouton "Voir la fiche technique" (lien PDF)
  - Indicateurs BIM (icônes IFC / RFA si disponibles)
- Section "Projets similaires" sous les recommandations :
  - Afficher 2-3 projets de référence liés aux produits recommandés
  - Chaque projet : image, titre, ville, type bâtiment, surface, année, labels

---

## Architecture des fichiers attendue

```
prescritech/
├── app/
│   ├── page.tsx                    # Page d'accueil — saisie du besoin
│   ├── resultats/
│   │   └── page.tsx                # Page de résultats — recommandations
│   ├── api/
│   │   └── analyser/
│   │       └── route.ts            # POST : analyse NLP + filtrage + enregistrement
│   └── layout.tsx
├── components/
│   ├── SearchForm.tsx               # Formulaire de saisie
│   ├── ProduitCard.tsx              # Carte produit recommandé
│   ├── ProjetCard.tsx               # Carte projet référence
│   └── ScoreBadge.tsx               # Badge de score de pertinence
├── lib/
│   ├── prisma.ts                    # Client Prisma singleton
│   ├── analyser-besoin.ts           # Appel OpenAI + extraction JSON
│   └── filtrer-produits.ts          # Logique de scoring + requête Prisma
├── prisma/
│   ├── schema.prisma
│   └── seed.ts                      # Chargement de mock_data.json
├── public/
├── schema.sql                       # Schéma SQL de référence
├── mock_data.json                   # Données fictives
└── .env.local                       # OPENAI_API_KEY + DATABASE_URL
```

---

## Prompt système OpenAI pour l'extraction sémantique

Utilise ce prompt système dans `analyser-besoin.ts` :

```
Tu es un assistant spécialisé en prescription technique dans le bâtiment.
Ton rôle est d'analyser une demande exprimée en langage naturel par un architecte ou un bureau d'études,
et d'en extraire des paramètres techniques structurés.

Réponds UNIQUEMENT en JSON valide, sans texte supplémentaire, avec cette structure exacte :
{
  "type_projet": "neuf | rénovation | indéterminé",
  "type_usage": "résidentiel | tertiaire | ERP | data_center | mixte | indéterminé",
  "type_espace": "string (ex: façade_extérieure, combles_perdus, bureau, salle_de_classe)",
  "normes_requises": ["liste de normes mentionnées ou déduites, ex: RE2020, ACERMI"],
  "contraintes_tags": ["liste de contraintes, ex: acoustique, thermique, incendie, humidité"],
  "surface_m2": number | null,
  "localisation": "string | null",
  "resume_besoin": "string court résumant le besoin en 1 phrase"
}
```

---

## Contraintes de développement

1. **Pas d'authentification** pour le MVP — sessions anonymes avec un `session_id` généré côté client (uuid stocké en localStorage)
2. **Responsive** : l'interface doit fonctionner sur desktop et tablette
3. **Loading states** : afficher un état de chargement pendant l'analyse IA (spinner + message "Analyse de votre besoin en cours…")
4. **Gestion d'erreurs** : si l'analyse OpenAI échoue, effectuer un filtrage basique par mots-clés
5. **Variables d'environnement** à configurer dans `.env.local` :
   - `DATABASE_URL` = connexion PostgreSQL
   - `OPENAI_API_KEY` = clé OpenAI
6. **Seed** : le script `prisma/seed.ts` doit lire `mock_data.json` et insérer toutes les données en respectant les foreign keys (ordre : fabricants → produits → projets_reference → produits_projets)

---

## Design et UX

- Interface sobre et professionnelle (pas de couleurs criardes)
- Palette : blanc + gris clair + bleu profond (#1B3A6B) comme couleur principale
- Typographie : Inter ou system-ui
- La page d'accueil doit inspirer confiance et professionnalisme (secteur B2B)
- Les badges de normes doivent être visuellement distincts (couleur selon famille : thermique, acoustique, sécurité incendie)

---

## Ordre de développement recommandé

1. Initialiser le projet Next.js 14 + Prisma + Tailwind
2. Configurer le schéma Prisma à partir de `schema.sql`
3. Créer et exécuter le seed avec `mock_data.json`
4. Implémenter `analyser-besoin.ts` (OpenAI)
5. Implémenter `filtrer-produits.ts` (scoring + requête Prisma)
6. Créer la route API `POST /api/analyser`
7. Créer les composants `ProduitCard`, `ProjetCard`, `ScoreBadge`
8. Créer la page d'accueil (`page.tsx`)
9. Créer la page de résultats (`resultats/page.tsx`)
10. Tests manuels avec les 5 fabricants et 9 produits du jeu de données
