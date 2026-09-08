# Analyse concurrents — Nouveau projet site

Analyse des codes sources fournis par Rémi. Objectif : extraire la structure,
la DA et les partis pris de conversion, pas copier.

Statut : 2 concurrents reçus sur 3 annoncés.

| # | Site | Secteur | Stack | Reçu |
|---|------|---------|-------|------|
| 1 | transport-medical.fr | Transport médical B2B — Paris / IDF | WordPress + Neve + Elementor Pro + Essential Addons + NitroPack | oui |
| 2 | ambulance-pegomas.fr | Ambulance / VSL / TPMR B2C local — Alpes-Maritimes | WordPress + Divi (contenu en modules Code HTML/CSS custom) | oui |
| 3 | — | — | — | en attente |

---

## 1. transport-medical.fr — le modèle B2B

**Cible** : laboratoires, hôpitaux, cliniques, pharma, vétérinaires, prothésistes.
Le site vend un contrat récurrent, pas une course unique.

### Direction artistique
- Primaire `#2aa9df` (bleu clair) · secondaire `#0e509a` · sombre `#14171c`
- Fond hero : dégradé `#e5eeff → #f1f6ff → transparent`
- Texte courant `#2f394b` · fond de section douce `#f5f7fe`
- Typos : **Spline Sans** (titres, 600), **Inter** (corps)
- Formes : cartes rayon 32px, boutons rayon 8px, cubes axonométriques en décor

### Structure de la page d'accueil (dans l'ordre)
1. Hero split — sur-titre en capitales espacées (`TRAÇABILITÉ | SÉCURITÉ | RAPIDITÉ`), H1 avec mot-clé coloré, paragraphe, 1 CTA « Échanger avec un expert », visuel à droite
2. Bandeau logos clients — « Ils nous ont fait confiance » (AP-HP, EFS…)
3. Bloc pédagogique + 3 info-box (solutions dédiées / traçabilité temps réel / conformité normes)
4. Compteurs animés — 120+ pros, 1012+ missions, 50k+ échantillons, 20+ ans
5. 4 modes de service — course urgente, navette régulière, livraison sur-mesure, coordination logistique
6. 6 types de marchandises transportées — cards avec lien « En savoir + » (produits biologiques, PSL, pharma, matériel, documents, contrôles sanitaires)
7. 3 sections sticky alternées texte/image — sécurité & traçabilité, éco-responsabilité, livraison express
8. CTA plein écran — devis + téléphone
9. Grille d'articles / services
10. **Tabs verticaux par segment client** (8 onglets) — établissements de santé, labos pharma, labos environnementaux, prothésistes, santé animale, diagnostic, pharmacie, matériel high-tech
11. Formulaire de devis

### Ce qui est bon à reprendre
- Le bloc **tabs par segment client** : une réponse par persona sans multiplier les pages du menu
- Le découpage **mode de service × type de marchandise** — deux axes de silo propres
- Les compteurs chiffrés placés tôt
- Schema.org : `Organization` + `WebPage` + `WebSite` + `BreadcrumbList`

### Ce qu'il ne faut PAS reprendre
- Tous les titres en `<h2>` (y compris le H1 du hero) — hiérarchie sémantique cassée
- Attributs `alt` bourrés de 40 mots-clés séparés par des virgules — keyword stuffing manifeste
- `<div class="feet-cache">` en pied de page : liens sortants cachés vers d'autres sites du groupe (transportpalettes.fr, coursierlyon.com…) avec `display:none`. Pratique à risque de pénalité.
- Poids du HTML (Elementor + 4 plugins) compensé par NitroPack — dette technique

---

## 2. ambulance-pegomas.fr — le modèle local / réassurance

**Cible** : patients, familles, EHPAD, cabinets médicaux d'un bassin de vie (35 km).
Le site vend la confiance et la disponibilité immédiate.

### Direction artistique
```
--bleu-medical      #1E3A5F      --bleu-medical-light  #2A4A73
--vert-sante        #1d9f92      --vert-sante-light    #26A69A
--bleu-ciel         #E8F4FC      --bleu-ciel-light     #F0F7FF
--gris-texte        #607D8B      --gris-border         #E0E0E0
--shadow-soft       0 2px 20px rgba(30,58,95,.08)
--transition        all .3s cubic-bezier(.4,0,.2,1)
```
- Typos : **Montserrat** 400-700 (titres), **Source Sans 3** 400-700 (corps)
- Formes : cartes rayon 24px, boutons pill (rayon 50px), badges pill
- Motif récurrent : badge pill en capitales + H2 avec un mot en vert + sous-titre gris

### Structure (très riche — 15 sections)
1. **Top-bar bleue** — zone géographique, 24h/24, badges « Pégomas et 35 km », « Agrément ARS n°195 », « Conventionné CPAM » (vert)
2. **Header sticky** — logo + tagline, nav 7 entrées à dropdowns, bloc téléphone avec icône + horaires
3. **Hero** — image + overlay dégradé bleu→vert, 2 badges, H1 avec mot coloré, 2 CTA (téléphone blanc + réserver fantôme)
4. **Nav icônes 6 colonnes** sous le hero — raccourcis vers les pages piliers
5. **Grille services 2×2** — 3 cards image avec boutons glassmorphism + 1 card CTA en dégradé listant les services et les tarifs
6. **Avis Google** (widget Trustindex) — note 4,7/5, 35 avis
7. **Tarifs CPAM détaillés** — 65% Sécu / 35% mutuelle, 100% si ALD, ambulance ~94€ + 2,44€/km, VSL ~36€ + 1,07€/km, majorations nuit/dimanche
8. **Partenaires** — logos CPAM, Carte Vitale, MAAF, Groupama, CNAS
9. **Pourquoi nous** — 6 cards cliquables
10. **À propos** — image + stat flottante « 7+ ans » + carte avis en dégradé vert
11. **Accompagnement** — 6 photos verticales (dialyse, hospitalisation, kiné, radiothérapie, chimio, enfants)
12. **Équipe** — section sombre, 3 cards + 3 stats (7 ambulanciers, 100% DEA, 24/7)
13. **Véhicules** — texte + 4 features + image + badge flottant
14. **Hygiène** — timeline 4 étapes numérotées (désinfection entre patients → quotidienne → hebdo → brumisation mensuelle)
15. **Confiance** — 4 stats sur image en parallaxe
16. **Zone + contact** — tags villes cliquables, map Google, bloc téléphone, formulaire
17. **Footer** — bandeau CTA vert, 4 colonnes, badges, réseaux sociaux colorés au survol
18. **Bouton flottant** bas-droite — panneau formulaire rapide + appel + WhatsApp

### Ce qui est excellent à reprendre
- **La réassurance en cascade** : agrément, conventionnement, avis, partenaires, protocoles d'hygiène, diplômes — la confiance est le produit
- **La transparence tarifaire** : tarifs réels affichés, mécanique de remboursement expliquée → capte toutes les requêtes « prix / remboursement »
- **Le maillage local** : tags villes en dur vers des pages dédiées par commune
- **Le bouton flottant** : formulaire court + tel + WhatsApp, toujours accessible
- **Schema `["LocalBusiness","MedicalBusiness"]`** complet — adresse, geo, horaires, `areaServed` (13 villes), `hasOfferCatalog` (6 services), `aggregateRating`, `sameAs` (7 profils)
- **Le formulaire** : honeypot anti-spam (`pegomas_hp1/hp2`), jeton JS, mesure du temps de remplissage, pattern de validation du téléphone français
- Palette accessible et cohérente, tokens CSS propres, responsive à 4 paliers (1200 / 992 / 768 / 480)

### Ce qu'il ne faut PAS reprendre
- `<!DOCTYPE html><html><head>` complets **imbriqués dans des modules Code Divi** → 3 documents HTML emboîtés dans la page. Aberration technique.
- Fonts et CSS rechargés dans chaque module
- Doublons de `<h1>` / balises méta
- `aggregateRating` en dur dans le JSON-LD (35 avis) alors que le widget en affiche 84 — incohérence exploitable par Google
- Faute de frappe CSS `.pegamas-float-btn` (classe morte)

---

## Synthèse — invariants du secteur

Les deux sites, malgré des cibles opposées, partagent :

| Élément | Présent chez les 2 | Note |
|---|---|---|
| Téléphone visible en permanence (header + hero + footer + flottant) | oui | non négociable |
| Mention 24h/24 – 7j/7 | oui | argument n°1 |
| Badge conventionnement / agrément | oui | réassurance réglementaire |
| Zone géographique explicite | oui | ancrage local |
| Cards services avec image + CTA | oui | format qui convertit |
| Formulaire de devis en bas de page | oui | — |
| Preuve sociale (logos ou avis) | oui | transport = logos clients, ambulance = avis Google |
| Segmentation par persona | tabs (B2B) / pages villes (B2C) | à trancher selon la cible du client |

**Différence structurante** : le B2B vend un **process** (traçabilité, conformité, contrat cadre),
le B2C local vend une **personne** (l'ambulancier diplômé, l'équipe, le protocole d'hygiène).
Le choix de l'axe dominant dépend de la cible du client.

---

## Cadrage arrêté

- **Client** : A2M Ambulance (Montpellier) — voir `reference/client/README.md`
- **Cible** : B2C (patients, familles)
- **Objectif de conversion** : formulaire + appels

→ Le modèle de référence est donc **ambulance-pegomas.fr** (local / réassurance),
pas transport-medical.fr (B2B / process). L'architecture visée est **service × commune**,
pas la segmentation par persona en onglets.

## En attente pour continuer

- [ ] 3e code source concurrent
- [ ] Charte graphique (couleurs hex, typos, logo SVG)
- [ ] Choix de la techno (statique / Astro / Next / reprise WordPress)
