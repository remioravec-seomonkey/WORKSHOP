# Site client — A2M Ambulance (Montpellier)

URL : https://www.a2m-ambulance.fr/
Relevé : 2026-09-08 · Cible : **B2C** · Objectif de conversion : **formulaire + appels**

---

## Stack en place

| Élément | Valeur |
|---|---|
| CMS | WordPress 7.1 |
| Thème | OceanWP (+ Ocean Extra) |
| Builder | Elementor Pro 4.2.4 |
| Cache | WP Rocket 3.23.3.3 |
| SEO | Yoast |
| Autres | Site Kit by Google, Complianz (RGPD), Accessibility OneTap, WP Call Button |

Poids de la page d'accueil : **509 Ko de HTML** pour **~1 390 mots visibles**.

---

## Arborescence réelle (18 pages au sitemap)

**Services (7)**
- `/ambulance-vsl-taxi-montpellier/` — page mère « Nos services »
- `/ambulance-montpellier-a2m-ambulance/`
- `/vsl-montpellier/`
- `/taxi-conventionne-montpellier/`
- `/ambulance-dialyse-montpellier/`
- `/transport-medicalise-montpellier/`
- `/rapatriement-sanitaire-france/`

**Villes (6)**
- `/ambulance-montpellier-ouest/`
- `/ambulance-saint-jean-de-vedas/`
- `/ambulance-laverune/`
- `/ambulance-juvignac/`
- `/ambulance-saint-georges-dorques/`
- `/ambulance-vsl-montpellier-ouest/` — page carte

**Autres (5)**
- `/` · `/contact/` · `/ambulance-hopitaux-montpellier/`
- `/ambulance-vsl-taxi-montpellier/faq-ambulance-montpellier/`
- `/recrutement-dea-montpellier/`

**Hors sitemap mais en ligne (200)** : `/mentions-legales/`, `/actualites/`

L'ossature service × ville est **la bonne**. Le problème n'est pas l'architecture, c'est
la conversion et la couverture.

---

## 🔴 Blocage n°1 — il n'y a AUCUN formulaire sur le site

Vérifié sur `/` et sur `/contact/`. Les seuls éléments `<form>` présents sont :
1. le formulaire de recherche du thème OceanWP (x2),
2. le panneau de réglages du plugin d'accessibilité.

Aucun WPForms, aucun Contact Form 7, aucun formulaire Elementor, aucun formulaire tiers,
aucune iframe de formulaire. La mention `wpforms` trouvée dans le code n'est qu'un
sélecteur CSS du thème OceanWP, pas un formulaire installé.

**Les seuls chemins de conversion existants sont `tel:` et `mailto:`.**

Sur la page d'accueil, il n'y a que **deux boutons** :

| CTA | Destination |
|---|---|
| « Appelez maintenant – 04 67 87 01 07 » | `tel:0467870107` |
| « Voir les avis Google » | Google Maps — **sort du site** |

Un bouton d'appel flottant existe (`wp-call-button` → `tel:+33467870107`) : c'est le seul
dispositif de conversion permanent, et il ne couvre que le canal téléphone.

**Conséquence directe** : la moitié de l'objectif — le formulaire — n'existe pas.
Tout visiteur qui ne veut pas ou ne peut pas téléphoner (hors horaires, sourd ou
malentendant, demande de devis à préparer, réservation de transport programmé
à J+3) n'a aucun moyen de laisser ses coordonnées.

---

## 🔴 Blocage n°2 — le balisage local est absent du schema

Le JSON-LD des pages ne déclare que :
`Organization`, `WebSite`, `WebPage`, `BreadcrumbList`, `ImageObject`, `SearchAction`.

Il manque tout ce qui fait le référencement local d'une ambulance :

| Manquant | Impact |
|---|---|
| `LocalBusiness` / `MedicalBusiness` | Pas de qualification d'activité locale |
| `address` + `geo` | Pas d'ancrage géographique structuré |
| `openingHoursSpecification` | Le « 7j/7 » n'est pas lisible par Google |
| `areaServed` | Les 5 communes ne sont pas déclarées |
| `hasOfferCatalog` | Les 6 services ne sont pas déclarés |
| `aggregateRating` | **La page affiche « 4,7/5 · +140 avis Google » en H2 mais ne le structure pas** |

Le concurrent ambulance-pegomas.fr déclare `["LocalBusiness","MedicalBusiness"]` complet
avec `areaServed` sur 13 villes, `hasOfferCatalog` sur 6 services et `aggregateRating`.
Sur une requête locale, c'est un écart net.

---

## 🟠 Défauts de balisage

| Page | Problème |
|---|---|
| `/contact/` | **Deux `<h1>`** — « CONTACT AMBULANCE - A2M AMBULANCE VSL TAXI CONVENTIONNE » et « Contact & prise en charge rapide 7j/7 » |
| `/actualites/` | **Aucun `<h1>`** — la page démarre en H2 |
| `/actualites/` | Les 5 articles ne sont **pas au sitemap** (aucun `post-sitemap.xml` généré) → contenu invisible pour Google |
| Global | Emojis dans le `<h1>`, les `<h2>` et **tous les libellés du menu** (🚑 📍 ✅ ❤️ 🏥 🌍 📋 🚙 🚕 🩺 ✈️ ℹ️ 📞 ❓ ⚖️ 👥) |

La page d'accueil elle-même est correcte : 1 H1, 12 H2, 13 H3, hiérarchie respectée,
**110 images toutes pourvues d'un `alt`**. C'est mieux que les deux concurrents analysés.

---

## 🟠 Direction artistique non cadrée

Aucune variable CSS de marque. Les couleurs sont posées à la main dans Elementor.
Relevé sur la page d'accueil — **neuf bleus différents** :

```
#0aa0d6  x17    cyan dominant
#0048fe  x14    bleu vif
#0b2c5f  x8     marine
#1e5bb8  x3
#0a62a3  x2
#0b3a78  x2
#00557f  x2
#0066b3  x2
#0b2d5c  x2
```
Plus un vert `#3bd615`, un jaune `#f4b400`, un bleu clair de fond `#e6f4ff`.

Aucune police déclarée en variable, aucun `@font-face`, aucun appel Google Fonts
identifiable dans le HTML servi.

C'est le symptôme classique d'un site construit section par section dans un page builder,
sans design system. **C'est précisément ce que ta charte graphique va corriger** — d'où
l'intérêt de la recevoir avant de coder quoi que ce soit.

---

## 🟠 Maillage interne pauvre

23 URL internes distinctes liées depuis la page d'accueil, dont l'essentiel provient du menu.
Peu de liens contextuels dans le corps de texte. Les pages villes ne semblent pas
se renvoyer entre elles.

---

## Ce qui fonctionne déjà et qu'il faut garder

- L'architecture **service × ville** — c'est le bon modèle pour du local B2C
- Le bouton d'appel flottant
- Le téléphone en clair partout, y compris dans le menu
- Les `alt` d'images tous remplis, sans bourrage — meilleur que les deux concurrents
- Le positionnement « conventionné CPAM » présent dans le `<title>` et la meta description
- La page FAQ, la page hôpitaux, la page recrutement — de bons actifs
- La preuve sociale existe (4,7/5, +140 avis) — elle est juste mal exploitée

---

## Écart mesuré face aux concurrents

| Critère | A2M | transport-medical.fr | ambulance-pegomas.fr |
|---|---|---|---|
| Formulaire de contact | **aucun** | oui (devis, 5 champs) | oui (2 : page + flottant) |
| Bouton d'appel flottant | oui | non | oui |
| WhatsApp | non | non | oui |
| Schema local complet | **non** | partiel | oui |
| `aggregateRating` structuré | **non** | non | oui |
| Tarifs affichés | **non** | non | **oui, détaillés** |
| Pages par commune | oui (5) | non | oui (10+) |
| Avis clients affichés | oui (lien sortant) | non | oui (widget intégré) |
| Badges de réassurance | à vérifier | oui | oui (ARS, CPAM) |
| Hiérarchie Hn correcte | oui (sauf 2 pages) | **non** | partiel |
| Poids HTML accueil | 509 Ko | ~255 Ko | lourd (Divi imbriqué) |

**Les deux angles morts d'A2M face à Pégomas** : la transparence tarifaire et le
formulaire. Pégomas affiche ses tarifs conventionnés en clair (ambulance ~94 € + 2,44 €/km,
VSL ~36 € + 1,07 €/km, 65 % Sécu / 35 % mutuelle, 100 % en ALD) et capte ainsi toutes les
requêtes « prix » et « remboursement ». A2M ne dit rien sur le prix.

---

## Priorités déduites (objectif formulaire + appels)

1. **Poser un formulaire** — page contact + version courte en bouton flottant, à côté de l'appel
2. **Structurer le schema local** — `LocalBusiness`/`MedicalBusiness` + `aggregateRating` + `areaServed` + `openingHours`
3. **Ouvrir une page tarifs / remboursement CPAM** — l'angle mort concurrentiel le plus rentable
4. **Cadrer la DA** sur la charte, en variables CSS
5. **Corriger** le double H1 de `/contact/`, le H1 absent de `/actualites/`, le sitemap des articles
6. **Densifier le maillage** entre pages villes et pages services

---

## Charte graphique

Reconstituée depuis le code source — voir `charte-graphique.md` (audit et système
consolidé) et `tokens.css` (variables prêtes à l'emploi).

Constat : **aucune charte n'est configurée**. Le kit Elementor est resté sur les
valeurs d'usine, à l'exception d'un seul token (`secondary: #003366`). Les couleurs
sont posées à la main dans trois endroits séparés, d'où **34 bleus distincts**,
7 verts et 4 polices chargées dont 2 inutilisées.

## Reste à obtenir

- [ ] 3e code source concurrent
- [ ] Validation de la charte consolidée par le client (marine `#0B2C5F`,
      cyan `#0AA0D6`, vert d'action `#22C55E`, titres Montserrat)
- [ ] Décision : refonte complète ou reprise de l'existant WordPress
