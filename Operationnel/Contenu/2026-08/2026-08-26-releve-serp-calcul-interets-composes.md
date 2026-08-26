# Relevé SERP — « calcul intérêts composés »

Google France · langue fr · desktop · profondeur 20 · **26 août 2026**

## Configuration absente

Aucun `client.json` dans le dossier de travail. Trois étapes du process sont **bloquées**,
jamais cochées par défaut :

| Étape | Ce qui manque | Question à poser |
|---|---|---|
| 1 — anti-cannibalisation | propriété Search Console | Quelle est la propriété GSC et le domaine du client visé ? |
| 3 — pages sœurs | sitemap | Quelle est l'URL du sitemap ? |
| Brief blocs 4 et 5 — maillage | `sources_url` | Quelles URL internes pour PFU, PEA, assurance vie, Livret A, page mère « outils », simulateur de crédit ? |

Seuils appliqués : **défauts du schéma** (title 60, meta 155, 2 CTA, 4 questions FAQ, paragraphes 4 lignes).

## Requête cible corrigée

« calcul effet cumulé » ne remonte **aucune donnée** en base France/français (DataForSEO Labs).
Le cluster réel se nomme *intérêts composés*.

| Requête | Volume/mois | KD |
|---|---:|---:|
| intérêts composés | 5 400 | 7 |
| **calcul intérêts composés** *(cible)* | **3 600** | **6** |
| calculatrice intérêts composés | 2 900 | 19 |
| simulateur intérêts composés | 1 000 | 19 |
| tableau calcul intérêts composés | 320 | 19 |
| règle des 72 | 170 | — |
| calcul intérêt composé mensuel | 140 | 11 |

## Top 5 organiques

| # | Domaine | Type | Mots | Outil | Date visible | Éléments |
|---|---|---|---:|---|---|---|
| 1 | finary.com | Outil + guide | ≈ 600 | oui | non | Courbe SVG 2 séries, infobulle, état partageable par URL, sommaire ancré. Aucun tableau. `WebApplication`. |
| 2 | gerezmieuxvotreargent.ca | Outil nu | 154 | oui (27 champs) | non | Zéro rédactionnel. Autorité institutionnelle canadienne. |
| 3 | beauvoisine.fr | Outil + FAQ | 941 | oui | 06/08/2026 | Graphe canvas, 1 tableau figé (100 €/mois), `FAQPage` — seul du top 5. |
| 4 | home.saxo | Guide long | 3 463 | oui | non | 8 H2 + 22 H3. Meta description restée en anglais. |
| 5 | maif.fr | Guide | 1 821 | **non** | 15/10/2025 | H2 numérotés, 14 visuels, aucun champ de saisie. |

## Blocs SERP

- **AI Overview : absent.** La place se joue en organique pur.
- **People Also Ask en `rank_absolute` 3**, donc au-dessus de trois des cinq premiers résultats :
  1. Quelle est la formule du rendement cumulé ?
  2. Comment calcule-t-on le cumul ?
  3. Comment calculer les intérêts cumulés ?
  4. Qu'est-ce que la règle des 72 ?
- Recherches associées : simulateur, mensuel, tableau, Excel, journalier, annuel.

## Sortie obligatoire

```
CONSTAT 1 : 4 des 5 pages portent un calculateur, aucune n'affiche le tableau année par année.
            « tableau calcul intérêts composés » = 320 rech./mois sans réponse au-dessus du pli.
CONSTAT 2 : aucune des 5 ne contient « PFU », « flat tax », « prélèvement forfaitaire » ni « 17,2 »
            (grep sur le HTML des 4 pages accessibles + source du n°1). Calcul servi 100 % brut
            alors que le PFU est à 31,4 % depuis le 01/01/2026.
CONSTAT 3 : longueur de 154 à 3 463 mots dans le même top 5. La longueur n'est pas le facteur,
            c'est l'outil. Le n°5 n'en a aucun et tient sur l'autorité de marque.
ANGLE     : plus démontré — même calcul, mené jusqu'au montant réellement encaissé.
PROMESSE  : « Vous saurez combien il vous reste vraiment, pas combien la formule affiche. »
```

## Chiffres datés du livrable

| Donnée | Valeur | Source | Date |
|---|---|---|---|
| PFU | **31,4 %** (12,8 % IR + 18,6 % PS) | entreprendre.service-public.gouv.fr, actualité A18796 | 10/02/2026, en vigueur au 01/01/2026 |
| Livret A | **1,7 %** | service-public.fr F2365, arrêté du 28/07/2026 | période 01/08/2026 → 31/01/2027 |

## Scénario de référence (10 000 € · 100 €/mois · 20 ans · 5 %)

| | Montant |
|---|---:|
| Capital brut | 67 113 € |
| Versements | 34 000 € |
| Intérêts | 33 113 € |
| Impôt PFU 31,4 % | **10 398 €** |
| **Capital net** | **56 716 €** |

Convention de calcul, identique à celle du n°1 : taux annuel effectif, versements investis en fin
de mois au taux mensuel équivalent `i = (1+t)^(1/12) − 1`.

## Contrôle avant livraison

| # | Critère | Verdict |
|---|---|---|
| 1 | Exact match — 3 occurrences (title, réponse encadrée, H2) | passé |
| 2 | Liens — 3 entrants prévus, 0 posé ; 6 sortants en attente | **bloqué** |
| 3 | Gabarit — aucune page sœur relevable | **bloqué** |
| 4 | Seuils — title 49/60, meta 148/155, 4 FAQ /4 | passé |
| 5 | Angle tenu — dans le title, la réponse encadrée, 4 des 7 H2 | passé |
| 6 | Citabilité — fait daté + définition autonome + 2 tableaux | **CITABLE** |
| 7 | Signal — title/P1/module/preuve/suite | **5/5** |

Statut : **livré**, pas « intégré ». Passe « terminé » après verdict OK au contrôle J+21.
