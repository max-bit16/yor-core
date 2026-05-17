# YOR — AJOUT DE CONTENU
# Yamen Global · Version 1.0 · Avril 2026
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## VUE D'ENSEMBLE

| Phase | Étape                     | Outil            | Délai   |
|-------|---------------------------|------------------|---------|
| 1     | Définition du contenu     | Claude (chat)    | J0      |
| 2     | Validation mot-clé        | Ubersuggest      | J0      |
| 3     | Rédaction du contenu      | Claude (chat)    | J0–J1   |
| 4     | Génération prompt         | Claude (chat)    | J1      |
| 5     | Exécution Claude Code     | Claude Code      | J1      |
| 6     | Vérification build        | Terminal / Dev   | J1      |
| 7     | Contrôle PageSpeed        | PageSpeed        | J1      |
| 8     | Indexation                | Search Console   | J1–J2   |

Délai total : **1 à 2 jours.**
On ne livre pas si le build échoue ou si le score SEO descend sous 100.

---

## PHASE 1 — DÉFINITION DU CONTENU (J0)

### Outil
Claude (chat)

### Objectif
Décider précisément quoi ajouter et pourquoi.

### Questions à répondre
1. **Type de contenu** — section, page, article de blog ?
2. **Objectif** — SEO local, conversion, crédibilité, information ?
3. **Position dans le site** — où s'insère-t-il dans l'arborescence ?
4. **Informations disponibles** — le client fournit quoi exactement ?

### Livrable
Fiche contenu : type + objectif + position + matière brute.

---

## PHASE 2 — VALIDATION MOT-CLÉ (J0)

### Outil
Ubersuggest (app.neilpatel.com/en/ubersuggest/keyword_bulk_analysis)

### Objectif
Vérifier que le contenu cible un mot-clé avec du volume réel.
Un contenu sans mot-clé validé ne sera pas indexé.

### Étapes
1. Identifier le mot-clé principal du contenu (ex. "cabinet conseil Paris 11")
2. Identifier 3 à 5 variantes (ex. "consultant stratégie Paris", "conseil entreprise Paris 11e")
3. Coller dans Ubersuggest → extraire les volumes
4. Choisir le mot-clé principal (volume ≥ 50/mois)
5. Garder les variantes pour les H3 et le corps du texte

### Livrable
Mot-clé principal validé + liste de variantes avec volumes.

---

## PHASE 3 — RÉDACTION DU CONTENU (J0–J1)

### Outil
Claude (chat)

### Objectif
Produire le texte final prêt à intégrer — titres, sous-titres,
corps du texte, meta description.

### Règles YOR
- Mot-clé principal dans le titre H2 et les 100 premiers mots
- Ville + arrondissement mentionnés en texte naturel (pas en liste)
- Chiffres concrets, exemples de missions réelles si possible
- Aucun jargon vague ("solutions sur mesure", "expertise reconnue")
- Meta description : 120–155 caractères, mot-clé + bénéfice

### Livrable
Contenu final structuré : label / H2 / intro / items / meta description.

---

## PHASE 4 — GÉNÉRATION DU PROMPT CLAUDE CODE (J1)

### Outil
Claude (chat)

### Objectif
Produire le prompt complet à coller dans Claude Code.
Le prompt doit être autonome — Claude Code n'a pas de contexte préalable.

### Le prompt doit inclure
1. Instruction de scan du repo (structure, composants, Framer Motion)
2. Classes CSS exactes extraites du site (ne pas approximer)
3. Contenu final rédigé en phase 3
4. Instruction d'intégration (position dans App.tsx)
5. Mise à jour navbar si nécessaire
6. Mise à jour JSON-LD (adresse, areaServed)
7. Vérification build npm run build
8. Git commit + push avec message conventionnel

### Livrable
Prompt Claude Code complet, copié dans le fichier de référence
`prompt_claudecode_ajout_contenu_[TYPE].md`

---

## PHASE 5 — EXÉCUTION CLAUDE CODE (J1)

### Outil
Claude Code (terminal, dans le repo client)

### Objectif
Créer le composant, l'intégrer, mettre à jour le SEO, pusher.

### Étapes
1. `cd [repo]` puis `claude`
2. Coller le prompt en une seule fois
3. Claude Code scanne, crée, intègre, vérifie, commit, push
4. Confirmer le message de commit et l'URL du push

### Livrable
Commit pushé sur GitHub. Vercel deploy déclenché automatiquement.

---

## PHASE 6 — VÉRIFICATION BUILD ET VISUEL (J1)

### Outil
Terminal + navigateur (localhost ou URL Vercel preview)

### Objectif
S'assurer que le contenu s'affiche correctement et que le
build est propre avant de tester les scores.

### Checklist
- [ ] `npm run build` → 0 erreur, 0 warning
- [ ] Section visible à la bonne position dans la page
- [ ] Design cohérent avec les sections adjacentes
- [ ] Hover effects fonctionnels
- [ ] Lien navbar pointe vers la bonne ancre
- [ ] Responsive mobile correct

### Livrable
Build propre confirmé. Contenu validé visuellement.

---

## PHASE 7 — CONTRÔLE PAGESPEED (J1)

### Outil
PageSpeed Insights (pagespeed.web.dev)

### Objectif
Vérifier que l'ajout de contenu n'a pas dégradé les scores.
Le contenu texte pur ne doit pas impacter la performance.

### Seuils minimum YOR
| Métrique       | Seuil     |
|----------------|-----------|
| SEO            | 100/100   |
| Performance    | ≥ 90/100  |
| Bonnes prat.   | ≥ 95/100  |

### Si un score baisse
Revenir dans Claude Code avec le rapport PageSpeed et corriger
avant de valider la livraison.

### Livrable
Capture PageSpeed horodatée avec scores conformes.

---

## PHASE 8 — INDEXATION (J1–J2)

### Outil
Google Search Console

### Objectif
Signaler à Google le nouveau contenu pour accélérer l'indexation.

### Étapes
1. Ouvrir Search Console sur la propriété du site
2. Outil d'inspection d'URL → coller l'URL de la page
3. "Demander l'indexation"
4. Si nouveau contenu sur landing page : demander l'indexation
   sur l'URL racine (ex. https://yamen-global.com)

### Délai d'indexation
En général : 24h à 7 jours selon la fréquence de crawl du site.

### Livrable
Demande d'indexation envoyée. Confirmation dans Search Console.

---

## RÉCAPITULATIF LIVRABLES

| Phase | Livrable |
|-------|----------|
| 1 | Fiche contenu (type, objectif, position, matière) |
| 2 | Mot-clé principal + variantes avec volumes validés |
| 3 | Contenu rédigé (H2, intro, items, meta) |
| 4 | Prompt Claude Code sauvegardé |
| 5 | Commit GitHub + deploy Vercel confirmé |
| 6 | Build propre + validation visuelle |
| 7 | Capture PageSpeed scores conformes |
| 8 | Indexation demandée dans Search Console |

---

*Yamen Global · YOR Ajout de contenu · Avril 2026*
*yamen-global.com*
