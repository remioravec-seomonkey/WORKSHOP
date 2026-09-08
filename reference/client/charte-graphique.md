# Charte graphique A2M Ambulance — reconstituée depuis le code source

Relevé : 2026-09-08 · Source : HTML servi de `a2m-ambulance.fr` + kit Elementor `post-737.css`
+ réglages OceanWP inline + `wp-custom-css` + styles inline des widgets HTML.

---

## Le constat préalable

**Il n'existe pas de charte graphique configurée.** Le kit Elementor — l'endroit où
la charte devrait vivre — est resté sur les **valeurs d'usine d'Elementor**, à une
exception près.

```css
.elementor-kit-737{
  --e-global-color-primary:   #6EC1E4;  /* défaut Elementor, jamais modifié */
  --e-global-color-secondary: #003366;  /* ← SEUL token réellement défini */
  --e-global-color-text:      #7A7A7A;  /* défaut Elementor */
  --e-global-color-accent:    #61CE70;  /* défaut Elementor */
  --e-global-typography-primary-font-family:   "Roboto";      /* défaut */
  --e-global-typography-secondary-font-family: "Roboto Slab"; /* défaut */
}
```

Résultat : les couleurs réelles ont été posées à la main, section par section, dans
trois endroits séparés (réglages OceanWP, `wp-custom-css`, attributs `style=` inline).
D'où l'inventaire ci-dessous.

---

## Inventaire relevé — ce qui est réellement dans le code

### Bleus et cyans — **34 valeurs distinctes**

| Hex | Où | Rôle observé |
|---|---|---|
| `#6EC1E4` | kit Elementor | défaut jamais utilisé |
| `#003366` | kit Elementor | secondaire (seul token voulu) |
| `#0AA0D6` | OceanWP accent | liens, boutons, bordures, auteur d'avis |
| `#00557F` | OceanWP | survol de bouton, titre bloc avis |
| `#0B2C5F` | OceanWP + custom CSS | texte du menu, item actif |
| `#0B2D5C` | inline | titres de la carte « zone » |
| `#0B2F66` | inline | panneaux marine (4 sections) |
| `#0B2250` | inline | encart contact bas de page |
| `#0F2B5B` | inline | panneau « Montpellier Transport médical » |
| `#073B78` | inline | panneau « Ambulance VSL et taxi » |
| `#0B3A78` | custom CSS | survol de sous-menu |
| `#1E5BB8` | OceanWP | survol du menu mobile |
| `#005BAA` | custom CSS | fond de la top-bar |
| `#0A62A3` | custom CSS | pastilles top-bar, titres icon-box |
| `#0073E6` | custom CSS | survol du menu principal |
| `#0066B3` | inline | libellé de zone |
| `#009CFF` | custom CSS | item de sous-menu actif |
| `#0B5ED7` | inline | liens des communes |
| `#0048FE` | plugin accessibilité | accent du widget |
| `#1E90FF` | custom CSS | bouton d'appel flottant (`.floating-call`) |
| `#00BCD4` | custom CSS | bouton d'appel mobile (`.bouton-appel-fixe`) |
| `#4CBEEB` | plugin WP Call Button | bouton d'appel du plugin |
| `#4054B2` | kit Elementor | défaut inutilisé |
| `#E6F4FF` `#E0F2FE` `#EFF6FF` `#EEF6FF` | OceanWP + inline | pastilles et survols clairs |
| `#F0F7FF` `#F7FAFF` `#F8FAFC` `#F8FAFF` `#F2F6FB` | inline | fonds de section |
| `#E5EEF8` `#E6EEF8` `#E5E7EB` `#E5E5E5` `#E4E7EE` | divers | bordures |

**Trois boutons d'appel de trois couleurs différentes coexistent** : `#00BCD4`
(CSS personnalisé mobile), `#1E90FF` (`.floating-call`) et `#4CBEEB` (plugin
WP Call Button — celui réellement affiché).

### Verts — 7 valeurs

| Hex | Où | Rôle |
|---|---|---|
| `#22C55E` | inline | **CTA « Appeler maintenant » — le plus fréquent** |
| `#2ECC71` | inline | CTA panneau « Transport médical » |
| `#25C76F` | inline | CTA panneau « Ambulance VSL » |
| `#1ECB73` | custom CSS | survol du menu principal |
| `#3BD615` | OceanWP | soulignement animé du menu (effect-three) |
| `#61CE70` | kit Elementor | défaut |
| `#23A455` | kit Elementor | défaut |

### Neutres et signal

`#1A1A1A` · `#1F2937` · `#333333` (texte courant OceanWP) · `#334155` · `#374151`
· `#4B5563` · `#7A7A7A` (défaut Elementor) — et `#F4B400` pour les étoiles d'avis.

---

## Typographies

**Quatre familles chargées**, trois réellement déclarées quelque part :

| Police | Chargée | Déclarée où |
|---|---|---|
| **Roboto** | oui | kit Elementor — corps, titres, boutons (400 / 500 / 600) |
| **Roboto Slab** | oui | kit Elementor — typographie « secondaire », non employée |
| **Montserrat** | oui | chargée, aucune déclaration trouvée dans le CSS servi |
| **Comfortaa** | oui | chargée, aucune déclaration trouvée dans le CSS servi |

Montserrat et Comfortaa sont téléchargées à chaque visite sans être utilisées :
deux requêtes de police pour rien.

### Échelle typographique OceanWP (réglages du thème)

```
body      16px / 1.8        h1  23px / 1.4
h2        20px / 1.4        h3  18px / 1.4
h4        17px / 1.4        h5  14px / 1.4
h6        15px / 1.4
titre de page       32px
menu déroulant      12px, interlettrage 0.6px
menu mobile         17px, interlettrage 0.5px
```

**Le H1 est réglé à 23px, soit plus petit que plusieurs paragraphes de la page.**
Dans les faits ces réglages sont contournés partout : les widgets Elementor et les
blocs HTML inline imposent leurs propres tailles (38px, 30px, 28px, 26px, 24px),
et le menu passe à 20px via `wp-custom-css`. L'échelle du thème ne sert donc à rien.

---

## Formes, ombres, gabarit

| Propriété | Valeur relevée | Source |
|---|---|---|
| Largeur de conteneur | **1220 px** | kit Elementor |
| Points de rupture | 1024 px / 767 px | kit Elementor |
| Espacement des widgets | 20 px | kit Elementor |
| Rayon des images | 0 | kit Elementor |
| Rayon des champs et boutons | 3 px | OceanWP |
| Rayons inline | 6, 8, 12, 14, 20, 22, 24, 26, 50, 999 px | styles inline |
| Ombre de bouton | `0 0 10px rgba(0,0,0,.5)` | kit Elementor |
| Ombres de carte | `0 10px 25px rgba(15,23,42,.08)` à `0 12px 30px rgba(0,0,0,.18)` | inline |
| Hauteur d'en-tête | 60 px | OceanWP |
| Logo | max 170 × 55 px | OceanWP |

L'ombre de bouton du kit (`rgba(0,0,0,0.5)`, soit 50 % d'opacité et aucun décalage)
est un halo noir centré : c'est la seule ombre vraiment discordante du lot.

---

## Identité de marque

- **Logo** : `A2M-LOGO-sans-tel-512-512-.png` (512 × 512, favicon et schema)
  et `cropped-cropped-A2M-LOGO-sans-tel.png` (529 × 160, en-tête)
- **Nom** : A2M Ambulance · **Baseline employée** : « Votre sérénité, notre priorité »
- **Téléphone** : 04 67 87 01 07 · **E-mail** : a2mambulance@gmail.com
- **Adresse** : 1570 Av. Léon Jouhaux, 34070 Montpellier
- **Coordonnées** : 43.5927603, 3.8198757
- **Mentions récurrentes** : conventionné CPAM, agréé CPAM, 7j/7, 4,7/5 sur +140 avis

---

## La charte consolidée que je propose

Trente-quatre bleus ne sont pas une identité. Voici le système ramené à ce qui est
réellement porteur de sens, en gardant les teintes déjà les plus employées sur le site
— rien n'est inventé, tout est choisi parmi l'existant.

### Palette

| Rôle | Token | Hex | Justification |
|---|---|---|---|
| **Marine — couleur de marque** | `--a2m-marine` | `#0B2C5F` | menu, item actif, titres ; la plus structurante, et proche du `#003366` du kit |
| Marine foncé | `--a2m-marine-dark` | `#0B2250` | encarts de contact |
| Marine clair | `--a2m-marine-light` | `#0B3A78` | survols de sous-menu |
| **Cyan — accent** | `--a2m-cyan` | `#0AA0D6` | accent OceanWP, liens, auteurs d'avis |
| Cyan foncé | `--a2m-cyan-dark` | `#00557F` | survols de bouton |
| Cyan moyen | `--a2m-cyan-mid` | `#0A62A3` | pastilles, titres d'icon-box |
| **Vert — action** | `--a2m-action` | `#22C55E` | CTA d'appel, le vert le plus fréquent |
| Vert foncé | `--a2m-action-dark` | `#16A34A` | survol (déduit, ton en dessous) |
| Ambre | `--a2m-amber` | `#F4B400` | étoiles d'avis |
| Fond clair | `--a2m-tint` | `#E0F2FE` | pastilles et badges |
| Fond de section | `--a2m-surface-alt` | `#F7FAFF` | alternance de sections |
| Bordure | `--a2m-line` | `#E5EEF8` | cartes et séparateurs |
| Texte | `--a2m-ink` | `#1F2937` | remplace `#333` et `#7A7A7A` |
| Texte secondaire | `--a2m-ink-soft` | `#4B5563` | paragraphes secondaires |

**Le vert reste la couleur d'action, exclusivement.** Aujourd'hui le vert sert aussi
au survol du menu (`#1ECB73`) et au soulignement animé (`#3BD615`) : à supprimer, sinon
le vert ne signale plus rien.

**Un seul bouton d'appel**, en `--a2m-action`. Les trois variantes actuelles
(`#00BCD4`, `#1E90FF`, `#4CBEEB`) disparaissent.

### Typographies

| Usage | Proposition | Pourquoi |
|---|---|---|
| Titres | **Montserrat** 600/700 | déjà chargée, non utilisée ; caractère plus affirmé que Roboto |
| Corps | **Roboto** 400/500 | déjà la police du kit, lisible, aucun coût de migration |
| À retirer | Roboto Slab, Comfortaa | chargées pour rien |

Alternative : tout en Roboto, et on retire trois polices sur quatre. Plus rapide,
moins de personnalité. À trancher avec le client.

### Échelle typographique corrigée

```
h1  clamp(30px, 4vw, 44px) / 1.15    h4  20px / 1.4
h2  clamp(26px, 3vw, 34px) / 1.2     h5  18px / 1.4
h3  24px / 1.3                       h6  16px / 1.4
corps 17px / 1.7    ·    petit 14px / 1.5
```

Le H1 passe de 23 px à 30–44 px : il redevient le titre de la page.

### Formes

```
rayon petit    8px    (champs, petits boutons)
rayon moyen   16px    (cartes)
rayon large   24px    (panneaux, encarts)
pilule       999px    (CTA, badges, chips)
```

### Ombres

```
--a2m-shadow-sm  0 2px 12px rgba(11,44,95,.06)
--a2m-shadow-md  0 10px 30px rgba(11,44,95,.10)
--a2m-shadow-lg  0 20px 50px rgba(11,44,95,.15)
```

L'ombre de bouton du kit (`0 0 10px rgba(0,0,0,.5)`) est à retirer.

### Gabarit

Conteneur 1220 px conservé. Points de rupture 1024 / 767 conservés, plus un palier
480 px absent aujourd'hui (les blocs inline se cassent en dessous).

---

## Contraste — deux points à vérifier

- `--a2m-action` `#22C55E` sur blanc : ratio ≈ 2,3:1. **Insuffisant pour du texte.**
  Acceptable en fond de bouton avec texte blanc (ratio ≈ 2,6:1 — toujours limite).
  Passer les CTA en `#16A34A` porte le texte blanc à ≈ 3,9:1, et à ≈ 4,6:1 avec `#15803D`.
- `#7A7A7A` sur blanc : ratio ≈ 4,7:1, tout juste conforme AA. Remplacé par `#4B5563`
  (≈ 7,5:1) dans la palette consolidée.

Ratios calculés sur les formules WCAG standard ; à revalider avec un outil dédié
avant mise en production.

---

## Fichier de tokens

Le système ci-dessus est disponible prêt à l'emploi dans `tokens.css`
(même dossier), en variables CSS.
