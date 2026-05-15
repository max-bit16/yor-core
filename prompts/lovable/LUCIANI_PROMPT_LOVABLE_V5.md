ÉTUDE LUCIANI — PROMPT LOVABLE V5
Cabinet d'Avocats · Dudelange, Grand-Duché de Luxembourg
Landing page · Design System ElevenLabs · Animations Premium
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Crée une landing page vitrine pour l'ÉTUDE LUCIANI,
cabinet d'avocats fondé en 2014 à Dudelange, Luxembourg.
Avocat : Maître Tom Luciani, Barreau de Luxembourg depuis 2007.
Cible : particuliers et entreprises au Grand-Duché,
clientèle francophone, germanophone et anglophone.


━━ 1. STACK ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

React + Vite + TypeScript + Tailwind CSS + Lucide-React.
AUCUNE librairie externe : pas de Framer Motion, GSAP, AOS.
Animations → Intersection Observer natif + CSS + rAF.
AUCUN composant shadcn/ui. Tailwind custom uniquement.
html lang="fr" · css scroll-behavior: smooth


━━ 2. POLICES ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Google Fonts dans index.css :
  Cormorant Garamond : weight 300
  Inter : weights 400, 500

HIÉRARCHIE :
  H1 Display   : Cormorant 300 · 48px/36px · lh 1.08 · ls -0.96px
  H2 Section   : Cormorant 300 · 36px/28px · lh 1.17
  H3 Card      : Cormorant 300 · 32px · lh 1.13
  Sous-titre   : Cormorant 300 · 22px · italic
  Body Large   : Inter 400 · 20px · lh 1.35
  Body Standard: Inter 400 · 18px · lh 1.50 · ls 0.18px
  Body UI      : Inter 400 · 16px · lh 1.50 · ls 0.16px
  Nav / UI     : Inter 500 · 15px · ls 0.15px
  Boutons      : Inter 500 · 15px
  Caption      : Inter 400 · 14px · ls 0.14px
  Labels       : Inter 500 · 12px · uppercase · ls 0.18em
  Small        : Inter 500 · 13px

DÉCORATION TYPOGRAPHIQUE SECTIONS :
  Chiffres 01/02/03/04 : Cormorant 300 · 180px · lh 1.0 · ls -4px
  color: rgba(0,0,0,0.03) · position absolute · top -20px · right 0
  pointer-events: none · user-select: none · z-index: 0


━━ 3. PALETTE & TOKENS ━━━━━━━━━━━━━━━━━━━━━━━━━

COULEURS :
  Blanc pur       : #ffffff
  Gris clair      : #f5f5f5
  Warm Stone      : #f5f2ef
  Noir            : #000000
  Gris foncé      : #4e4e4e
  Warm Gray       : #777169
  Bordure         : #e5e5e5
  Bordure subtile : rgba(0,0,0,0.05)
  Stats bg        : #0a0a0a
  Marquee bg      : #f5f2ef
  Or avis         : #c9a84c   → étoiles Google

OMBRES — inset OBLIGATOIRE :

  --shadow-outline-ring :
    rgba(0,0,0,0.075) 0px 0px 0px 0.5px inset,
    rgba(0,0,0,0.06)  0px 0px 0px 1px,
    rgba(0,0,0,0.04)  0px 1px 2px,
    rgba(0,0,0,0.04)  0px 2px 4px

  --shadow-card :
    rgba(0,0,0,0.4)  0px 0px 1px,
    rgba(0,0,0,0.04) 0px 4px 4px

  --shadow-card-hover :
    rgba(0,0,0,0.4)  0px 0px 1px,
    rgba(0,0,0,0.06) 0px 4px 16px,
    rgba(78,50,23,0.05) 0px 8px 24px

  --shadow-warm :
    rgba(78,50,23,0.04) 0px 6px 16px

TOKENS LAYOUT :
  Container : max-w-6xl mx-auto px-6 md:px-12
  Section   : py-28 md:py-36
  Card gap  : gap-6 · Card radius : 20px


━━ 4. COMPOSANTS DE BASE ━━━━━━━━━━━━━━━━━━━━━━━

─── BOUTON PILL NOIR ───────────────────────────────
  bg: #000 · color: #fff · padding: 12px 20px
  radius: 9999px · font: Inter 500 15px
  box-shadow: --shadow-card
  transition: opacity 200ms ease, transform 150ms ease,
              box-shadow 200ms ease
  hover: opacity 0.82 · scale(1.02)
         box-shadow: --shadow-card-hover
  Effet magnétique : voir 5H

─── BOUTON PILL WARM STONE ────────────────────────
  bg: rgba(245,242,239,0.8) · color: #000
  padding: 12px 20px 12px 14px   ← asymétrique
  radius: 30px · font: Inter 500 15px
  border: 1px solid rgba(0,0,0,0.05)
  box-shadow: --shadow-warm
  transition: background-color 200ms ease,
              box-shadow 200ms ease, transform 150ms ease
  hover: bg #ede9e5 · scale(1.02)
         box-shadow: rgba(78,50,23,0.08) 0px 8px 24px
  Effet magnétique : voir 5H

─── LABEL PILL ────────────────────────────────────
  bg: rgba(245,242,239,0.8) · color: #4e4e4e
  padding: 6px 14px · radius: 9999px
  font: Inter 500 12px uppercase ls 0.18em
  border: 1px solid rgba(0,0,0,0.05)
  box-shadow: --shadow-warm

─── CARD SERVICE ───────────────────────────────────
  bg: #fff · border: 1px solid #e5e5e5
  box-shadow: --shadow-outline-ring
  radius: 20px · padding: 32px
  position relative · overflow hidden
  transition: transform 300ms ease, box-shadow 300ms ease
  Tilt 3D + icon circle + glow : voir 5E/5F/5G

─── CARD INFO ──────────────────────────────────────
  bg: #fff · border: 1px solid #e5e5e5
  box-shadow: --shadow-outline-ring
  radius: 20px · padding: 32px
  Warm glow cursor : voir 5N

─── CARD AVIS ──────────────────────────────────────
  bg: #fff · border: 1px solid #e5e5e5
  box-shadow: --shadow-outline-ring
  radius: 20px · padding: 40px
  Lift hover : translateY(-3px) · box-shadow --shadow-card-hover
  transition: transform 250ms ease, box-shadow 250ms ease


━━ 5. SYSTÈME D'ANIMATIONS ━━━━━━━━━━━━━━━━━━━━━

━━ 5A. BARRE DE PROGRESSION SCROLL ━━━━━━━━━━━━━━

ScrollProgress.tsx — fixed top-0 left-0 z-[100]
height: 2px · bg: #000 · transform-origin: left
Width calculée via rAF :
  progress = scrollY / (scrollHeight - innerHeight)
  el.style.transform = `scaleX(${progress})`
Pas de transition CSS — mise à jour directe via rAF.

━━ 5B. HOOK useReveal (src/hooks/useReveal.ts) ━━━

  export function useReveal(opts?: IntersectionObserverInit) {
    const ref = useRef<HTMLElement>(null)
    useEffect(() => {
      const el = ref.current; if (!el) return
      const obs = new IntersectionObserver(([e]) => {
        if (e.isIntersecting) { el.classList.add('visible'); obs.unobserve(el) }
      }, { threshold: 0.12, rootMargin: '0px 0px -40px 0px', ...opts })
      obs.observe(el)
      return () => obs.disconnect()
    }, [])
    return ref
  }

━━ 5C. CLASSES CSS — index.css ━━━━━━━━━━━━━━━━━

/* ── Fade + rise standard ── */
.reveal {
  opacity: 0;
  transform: translateY(28px);
  transition: opacity 700ms cubic-bezier(0.16,1,0.3,1),
              transform 700ms cubic-bezier(0.16,1,0.3,1);
  transition-delay: var(--delay, 0ms);
}
.reveal.visible { opacity: 1; transform: translateY(0); }

/* ── Slide gauche / droite ── */
.reveal-left  { opacity: 0; transform: translateX(-32px);
  transition: opacity 700ms cubic-bezier(0.16,1,0.3,1),
              transform 700ms cubic-bezier(0.16,1,0.3,1); }
.reveal-right { opacity: 0; transform: translateX(32px);
  transition: opacity 700ms cubic-bezier(0.16,1,0.3,1),
              transform 700ms cubic-bezier(0.16,1,0.3,1); }
.reveal-left.visible, .reveal-right.visible
  { opacity: 1; transform: translateX(0); }

/* ── Clip-path masque H2 ── */
.reveal-clip { overflow: hidden; }
.reveal-clip > span {
  display: block;
  transform: translateY(110%);
  transition: transform 900ms cubic-bezier(0.16,1,0.3,1);
  transition-delay: var(--delay, 0ms);
}
.reveal-clip.visible > span { transform: translateY(0); }

/* ── Séquence entrée hero ── */
.hero-item {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 700ms cubic-bezier(0.16,1,0.3,1),
              transform 700ms cubic-bezier(0.16,1,0.3,1);
}
.hero-item.entered { opacity: 1; transform: translateY(0); }

/* ── Split words H1 ── */
.word-reveal {
  display: inline-block;
  overflow: hidden;
  vertical-align: bottom;
}
.word-reveal > span {
  display: inline-block;
  transform: translateY(110%);
  transition: transform 800ms cubic-bezier(0.16,1,0.3,1);
}
.word-entered .word-reveal > span { transform: translateY(0); }

/* ── Line draw ── */
.line-draw {
  width: 0;
  height: 1px;
  background: #e5e5e5;
  transition: width 1000ms cubic-bezier(0.16,1,0.3,1);
  transition-delay: var(--delay, 200ms);
}
.line-draw.visible { width: 100%; }

/* ── Fade scale (chiffres, étoiles) ── */
.reveal-scale {
  opacity: 0;
  transform: scale(0.92);
  transition: opacity 600ms cubic-bezier(0.16,1,0.3,1),
              transform 600ms cubic-bezier(0.16,1,0.3,1);
  transition-delay: var(--delay, 0ms);
}
.reveal-scale.visible { opacity: 1; transform: scale(1); }

━━ 5D. SÉQUENCE HERO — ENTRÉE PAGE LOAD ━━━━━━━━

useEffect au mount. Ajoute la classe .entered avec delays :
  Badge pill      : 80ms
  H1 (mots)       : 200ms   ← déclenche aussi word-entered
  Chapeau         : 380ms
  Badges langues  : 500ms
  CTAs            : 610ms
  Ligne infos     : 710ms

━━ 5E. SPLIT-WORD REVEAL SUR H1 ━━━━━━━━━━━━━━━

Le H1 "Défendre vos intérêts au Grand-Duché" est découpé
mot par mot. Chaque mot est enveloppé dans .word-reveal > span.
Stagger de 60ms par mot via CSS var --delay.

Résultat : chaque mot monte depuis en-dessous de son masque,
l'un après l'autre — sensation cinématique vs bloc unique.

Exemple JSX :
  {["Défendre", "vos", "intérêts", "au", "Grand-Duché"]
    .map((w, i) => (
      <span className="word-reveal" style={{ '--delay': `${i*60}ms` }}>
        <span>{w}&nbsp;</span>
      </span>
  ))}

━━ 5F. TILT 3D CARDS SERVICES ━━━━━━━━━━━━━━━━━

onMouseMove sur .service-card :
  rect = card.getBoundingClientRect()
  x = (e.clientX - rect.left) / rect.width  - 0.5  → [-0.5, 0.5]
  y = (e.clientY - rect.top)  / rect.height - 0.5  → [-0.5, 0.5]
  transform: perspective(900px)
    rotateX(${-y * 7}deg) rotateY(${x * 7}deg)
    translateZ(6px) scale(1.01)

onMouseLeave :
  transition: transform 400ms cubic-bezier(0.16,1,0.3,1)
  transform: perspective(900px) rotateX(0) rotateY(0)
    translateZ(0) scale(1)

━━ 5G. CERCLE ICON AU HOVER CARDS ━━━━━━━━━━━━━

Derrière chaque icône Lucide dans .service-card :
  Un ::before pseudo-element :
    width: 44px · height: 44px · radius: 50%
    bg: rgba(245,242,239,0.8)
    position: absolute · top: 24px · left: 24px
    transform: scale(0)
    transition: transform 300ms cubic-bezier(0.16,1,0.3,1)
  .service-card:hover ::before → transform: scale(1)
  z-index: 0 · icône z-index: 1

━━ 5H. BOUTONS MAGNÉTIQUES ━━━━━━━━━━━━━━━━━━━━

Sur les deux CTAs hero et les boutons de contact :
onMouseMove :
  rect = btn.getBoundingClientRect()
  x = (e.clientX - rect.left - rect.width/2)  * 0.25
  y = (e.clientY - rect.top  - rect.height/2) * 0.25
  btn.style.transform = `translate(${x}px, ${y}px) scale(1.02)`
onMouseLeave :
  transition: transform 400ms cubic-bezier(0.16,1,0.3,1)
  btn.style.transform = 'translate(0,0) scale(1)'

Déplacement max : ≈ ±8px selon la taille du bouton.
Ne pas appliquer sur le bouton compact de la nav.

━━ 5I. PARALLAX + KEN BURNS IMAGE HERO ━━━━━━━

IMAGE wrapper : overflow hidden · position absolute · inset 0

IMG tag :
  @keyframes kenBurns {
    from { transform: scale(1.0); }
    to   { transform: scale(1.06); }
  }
  animation: kenBurns 14s ease-in-out alternate infinite

Parallax via rAF (séparé du Ken Burns) :
  parallaxEl.style.transform = `translateY(${scrollY * 0.15}px)`
  Clamp: max 80px

━━ 5J. HOOK useCounter ━━━━━━━━━━━━━━━━━━━━━━━━

  src/hooks/useCounter.ts
  duration: 1800ms · easing: t => 1 - Math.pow(2, -10 * t)
  Déclenché par IntersectionObserver (threshold 0.5)

  Au terme — pulse sur le chiffre :
    @keyframes pulse {
      0%  { transform: scale(1); }
      40% { transform: scale(1.08); }
      100%{ transform: scale(1); }
    }
    animation: pulse 350ms ease-in-out

  Valeurs : 17 → "17+" · 2007 → "2007" · 4 → "4" · 4 → "4"

━━ 5K. NAV SCROLL-AWARE + SCROLL-SPY ━━━━━━━━━━

SCROLL-AWARE (opacity/blur) :
  scrollY === 0 : bg transparent · no shadow
  scrollY > 40  : bg rgba(255,255,255,0.92) · backdrop-blur-md
                  border-bottom: 1px solid rgba(0,0,0,0.05)
                  box-shadow: rgba(0,0,0,0.04) 0px 4px 4px
  transition: background 300ms ease, box-shadow 300ms ease

SCROLL-SPY (lien actif) :
  IntersectionObserver sur #hero/#domaines/#profil/#contact
  threshold: [0.3]
  Le lien correspondant à la section visible reçoit
  l'état "actif" : underline scaleX(1) permanent (non hover)
  Transition : smooth comme le hover

━━ 5L. CLIP-PATH H2 + STAGGER SECTIONS ━━━━━━━

Tous les H2 via .reveal-clip > span (voir 5C).

Les 3 blocs de la section Approche entrent en stagger :
  bloc 1 : --delay 0ms
  bloc 2 : --delay 150ms
  bloc 3 : --delay 300ms
  Chacun avec className="reveal"

━━ 5M. LINE DRAW SÉPARATEURS ━━━━━━━━━━━━━━━━━

Entre chaque grande section, un séparateur :
  div.line-draw (voir 5C) · max-w-6xl mx-auto px-6
  Déclenché par IntersectionObserver threshold 0.5
  Se dessine de gauche à droite en 1000ms
  Couleur : #e5e5e5 · hauteur : 1px

━━ 5N. HOVER NAV UNDERLINE ━━━━━━━━━━━━━━━━━━━

Liens nav — ::after :
  content '' · display block · height 1px · bg #000
  transform: scaleX(0) · transform-origin: left
  transition: transform 220ms ease
  hover → scaleX(1)

━━ 5O. HOVER IMAGES SECTIONS ━━━━━━━━━━━━━━━━━

Sections Tom Luciani et Approche — le wrapper image :
  overflow: hidden · radius 20px
  img transition: transform 600ms ease
  hover (sur le wrapper) : img → scale(1.04)

━━ 5P. WARM GLOW CARDS INFO ━━━━━━━━━━━━━━━━━━

Cards ADRESSE, TÉLÉPHONE, HORAIRES :
  ::before pseudo-element via onMouseMove :
    background: radial-gradient(
      circle at var(--mx) var(--my),
      rgba(245,242,239,0.7) 0%,
      transparent 65%
    )
    position absolute · inset 0 · radius 20px
    opacity 0 → 1 (transition 300ms)
    pointer-events none

━━ 5Q. CARROUSEL AVIS CLIENTS ━━━━━━━━━━━━━━━━

src/components/TestimonialsCarousel.tsx

5 avis affichés un par un. Auto-advance toutes les 5s.
Pause sur hover de la zone carrousel.

TRANSITION ENTRE AVIS :
  Crossfade : opacity 0 → 1 sur 500ms ease
  translateX(12px) → translateX(0) sur entrée

IMPLÉMENTATION :
  useState(activeIndex) · useEffect pour l'interval
  clearInterval sur hover (onMouseEnter) · relance onMouseLeave
  Pas de slide physique — crossfade pur

DOT INDICATORS :
  5 dots · bg: #e5e5e5 → active: #000
  width: 20px → active: 32px (pill) · transition 300ms
  height: 4px · radius 9999px · cursor pointer
  Clic → navigation directe vers l'avis

ACCESSIBILITÉ :
  aria-live="polite" sur la zone de contenu
  Boutons dots avec aria-label="Avis N"


━━ 6. NAVIGATION ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

fixed top-0 z-50 · w-full · h-16
Scroll-aware + scroll-spy (5K)
Intérieur : container standard · flex items-center justify-between

  GAUCHE : Cormorant 300 20px #000 "Étude Luciani" → #hero
  CENTRE : 3 liens Inter 500 15px (>1024px)
    #domaines · #profil · #contact
    Underline hover (5N) · Underline actif scroll-spy (5K)
  DROITE : BOUTON PILL COMPACT NOIR → tel:+35220331456
  MOBILE : hamburger Menu Lucide · drawer bg #fff · 1024px


━━ 7. SECTION HERO ━━━━━━━━━━━━━━━━━━━━━━━━━━━━

id="hero" · bg: #ffffff · min-h-screen · relative · overflow-hidden

IMAGE + Ken Burns + parallax (5I) :
  https://source.unsplash.com/vBKCJbjH8cs/1920x1080
  Overlay: bg-gradient-to-r from-white/98 via-white/80 to-white/8

CONTENU col gauche · flex flex-col gap-8
  justify-center · min-h-screen · pl-6 md:pl-16 · max-w-xl

  Badge LABEL PILL .hero-item delay 80ms
  H1 split-word .hero-item delay 200ms (5E)
  Chapeau Body Large #4e4e4e .hero-item delay 380ms
  Badges langues flex gap-2 .hero-item delay 500ms
    "🇱🇺 LU" · "🇫🇷 FR" · "🇩🇪 DE" · "🇬🇧 EN"
    pills bg rgba(245,242,239,0.8) · box-shadow --shadow-warm
  CTAs flex gap-3 .hero-item delay 610ms (boutons magnétiques 5H)
    PILL NOIR "Prendre rendez-vous" → tel:+35220331456
    PILL WARM "Nos domaines" → #domaines
  Ligne infos Caption #777169 .hero-item delay 710ms
    "40, rue du Commerce · L-3450 Dudelange
     Tél. 20 33 14 56 · Lun–Ven 9h–19h"


━━ 8. STRIP MARQUEE ━━━━━━━━━━━━━━━━━━━━━━━━━━━

Après hero. bg: #f5f2ef · py-3 · overflow hidden
border-top/bottom: 1px solid rgba(0,0,0,0.06)

Texte : "Droit Civil · Droit Pénal · Droit Commercial ·
  Immigration · Luxembourg · Depuis 2007 ·
  Barreau de Luxembourg · Dudelange ·"
Inter 500 · 12px · uppercase · ls 0.2em · #777169
2 copies pour boucle · @keyframes marquee 30s linear infinite


━━ 9. SECTION CHIFFRES CLÉS ━━━━━━━━━━━━━━━━━━━

bg: #0a0a0a · py-24 md:py-28 · container standard
grid-cols-2 md:grid-cols-4

Chiffre useCounter .reveal-scale :
  Cormorant 300 · 64px · #fff · pulse final (5J)
Label : Inter 500 12px uppercase ls 0.18em rgba(255,255,255,0.4)
Séparateurs : 1px solid rgba(255,255,255,0.06)

  "17+" · "Années au barreau"
  "2007" · "Inscription au barreau"
  "4" · "Domaines d'expertise"
  "4" · "Langues de consultation"

DÉCORATION : "LUCIANI" position absolute centré
  Cormorant 300 · 200px · rgba(255,255,255,0.02) · ls -4px


━━ 10. SECTION DOMAINES D'EXPERTISE ━━━━━━━━━━━

id="domaines" · bg: #ffffff · py-28 md:py-36
container standard · position relative · overflow hidden
Numéro décoratif "01"

LINE DRAW separator en haut de section.

EN-TÊTE .reveal · text-center · mb-16 :
  LABEL PILL · H2 .reveal-clip · Body Large #4e4e4e

4 CARDS SERVICES — stagger 0/120/240/360ms
  Tilt 3D (5F) · Cercle icon (5G) · Icône hover (5L)

  CARD 1 — Scale · "Droit Civil"
  CARD 2 — Shield · "Droit Pénal"
  CARD 3 — Briefcase · "Droit Commercial"
  CARD 4 — Building2 · "Administratif & Immigration"

  Contenu : icône w-6 h-6 · H3 32px · sous-titre Body UI
  3 points 14px #777169 "—" + texte (voir section 10 V4)


━━ 11. SECTION TOM LUCIANI ━━━━━━━━━━━━━━━━━━━━

id="profil" · bg: #f5f5f5 · py-28 md:py-36
container standard · position relative
Numéro décoratif "02"

LINE DRAW separator en haut de section.

grid-cols-1 md:grid-cols-2 gap-16 items-center

COL IMAGE .reveal-left (hover zoom 5O) :
  https://source.unsplash.com/HJckKnwCXxQ/900x600
  rounded-[20px] · aspect-[4/3] · box-shadow --shadow-outline-ring

COL TEXTE .reveal :
  LABEL PILL · H2 .reveal-clip
  Sous-titre Cormorant 300 22px italic #4e4e4e
  2 paragraphes Body Standard #4e4e4e
  Badges langues pills bg-white
  Caption diplôme #777169


━━ 12. SECTION APPROCHE ━━━━━━━━━━━━━━━━━━━━━━━

bg: #ffffff · py-28 md:py-36
container standard · position relative
Numéro décoratif "03"

LINE DRAW separator en haut de section.

grid-cols-1 md:grid-cols-2 gap-16 items-center

COL TEXTE .reveal :
  LABEL PILL · H2 .reveal-clip
  3 BLOCS stagger reveal 0/150/300ms (5L)
  CheckCircle · Globe · MapPin + H3 + Body Standard

COL IMAGE .reveal-right (hover zoom 5O) :
  https://source.unsplash.com/DZpc4UY8ZtY/800x1000
  rounded-[20px] · aspect-[3/4] · box-shadow --shadow-outline-ring
  overlay bg-gradient-to-t from-black/10 to-transparent


━━ 13. SECTION AVIS CLIENTS ━━━━━━━━━━━━━━━━━━━

bg: #f5f5f5 · py-28 md:py-36
container standard · position relative

LINE DRAW separator en haut de section.

EN-TÊTE .reveal · text-center · mb-16 :
  LABEL PILL : "Avis clients"
  H2 .reveal-clip : "Ce que disent
                     nos clients"
  Body Large #4e4e4e max-w-lg mx-auto :
    "Des centaines de particuliers et professionnels font
    confiance au Cabinet Luciani au Grand-Duché."

CARROUSEL (TestimonialsCarousel.tsx — voir 5Q) :
  max-w-2xl mx-auto · position relative

  Chaque CARD AVIS (crossfade, 5Q) :
    padding: 40px · radius: 20px · bg: #fff
    box-shadow: --shadow-outline-ring

    GUILLEMET décoratif :
      Cormorant 300 · 96px · lh 0.8
      color: rgba(245,242,239,0.8) — warm stone très clair
      position absolute · top: 24px · left: 28px
      font-family: serif · content: '"' (unicode)
      pointer-events none

    ÉTOILES (5 étoiles) flex gap-1 mb-6 :
      ★ × 5 · color: #c9a84c · font-size: 16px

    TEXTE citation · position relative z-10 :
      Inter 400 · 18px · #4e4e4e · lh 1.65 · ls 0.18px
      font-style: italic

    AUTEUR · mt-6 flex items-center gap-3 :
      Initiale dans un cercle 36px :
        bg: rgba(245,242,239,0.8)
        Inter 500 · 14px · #777169
      Colonne :
        Nom : Cormorant 300 · 20px · #000
        Badge : Inter 500 · 11px · uppercase · ls 0.18em
                color: #777169
                "Local Guide · Google Maps"

  ─── 5 AVIS SÉLECTIONNÉS ───────────────────────

  AVIS 1 — Miguelito (Local Guide · 41 avis)
    "Je recommande Maître Luciani les yeux fermés.
    C'est un avocat extrêmement aimable, professionnel
    et humain."
    Initiale : "M"

  AVIS 2 — Michel Keser (Local Guide · 18 avis)
    "Maître Luciani est un must en matière de défense.
    Très à l'écoute et méticuleux dans ses approches.
    À recommander vivement pour toute personne devant
    se défendre devant la loi."
    Initiale : "M"

  AVIS 3 — Joelle Brink
    "La profession juridique a besoin de plus d'avocats
    comme vous — intelligents, passionnés, débrouillards,
    résilients et compatissants."
    Initiale : "J"

  AVIS 4 — manu hous (Local Guide · 27 avis)
    "Très professionnel, je recommande ce cabinet
    et Maître Luciani."
    Initiale : "M"

  AVIS 5 — Pedro Campos (Local Guide · 115 avis)
    "Un très bon cabinet d'avocats, je conseille."
    Initiale : "P"

  ─── DOT INDICATORS ────────────────────────────
    flex gap-2 justify-center mt-10
    dot inactif : w-5 h-1 bg #e5e5e5 radius 9999px
    dot actif   : w-8 h-1 bg #000 radius 9999px
    transition: width 300ms ease, background 300ms ease

  NOTE GOOGLE · mt-8 text-center :
    Caption #777169 · "Avis vérifiés sur Google Maps"


━━ 14. SECTION CONTACT ━━━━━━━━━━━━━━━━━━━━━━━━

id="contact" · bg: #ffffff · py-28 md:py-36
container standard · position relative · overflow-hidden
Numéro décoratif "04"

LINE DRAW separator en haut de section.

IMAGE DÉCORATIVE :
  https://source.unsplash.com/DqHa4YO9mjc/1200x800
  position absolute · right 0 · top 0 · bottom 0
  width 40% · object-cover · opacity 0.07 · pointer-events none

CONTENU max-w-4xl mx-auto · position relative z-10

  EN-TÊTE .reveal · text-center mb-16 :
    LABEL PILL "Contact"
    H2 .reveal-clip "Consultations sur rendez-vous"
    Body Large #4e4e4e max-w-lg mx-auto

  3 CARDS INFO stagger 0/120/240ms
    Warm glow cursor (5P) · bouton magnétique sur TÉLÉPHONE (5H)

    ADRESSE : MapPin · 40 rue du Commerce · Maps
    TÉLÉPHONE : Phone · 20 33 14 56 · 14h-18h
      PILL WARM STONE → tel:+35220331456 (magnétique)
    HORAIRES : Clock · Lun-Ven · 9h-19h

  Note .reveal mt-12 text-center Caption #777169 :
    "Cabinet opérant en collaboration avec l'Étude Majerus,
    Esch-sur-Alzette · Fax : 26 52 10 34"


━━ 15. FOOTER ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

bg: #000 · py-12 · border-top rgba(255,255,255,0.06)
container standard · flex justify-between flex-wrap gap-8

  GAUCHE : Cormorant 300 20px #fff "Étude Luciani"
    Inter 400 13px rgba(255,255,255,0.4) :
    "Cabinet d'avocats · Dudelange, Luxembourg"
    "Barreau de Luxembourg · Inscrit depuis le 24/05/2007"

  DROITE text-right : Inter 400 13px rgba(255,255,255,0.4)
    "© 2026 Étude Luciani. Tous droits réservés."
    "40, rue du Commerce · L-3450 Dudelange"


━━ 16. RÈGLES ABSOLUES ━━━━━━━━━━━━━━━━━━━━━━━━

✗ Aucun formulaire — uniquement tel:, Google Maps
✗ Aucune image IA, aucun placeholder inventé
✗ Aucune librairie animation externe
✗ Aucun composant shadcn/ui
✗ Aucune couleur hors palette section 3
✗ Shadow inset 0.5px sur chaque card (obligatoire)
✗ Card radius < 16px interdit
✗ Warm Stone radius = 30px, padding asymétrique

✓ lang="fr" · scroll-behavior smooth
✓ Un seul H1 · GPU-composited (transform + opacity only)
✓ Alt descriptif FR sur toutes les images
✓ rel="noopener noreferrer" liens externes
✓ Hamburger à 1024px
✓ Mobile-first · 375px + 1280px
✓ src/hooks/ : useReveal · useCounter
✓ src/components/ : ScrollProgress · TestimonialsCarousel
✓ Nav transparente → opaque au scroll
✓ Nav scroll-spy (section active)
✓ H1 split-word (mot par mot)
✓ H2 clip-path reveal partout
✓ Line draw entre chaque section
✓ Ken Burns + parallax composés (wrappers séparés)
✓ Tilt 3D ±7deg max
✓ Boutons magnétiques ±8px max (sauf nav)
✓ Warm glow cursor sur cards info
✓ Cercle icon au hover cards services
✓ Carrousel avis 5s auto-advance + pause hover
✓ Dots actifs pill → inactifs compact
