# `sommaire` · Sommaire

> Le plan de la présentation : une partie par ligne, numérotée d’office, la partie en cours mise en avant.

## Quand l’employer

- **Dans la matière, tu as trouvé** : une table des matières ou un plan en trois à six parties ; un ordre du
  jour de réunion ; les chapitres d’un rapport ou d’un dossier ; un déroulé annoncé (« nous verrons d’abord…,
  puis… ») ; une présentation qui dépassera dix slides, et qu’il faut baliser.
- **Plutôt que** : `contenu` si les points sont des arguments ou des constats, non les parties de l’exposé ;
  `etapes` si la matière décrit une méthode ou un processus (l’ordre des choses, non l’ordre de l’exposé) ;
  `section`, qui ouvre une seule partie, là où le sommaire les annonce toutes (la structure type : `titre`,
  `sommaire`, puis une `section` par partie).
- **Pas pour** : une liste de plus de huit entrées (regroupe-les en parties) ; une présentation courte, de six
  à huit slides, qui n’a pas besoin de plan.

Le sommaire peut revenir entre deux parties, avec les parties passées cochées et celle qui s’ouvre en avant.

## Structure de l’information

```text
┌────────────────────────────────────────────────────────────┐
│ eyebrow                                                    │
│ title : le message du plan                                 │
│                                                            │
│ ────────────────────────────────────────────────────────── │
│ 01   Titre                                     Description │
│ ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ │
│ 02   Titre (« > » : la partie en cours)        Description │
│ ────────────────────────────────────────────────────────── │
│ 03   Titre                                     Description │
│ ────────────────────────────────────────────────────────── │
│ 04   Titre                                     Description │
└────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
sommaire
├── title      : le message du plan, une phrase courte (« Ce que nous allons parcourir. »)
├── eyebrow    : le repère, « Sommaire », « Où nous en sommes » (facultatif)
├── content    : 3 à 6 lignes « Titre | Description », une par partie, dans l’ordre de l’exposé
│     ├── repère : « > » la partie en cours, « x » une partie déjà vue (facultatif, en tête de ligne)
│     ├── Titre : le nom de la partie, deux à cinq mots ; TalkNote pose le numéro 01, 02…
│     └── Description : ce que la partie contient, une ligne courte (facultatif)
├── suitSections : true, les parties suivent les slides section (facultatif)
└── notes      : ce que le présentateur dit et qui n’est pas écrit
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `title` | Le message du plan, pas le mot « Sommaire » (il va dans `eyebrow`). | Une phrase courte ; au-delà de 64 caractères, le corps du titre baisse. |
| `eyebrow` | Le surtitre : `Sommaire`, `Où nous en sommes`, `Ordre du jour`. | Facultatif. Avec `tampon`, vide = « Sommaire ». |
| `content` | Les parties, une par ligne, dans l’ordre. | Trois à six lignes en liste, huit au plus en `colonnes`. Syntaxe ci-dessous. |
| `disposition` | `""`, `colonnes` ou `ligne`. | Voir « Dispositions ». |
| `suitSections` | `true` : les parties sont les slides `section` de la présentation, dans l’ordre, tenues à jour par TalkNote. | Booléen sans guillemets ; facultatif. Écris quand même `content`. |

`content2`, `content3`, `author` et `image` ne servent pas ici. Les champs communs (`anim`, `transition`,
`notes`, `progressive`) : voir `references/format-json.md`.

## Syntaxe de `content`

- Une ligne par partie, dans l’ordre de la présentation : `Titre | Description`. La description est
  facultative, `Titre` seul suffit.
  `Les résultats mesurés | Énergie, confort, usages.`
- Le numéro (`01`, `02`…) est posé par TalkNote dans l’ordre des lignes : n’écris ni `1.` ni `Partie 1` dans
  le titre.
- `> ` en tête de ligne : la partie en cours (numéro et titre en couleur d’accent, filet épais). `x ` en tête,
  suivi d’une espace : une partie déjà vue (titre grisé). Un sommaire d’ouverture n’en a aucun ; un sommaire
  qui revient marque `x ` les parties d’avant et `> ` celle qui s’ouvre, une seule.
  `x Le programme | Pourquoi, pour qui.`
  `> Les chantiers | Ce qui a été livré.`
- `(nom)` après le repère, avant le titre : un pictogramme devant le titre (`> (chantier) Les chantiers | …`).
  Noms reconnus : `references/pictogrammes.md`.
- Deux cellules : ce qui suit un deuxième `|` n’est pas affiché (`bdt` le joint à la description).
- Gras, surligné, ` // ` : la syntaxe commune de `references/format-json.md`. Reste sobre, un titre de partie se
  lit d’un coup.
- Limites : six parties en liste. Dès six, la liste se resserre (corps plus petit) ; sept ou huit, prends
  `colonnes` ; au-delà de huit, regroupe.

**Suivre les sections.** Avec `"suitSections": true`, TalkNote réécrit `content` à l’ouverture avec les titres
des slides `section`, dans leur ordre, sans leur point final, et le tient à jour ; les repères `x ` et `> `
viennent de la place du sommaire dans la présentation. Écris tout de même `content`, avec les titres des
sections tels quels : TalkNote retrouve chaque ligne par son titre et garde sa description. Une `section`
d’annexes porte `"horsSommaire": true` (un champ de la slide `section`) pour ne pas y figurer.

## Dispositions

| `disposition` | Composition | La choisir quand |
| --- | --- | --- |
| `""` | Liste : numéro à gauche, titre, description alignée à droite, un filet entre les parties. | Trois à six parties : le cas courant. |
| `colonnes` | Deux colonnes remplies rangée par rangée (01 02, 03 04…), la description sous le titre. | Sept ou huit parties, ou des descriptions longues. |
| `ligne` | Les parties côte à côte, le numéro en très grand, le titre puis la description dessous. | Cinq parties au plus, aux titres courts. Dès six, TalkNote revient à la liste. |

```text
colonnes
┌────────────────────────────────────────────────────────────┐
│ title                                                      │
│ 01  Titre                                        02  Titre │
│     Description                                Description │
│ 03  Titre                                        04  Titre │
│     Description                                Description │
│ 05  Titre                                        06  Titre │
│     Description                                Description │
└────────────────────────────────────────────────────────────┘
```

```text
ligne
┌────────────────────────────────────────────────────────────┐
│ title                                                      │
│                                                            │
│ 01            02            03            04               │
│ Titre         Titre         Titre         Titre            │
│ Description   Description   Description   Description      │
└────────────────────────────────────────────────────────────┘
```

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : tout s’applique ;
  avec `marge`, le surtitre passe dans la gouttière.
- **Modèles complets qui redessinent ce type** (`compose`) : `tampon`, `bloc`, `opale`, `bdt`.
  - `tampon` : le titre de chaque partie et le numéro de page de sa `section` (« p. 04 ») ; les descriptions
    ne sont pas affichées ; `colonnes` et `ligne` s’appliquent.
  - `bloc` : titre, description et page de la section ; `colonnes` et `ligne` s’appliquent.
  - `opale` : une liste numérotée, sept parties au plus ; `colonnes` et `ligne` sont ignorées.
  - `bdt` : déjà sur deux colonnes (trois parties par colonne), six parties au plus, page de la section ;
    `colonnes` est ignorée, `ligne` s’applique jusqu’à cinq parties ; les repères `>` et `x` n’y changent rien.

  Les pages : la k-ième partie prend la page de la k-ième slide `section`. Liste les parties dans l’ordre
  exact des sections, une par section, sinon les numéros de page se décalent.
- Les autres modèles complets (`revue`, `chantier`, `marqueur`, `pastille`, `anneau`, `crayon`, `cimaise`,
  `aube`) habillent le rendu Libre : toutes les dispositions s’appliquent.
- **Plateforme** (`"modele": "plateforme"`) : `colonnes` et `ligne` s’appliquent ; pas de pictogramme, le mot
  entre parenthèses est retiré.

## Pièges

- « Sommaire » en `title` : c’est un surtitre. Le titre dit quelque chose (« Ce que nous allons parcourir. »).
- Un numéro écrit à la main (`1. Le contexte`, `Partie 1 · Le contexte`) : il double celui que TalkNote pose.
- Un `|` dans une description : tout ce qui le suit disparaît. Remplace-le par une virgule ou un point.
- Deux lignes `> `, ou un `x ` après la partie en cours : le sommaire ne raconte plus où l’on en est. Une
  seule `> `, les `x ` avant elle.
- Une description longue en liste : la colonne de droite est étroite, elle passe à la ligne vers quarante
  caractères. Une idée par description, ou `colonnes`.
- `ligne` avec six parties, ou des titres longs : la liste revient, ou les titres passent sur deux lignes.
- Des parties qui ne suivent pas les sections (`tampon`, `bloc`, `bdt`) : les numéros de page se trompent. Une
  section en `horsSommaire` les décale aussi : ces trois modèles comptent toutes les sections, `suitSections`
  non.

## JSON

Le sommaire d’ouverture, en liste :

```json
{ "layout": "sommaire", "eyebrow": "Sommaire", "title": "Ce que nous allons parcourir.", "content": "Le contexte | Pourquoi un schéma directeur numérique maintenant.\nLe diagnostic | Ce que les agents et les usagers nous ont dit.\nLes quatre chantiers | Guichet unique, données, équipements, formation.\nLe calendrier et le budget | Trois ans, 4,2 M€, un comité par trimestre.\nLes décisions attendues | Ce que le conseil doit trancher ce soir.", "notes": "Annoncer que les décisions sont regroupées en partie 5 : inutile de les anticiper pendant le diagnostic." }
```

Le sommaire qui revient entre deux parties, en `ligne`, avec les repères et un pictogramme par partie :

```json
{ "layout": "sommaire", "eyebrow": "Où nous en sommes", "title": "Troisième partie : les usages.", "disposition": "ligne", "content": "x (document) Le contexte | Le plan de mobilité 2024-2030.\nx (loupe) Le diagnostic | Flux, temps de parcours, accidents.\n> (personne) Les usages | Enquête auprès de 2 400 habitants.\n(calendrier) La suite | Concertation, puis vote du plan.", "notes": "Un rappel de trente secondes, pas plus : la troisième partie commence à la slide suivante." }
```

Sept parties en `colonnes`, tenues à jour d’après les slides `section` :

```json
{ "layout": "sommaire", "eyebrow": "Rapport annuel 2025", "title": "Le service de l’eau en sept chapitres.", "disposition": "colonnes", "suitSections": true, "content": "Le territoire desservi | 31 communes, 84 000 abonnés.\nLa qualité de l’eau | 100 % des analyses conformes.\nLe réseau et les fuites | Rendement passé de 78 à 84 %.\nLes travaux de l’année | 11 km de canalisations renouvelées.\nLe prix et les recettes | 3,92 € le mètre cube, tarif inchangé.\nLa satisfaction des usagers | Enquête annuelle : 87 % de satisfaits.\nLes projets 2026 | Usine de traitement et télérelève.", "notes": "[À vérifier] Le rendement du réseau : 84 % vient du rapport provisoire." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
