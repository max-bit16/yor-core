# YOR — Recommandations Design & Workflow à Évaluer

> Ce document liste des améliorations identifiées à partir de la veille Gemini 3.1 / AntiGravity (avril 2026).
> Ces éléments ne sont PAS intégrés par défaut dans le workflow YOR.
> Avant chaque projet, Claude te demande lesquels activer selon le contexte client.

---

## Comment utiliser ce document

Au démarrage de chaque projet, Claude passe en revue les recommandations ci-dessous
et te conseille sur leur pertinence selon : le secteur client, le budget, le niveau
d'ambition visuelle, et le délai. Tu valides ou refuses chaque option. Rien n'est
appliqué sans ta confirmation.

---

## Recommandation 1 — SVG animé dans le Hero

**Quoi :** Remplacer l'absence d'image dans le Hero par un SVG animé généré (formes géométriques, lignes cinétiques, particules légères). Pas d'image IA — juste du code SVG/CSS.

**Pourquoi ça marche :** Gemini 3.1 Pro génère des SVG animés directement depuis un prompt texte, propres et prêts pour le web. Ça donne du mouvement sans alourdir la performance.

**Impact performance :** Neutre si SVG inline ou en fichier léger. À vérifier au PageSpeed avant livraison.

**Pertinent pour :** Clients avec une identité visuelle forte (studio, agence, conseil), secteurs créatifs, sites haut de gamme. Moins pertinent pour artisans ou professions libérales classiques.

**Comment l'activer :** Ajouter dans le prompt Lovable, section Hero :
```
Hero : ajoute un SVG animé en arrière-plan — formes géométriques
abstraites en dégradé violet/ivoire, animation CSS lente (20s loop),
opacity 15% maximum pour ne pas écraser la typographie.
Inline SVG dans le composant, pas de fichier externe.
```

**Risque :** Lovable peut générer un SVG trop lourd ou mal optimisé. À auditer dans Claude Code avant push.

---

## Recommandation 2 — Glassmorphism léger sur les cards Bento

**Quoi :** Appliquer un effet verre dépoli subtil sur les blocs de la Bento Grid (backdrop-filter: blur + fond semi-transparent) à la place du fond #0D0D0D plein.

**Pourquoi ça marche :** Tendance 2026 identifiée par Viktor Oddy. Fonctionne bien avec le fond sombre YOR. Donne de la profondeur sans image.

**Impact performance :** `backdrop-filter` peut peser sur le rendu GPU sur mobile. À tester mobile avant livraison — si score mobile descend sous 90, on retire.

**Pertinent pour :** Clients avec budget Standard ou plus, secteurs premium (luxe, conseil, tech). Pas adapté aux sites artisans où la simplicité rassure.

**Comment l'activer :** Dans le prompt Lovable, section Bento Grid :
```
Bento Grid : applique un glassmorphism léger sur chaque bloc —
background: rgba(245, 240, 235, 0.04), backdrop-filter: blur(12px),
border: 1px solid rgba(245, 240, 235, 0.08).
Tester que le rendu mobile reste fluide.
```

**Risque :** Support partiel sur certains navigateurs anciens (Safari < 14). Acceptable pour la cible YOR.

---

## Recommandation 3 — Exploration de variantes avec Gemini 3.1 Pro Canvas avant de locker le prompt Lovable

**Quoi :** Avant d'envoyer le prompt final à Lovable, passer 15–20 minutes sur Gemini Canvas (gemini.google.com, modèle 3.1 Pro, mode Canvas activé) pour tester 2–3 directions visuelles à partir d'un prompt léger.

**Pourquoi ça marche :** Gemini génère de l'HTML/CSS interactif directement dans le navigateur. Ça permet de montrer une direction au client AVANT de consommer les tokens Lovable, et d'éviter les allers-retours.

**Impact workflow :** Ajoute ~30 minutes en J1, économise potentiellement 2–3 itérations Lovable.

**Pertinent pour :** Clients hésitants sur la direction visuelle, projets Standard avec plusieurs pages, clients qui veulent "voir quelque chose" avant de valider.

**Comment l'activer :** Session Gemini Canvas avec ce prompt type :
```
Crée une landing page hero pour [SECTEUR], ambiance [MOT CLÉ VIBE],
palette sombre fond #0D0D0D accent #6B3FA0, typographie serif pour
les titres. Pas d'image. Résultat en HTML/CSS interactif.
```
Capture d'écran → partage client → validation → prompt Lovable complet.

**Risque :** L'output Gemini Canvas n'est pas du React/Tailwind — c'est une exploration, pas du code livrable. Ne pas confondre avec le produit final.

---

## Recommandation 4 — AntiGravity comme alternative à Claude Code

**Quoi :** Google AntiGravity (antigravity.google) est un IDE agentique basé sur VS Code avec Gemini 3.1 Pro intégré. L'agent peut lire le repo, exécuter des commandes terminal, ouvrir le navigateur et vérifier le résultat lui-même.

**Pourquoi c'est intéressant :** Pour les projets complexes (5+ pages, animations, contenu riche), AntiGravity peut exécuter les 7 étapes SEO de façon plus autonome que Claude Code — il voit le navigateur et corrige en temps réel.

**Impact workflow :** Remplace la phase Claude Code (J8–J9). Même résultat attendu, potentiellement moins d'allers-retours sur les erreurs de build.

**Pertinent pour :** Projets Standard avec beaucoup de pages, clients avec des demandes de personnalisation post-Lovable, quand Claude Code boucle sur une erreur.

**Prérequis :** Installation locale (Mac/Windows), compte Gmail personnel, Chrome. Gratuit avec quota limité sur Gemini 3 Pro.

**Risque :** Outil en preview, quotas limités, moins maîtrisé que Claude Code dans le workflow actuel. À tester sur un projet interne avant de l'utiliser en production client.

**Statut :** Non testé sur YOR. À expérimenter sur le prochain projet interne.

---

## Récapitulatif — Matrice de pertinence

| Recommandation | Starter | Standard | Premium | Délai serré | Client conservateur |
|---|---|---|---|---|---|
| SVG animé Hero | ⚠️ selon secteur | ✅ | ✅ | ❌ | ❌ |
| Glassmorphism Bento | ❌ | ⚠️ selon secteur | ✅ | ⚠️ à tester | ❌ |
| Gemini Canvas exploration | ❌ | ✅ | ✅ | ❌ | ✅ |
| AntiGravity vs Claude Code | ❌ | ⚠️ si erreurs | ✅ | ❌ | — |

✅ Recommandé · ⚠️ À évaluer · ❌ Ne pas activer

---

*Document créé : avril 2026 — Source : veille Gemini 3.1 / Viktor Oddy / Meng To / Adrien Ninet*
*À mettre à jour après chaque test en conditions réelles.*
