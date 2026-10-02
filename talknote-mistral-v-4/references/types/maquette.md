# `maquette` · Maquette d’écran

> Une interface posée dans son appareil — ordinateur portable, écran de bureau, téléphone ou tablette —
> à côté de ce qu’elle change pour ceux qui s’en servent.

## Quand l’employer

- **Dans la matière, tu as trouvé** : des captures d’écran d’une application, d’un site ou d’un extranet ;
  un paragraphe qui décrit ce qu’un outil permet de faire, avec trois ou quatre usages ; une démonstration
  prévue dans la réunion, qu’on ne pourra peut-être pas faire ; des chiffres d’usage (utilisateurs,
  disponibilité, délai) attachés à un service en ligne.
- **Plutôt que** : `media` si l’image est un schéma, un plan ou une capture à lire en grand, sans cadre
  d’appareil et sans texte à côté ; `imagetexte` si c’est une photo — terrain, bâtiment, personnes — avec
  sa légende et son crédit ; `dashboard` si ce sont les chiffres qui comptent, pas l’interface.
- **Pas pour** : une capture dense à lire ligne à ligne ; remplacer une démonstration en direct.

## Structure de l’information

```text
┌──────────────────────────────────────────────────────────────┐
│ eyebrow                     ┌─────────────────────────────┐  │
│                             │ ● ● ●                       │  │
│ title : ce que              │ ┌────┐ ┌────────────────┐   │  │
│ l’outil change              │ │ nav│ │ ▆▆▆▆▆          │   │  │
│                             │ │    │ │ ───────────    │   │  │
│ content : le chapeau        │ │    │ │ ┌────┬────┐    │   │  │
│ ◆ puce                      │ │    │ │ │ 70 │−47%│    │   │  │
│ ◆ puce                      │ └────┘ └─┴────┴────┴────┘   │  │
│ ◆ puce                      └─────────────────────────────┘  │
│                               les cases viennent de content2 │
└──────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
maquette
├── title      : ce que l’outil change, en une phrase (soixante caractères environ)
├── content    : une phrase de chapeau, puis quatre puces « - » au plus
├── cadre      : l’appareil — portable (défaut), bureau, mobile, tablette
├── content2   : les chiffres du faux écran, « Valeur | Libellé », trois lignes au plus
│     ├── Valeur  : le nombre, très court (« 70 », « 99,9 % », « 3 j »)
│     └── Libellé : ce qu’il compte, deux ou trois mots
├── eyebrow    : repère court (« Outil de suivi · Mobile ») (facultatif)
├── ecrans     : 1 (défaut) ; jusqu’à 3 en mobile, 2 en tablette
└── notes      : la démonstration qu’on ne fera pas, ce qu’on montrerait vraiment à l’écran
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `eyebrow` | Repère au-dessus du titre : « Outil de suivi », « Sur le chantier ». | Facultatif, deux ou trois mots. |
| `title` | Ce que l’outil change pour ceux qui s’en servent, pas son nom de code. | Soixante caractères environ ; au-delà de 64 il s’affiche plus petit. |
| `content` | Le chapeau, puis les usages. | Une phrase, puis quatre puces `- ` : rien ne coupe la cinquième, c’est la place qui manque. Les puces apparaissent une à une. |
| `content2` | Les chiffres écrits dans le faux écran. | Trois lignes au plus, syntaxe ci-dessous. Inutile pour un écran qui porte une capture. |
| `cadre` | L’appareil dessiné. | `portable` (défaut), `bureau`, `mobile` ou `tablette`. Rien d’autre. |
| `ecrans` | Plusieurs appareils côte à côte. | Nombre de 1 à 3, sans guillemets. 3 en `mobile`, 2 en `tablette`, 1 ailleurs. |
| `disposition` | `""`, `inverse` ou `grand`. | Voir ci-dessous. |
| `image` | La capture du premier écran. | Laisse `""` : le faux écran suffit (voir `references/images.md`). |
| `captures` | Les captures des écrans 2 et 3. | Laisse `[]`. |

`content3`, `author`, `accent` et `fond` ne servent pas. Les champs communs (`anim`, `transition`,
`notes`, `progressive`) : voir `references/format-json.md`.

## Syntaxe de `content`

Toute ligne sans tiret devient le chapeau, en gris, sous le titre ; les lignes en `- `, `* ` ou `• `
deviennent des puces losange, celles en `1. ` des puces numérotées — quatre au plus.

```text
Un tableau de bord partagé entre la cellule d’ingénierie, les communes et les écoles.
- Relevés des compteurs importés chaque nuit
```

`(nom)` en tête d’une puce remplace le losange par un pictogramme (noms dans
`references/pictogrammes.md`). N’emploie pas d’intertitre `# ` : ce gabarit le ramène à une ligne de
chapeau. `**gras**`, `*italique*`, `==surligné==` : voir `references/format-json.md`.

## Syntaxe de `content2`

Une ligne par carte du faux écran, `Valeur | Libellé`, **trois lignes au plus**. La valeur d’abord, son
libellé ensuite ; une ligne sans valeur est ignorée.

```text
70 | Écoles suivies
−47 % | Consommation
3 | Alertes ouvertes
```

- En `bureau` et en `tablette`, seules les **deux premières** lignes s’affichent : les plus fortes en tête.
- `content2` vide **et** aucune capture : le faux écran se remplit tout seul de chiffres d’exemple —
  `812 Utilisateurs`, `99,9% SLA`, `+42 NPS` en `portable`, `bureau` et `tablette` ;
  `812 Utilisateurs actifs`, `99,94% Disponibilité`, `+42 NPS pilote` en `mobile`. Écris les tiens, ou
  assume ces valeurs-là.
- Avec plusieurs écrans et sans capture, chaque appareil reprend les mêmes lignes, décalées d’un rang : le
  deuxième commence par la deuxième valeur, le troisième par la troisième.
- Avec une capture, l’écran qui la porte ne lit plus `content2` ; les autres écrans gardent le faux écran.

## Dispositions

| `disposition` | Composition | La choisir quand |
| --- | --- | --- |
| `""` | Surtitre, titre et texte à gauche ; l’appareil à droite, sur un peu plus de la moitié. | Par défaut : le texte se lit d’abord, l’écran illustre. |
| `inverse` | L’appareil à gauche, le texte à droite. | L’écran est le sujet, ou la slide précédente finissait à droite. |
| `grand` | L’écran occupe les deux tiers, le texte se resserre à côté. **Opale seulement.** | Une interface dense qu’on veut vraiment voir — avec `"modele": "opale"`. |

```text
inverse : ┌────────────────────────┬─────────────────────────┐
          │   ┌────────────────┐   │ eyebrow                 │
          │   │     écran      │   │ title                   │
          │   └────────────────┘   │ chapeau + puces         │
          └────────────────────────┴─────────────────────────┘
```

```text
grand   : ┌──────────────┬───────────────────────────────────┐
          │ title court  │    ┌─────────────────────────┐    │
          │ chapeau      │    │          écran          │    │
          │              │    └─────────────────────────┘    │
          └──────────────┴───────────────────────────────────┘
```

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : `""` et
  `inverse` s’appliquent ; `grand` non, elle est réservée à Opale. L’appareil est noir, son écran prend le
  papier du thème, et l’accent colore la pastille de la barre, la ligne active de la navigation, le bouton.
- **Modèles complets** qui redessinent ce type (`compose`) : `opale` seulement. Le texte passe derrière la
  vitre dépolie et l’appareil se pose à cheval sur le bord du panneau ; il garde `inverse` et `grand`.
  Les autres modèles complets (`revue`, `chantier`, `marqueur`, `tampon`, `pastille`, `bloc`, `anneau`,
  `crayon`, `cimaise`, `aube`, `bdt`) habillent le rendu Libre avec leurs polices, leur accent et leurs
  repères, et gardent `inverse`.
- **Plateforme** (`"modele": "plateforme"`) : son propre gabarit — titre replié sur une colonne étroite
  (seize caractères par ligne : garde-le court), texte à gauche, appareil à droite, cadre noir, écran
  ivoire, accent rouge ; il garde
  `inverse`. Le bandeau du faux écran y porte « Plateforme », et non le titre de la présentation. Pas de
  pictogramme.

## Pièges

- Laisser `content2` vide en croyant que l’écran restera neutre : il affichera `812 Utilisateurs`,
  `99,9% SLA`, `+42 NPS` — ou `812 Utilisateurs actifs`, `99,94% Disponibilité`, `+42 NPS pilote` en
  `mobile` —, que le public prendra pour de vraies données.
- Une quatrième ligne dans `content2` ne s’affiche jamais ; en `bureau` et `tablette`, la troisième non
  plus. Valeur et libellé tiennent chacun sur une seule ligne, rognée par des points de suspension si elle
  dépasse : « 99,9 % » tient, « 99,9 % de disponibilité » est coupée — la suite va dans le libellé,
  lui-même limité à deux ou trois mots.
- `"ecrans": 3` avec `cadre: "portable"` ou `"bureau"` : ramené à 1 sans message. Et dès deux écrans, le
  texte n’a plus que 40 % de la largeur : titre et chapeau courts, deux ou trois puces.
- `"disposition": "grand"` sans `"modele": "opale"` : ignorée, la slide reprend « Texte à gauche ».
- Le bandeau du faux écran (`mobile`, `tablette`) reprend le titre de la présentation : un titre long y
  est rogné. Un `|` écrit dans un libellé de `content2` coupe la cellule et décale tout.
- Une adresse web dans `image` est refusée ; seule une donnée `data:image/…` est gardée. Sans fichier,
  laisse `image` vide et écris `Image à ajouter : …` dans `notes`.

## JSON

La disposition par défaut, un ordinateur portable et les chiffres du faux écran :

```json
{ "layout": "maquette", "eyebrow": "Outil de suivi", "title": "Chaque école suit sa consommation, mois après mois.", "content": "Un tableau de bord partagé entre la cellule d’ingénierie, les communes et les écoles.\n- Relevés des compteurs importés chaque nuit\n- Alerte dès qu’une école dérive\n- Comparaison avec les écoles de même taille", "content2": "70 | Écoles suivies\n−47 % | Consommation\n3 | Alertes ouvertes", "cadre": "portable", "notes": "Proposer la démonstration après la séance plutôt que pendant : la connexion de la salle est incertaine. Image à ajouter : la capture du tableau de bord, si on préfère le vrai écran." }
```

Un écran de bureau, posé à gauche, deux chiffres seulement :

```json
{ "layout": "maquette", "eyebrow": "Outil de suivi · Cellule d’ingénierie", "title": "La vue d’ensemble, pour arbitrer.", "content": "Pensée pour les quatre personnes qui suivent soixante-dix écoles à la fois.\n- Carte des chantiers et de leurs retards\n- Budget engagé par commune\n- Historique des interventions", "content2": "44 | Écoles engagées\n58 % | Budget engagé", "cadre": "bureau", "disposition": "inverse" }
```

Trois téléphones côte à côte : titre et chapeau resserrés.

```json
{ "layout": "maquette", "eyebrow": "Sur le chantier", "title": "Signaler, suivre, lever.", "content": "Une réserve se signale en moins d’une minute, photo comprise.\n- Fonctionne sans réseau\n- Suivi de la levée\n- Bilan de la semaine", "content2": "12 | Réserves ouvertes\n3 j | Délai de levée\n96 % | Réserves levées", "cadre": "mobile", "ecrans": 3, "notes": "Les mêmes chiffres, décalés d’un rang d’un écran à l’autre. Dire que les conducteurs de travaux s’en servent depuis mars, et que la levée des réserves a gagné une semaine." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
