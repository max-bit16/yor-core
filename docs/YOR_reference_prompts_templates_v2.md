# YOR — Référence Prompts & Templates (v2)

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

## Prompt Lovable — Template élégance YOR (v2)

> Mise à jour : ajout de la règle de cohérence inter-sections
> et précision des specs par section pour éviter les outputs génériques.

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

COHÉRENCE INTER-SECTIONS (règle absolue) :
Chaque section doit hériter des mêmes tokens visuels :
— Mêmes couleurs (fond, accent, texte) sans exception
— Même border-radius sur tous les blocs et boutons
— Même taille de police pour les titres H2 et les labels
— Même style de bouton (outline ou filled) dans tout le site
— Même espacement vertical entre les blocs (gap identique)
— Pas de section avec une police, une couleur ou un radius
   différent des autres — l'œil doit percevoir un seul système.

Sections :
1. Hero plein écran
   — Titre Playfair Display 96px italic
   — Sous-titre DM Sans 18px, opacité 70%
   — 3 stats géantes en Playfair Display (ex : "48h", "100%", "12 ans")
   — 1 bouton CTA accent #6B3FA0
   — Aucune image, aucun placeholder

2. Bento Grid services
   — 6 blocs asymétriques (2 grands + 4 petits)
   — 1 icône Lucide-React par bloc avec aria-label
   — Titre H2 par bloc + 1 phrase descriptive
   — Fond #0D0D0D avec bordure subtile #F5F0EB/10

3. Section confiance
   — Secteurs ou types de clients en ligne horizontale
   — Icônes Lucide uniquement, pas de logos
   — Texte court centré DM Sans

4. FAQ accordéon
   — 4 questions avec ChevronDown Lucide
   — Animation d'ouverture fluide
   — Même border-radius que les blocs bento

5. Contact
   — Formulaire 3 champs (Nom, Email, Message)
   — Infos de contact (adresse, téléphone, email)
   — Bouton CTA cohérent avec le Hero

Services : [SERVICES]
Différence : [USP]
FAQ : [FAQ]
Meta description : "[META]"
OpenGraph dans le head.
Mobile-first. Pas d'animations lourdes.
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
