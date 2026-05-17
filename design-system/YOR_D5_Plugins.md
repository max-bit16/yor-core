# YOR — DOSSIER 5 : CLAUDE CODE PLUGINS
# Yamen Global · Version 1.0 · Avril 2026
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## QU'EST-CE QU'UN PLUGIN CLAUDE CODE ?

Claude Code supporte des plugins — des extensions installées une
fois qui ajoutent des skills (compétences), des agents, des hooks
et des commandes slash. Une fois installés, ils s'activent
automatiquement selon le contexte, sans avoir à les invoquer
manuellement à chaque session.

Les plugins YOR s'installent dans Claude Code via le terminal.
Ils persistent entre les projets sauf indication contraire.

---

## TABLEAU RÉCAPITULATIF

| Plugin | Type | Phase YOR | Priorité |
|--------|------|-----------|----------|
| Frontend Design | Officiel Anthropic | Phase 4 (Lovable → Claude Code) | ⭐ Essentiel |
| Code Review | Officiel Anthropic | Phase 7 (avant deploy) | ⭐ Essentiel |
| Security Guidance | Officiel Anthropic | Avant livraison finale | ✅ Utile |
| claude-mem | Community | Maintenance mensuelle | ✅ Utile |
| Superpowers | Community | Si workflow délégué | 🔵 Optionnel |
| gstack | Community | Si workflow avancé | 🔵 Optionnel |

---

## PLUGIN 01 — FRONTEND DESIGN

**Source :** Officiel Anthropic
**URL :** claude.com/plugins/frontend-design
**Installs :** 413 000+

### Ce que ça fait
Oriente Claude Code vers des interfaces distinctives et
production-grade. Évite l'esthétique IA générique (fonts
système, gradients violets prévisibles, composants cookie-cutter).

Avant de générer du code frontend, il établit une direction
esthétique — brutalist, luxury, playful, etc. — puis code
en cohérence avec cette direction.

### Utilité YOR
Phase 7 — quand Claude Code optimise le SEO (meta tags,
JSON-LD, .webp), il doit lire le DESIGN.md du projet et
ne pas altérer le travail de Lovable. Ce plugin renforce
cette cohérence et guide Claude vers du code visuellement
soigné si on lui demande d'ajouter un composant.

Utile aussi pour la maintenance mensuelle quand on ajoute
une nouvelle page ou section.

### Installation
```bash
# Dans Claude Code (terminal)
/plugin install frontend-design@claude-plugins-official
```

### Commande de vérification
```bash
/help
# Chercher "frontend-design" dans la liste des plugins actifs
```

### Utilisation dans YOR
Activer en début de session de maintenance ou d'ajout de page :
```
I need to add a new page to this project.
Read DESIGN.md first, then use the frontend-design skill
to ensure the new page matches the existing design system.
```

---

## PLUGIN 02 — CODE REVIEW

**Source :** Officiel Anthropic
**URL :** claude.com/plugins/code-review
**Installs :** 129 000+

### Ce que ça fait
Revue de code automatisée avec 5 agents spécialisés en parallèle :
- Vérification conformité CLAUDE.md
- Détection de bugs
- Analyse du contexte git (historique)
- Revue des commentaires PR précédents
- Vérification des commentaires dans le code

Chaque finding est scoré de 0 à 100. Seuls les problèmes
à 80+ sont remontés, réduisant les faux positifs.

### Utilité YOR
Phase 7 — avant chaque git push vers Vercel, vérifier que
les 7 optimisations SEO (sitemap, robots, meta, webp, polices,
JSON-LD, build) n'ont pas introduit de régression dans le code.

Commande à lancer sur la branche de travail avant de pousser :
```
/code-review
```

### Installation
```bash
/plugin install code-review@claude-plugins-official
```

### Utilisation dans YOR
```bash
# Après les 7 étapes d'optimisation SEO, avant le git push :
/code-review
# Claude analyse les changements et signale les problèmes > 80/100
# Corriger les critiques avant de pousser
git push
```

---

## PLUGIN 03 — SECURITY GUIDANCE

**Source :** Officiel Anthropic
**URL :** claude.com/plugins/security-guidance
**Installs :** 41 000+

### Ce que ça fait
Hook de sécurité automatique. Intercepte les opérations
Write, Edit et MultiEdit et scanne le code pour 8 catégories
de vulnérabilités avant d'appliquer les changements :
- Command injection (GitHub Actions, child_process.exec)
- eval() et new Function()
- XSS (dangerouslySetInnerHTML, innerHTML)
- Python pickle désérialisation
- os.system() injection

Fonctionne en arrière-plan — aucune commande à taper.
Un warning s'affiche si un pattern dangereux est détecté.

### Utilité YOR
Avant livraison finale : le repo GitHub est livré au client.
Il ne doit contenir aucune clé API exposée, aucun pattern
XSS dans les formulaires de contact, aucune dépendance
vulnérable injectée par erreur.

Ce plugin tourne en continu pendant la Phase 7 et bloque
les patterns dangereux avant qu'ils n'atteignent le repo.

### Installation
```bash
/plugin install security-guidance@claude-plugins-official
```

### Note YOR
S'installe une fois globalement. Actif sur tous les projets.
Pas de commande spécifique — il fonctionne automatiquement.

---

## PLUGIN 04 — CLAUDE-MEM

**Source :** Community (thedotmack)
**URL :** github.com/thedotmack/claude-mem
**Stars :** 48 000+

### Ce que ça fait
Mémoire persistante entre les sessions Claude Code.
Capture automatiquement tout ce que Claude fait pendant
une session (observations), compresse avec IA, et injecte
le contexte pertinent dans les sessions futures.

Ce que ça mémorise : décisions prises, bugs corrigés,
préférences projet, patterns de code, commandes utilisées.

Stockage : SQLite local (~/.claude-mem/claude-mem.db)
Interface web : http://localhost:37777 (visualisation)

### Utilité YOR
Maintenance mensuelle — quand on revient sur un projet
client 30 jours plus tard pour ajouter une page ou corriger
un bug, Claude-mem se souvient du contexte : stack, décisions
de design, mots-clés SEO ciblés, seuils PageSpeed atteints.

Sans ce plugin : réécrire le contexte à chaque session.
Avec : Claude Code reprend là où il s'était arrêté.

Utile aussi si on délègue des projets à un collaborateur
— les mémoires peuvent être synchronisées entre machines.

### Installation
```bash
# Méthode recommandée via marketplace Claude Code
/plugin marketplace add thedotmack/claude-mem
/plugin install claude-mem

# Alternative via npm
npx claude-mem install

# Redémarrer Claude Code après installation
# Premier démarrage : ~30s de setup (unique)
```

### Prérequis
- Node.js 18.0.0+
- Claude Code version récente

### Commandes utiles
```bash
# Rechercher dans la mémoire (dans Claude Code)
# "Qu'avons-nous fait sur le projet Renaud Voss ?"
# Claude-mem cherche automatiquement les observations passées

# Vérifier le worker
# http://localhost:37777 (interface web)
```

### Utilisation dans YOR
```
# En début de session de maintenance :
"What do you remember about this project?
Check your memory for previous work on [NOM CLIENT]."

# Claude-mem injecte automatiquement le contexte pertinent
```

---

## PLUGIN 05 — SUPERPOWERS

**Source :** Community (obra / Jesse Vincent)
**URL :** github.com/obra/superpowers
**Stars :** 136 000+

### Ce que ça fait
Framework de workflow structuré pour Claude Code.
Impose une méthode en 7 phases : brainstorm → plan →
implémentation TDD → code review → finishing.

Skills inclus :
- `brainstorming` — Socratic design refinement avant de coder
- `writing-plans` — Plan d'implémentation structuré
- `subagent-driven-development` — Tâches parallèles
- `test-driven-development` — RED-GREEN-REFACTOR strict
- `systematic-debugging` — Diagnostic méthodique
- `using-git-worktrees` — Features isolées en branches
- `requesting-code-review` — Review automatique entre tâches

### Utilité YOR
Optionnel pour le workflow solo. Devient utile si :
- On délègue le workflow YOR à un collaborateur
- On veut forcer une méthode reproductible sur tous les projets
- On travaille sur des projets plus complexes que des sites vitrines

Pour un site vitrine standard YOR (10 jours), Superpowers
est trop lourd. Le gain est visible sur des projets > 5 pages
avec du code custom ou des intégrations.

### Installation
```bash
# Méthode officielle Claude Code
/plugin install superpowers@claude-plugins-official

# Alternative via marketplace Superpowers
/plugin marketplace add obra/superpowers-marketplace
/plugin install superpowers@superpowers-marketplace

# Redémarrer Claude Code
```

### Commandes principales
```bash
/superpowers:brainstorm   # Brainstorming avant de coder
/superpowers:write-plan   # Écrire le plan d'implémentation
/superpowers:execute-plan # Exécuter le plan par sous-agents
/code-reviewer            # Review du travail accompli
```

### Utilisation dans YOR (si activé)
```
# Début de Phase 7 avec Superpowers :
/superpowers:write-plan
"Optimize this React/Vite site for SEO:
1. Generate sitemap.xml
2. Create robots.txt
3. Add meta tags
4. Convert images to .webp
5. Host fonts locally
6. Add JSON-LD LocalBusiness
7. Verify build passes"

# Puis exécution par sous-agents parallèles
/superpowers:execute-plan
```

---

## PLUGIN 06 — GSTACK

**Source :** Community (Garry Tan, YC)
**URL :** github.com/garrytan/gstack
**Description :** Setup Claude Code de Garry Tan (Y Combinator)

### Ce que ça fait
23 skills organisés en rôles de "virtual software team" :
CEO, Designer, Eng Manager, Release Manager, Doc Engineer, QA.

Skills les plus pertinents pour YOR :
- `/design-consultation` — construit un design system et écrit DESIGN.md
- `/design-review` — audit visuel 80 points du site live avec scores
- `/design-shotgun` — génère 3 variantes de hero section à comparer
- `/ship` — pipeline complet lint → review → deploy en une commande
- `/qa` — tests QA sur le site déployé
- `/retro` — retrospective hebdomadaire avec metrics
- `/land-and-deploy` — deploy configuré une fois, réutilisé

### Utilité YOR
`/design-review` est particulièrement intéressant : il audite
le site en production et remonte les problèmes de design avec
un score et des fixes suggérés. Utile après livraison pour
affiner la qualité visuelle.

`/design-consultation` peut générer un DESIGN.md automatiquement
à partir de zéro (alternative à l'approche manuelle du Dossier 4).

`/ship` automatise le pipeline git push → Vercel. Utile pour
la maintenance mensuelle où on fait beaucoup de petits commits.

### Installation
```bash
# Installation globale (recommandée)
git clone --depth 1 https://github.com/garrytan/gstack.git \
  ~/.claude/skills/gstack \
  && cd ~/.claude/skills/gstack \
  && ./setup

# Mise à jour
/gstack-upgrade
```

### Prérequis
- Bun (runtime JavaScript — installé automatiquement si absent)
- Claude Code avec accès terminal

### Commandes YOR pertinentes
```bash
/design-consultation  # Créer DESIGN.md depuis zéro
/design-review        # Auditer le site en production
/design-shotgun       # Générer 3 variantes hero à comparer
/ship                 # Commit + review + push en une commande
/qa                   # Tests QA sur le site déployé
```

### Note importante
gstack est conçu pour des workflows de développement plus larges.
Pour YOR, utiliser uniquement les 5 commandes listées ci-dessus.
Ne pas activer les features browser automation (Chromium)
sauf si nécessaire — elles consomment des ressources.

---

## ORDRE D'INSTALLATION RECOMMANDÉ POUR YOR

```bash
# 1. Plugins essentiels (installer en premier)
/plugin install frontend-design@claude-plugins-official
/plugin install code-review@claude-plugins-official
/plugin install security-guidance@claude-plugins-official

# 2. Mémoire persistante (installer ensuite)
/plugin marketplace add thedotmack/claude-mem
/plugin install claude-mem
# Redémarrer Claude Code

# 3. Optionnels (selon les besoins)
# Superpowers (si workflow délégué)
/plugin install superpowers@claude-plugins-official

# gstack (si audit design ou automation avancée)
git clone --depth 1 https://github.com/garrytan/gstack.git \
  ~/.claude/skills/gstack && cd ~/.claude/skills/gstack && ./setup
```

---

## UTILISATION PAR PHASE YOR

### Phase 4 — Génération site (Lovable)
→ Pas de plugin Claude Code — phase dans Lovable

### Phase 7 — Optimisation SEO (Claude Code)
```
1. Lancer Claude Code dans le repo
2. "Read DESIGN.md before making any changes"
3. Exécuter le prompt SEO des 7 étapes (Dossier YOR_reference)
4. Plugin Security Guidance actif en arrière-plan (auto)
5. /code-review avant chaque git push
```

### Phase 9 — Déploiement Vercel
```
# Avec gstack (optionnel) :
/ship  # Automatise le pipeline complet
```

### Maintenance mensuelle
```
1. Ouvrir Claude Code dans le repo client
2. "What do you remember about this project?" (claude-mem)
3. "Read DESIGN.md before making any changes"
4. Exécuter la modification demandée
5. /code-review
6. git push
```

---

## VÉRIFICATION DE L'INSTALLATION

```bash
# Dans Claude Code, lister les plugins actifs :
/plugin

# Vérifier que ces plugins apparaissent :
# ✅ frontend-design
# ✅ code-review
# ✅ security-guidance
# ✅ claude-mem (si installé)

# Tester claude-mem :
# Demander à Claude Code : "What do you remember about recent work?"
# Si claude-mem est actif, il cherche dans sa base de données
```

---

## NOTES DE VERSION

v1.0 — Avril 2026
- 6 plugins documentés avec installation et usage YOR
- Plugins 1, 2, 3 officiels Anthropic — stables
- claude-mem : 48k stars, très actif (v12+ en avril 2026)
- Superpowers : 136k stars, le plus populaire du marché
- gstack : outil de Garry Tan (YC), très complet

## À FAIRE (prochaines versions)
- [ ] Tester claude-mem sur un projet maintenance réel et noter
      ce que la mémoire retient / ne retient pas
- [ ] Tester /design-review gstack sur photo-pros.vercel.app
      et documenter le score et les findings
- [ ] Vérifier si claude-mem est compatible avec le DESIGN.md
      (est-ce qu'il mémorise les design tokens ?)
- [ ] Créer un CLAUDE.md YOR standard à placer dans chaque repo
      client (résume les règles YOR pour Claude Code)
