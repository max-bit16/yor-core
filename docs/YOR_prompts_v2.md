# YOR — Référence Prompts & Templates · v2.0
# Yamen Global · Avril 2026
# Mise à jour : scroll-triggered animations + conversion-first design

---

## PHILOSOPHIE v2

Un site YOR fait deux choses : il classe sur Google (SEO 100/100) et
il convertit les visiteurs en leads (appels, formulaires, messages).
La v1 optimisait le premier. La v2 optimise les deux simultanément.

**Principe d'animation** : Intersection Observer natif uniquement.
Zéro librairie externe. Zéro impact PageSpeed. Les éléments entrent
dans le viewport → ils s'animent. C'est tout.

**Principe de conversion** : CTA à chaque point de décision, pas
seulement en bas de page. Preuve sociale avant le formulaire.
Numéro de téléphone toujours visible sur mobile.

---

## PROMPT LOVABLE — Template YOR v2

```
Crée un site vitrine professionnel pour [NOM], [SECTEUR] basé(e)
à [VILLE]. Cible : [CIBLE].

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STACK & CONTRAINTES ABSOLUES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Stack : React + Vite + Tailwind CSS + Lucide-React
Polices : Playfair Display (titres) + DM Sans (corps)
Hébergement cible : Vercel
Icônes : Lucide-React UNIQUEMENT — pas de SVG custom, pas d'emoji
Images : balises <img> avec src réel (Unsplash/Pexels URL), dimensions
         fixes (width + height explicites), alt descriptif, loading="lazy"
         AUCUNE image IA générée, AUCUN placeholder coloré

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PALETTE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Fond : #0D0D0D
Fond cards : #1A1A1A
Accent : #6B3FA0
Accent hover : #7B4FB0
Texte : #F5F0EB
Texte secondaire : #888888
Bordures : #2A2A2A

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ANIMATIONS — RÈGLES D'IMPLÉMENTATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Utilise UNIQUEMENT l'Intersection Observer API natif du navigateur.
Aucune librairie externe (pas de Framer Motion, pas d'AOS, pas de GSAP).

Crée un hook custom useInView :

  const useInView = (threshold = 0.15) => {
    const ref = useRef(null);
    const [inView, setInView] = useState(false);
    useEffect(() => {
      const obs = new IntersectionObserver(([entry]) => {
        if (entry.isIntersecting) { setInView(true); obs.disconnect(); }
      }, { threshold });
      if (ref.current) obs.observe(ref.current);
      return () => obs.disconnect();
    }, [threshold]);
    return [ref, inView];
  };

Pattern d'animation Tailwind pour chaque élément animé :
  className={`transition-all duration-700 ease-out
    ${inView ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'}`}

Stagger sur les grilles (bento, cartes, logos) :
  style={{ transitionDelay: `${index * 120}ms` }}

Parallax hero (facultatif, un seul élément) :
  Utilise un useEffect avec window.addEventListener('scroll') qui modifie
  transform: translateY() sur l'élément de fond uniquement.
  Jamais sur top/margin/padding (déclenche un reflow).

Compteurs animés sur les chiffres clés :
  Quand la section entre dans le viewport, les chiffres s'incrémentent
  de 0 à leur valeur finale en 1.5s avec easeOut.

Scroll progress bar :
  Ligne fine (2px) en haut de page, couleur #6B3FA0.
  Largeur = (window.scrollY / (document.body.scrollHeight - window.innerHeight)) * 100%
  Mise à jour dans un requestAnimationFrame.

Toutes les transitions : duration-600 à duration-800, jamais plus long.
will-change: transform, opacity sur les éléments animés.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STRUCTURE DU SITE — CONVERSION-FIRST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Le site est conçu pour générer des leads, pas seulement informer.
Chaque section a un rôle dans le tunnel de conversion.

— HEADER STICKY (z-index: 50)
  Logo gauche + téléphone cliquable (tel:[TÉLÉPHONE]) + bouton CTA droit
  Fond transparent au scroll 0 → fond #0D0D0D/95 avec backdrop-blur-sm
  après 80px de scroll. Sur mobile : toujours fond sombre.

— SECTION 1 : HERO PLEIN ÉCRAN
  H1 unique Playfair 96px italic : "[SECTEUR] à [VILLE] — [NOM]"
  Sous-titre DM Sans 20px : proposition de valeur en 1 ligne
  Ligne de réassurance : [CHIFFRE] clients · [DÉLAI] de livraison · [GARANTIE]
  → ces 3 éléments animent en stagger au chargement
  Deux boutons côte à côte :
    Principal : "Demander un devis gratuit" → ancre vers #contact
    Secondaire (outline) : "Voir nos réalisations" → ancre vers #services
  Image ou visuel fort en arrière-plan (parallax léger, overlay gradient)
  Scroll indicator (ChevronDown Lucide, animation bounce CSS)

— SECTION 2 : SERVICES (Bento Grid)
  Titre H2 Playfair centré
  Sous-label DM Sans uppercase : "CE QUE NOUS FAISONS"
  Grille asymétrique 6 blocs — cartes #1A1A1A, bordure #2A2A2A
  Chaque carte : icône Lucide #6B3FA0 + titre H3 + description 2 lignes
  Hover : border-color #6B3FA0, légère élévation (shadow)
  Animation : stagger Intersection Observer, délai 120ms entre cartes
  CTA en bas de section : "[NOM], c'est [USP en 6 mots]" + bouton outline

— SECTION 3 : PREUVES SOCIALES
  Sous-section A — Chiffres clés (3 stats géantes)
    Chiffres Playfair Display 5rem, animés avec compteur
    Labels DM Sans uppercase 0.75rem #888888
    Exemples : "127 clients accompagnés" · "4,9/5 de satisfaction" · "48h de livraison"
  Sous-section B — Témoignages (2 à 3 citations)
    Citation Playfair italic 1.1rem
    Nom + titre DM Sans 0.85rem #888888
    Étoiles Lucide Star remplies en #6B3FA0
  Animation : fade-in + translate en entrée viewport

— SECTION 4 : CTA INTERMÉDIAIRE
  Section courte (~200px), fond #6B3FA0
  Headline Playfair 2.5rem italic : "[Phrase déclencheur d'action]"
  Exemples : "Prêt à dépasser vos concurrents ?" · "Votre prochain client vous cherche."
  Bouton blanc centré : "Obtenir un devis en 24h"
  Cette section brise le scroll et force une décision.

— SECTION 5 : PROCESSUS (optionnel pour Standard)
  3 ou 4 étapes numérotées, icônes Lucide
  Animation : apparition séquentielle gauche → droite

— SECTION 6 : FAQ ACCORDÉON
  4 à 6 questions, icône ChevronDown Lucide
  Questions centrées sur les objections d'achat (prix, délai, garanties)
  Animation : fade-in section entière

— SECTION 7 : CONTACT (ancre #contact)
  Headline : "Parlons de votre projet" — pas "Contact"
  Sous-titre : "[DÉLAI DE RÉPONSE] · Devis gratuit · Sans engagement"
  Aucun formulaire. Uniquement des liens directs :

  Grille de cartes de contact (2 colonnes sur desktop, 1 sur mobile) :
    Carte 1 — Téléphone
      Icône Phone Lucide + label "Appelez directement"
      Lien <a href="tel:[TÉLÉPHONE]">[TÉLÉPHONE FORMATÉ]</a>
      Hover : fond #6B3FA0, texte blanc
    Carte 2 — Email
      Icône Mail Lucide + label "Écrivez-nous"
      Lien <a href="mailto:[EMAIL]">[EMAIL]</a>
      Hover : fond #6B3FA0, texte blanc
    Carte 3 — Adresse (si pertinent)
      Icône MapPin Lucide + label "Retrouvez-nous"
      Lien <a href="https://maps.google.com/?q=[ADRESSE ENCODÉE]"
             target="_blank" rel="noopener">[ADRESSE]</a>
      Hover : fond #6B3FA0, texte blanc
    Carte 4 — Réseau principal (Instagram ou LinkedIn selon secteur)
      Icône Instagram ou Linkedin Lucide + label "Suivez notre travail"
      Lien <a href="[URL RÉSEAU]" target="_blank" rel="noopener">@[HANDLE]</a>
      Hover : fond #6B3FA0, texte blanc

  Si le client a plusieurs réseaux, les afficher en ligne d'icônes
  sous les cartes (Instagram, LinkedIn, Facebook selon pertinence).
  Icônes Lucide, taille w-5 h-5, couleur #888888 → #F5F0EB au hover.

— STICKY MOBILE CTA (position: fixed, bottom: 0, z-index: 40)
  Visible uniquement sur mobile (md:hidden)
  Deux boutons pleine largeur côte à côte :
    Gauche : icône Phone + "Appeler" → lien tel:[TÉLÉPHONE]
    Droite : icône Mail + "Écrire" → lien mailto:[EMAIL]
  Fond #0D0D0D, bordure top 1px #2A2A2A

— FOOTER
  Logo + description courte + liens navigation + mentions légales
  Ligne SEO : "[SECTEUR] à [VILLE] | [NOM] — [ACCROCHE 1 LIGNE]"

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STRUCTURE HTML SÉMANTIQUE SEO
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

- H1 unique sur la page : "[SECTEUR] à [VILLE] — [NOM]"
- H2 par section principale
- H3 pour les titres de cartes services
- aria-label sur chaque icône Lucide
- alt descriptif sur chaque image (pas d'alt vide)
- Balises OpenGraph dans le head (og:title, og:description, og:type, og:url)
- Meta description dans le head : "[META]" (≤ 155 caractères)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CONTENU CLIENT — À REMPLIR
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Services : [SERVICES]
Différenciation (USP) : [USP]
Chiffres clés : [STATS — ex: 127 clients · 4,9/5 · 48h]
Témoignages : [CITATIONS avec nom et contexte]
FAQ : [QUESTIONS + RÉPONSES]
Téléphone : [TÉLÉPHONE]
Email : [EMAIL]
Adresse : [ADRESSE]
Meta description : "[META]"

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PERFORMANCE & RÈGLES FINALES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

- Bundle JS cible : < 200kb gzippé
- Aucun appel réseau externe en production (polices en local)
- Images : width + height explicites pour éviter le CLS
- Pas de layout shift sur les animations (transform uniquement, jamais layout)
- Mobile-first strict
- npm run build doit passer à zéro erreur
```

---

## PROMPT CLAUDE CODE SEO + ANIMATIONS (v2)

```
Voici mon repo exporté depuis Lovable. Lis d'abord DESIGN.md si présent.
Analyse toute la structure du projet. Puis exécute dans cet ordre :

SEO TECHNIQUE (priorité absolue — ne jamais sauter ces étapes)
1. Génère /public/sitemap.xml dynamique avec toutes les pages
2. Crée /public/robots.txt (User-agent: * / Allow: /)
3. Optimise toutes les balises meta (title unique, description ≤ 155 chars,
   OpenGraph : og:title, og:description, og:type, og:url, og:image)
4. Convertis toutes les images en format .webp — préserve les dimensions
   originales, ajoute loading="lazy" et width/height explicites sur chaque <img>
5. Télécharge les polices Google Fonts (Playfair Display, DM Sans) et
   héberge-les en local dans /src/assets/fonts/ — supprime tout appel
   Google Fonts externe
6. Ajoute un JSON-LD Schema de type LocalBusiness dans le head
7. Vérifie que npm run build passe sans erreur ni warning

OPTIMISATION CONVERSION (si non déjà présents dans le code Lovable)
8. Vérifie que tous les liens de contact sont corrects :
   - Téléphone : <a href="tel:[NUMÉRO]"> (pas de texte brut)
   - Email : <a href="mailto:[EMAIL]"> (pas de texte brut)
   - Adresse : lien Google Maps en target="_blank" rel="noopener"
   - Réseaux sociaux : target="_blank" rel="noopener" sur chaque lien
9. Vérifie que le sticky mobile (position fixed, bottom-0) existe
   avec liens tel: et mailto: — sinon crée-le
10. Vérifie que le hook useInView utilise IntersectionObserver natif
    (pas de librairie externe) — sinon implémente-le

RÈGLES ABSOLUES
- Ne touche pas au design Tailwind ni aux composants UI existants
  sans me demander explicitement
- Ne modifie pas les couleurs, typographies ou espacements définis dans DESIGN.md
- Montre-moi un résumé de chaque modification effectuée
- Si une étape échoue, explique pourquoi avant de continuer
```

---

## DESIGN.md — SECTION ANIMATIONS (à ajouter dans chaque DESIGN.md)

Coller cette section dans le DESIGN.md de chaque projet, après la section Composants :

```markdown
## Animations & Interactions

### Principe
Intersection Observer natif uniquement.
Zéro librairie externe (ni Framer Motion, ni AOS, ni GSAP).
Impact PageSpeed : nul.

### Hook useInView
Fichier : /src/hooks/useInView.ts
Seuil : 0.15 (l'élément est à 15% visible avant de déclencher)
Once : true (l'animation ne se rejoue pas au re-scroll)

### Classes d'animation Tailwind
Entrée standard :
  opacity-0 translate-y-8 → opacity-100 translate-y-0
  transition-all duration-700 ease-out

Entrée latérale gauche :
  opacity-0 -translate-x-8 → opacity-100 translate-x-0
  transition-all duration-700 ease-out

Entrée latérale droite :
  opacity-0 translate-x-8 → opacity-100 translate-x-0
  transition-all duration-700 ease-out

Zoom léger (cards) :
  opacity-0 scale-95 → opacity-100 scale-100
  transition-all duration-500 ease-out

### Stagger
Grilles et listes : transitionDelay = index * 120ms
Maximum 6 éléments en stagger (au-delà, grouper)

### Parallax
1 seul élément parallax par page (hero background)
Amplitude : 0.3 (scroll px * 0.3 = translateY px)
Jamais sur un élément de texte — uniquement sur fond

### Compteurs
Éléments ciblés : chiffres clés dans la section Stats
Durée : 1500ms, easing easeOutQuart
Déclenchement : Intersection Observer sur la section parent

### Scroll progress bar
Position : fixed top-0 left-0, height 2px, z-index 60
Couleur : [ACCENT PRINCIPAL]
Implémentation : requestAnimationFrame, width en %

### Règles absolues animations
- Jamais will-change sur plus de 5 éléments simultanément
- Jamais d'animation sur une propriété de layout (width, height, top, margin)
- Uniquement transform et opacity (GPU-composited)
- Durée min 400ms, max 900ms
- Sur mobile : réduire amplitude de translate de 50%
  (translate-y-8 → translate-y-4, translate-x-8 → translate-x-4)
```

---

## SECTION CONVERSION — À AJOUTER DANS LE BRIEF CLIENT

Questions supplémentaires à poser au client pour alimenter les éléments
de conversion du site :

```
CHIFFRES CLÉS (pour section Stats)
→ Combien de clients avez-vous accompagnés ?
→ Depuis quelle année exercez-vous ?
→ Quel est votre délai de livraison/intervention habituel ?
→ Avez-vous une note Google (4.8/5, 127 avis) ?

TÉMOIGNAGES (pour section Preuves sociales)
→ 2 à 3 citations de clients avec prénom, nom, contexte
→ Si pas de témoignages écrits : peut-on reformuler un email reçu ?

DÉCLENCHEUR D'URGENCE
→ Quelle est votre promesse principale en 1 phrase ?
  Exemples : "Devis en 24h", "Intervention sous 48h", "Résultat garanti"
→ Quelle objection revient le plus souvent chez vos prospects ?
  (→ alimente la FAQ et le CTA intermédiaire)

CONTACT DIRECT
→ Téléphone professionnel (pour lien tel: + sticky mobile)
→ Email professionnel (pour lien mailto:)
→ Adresse physique si pertinente (pour lien Google Maps)
→ Réseaux sociaux actifs : Instagram, LinkedIn, Facebook (URL complètes)
→ Délai de réponse habituel (ex: "sous 2h", "le jour même")
```

---

## CHECKLIST LIVRAISON YOR v2

### SEO Technique
- [ ] H1 unique présent, contient mot-clé + ville
- [ ] Meta description ≤ 155 caractères
- [ ] OpenGraph : og:title, og:description, og:type, og:url, og:image
- [ ] /public/sitemap.xml accessible en ligne
- [ ] /public/robots.txt accessible en ligne
- [ ] JSON-LD LocalBusiness dans le head
- [ ] Images en .webp, lazy loading, width + height explicites, alt non vide
- [ ] Polices hébergées en local (zéro appel Google Fonts)
- [ ] npm run build : 0 erreur, 0 warning
- [ ] Score SEO Lighthouse : 100/100
- [ ] Score Performance bureau : 90+
- [ ] Score Performance mobile : 90+
- [ ] HTTPS actif (cadenas vert)
- [ ] Search Console : propriété vérifiée
- [ ] Sitemap soumis dans Search Console
- [ ] Demande d'indexation envoyée

### Conversion
- [ ] Header sticky avec téléphone cliquable (lien tel:)
- [ ] CTA dans le hero avec texte spécifique ("Devis gratuit en 24h")
- [ ] Section Stats avec chiffres réels du client
- [ ] 2+ témoignages clients avec nom et contexte
- [ ] CTA intermédiaire (section #6B3FA0 courte, bouton blanc)
- [ ] FAQ avec questions orientées objections d'achat
- [ ] Section contact : zéro formulaire, uniquement liens directs
- [ ] Lien tel: fonctionnel (testé sur mobile)
- [ ] Lien mailto: fonctionnel
- [ ] Lien Google Maps en target="_blank" + rel="noopener"
- [ ] Liens réseaux sociaux en target="_blank" + rel="noopener"
- [ ] Sticky mobile (Phone + Mail) visible sur mobile
- [ ] Numéro de téléphone en lien tel: sur toute la page
- [ ] Aucun CLS (Cumulative Layout Shift) sur les animations

### Animations
- [ ] useInView hook implémenté avec IntersectionObserver natif
- [ ] Scroll progress bar active
- [ ] Bento grid : stagger 120ms entre cartes
- [ ] Section Stats : compteurs animés au scroll
- [ ] Aucune librairie d'animation externe dans le bundle
- [ ] will-change uniquement sur les éléments en cours d'animation

---

## PROMPT CORRECTION PAGESPEED (inchangé)

```
Voici le rapport PageSpeed Insights de notre site :
[COLLER LE RAPPORT]

Règle chaque point en rouge ou orange dans l'ordre de priorité.
Ne touche pas au design Tailwind ni aux composants existants.
Après chaque correction, explique ce que tu as modifié.
```

---

## PROMPT INJECTION BALISE SEARCH CONSOLE (inchangé)

```
Injecte cette balise dans le <head> de index.html juste après
la balise charset, sans toucher à autre chose. Puis git push :

[COLLER LA BALISE GOOGLE]
```

---

## PROMPT AJOUT PAGE/ARTICLE (maintenance)

```
Dans le repo, crée une nouvelle page "[TITRE]" avec le même
style et la même structure que les pages existantes.
Lis DESIGN.md avant de commencer.

Contenu : [INFOS]
Mots-clés cibles : [MOTS-CLÉS]
Meta description : [META]

La page doit inclure :
- Les mêmes animations useInView que les autres pages
- Un CTA vers la page contact
- La mise à jour du sitemap.xml

Ne touche pas aux autres composants. Git push quand c'est prêt.
```

---

## TARIFS DE RÉFÉRENCE (inchangé)

| Offre | Tarif |
|---|---|
| One-Shot Starter (3–4 pages) | 800–1 200€ |
| One-Shot Standard (5+ pages + contenu) | 1 500–2 500€ |
| Maintenance + hébergement | 29–99€/mois |
| SEO contenu (2 pages/mois) | 200–500€/mois |
| Ticket modification ponctuelle | 50€ |

---

## CONTACTS & RESSOURCES

- Email Max : levysoulamax@yamen-global.com
- Email client Photo Pro : levysoulamax@gmail.com
- Repo Photo Pro : github.com/max-bit16/photo-pros
- Site Photo Pro : https://photo-pros.vercel.app
- PageSpeed : pagespeed.web.dev
- Search Console : search.google.com/search-console
- Vercel : vercel.com
- Netlify Drop : netlify.com/drop

---

## CHANGELOG

v2.1 — Avril 2026
- Section contact : suppression du formulaire, remplacement par grille de
  liens directs (tel:, mailto:, Google Maps, réseaux sociaux)
- Sticky mobile : mailto: remplace l'ancre #contact
- Brief client : section "Contact direct" mise à jour
- Checklist : items formulaire remplacés par vérification liens directs

v2.0 — Avril 2026
- Prompt Lovable : ajout couche animations (Intersection Observer, stagger,
  parallax, compteurs, scroll progress bar)
- Prompt Lovable : refonte structure conversion-first (header sticky, CTA
  intermédiaire, sticky mobile, réassurance avant formulaire)
- Prompt Claude Code : étapes 8-10 ajoutées (vérification conversion)
- DESIGN.md : section "Animations & Interactions" ajoutée pour tous les skins
- Brief client : section "Conversion" ajoutée (chiffres, témoignages, urgence)
- Checklist : section "Conversion" et "Animations" ajoutées

v1.0 — Mars 2026
- Version initiale
