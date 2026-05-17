# YOR — DOSSIER 3 : PROMPTS PAR SECTEUR
# Yamen Global · Version 1.0 · Avril 2026
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## COMMENT UTILISER CE FICHIER

Chaque prompt est un site vitrine complet pour un secteur donné.
Il intègre les contraintes YOR (zéro image IA, Lucide, Tailwind,
SEO technique) et les spécificités métier (terminologie, sections
prioritaires, arguments de confiance propres au secteur).

Pour chaque client :
1. Choisir le prompt du secteur correspondant
2. Remplacer toutes les variables [entre crochets]
3. Vérifier que le skin recommandé correspond à l'ambiance voulue
   (sinon, substituer avec un skin du Dossier 1)
4. Coller dans Lovable

Ces prompts remplacent le prompt générique du Dossier 1 quand
on veut aller plus vite et plus juste sur un secteur connu.

---

## TABLEAU RÉCAPITULATIF

| Secteur | Skin recommandé | Skin alternatif | Cas client |
|---------|-----------------|-----------------|------------|
| 01 Avocat / Cabinet | PRESTIGE | EDITORIAL | Renaud Voss ✅ |
| 02 Photographe | DARK | BOLD | Photo Pro ✅ |
| 03 Consultant / Conseil | GLOBAL | EDITORIAL | Yamen Global ✅ |
| 04 Artisan | BOLD | GLOBAL | — |
| 05 Bien-être / Santé douce | SOFT | MINIMAL | — |
| 06 Médecin / Paramédical | SOFT | PRESTIGE | — |
| 07 Architecte / Design int. | EDITORIAL | PRESTIGE | — |
| 08 Restaurant / Traiteur | BOLD | DARK | — |
| 09 Agent immobilier | GLOBAL | PRESTIGE | — |
| 10 Studio créatif / Agence | DARK | BOLD | — |

---

## SECTEUR 01 — AVOCAT / CABINET JURIDIQUE

**Skin recommandé :** PRESTIGE
**Cas client :** Renaud Voss — prestige-legal.vercel.app
**Mots-clés types :** avocat droit des affaires Paris, cabinet
avocat [ville], avocat [spécialité] [ville]

**Sections prioritaires :**
Confiance > Spécialité > Équipe > Témoignages > Contact

```
Crée un site vitrine pour [NOM DU CABINET], cabinet d'avocats
spécialisé en [SPÉCIALITÉ] à [VILLE].
Cible : [dirigeants / PME / particuliers / startups].

STYLE : serif luxury, cream editorial, old-money, institutional,
understated elegance, dense layout, law firm.

CONTRAINTE ABSOLUE : aucune image IA, aucun placeholder.
Design basé sur typographie + icônes SVG Lucide uniquement.

Stack : React + Tailwind CSS + Lucide-React
Polices : Playfair Display (titres) + DM Sans (corps)

Palette :
— Fond : #F0EDE6
— Texte : #1C1C1C
— Accent : #2C4A3E
— Cards : #FAFAF7
— Bordures : #E0DBD3

H1 unique : "Avocat [SPÉCIALITÉ] à [VILLE] — [NOM CABINET]"

Sections dans l'ordre :
1. Hero sobre — Playfair 72px italic, fond crème, accroche
   institutionnelle (ex : "Le droit des affaires au service
   de votre croissance.")
2. Domaines d'intervention — grille 2x3, cards bordurées,
   icône Lucide (Scale, FileText, Briefcase, Shield, Building2),
   titre + 2 lignes de description par domaine
3. Philosophie / Approche — 2 colonnes, texte long Playfair
   italic en citation + corps DM Sans
4. L'équipe — [N] avocats présentés en cards horizontales,
   nom + titre + spécialité (pas de photo — initiales dans
   cercle couleur accent)
5. Témoignages clients — 3 cards, fond #FAFAF7, secteur en badge
6. Confiance — logos clients ou secteurs servis en ligne
7. Contact — formulaire 4 champs (nom, société, email, message)
   + adresse + numéro de téléphone

Domaines : [LISTE DES DOMAINES]
Avocats : [LISTE NOM + TITRE]
Adresse : [ADRESSE]
Téléphone : [TEL]
Témoignages : [TÉMOIGNAGES]
Meta description : "[META 155 chars]"
OpenGraph. Mobile-first. Pas d'animations lourdes.
```

---

## SECTEUR 02 — PHOTOGRAPHE COMMERCIAL

**Skin recommandé :** DARK
**Cas client :** Photo Pro — photo-pros.vercel.app
**Mots-clés types :** photographe [spécialité] Paris, shooting
produit Paris, photographie corporate [ville]

**Sections prioritaires :**
Portfolio (visuel) > Services > Processus > Tarifs > Contact

```
Crée un site vitrine pour [NOM], photographe [SPÉCIALITÉ]
basé(e) à [VILLE]. Cible : [marques / agences / e-commerce /
entreprises].

STYLE : cinematic, typographic dominance, deep contrast,
editorial dark, premium dark, moody, portfolio-forward.

CONTRAINTE ABSOLUE : aucune image IA, aucun placeholder.
Design basé sur typographie + icônes SVG Lucide uniquement.
Zones prévues pour photos réelles à uploader après livraison.

Stack : React + Tailwind CSS + Lucide-React
Polices : Playfair Display (titres) + DM Sans (corps)

Palette :
— Fond : #0D0D0D
— Accent : #6B3FA0
— Texte : #F5F0EB
— Cards : #1A1A1A

H1 unique : "Photographe [SPÉCIALITÉ] à [VILLE] — [NOM]"

Sections dans l'ordre :
1. Hero plein écran — Playfair 96px italic + 3 stats clés
   (ex : "+200 clients" / "48h livraison" / "10 ans exp.")
   fond noir, pas d'image en fond (placeholder neutre #1A1A1A)
2. Services — Bento Grid 6 blocs asymétriques, icône Lucide
   (Camera, Image, Zap, Package, Star, Clock), titre + description
3. Galerie placeholder — grille 3x2, blocs #1A1A1A avec label
   DM Sans centré "Photo [TITRE PROJET]" — zones pour vraies
   photos après livraison
4. Process — 4 étapes numérotées Playfair, icons Lucide
   (ex : Brief → Shooting → Retouche → Livraison)
5. Clients / Marques — noms en ligne, DM Sans uppercase, #444444
6. Tarifs — 3 formules en cards, fond #1A1A1A, bordure accent,
   prix Playfair grand, liste de prestations par formule
7. FAQ accordéon — 5 questions, ChevronDown Lucide
8. Contact — formulaire 4 champs + email + numéro

Services : [LISTE SERVICES]
Stats : [STAT1] / [STAT2] / [STAT3]
Process : [ÉTAPE1] / [ÉTAPE2] / [ÉTAPE3] / [ÉTAPE4]
Tarifs : [FORMULE1 + PRIX] / [FORMULE2 + PRIX] / [FORMULE3 + PRIX]
FAQ : [QUESTIONS/RÉPONSES]
Meta description : "[META 155 chars]"
OpenGraph. Mobile-first. Pas d'animations lourdes.
```

---

## SECTEUR 03 — CONSULTANT / CABINET DE CONSEIL

**Skin recommandé :** GLOBAL
**Cas client :** Yamen Global — yamen-global.com
**Mots-clés types :** consultant stratégie [ville], cabinet conseil
[spécialité] Paris, consultant [secteur] [ville]

**Sections prioritaires :**
Crédibilité > Offre > Process > Références > Contact

```
Crée un site vitrine pour [NOM], [TYPE DE CONSEIL]
basé(e) à [VILLE]. Cible : [dirigeants / PME / ETI / fonds].

STYLE : clean corporate, airy layout, confident spacing,
strategic, world-class, editorial white, international.

CONTRAINTE ABSOLUE : aucune image IA, aucun placeholder.
Design basé sur typographie + icônes SVG Lucide uniquement.

Stack : React + Tailwind CSS + Lucide-React
Polices : Playfair Display (titres) + DM Sans (corps)

Palette :
— Fond : #FAFAF8
— Texte : #111111
— Accent : #C8965A
— Sections alternées : #F2EFE9
— Bordures : #E5E0D8

H1 unique : "[TYPE CONSEIL] à [VILLE] — [NOM]"

Sections dans l'ordre :
1. Hero aéré — Playfair 80px, espace blanc, sous-titre court
   et percutant, CTA "Prendre contact"
2. Offres / Services — grid 2 colonnes, icônes Lucide
   (TrendingUp, Target, Map, BarChart2, Lightbulb, Globe),
   titre Playfair + description DM Sans
3. Chiffres clés — 3 stats géantes Playfair sur fond #F2EFE9
4. Process — 4 étapes numérotées Playfair, layout vertical,
   numéro très grand et léger (opacity-20)
5. Manifeste / Approche — texte seul, 2 paragraphes,
   quote Playfair italic
6. Secteurs clients — badges DM Sans uppercase, flex wrap
7. Contact — formulaire sobre + email direct

Offres : [LISTE OFFRES]
Stats : [STAT1] / [STAT2] / [STAT3]
Process : [ÉTAPE1] / [ÉTAPE2] / [ÉTAPE3] / [ÉTAPE4]
Secteurs clients : [LISTE SECTEURS]
Meta description : "[META 155 chars]"
OpenGraph. Mobile-first. Pas d'animations lourdes.
```

---

## SECTEUR 04 — ARTISAN

**Skin recommandé :** BOLD
**Mots-clés types :** [métier] [ville], artisan [spécialité] [ville],
[métier] pas cher [ville], devis [métier] [ville]

**Sections prioritaires :**
Réassurance > Services > Zone d'intervention > Avis > Contact

```
Crée un site vitrine pour [NOM], [MÉTIER ARTISAN]
à [VILLE]. Cible : [particuliers / entreprises / syndics].

STYLE : bold disruptive, high-impact, stark contrast,
raw typography, oversized headlines, trustworthy craftsman.

CONTRAINTE ABSOLUE : aucune image IA, aucun placeholder.
Design basé sur typographie + icônes SVG Lucide uniquement.

Stack : React + Tailwind CSS + Lucide-React
Polices : Playfair Display (titres) + DM Sans (corps)

Palette :
— Fond : #FFFFFF
— Texte : #0A0A0A
— Accent : [COULEUR MÉTIER — ex: #E63329 plombier /
  #F5A623 électricien / #2D6A4F menuisier]
— Sections alternées : #0A0A0A (fond noir)

H1 unique : "[MÉTIER] à [VILLE] — [NOM]"

Sections dans l'ordre :
1. Hero fullscreen fond noir — Playfair 100px bold blanc,
   accroche directe (ex : "Plombier à Paris. Disponible 24h/24."),
   CTA accent "Appeler maintenant" + numéro visible
2. Réassurance rapide — 4 badges flex, fond accent, texte blanc,
   DM Sans bold (ex : "Devis gratuit" / "Certifié RGE" /
   "Intervention en 2h" / "10 ans de métier")
3. Services — grille 3 colonnes cards fond blanc bordure épaisse
   noire, icône Lucide, titre court DM Sans bold
4. Zone d'intervention — liste des villes / arrondissements
   en flex wrap badges outline
5. Réalisations — 3 cards fond #F5F5F5 avec titre projet +
   description courte (pas de photos — prévoir zones à remplir)
6. Avis clients — 4 avis en cards, étoiles SVG couleur accent,
   nom + ville + note
7. Contact urgent — fond noir, téléphone Playfair 56px accent,
   formulaire 3 champs (nom, téléphone, description problème)

Services : [LISTE SERVICES]
Zone : [LISTE VILLES / ARRONDISSEMENTS]
Avis : [NOM + NOTE + TEXTE x4]
Téléphone : [NUMÉRO]
Certifications : [LISTE]
Meta description : "[META 155 chars]"
OpenGraph. Mobile-first. Pas d'animations lourdes.
```

---

## SECTEUR 05 — BIEN-ÊTRE / SANTÉ DOUCE

**Skin recommandé :** SOFT
**Mots-clés types :** [praticien] [ville], [spécialité] [ville],
séance [praticien] [ville], cabinet [spécialité] [ville]

**Sections prioritaires :**
Confiance > Approche > Soins > Tarifs > RDV

```
Crée un site vitrine pour [NOM], [PRATICIEN / SPÉCIALITÉ]
à [VILLE]. Cible : [adultes / familles / sportifs / femmes].

STYLE : soft gradients, rounded corners, muted earth tones,
wellness, warm, approachable, human, cozy.

CONTRAINTE ABSOLUE : aucune image IA, aucun placeholder.
Design basé sur typographie + icônes SVG Lucide uniquement.

Stack : React + Tailwind CSS + Lucide-React
Polices : Playfair Display (titres) + DM Sans (corps)

Palette :
— Fond : #FDF8F3
— Texte : #3D2B1F
— Accent : #D4856A
— Secondaire : #7EB5A6
— Cards : #FFFFFF
— Border-radius : 2xl partout

H1 unique : "[SPÉCIALITÉ] à [VILLE] — [NOM]"

Sections dans l'ordre :
1. Hero centré doux — Playfair 72px italic, fond dégradé pêche
   très doux, icône Lucide centrée (Heart / Leaf / Sparkles),
   sous-titre rassurant, CTA "Prendre rendez-vous"
2. À propos / Approche — texte chaleureux 2 paragraphes,
   liste de valeurs avec icônes Lucide Check couleur accent
3. Soins proposés — 3 à 6 cards arrondies, icône Lucide
   couleur sauge, titre + courte description + durée + prix
4. Déroulement d'une séance — 3 étapes illustrées icônes Lucide,
   fond #F0F7F5 (vert très doux)
5. Témoignages — 2 à 3 citations Playfair italic, nom + prénom
6. Tarifs — tableau simple ou cards 2 colonnes, prix clairs
7. Localisation — adresse + horaires + info pratiques
   (transports, parking)
8. Contact / RDV — formulaire 4 champs + lien Doctolib si existant

Soins : [LISTE SOINS + DURÉE + PRIX]
Adresse : [ADRESSE COMPLÈTE]
Horaires : [HORAIRES]
Témoignages : [TEXTE + NOM x3]
Meta description : "[META 155 chars]"
OpenGraph. Mobile-first. Pas d'animations lourdes.
```

---

## SECTEUR 06 — MÉDECIN / PARAMÉDICAL

**Skin recommandé :** SOFT (si généraliste) / PRESTIGE (si spécialiste)
**Mots-clés types :** [spécialité] [ville], docteur [spécialité]
[ville], cabinet médical [ville]

**Sections prioritaires :**
Confiance médicale > Spécialités > Praticiens > Infos pratiques > RDV

```
Crée un site vitrine pour [NOM DU CABINET / DR NOM],
[SPÉCIALITÉ MÉDICALE] à [VILLE].
Cible : [patients adultes / enfants / sportifs].

STYLE : clean medical, trustworthy, soft professional,
reassuring, accessible, clear hierarchy.

CONTRAINTE ABSOLUE : aucune image IA, aucun placeholder.
Design basé sur typographie + icônes SVG Lucide uniquement.

Stack : React + Tailwind CSS + Lucide-React
Polices : Playfair Display (titres) + DM Sans (corps)

Palette :
— Fond : #F8FAFB (blanc légèrement bleuté)
— Texte : #1A2332
— Accent : #2E6DA4 (bleu médical sobre)
— Cards : #FFFFFF
— Bordures : #E2EAF0

H1 unique : "[SPÉCIALITÉ] à [VILLE] — Dr [NOM] / Cabinet [NOM]"

Sections dans l'ordre :
1. Hero rassurant — Playfair 64px, fond très clair, accroche
   sobre et professionnelle, bouton "Prendre rendez-vous" accent
2. Spécialités / Actes — grille 2x3 cards blanc, icône Lucide
   (Stethoscope, Heart, Brain, Eye, Bone, Activity),
   titre + 2 lignes description
3. Le praticien / L'équipe — carte horizontale, initiales dans
   cercle bleu, nom + titre + formation + années d'expérience
4. Informations pratiques — horaires + adresse + accès
   (transports), fond #F0F5FA, layout 2 colonnes
5. Prise de rendez-vous — encart centré, fond accent,
   texte blanc, bouton Doctolib ou formulaire, numéro visible
6. FAQ — 4 questions pratiques accordéon (mutuelle, délais,
   urgences, documents à apporter)

Spécialités : [LISTE]
Praticiens : [NOM + TITRE + FORMATION]
Adresse : [ADRESSE]
Horaires : [HORAIRES]
Téléphone : [TEL]
Doctolib : [URL si existant]
Meta description : "[META 155 chars]"
OpenGraph. Mobile-first. Pas d'animations lourdes.
```

---

## SECTEUR 07 — ARCHITECTE / DESIGNER D'INTÉRIEUR

**Skin recommandé :** EDITORIAL
**Mots-clés types :** architecte [ville], designer intérieur [ville],
cabinet architecture [ville], rénovation [ville]

**Sections prioritaires :**
Portfolio > Approche > Services > Process > Contact

```
Crée un site vitrine pour [NOM], [ARCHITECTE / DESIGNER INT.]
à [VILLE]. Cible : [particuliers premium / promoteurs / entreprises].

STYLE : magazine grid, asymmetric columns, thin serif,
white space, intellectual, editorial, refined, portfolio-forward.

CONTRAINTE ABSOLUE : aucune image IA, aucun placeholder.
Zones prévues pour photos de réalisations réelles à uploader.
Design basé sur typographie + icônes SVG Lucide uniquement.

Stack : React + Tailwind CSS + Lucide-React
Polices : Playfair Display weight-300 (titres) + DM Sans (corps)

Palette :
— Fond : #FFFFFF
— Texte : #1A1A1A
— Accent : #C0A882
— Séparateurs : #DDDDDD (1px)
— Aucun fond de section coloré

H1 unique : "Architecte à [VILLE] — [NOM]"

Sections dans l'ordre :
1. Hero éditorial — Playfair 88px weight-300 italic, colonnes
   asymétriques (60/40), méta à droite (localisation, fondé en,
   projets réalisés)
2. Portfolio — grille 3 colonnes asymétrique, blocs placeholder
   fond #F0F0F0, label projet DM Sans 11px uppercase. Chaque bloc
   = titre projet + type + surface/budget si disponible
3. Approche / Philosophie — texte long 2 colonnes, citation
   Playfair italic encadrée en accent
4. Services — liste numérotée Playfair, sans cards ni fond coloré
5. Process — 5 étapes en ligne horizontal desktop, vertical mobile,
   numéros Playfair 48px opacity-20
6. Contact — minimaliste, email + téléphone, formulaire 4 champs

Portfolio : [LISTE PROJETS + TYPE]
Services : [LISTE]
Process : [ÉTAPES]
Email : [EMAIL]
Meta description : "[META 155 chars]"
OpenGraph. Mobile-first. Pas d'animations lourdes.
```

---

## SECTEUR 08 — RESTAURANT / TRAITEUR

**Skin recommandé :** BOLD (contemporain) ou DARK (gastronomique)
**Mots-clés types :** restaurant [cuisine] [ville], traiteur [ville],
restaurant gastronomique [ville], livraison [cuisine] [ville]

**Sections prioritaires :**
Appétence visuelle > Menu > Réservation > Localisation > À propos

```
Crée un site vitrine pour [NOM DU RESTAURANT], [TYPE DE CUISINE]
à [VILLE]. Cible : [familles / professionnels / touristes / foodies].

STYLE : [bold appetizing OU cinematic gastronomic], high-impact,
food-forward, warm contrast, inviting.

CONTRAINTE ABSOLUE : aucune image IA, aucun placeholder.
Zones prévues pour vraies photos plats à uploader.
Design basé sur typographie + icônes SVG Lucide uniquement.

Stack : React + Tailwind CSS + Lucide-React
Polices : Playfair Display (titres) + DM Sans (corps)

Palette BOLD : Fond #FFFFFF / Texte #0A0A0A / Accent #E63329
Palette DARK : Fond #0D0D0D / Texte #F5F0EB / Accent #C8965A

H1 unique : "Restaurant [CUISINE] à [VILLE] — [NOM]"

Sections dans l'ordre :
1. Hero fullscreen — Playfair 88px italic, accroche courte
   et gourmande, fond couleur selon palette, bouton
   "Réserver une table"
2. Notre carte — 3 à 4 catégories en onglets (Entrées / Plats /
   Desserts / Boissons), chaque plat = nom + description + prix
   Format DM Sans, zones photo placeholder #1A1A1A ou #F5F5F5
3. Notre histoire — 2 colonnes, texte Playfair italic quote +
   corps DM Sans, fondateur + année
4. Événements / Privatisation — encart fond accent si disponible
5. Avis — 3 avis Google stylisés (étoiles + texte + prénom)
6. Réservation — bouton centré lien TheFork / LaFourchette
   OU formulaire 4 champs (date, heure, couverts, nom)
7. Infos pratiques — adresse + horaires + téléphone + parking

Menu : [PLATS PAR CATÉGORIE + PRIX]
Horaires : [HORAIRES]
Adresse : [ADRESSE]
Téléphone : [TEL]
Réservation : [URL ou formulaire]
Meta description : "[META 155 chars]"
OpenGraph. Mobile-first. Pas d'animations lourdes.
```

---

## SECTEUR 09 — AGENT IMMOBILIER / AGENCE

**Skin recommandé :** GLOBAL
**Mots-clés types :** agent immobilier [ville], agence immobilière
[ville], vente appartement [ville], estimation immobilière [ville]

**Sections prioritaires :**
Crédibilité > Services > Biens (placeholder) > Process > Contact

```
Crée un site vitrine pour [NOM / AGENCE], agent immobilier
à [VILLE]. Cible : [vendeurs / acheteurs / investisseurs / bailleurs].

STYLE : clean corporate, confident spacing, trustworthy, airy,
professional real estate, editorial white.

CONTRAINTE ABSOLUE : aucune image IA, aucun placeholder photo.
Zones prévues pour photos biens réels à uploader.
Design basé sur typographie + icônes SVG Lucide uniquement.

Stack : React + Tailwind CSS + Lucide-React
Polices : Playfair Display (titres) + DM Sans (corps)

Palette :
— Fond : #FAFAF8
— Texte : #111111
— Accent : #1B4F72 (bleu confiance)
— Sections alternées : #F2EFE9
— Bordures : #E5E0D8

H1 unique : "Agent immobilier à [VILLE] — [NOM]"

Sections dans l'ordre :
1. Hero — Playfair 80px, accroche vendeur/acheteur, encart
   "Estimation gratuite" en accent, stats clés (biens vendus,
   délai moyen, satisfaction)
2. Services — 3 cards (Vente / Achat / Location / Gestion)
   icônes Lucide (Home, Key, Building, BarChart2)
3. Biens à la vente — grille 3 colonnes, cards placeholder
   fond #F0F0F0, label DM Sans (type + ville + prix indicatif)
4. Notre secteur — zones couvertes en flex wrap badges
5. Process vente — 5 étapes numérotées Playfair
   (Estimation → Mandat → Diffusion → Visites → Signature)
6. Témoignages — 3 avis, nom + type de transaction + note
7. Contact / Estimation — formulaire 5 champs + téléphone direct

Services : [LISTE]
Secteur : [LISTE VILLES / QUARTIERS]
Stats : [BIENS VENDUS] / [DÉLAI MOYEN] / [SATISFACTION]
Téléphone : [TEL]
Meta description : "[META 155 chars]"
OpenGraph. Mobile-first. Pas d'animations lourdes.
```

---

## SECTEUR 10 — STUDIO CRÉATIF / AGENCE

**Skin recommandé :** DARK
**Mots-clés types :** agence [spécialité] [ville], studio [design /
vidéo / photo] [ville], agence communication [ville]

**Sections prioritaires :**
Portfolio > Expertise > Clients > Process > Contact

```
Crée un site vitrine pour [NOM], [TYPE DE STUDIO / AGENCE]
à [VILLE]. Cible : [marques / startups / ETI / agences].

STYLE : cinematic, typographic dominance, deep contrast,
editorial dark, premium portfolio, agency-forward, bento grid.

CONTRAINTE ABSOLUE : aucune image IA, aucun placeholder.
Zones prévues pour visuels de projets réels à uploader.
Design basé sur typographie + icônes SVG Lucide uniquement.

Stack : React + Tailwind CSS + Lucide-React
Polices : Playfair Display (titres) + DM Sans (corps)

Palette :
— Fond : #0D0D0D
— Accent : #6B3FA0
— Texte : #F5F0EB
— Cards : #1A1A1A

H1 unique : "[TYPE AGENCE] à [VILLE] — [NOM]"

Sections dans l'ordre :
1. Hero plein écran — Playfair 96px italic, stats (projets /
   clients / années), fond noir
2. Expertises — Bento Grid 6 blocs asymétriques, icônes Lucide
   (Pen, Camera, Code2, TrendingUp, Film, Palette),
   titre + description courte
3. Projets — grille 2 colonnes, cards fond #1A1A1A grandes,
   label projet DM Sans 11px uppercase, zones photo à remplir
4. Clients — logos texte en ligne (noms des marques en DM Sans
   uppercase, opacity-60)
5. Process — 4 étapes numérotées, fond alterné #111111
6. Contact — fond #0D0D0D, email grand Playfair,
   formulaire 4 champs

Expertises : [LISTE]
Projets : [LISTE PROJETS + TYPE]
Clients : [LISTE NOMS]
Process : [ÉTAPES]
Email : [EMAIL]
Meta description : "[META 155 chars]"
OpenGraph. Mobile-first. Pas d'animations lourdes.
```

---

## RÈGLES COMMUNES À TOUS LES SECTEURS

### Ce qui ne change jamais
- Stack React + Vite + Tailwind CSS + Lucide-React
- Polices Playfair Display + DM Sans hébergées en local
- H1 unique contenant mot-clé + ville
- Meta description ≤ 155 caractères
- OpenGraph dans le head
- Mobile-first
- Pas d'animations lourdes
- Zéro image IA, zéro placeholder générique

### Ce qui s'adapte par secteur
- Palette et skin (voir Dossier 1)
- Sections prioritaires (ordre et nombre)
- Terminologie (avis vs témoignages, soins vs services, etc.)
- Arguments de confiance (certifications, années, labels)
- Type de CTA (appeler vs réserver vs prendre RDV vs devis)

### Zones photo
Pour les secteurs avec portfolio ou visuels (photographe,
architecte, restaurant, agence) : les zones photo sont des blocs
fond neutre avec label. Le client uploade ses vraies photos après
la livraison YOR. Ne jamais utiliser d'images générées par IA.

---

## NOTES DE VERSION

v1.0 — Avril 2026
- 10 secteurs initiaux couverts
- Secteurs 01, 02, 03 validés sur cas clients réels
- Secteurs 04 à 10 à valider sur prochains clients

## À FAIRE (prochaines versions)
- [ ] Ajouter secteur 11 — Coach / Formateur
- [ ] Ajouter secteur 12 — Professionnel du sport / Coach sportif
- [ ] Ajouter secteur 13 — Comptable / Expert-comptable
- [ ] Ajouter secteur 14 — Médecin spécialiste (variante PRESTIGE)
- [ ] Documenter les cas clients réels pour secteurs 04 à 10
- [ ] Créer variante "multipage" pour chaque secteur
  (Starter = 1 page / Standard = 5+ pages)
