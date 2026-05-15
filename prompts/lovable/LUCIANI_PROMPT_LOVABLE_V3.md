ÉTUDE LUCIANI — PROMPT LOVABLE V3
Cabinet d'Avocats · Dudelange, Grand-Duché de Luxembourg
Landing page · Design System ElevenLabs
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Crée une landing page vitrine pour l'ÉTUDE LUCIANI,
cabinet d'avocats fondé en 2014 à Dudelange, Luxembourg.
Avocat : Maître Tom Luciani, Barreau de Luxembourg depuis 2007.
Cible : particuliers et entreprises au Grand-Duché,
clientèle francophone, germanophone et anglophone.


━━ 1. STACK ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

React + Vite + TypeScript + Tailwind CSS + Lucide-React.
AUCUNE librairie externe : pas de Framer Motion, GSAP, AOS.
Toutes les animations → Intersection Observer natif + CSS.
AUCUN composant shadcn/ui. Tailwind custom uniquement.
Déclarer lang="fr" dans index.html.


━━ 2. POLICES ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Google Fonts dans index.css :
  Cormorant Garamond : weight 300 uniquement
  Inter : weights 400, 500

HIÉRARCHIE TYPOGRAPHIQUE (d'après design system ElevenLabs) :

  H1 Display Hero :
    Cormorant 300 · 48px desktop / 36px mobile
    line-height 1.08 · letter-spacing -0.96px

  H2 Section Heading :
    Cormorant 300 · 36px desktop / 28px mobile
    line-height 1.17

  H3 Card Heading :
    Cormorant 300 · 32px
    line-height 1.13

  Sous-titre éditorial :
    Cormorant 300 · 22px · italic

  Body Large (intro, chapeaux) :
    Inter 400 · 20px · line-height 1.35

  Body Standard :
    Inter 400 · 18px · line-height 1.50 · letter-spacing 0.18px

  Body UI :
    Inter 400 · 16px · line-height 1.50 · letter-spacing 0.16px

  Nav / UI :
    Inter 500 · 15px · letter-spacing 0.15px

  Boutons :
    Inter 500 · 15px

  Caption / Métadonnées :
    Inter 400 · 14px · letter-spacing 0.14px

  Labels uppercase :
    Inter 500 · 12px · text-transform uppercase · letter-spacing 0.18em

  Small (tags, badges) :
    Inter 500 · 13px


━━ 3. PALETTE & TOKENS ━━━━━━━━━━━━━━━━━━━━━━━━━

Respecter scrupuleusement ces valeurs — ne pas substituer.

COULEURS :
  Blanc pur       : #ffffff  → hero, cards, boutons
  Gris clair      : #f5f5f5  → sections alternées
  Warm Stone      : #f5f2ef  → surfaces warm, tint de fond
  Noir            : #000000  → texte principal, headings, CTA noir
  Gris foncé      : #4e4e4e  → texte secondaire, descriptions
  Warm Gray       : #777169  → texte tertiaire, muted, icônes
  Bordure         : #e5e5e5  → bordures explicites
  Bordure subtile : rgba(0, 0, 0, 0.05)

SYSTÈME D'OMBRES — RÈGLE CRITIQUE :
  Chaque shadow de card inclut OBLIGATOIREMENT une composante
  inset (demi-pixel). Ce sont les bords à peine visibles qui
  donnent aux surfaces leur qualité physique.

  --shadow-inset-edge :
    rgba(0,0,0,0.075) 0px 0px 0px 0.5px inset

  --shadow-outline-ring (Level 1 — cards standard) :
    rgba(0,0,0,0.075) 0px 0px 0px 0.5px inset,
    rgba(0,0,0,0.06) 0px 0px 0px 1px,
    rgba(0,0,0,0.04) 0px 1px 2px,
    rgba(0,0,0,0.04) 0px 2px 4px

  --shadow-card (Level 2 — cards proéminentes, boutons) :
    rgba(0,0,0,0.4) 0px 0px 1px,
    rgba(0,0,0,0.04) 0px 4px 4px

  --shadow-card-hover :
    rgba(0,0,0,0.4) 0px 0px 1px,
    rgba(0,0,0,0.06) 0px 4px 12px

  --shadow-warm (bouton warm stone, CTAs featured) :
    rgba(78, 50, 23, 0.04) 0px 6px 16px

TOKENS LAYOUT :
  Container : max-w-6xl mx-auto px-6 md:px-12
  Section   : py-28 md:py-36
  Card gap  : gap-6
  Card radius : 16px–20px (jamais < 16px)


━━ 4. COMPOSANTS DE BASE ━━━━━━━━━━━━━━━━━━━━━━━

Définition unique. Ne pas créer de variantes non listées.

─── BOUTON PILL NOIR (CTA primaire) ───────────────
  bg: #000000 · color: #ffffff
  padding: 12px 20px · radius: 9999px
  font: Inter 500 15px
  box-shadow: --shadow-card
  transition: opacity 200ms ease, transform 150ms ease
  hover: opacity 0.82 · scale(1.02)

─── BOUTON PILL WARM STONE (CTA secondaire / featured) ─
  bg: rgba(245, 242, 239, 0.8) · color: #000000
  padding: 12px 20px 12px 14px  ← ASYMÉTRIQUE (plus à droite)
  radius: 30px                   ← PAS 9999px — règle ElevenLabs
  font: Inter 500 15px
  border: 1px solid rgba(0,0,0,0.05)
  box-shadow: --shadow-warm
  transition: background-color 200ms ease,
              box-shadow 200ms ease, transform 150ms ease
  hover: background #ede9e5 · scale(1.02)

─── BOUTON PILL COMPACT NOIR (nav) ────────────────
  Identique PILL NOIR · padding: 8px 16px

─── BOUTON PILL BLANC (CTA sur fond coloré) ───────
  bg: #ffffff · color: #000000
  radius: 9999px
  box-shadow: rgba(0,0,0,0.4) 0px 0px 1px,
              rgba(0,0,0,0.04) 0px 4px 4px
  font: Inter 500 15px

─── LABEL PILL (badge non-cliquable) ──────────────
  bg: rgba(245, 242, 239, 0.8)
  color: #4e4e4e
  padding: 6px 14px · radius: 9999px
  font: Inter 500 12px uppercase letter-spacing 0.18em
  border: 1px solid rgba(0,0,0,0.05)
  box-shadow: --shadow-warm

─── CARD SERVICE ───────────────────────────────────
  bg: #ffffff
  border: 1px solid #e5e5e5
  box-shadow: --shadow-outline-ring
  radius: 20px · padding: 32px
  transition: transform 250ms ease, box-shadow 250ms ease
  hover: translateY(-4px) scale(1.01)
         box-shadow: --shadow-card-hover

─── CARD INFO (contact — sans hover transform) ─────
  bg: #ffffff
  border: 1px solid #e5e5e5
  box-shadow: --shadow-outline-ring
  radius: 20px · padding: 32px


━━ 5. SYSTÈME D'ANIMATIONS ━━━━━━━━━━━━━━━━━━━━━

PRINCIPE : subtil, rapide, cohérent sur toute la page.
GPU-composited uniquement (transform + opacity).

━━ 5A. HOOK useReveal (src/hooks/useReveal.ts) ━━━

  import { useEffect, useRef } from 'react'

  export function useReveal() {
    const ref = useRef<HTMLElement>(null)
    useEffect(() => {
      const el = ref.current
      if (!el) return
      const obs = new IntersectionObserver(
        ([entry]) => {
          if (entry.isIntersecting) {
            el.classList.add('visible')
            obs.unobserve(el)
          }
        },
        { threshold: 0.12, rootMargin: '0px 0px -40px 0px' }
      )
      obs.observe(el)
      return () => obs.disconnect()
    }, [])
    return ref
  }

━━ 5B. CLASSES CSS (dans index.css) ━━━━━━━━━━━━━

.reveal {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 600ms cubic-bezier(0.16,1,0.3,1),
              transform 600ms cubic-bezier(0.16,1,0.3,1);
  transition-delay: var(--delay, 0ms);
}
.reveal-left {
  opacity: 0;
  transform: translateX(-24px);
  transition: opacity 600ms cubic-bezier(0.16,1,0.3,1),
              transform 600ms cubic-bezier(0.16,1,0.3,1);
}
.reveal-right {
  opacity: 0;
  transform: translateX(24px);
  transition: opacity 600ms cubic-bezier(0.16,1,0.3,1),
              transform 600ms cubic-bezier(0.16,1,0.3,1);
}
.reveal.visible,
.reveal-left.visible,
.reveal-right.visible {
  opacity: 1;
  transform: translate(0, 0);
}

━━ 5C. STAGGER CARTES DOMAINES ━━━━━━━━━━━━━━━━━

4 cards avec className="reveal" et delays :
  card 1 : style={{ '--delay': '0ms' }}
  card 2 : style={{ '--delay': '120ms' }}
  card 3 : style={{ '--delay': '240ms' }}
  card 4 : style={{ '--delay': '360ms' }}

━━ 5D. HOOK useCounter (src/hooks/useCounter.ts) ━

  Prend (target: number, duration = 1400)
  Déclenché par IntersectionObserver (même pattern useReveal)
  Utilise requestAnimationFrame + easing linéaire
  Retourne la valeur courante à afficher

  Valeurs : 17 → "17+" · 2007 → "2007" · 4 → "4" · 4 → "4"

━━ 5E. HOVER NAV — UNDERLINE GLISSANT ━━━━━━━━━━

Liens nav — pseudo-élément ::after :
  content: '' · display: block · height: 1px
  background: #000000
  transform: scaleX(0) · transform-origin: left
  transition: transform 200ms ease
  hover: transform: scaleX(1)

━━ 5F. HOVER ICÔNES DANS CARDS ━━━━━━━━━━━━━━━━

Icônes Lucide dans .service-card :
  color: #777169
  transition: transform 200ms ease, color 200ms ease
  .service-card:hover → scale(1.15) · color: #000000

━━ 5G. TRANSITION LIENS TEXTE ━━━━━━━━━━━━━━━━━

Liens non-bouton :
  color: #4e4e4e · transition: color 150ms ease
  hover: color: #000000


━━ 6. NAVIGATION ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

position: fixed top-0 z-50 · w-full
bg: #ffffff opacity 90% · backdrop-blur-md
border-bottom: 1px solid rgba(0,0,0,0.05)
height: 64px (h-16)

Intérieur container standard :
  flex items-center justify-between

  GAUCHE — Logo :
    Cormorant 300 · 20px · #000
    "Étude Luciani" → ancre #hero

  CENTRE — 3 liens (masqués mobile, visibles à 1024px) :
    Inter 500 · 15px · letter-spacing 0.15px
    color: #4e4e4e → hover #000 (150ms)
    underline hover glissant (5E)
    "Domaines" → #domaines
    "Tom Luciani" → #profil
    "Contact" → #contact

  DROITE — BOUTON PILL COMPACT NOIR :
    "Prendre rendez-vous" → tel:+35220331456

  MOBILE — hamburger à 1024px (icône Menu Lucide)
    Drawer latéral · bg: #ffffff · fermeture au tap


━━ 7. SECTION HERO ━━━━━━━━━━━━━━━━━━━━━━━━━━━━

id="hero" · bg: #ffffff (blanc pur)
min-h-screen · relative · overflow-hidden

IMAGE (Philharmonie Luxembourg) :
  https://source.unsplash.com/vBKCJbjH8cs/1920x1080
  position: absolute · inset-0 · object-cover · object-right
  Overlay : bg-gradient-to-r
    from-white/98 via-white/75 to-white/5
  → Texte sur fond blanc à gauche, image visible à droite

CONTENU — col gauche · flex flex-col gap-8
  justify-center · min-h-screen · pl-6 md:pl-16 · max-w-xl

  ① LABEL PILL className="reveal" :
       "Barreau de Luxembourg · Depuis 2007"

  ② H1 className="reveal" :
       "Défendre vos intérêts
        au Grand-Duché"
       Cormorant 300 · 48px/36px · lh 1.08 · ls -0.96px

  ③ Chapeau Body Large className="reveal" :
       Inter 400 · 20px · #4e4e4e · lh 1.35
       "Cabinet d'avocats à Dudelange, au cœur du Grand-Duché
       de Luxembourg. Droit civil, pénal, commercial et
       administratif. Consultations en luxembourgeois,
       français, allemand ou anglais."

  ④ BADGES LANGUES className="reveal" :
       flex gap-2 flex-wrap
       4 pills · bg: rgba(245,242,239,0.8)
       border: 1px solid rgba(0,0,0,0.05)
       Inter 500 · 13px · rounded-[9999px] · px-3 py-1
       box-shadow: --shadow-warm
       "🇱🇺 LU" · "🇫🇷 FR" · "🇩🇪 DE" · "🇬🇧 EN"

  ⑤ CTAs flex gap-3 flex-wrap className="reveal" :
       BOUTON PILL NOIR : "Prendre rendez-vous"
         → tel:+35220331456
       BOUTON PILL WARM STONE : "Nos domaines"
         → ancre #domaines

  ⑥ Ligne infos className="reveal" :
       Inter 400 · 14px · #777169 · letter-spacing 0.14px
       "40, rue du Commerce · L-3450 Dudelange
        Tél. 20 33 14 56 · Lun–Ven 9h–19h"


━━ 8. SECTION CHIFFRES CLÉS ━━━━━━━━━━━━━━━━━━━

bg: #f5f5f5 · py-20 md:py-24 · container standard

grid-cols-2 md:grid-cols-4 · gap-8
Séparateurs verticaux desktop :
  1px solid rgba(0,0,0,0.06) entre colonnes

Chaque stat — useCounter — text-center :
  Chiffre :
    Cormorant 300 · 56px · lh 1.0 · #000
  Label :
    Inter 500 · 12px · uppercase · ls 0.18em · #777169

  "17+" · "Années au barreau"
  "2007" · "Inscription au barreau"
  "4" · "Domaines d'expertise"
  "4" · "Langues de consultation"


━━ 9. SECTION DOMAINES D'EXPERTISE ━━━━━━━━━━━━

id="domaines" · bg: #ffffff · py-28 md:py-36
container standard

EN-TÊTE className="reveal" · text-center · mb-16 :
  LABEL PILL : "Nos domaines"
  H2 : "Une expertise complète
        pour chaque situation"
  Body Large · max-w-xl · mx-auto · #4e4e4e :
    "Que vous soyez particulier ou professionnel,
    le Cabinet Luciani vous accompagne avec rigueur
    et humanité dans toutes vos démarches juridiques."

GRILLE 4 CARDS SERVICES (stagger 5C) :
grid-cols-1 sm:grid-cols-2 lg:grid-cols-4

Chaque CARD SERVICE :
  Icône Lucide w-6 h-6 #777169 mb-5 (hover via 5F)
  H3 Cormorant 300 32px #000 lh 1.13
  Sous-titre Body UI #4e4e4e lh 1.5 mt-2
  Liste 3 points · Inter 400 14px #777169 · "—" + texte · mt-4

  CARD 1 — Scale · "Droit Civil"
    Sous-titre : "Famille, successions, bail à loyer,
                  droit du travail, responsabilité civile."
    — Divorce, garde d'enfants, successions
    — Licenciement, rédaction de contrats de travail
    — Litiges locatifs, procédures d'expulsion

  CARD 2 — Shield · "Droit Pénal"
    Sous-titre : "Défense pénale, droit routier,
                  procédure et exécution des peines."
    — Ivresse au volant, restitution de permis
    — Défense en cas d'atteintes aux personnes
    — Plaintes pénales, demandes de mise en liberté

  CARD 3 — Briefcase · "Droit Commercial"
    Sous-titre : "Constitution de sociétés, contentieux
                  commercial, gestion des faillites."
    — Constitution de sociétés, baux commerciaux
    — Recouvrement de créances
    — Défense devant le Tribunal de commerce

  CARD 4 — Building2 · "Administratif & Immigration"
    Sous-titre : "Recours administratifs, urbanisme,
                  droit des étrangers et immigration."
    — Contestation de décisions administratives
    — Autorisations communales et urbanisme
    — Dossiers d'immigration, statut de réfugié


━━ 10. SECTION TOM LUCIANI ━━━━━━━━━━━━━━━━━━━━

id="profil" · bg: #f5f5f5 · py-28 md:py-36
container standard

Layout : grid-cols-1 md:grid-cols-2 gap-16 items-center

COL IMAGE — className="reveal-left" :
  rounded-[20px] overflow-hidden aspect-[4/3]
  box-shadow: --shadow-outline-ring
  https://source.unsplash.com/HJckKnwCXxQ/900x600
  object-cover

COL TEXTE — className="reveal" · flex flex-col gap-6 :
  LABEL PILL : "Votre avocat"

  H2 : "Maître Tom Luciani"

  Cormorant 300 22px italic #4e4e4e :
    "Avocat à la Cour · Barreau de Luxembourg"

  Body Standard #4e4e4e :
    "Né à Esch-sur-Alzette, Maître Luciani est inscrit
    au Barreau de Luxembourg depuis le 24 mai 2007. Après
    une première expérience au sein de l'Étude Wies &
    Majerus, il rejoint l'Étude Majerus à Esch-sur-Alzette
    en 2009, où il acquiert une expertise solide
    en contentieux."

  Body Standard #4e4e4e :
    "En novembre 2014, il fonde son cabinet à Dudelange —
    quatrième ville du Grand-Duché — à distance optimale
    des juridictions de Luxembourg et du Tribunal
    d'Esch-sur-Alzette. Titulaire d'une maîtrise en Droit
    Privé et Études Européennes, Université Robert
    Schumann de Strasbourg."

  BADGES LANGUES — flex wrap gap-2 :
    Pills · bg: #ffffff · border: 1px solid #e5e5e5
    box-shadow: rgba(0,0,0,0.04) 0px 2px 4px
    Inter 500 13px #4e4e4e · rounded-[9999px] · px-4 py-1.5
    "🇱🇺 Luxembourgeois" · "🇫🇷 Français"
    "🇩🇪 Allemand" · "🇬🇧 Anglais"

  Caption #777169 letter-spacing 0.14px :
    "— Maîtrise Droit Privé & Études Européennes,
       Université Robert Schumann, Strasbourg"


━━ 11. SECTION APPROCHE ━━━━━━━━━━━━━━━━━━━━━━━

bg: #ffffff · py-28 md:py-36 · container standard

Layout : grid-cols-1 md:grid-cols-2 gap-16 items-center

COL TEXTE — className="reveal" · flex flex-col gap-6 :
  LABEL PILL : "Notre approche"
  H2 : "Rigueur et humanité,
        à chaque étape"

  3 BLOCS · flex flex-col gap-10 · mt-4 :
    Chaque bloc : flex gap-4 items-start
    Icône Lucide w-5 h-5 #777169 flex-shrink-0 mt-1

    CheckCircle · H3 Cormorant 300 32px : "Écoute et précision"
    Body Standard #4e4e4e :
      "Chaque dossier est traité avec une attention
      personnelle. Nous commençons par écouter, comprendre,
      puis construire la meilleure stratégie pour vos intérêts."

    Globe · H3 : "Accessibilité multilingue"
    Body Standard #4e4e4e :
      "Consultations en luxembourgeois, français, allemand
      ou anglais. Le Cabinet est pensé pour accueillir
      toute la diversité du Grand-Duché."

    MapPin · H3 : "Proximité avec les juridictions"
    Body Standard #4e4e4e :
      "Situé à Dudelange, le Cabinet opère en collaboration
      avec l'Étude Majerus. À distance optimale des
      tribunaux de Luxembourg et d'Esch-sur-Alzette."

COL IMAGE — className="reveal-right" :
  rounded-[20px] overflow-hidden aspect-[3/4]
  box-shadow: --shadow-outline-ring
  https://source.unsplash.com/DZpc4UY8ZtY/800x1000
  object-cover
  overlay subtil : bg-gradient-to-t from-black/10 to-transparent


━━ 12. SECTION CONTACT ━━━━━━━━━━━━━━━━━━━━━━━━

id="contact" · bg: #f5f5f5 · py-28 md:py-36
container standard · position relative · overflow-hidden

IMAGE DÉCORATIVE :
  https://source.unsplash.com/DqHa4YO9mjc/1200x800
  position: absolute · right: 0 · top: 0 · bottom: 0
  width: 40% · object-cover · opacity: 0.07
  pointer-events: none · user-select: none

CONTENU max-w-4xl mx-auto · position relative z-10 :

  EN-TÊTE className="reveal" · text-center · mb-16 :
    LABEL PILL : "Contact"
    H2 : "Consultations sur rendez-vous"
    Body Large · max-w-lg · mx-auto · #4e4e4e :
      "Le Cabinet reçoit sur rendez-vous, du lundi au
      vendredi. Contactez-nous par téléphone pour
      convenir d'une consultation."

  GRILLE 3 CARDS INFO (stagger, --delay: 0/120/240ms) :
    grid-cols-1 md:grid-cols-3 gap-6

    CARD ADRESSE :
      MapPin · w-5 h-5 · #777169 · mb-4
      Label uppercase · "ADRESSE"
      Cormorant 300 · 26px · #000 · lh 1.5 :
        "40, rue du Commerce
         L-3450 Dudelange
         Grand-Duché de Luxembourg"
      Lien Inter 500 13px #000 underline mt-4
        transition color 150ms hover: #777169
        "Voir sur Google Maps"
        → target="_blank" rel="noopener noreferrer"

    CARD TÉLÉPHONE :
      Phone · w-5 h-5 · #777169 · mb-4
      Label uppercase · "TÉLÉPHONE"
      Cormorant 300 · 32px · #000 : "20 33 14 56"
      Caption #777169 mt-1 : "Permanence : 14h00 – 18h00"
      BOUTON PILL WARM STONE mt-6 :
        "Appeler maintenant" → tel:+35220331456

    CARD HORAIRES :
      Clock · w-5 h-5 · #777169 · mb-4
      Label uppercase · "HORAIRES"
      Cormorant 300 · 32px · #000 : "Lun – Ven"
      Caption #777169 mt-1 : "9h00 – 19h00"
      Caption #777169 mt-3 italic :
        "Uniquement sur rendez-vous"

  Note className="reveal" · text-center · mt-12 :
    Caption · #777169 · letter-spacing 0.14px :
    "Cabinet opérant en collaboration avec l'Étude Majerus,
    Esch-sur-Alzette · Fax : 26 52 10 34"


━━ 13. FOOTER ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

bg: #000000 · py-12 · px-6
border-top: 1px solid rgba(255,255,255,0.06)

max-w-6xl mx-auto · flex justify-between items-center
flex-wrap gap-8

  GAUCHE :
    Cormorant 300 · 20px · #ffffff : "Étude Luciani"
    Inter 400 · 13px · rgba(255,255,255,0.4) · mt-1 :
      "Cabinet d'avocats · Dudelange, Luxembourg"
      "Barreau de Luxembourg · Inscrit depuis le 24/05/2007"

  DROITE · text-right :
    Inter 400 · 13px · rgba(255,255,255,0.4) :
      "© 2026 Étude Luciani. Tous droits réservés."
      "40, rue du Commerce · L-3450 Dudelange"


━━ 14. RÈGLES ABSOLUES ━━━━━━━━━━━━━━━━━━━━━━━━

✗ Aucun formulaire — uniquement tel:, Google Maps
✗ Aucune image IA, aucun placeholder inventé
✗ Aucune librairie d'animation externe
✗ Aucun composant shadcn/ui
✗ Aucune couleur hors palette section 3
✗ Shadow inset (0.5px) OBLIGATOIRE sur chaque card
✗ border-radius cards jamais < 16px
✗ Warm Stone Pill radius = 30px, padding asymétrique

✓ lang="fr" dans <html>
✓ Un seul H1 sur la page
✓ GPU-composited uniquement : transform + opacity
✓ Toutes les images avec alt descriptif en français
✓ Liens externes : rel="noopener noreferrer"
✓ Hamburger mobile à 1024px
✓ Mobile-first · testé 375px et 1280px
✓ Hooks useReveal + useCounter dans src/hooks/
✓ Fond hero : #ffffff (blanc pur, PAS #f5f5f5)
✓ Boutons nav : Inter 500 15px (pas 14px)
✓ Chapeaux sections : Inter 400 20px (Body Large)
