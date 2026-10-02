# `chiffre` · Chiffres clés

> Un à quatre nombres écrits en très grand, chacun avec son libellé et sa ligne de contexte : peu de texte
> autour, le chiffre parle seul.

## Quand l’employer

- **Dans la matière, tu as trouvé** : un à quatre nombres qui portent à eux seuls le message (« 70 écoles »,
  « 38 M€ », « 2028 ») ; un encadré « en chiffres » dans un rapport ou une plaquette ; un ordre de grandeur
  qui surprend ; un résultat unique à faire résonner après une démonstration ; une date-butoir isolée.
- **Plutôt que** : `kpi` dès que chaque nombre a une évolution à montrer (une variation, un écart à
  l’objectif, un commentaire de suivi) ; `graph` au-delà de quatre valeurs, ou quand ce sont la comparaison,
  la répartition ou la tendance qui comptent plus que les nombres eux-mêmes ; `faits` quand ce sont des
  réalisations ou des décisions, avec un nombre au mieux accessoire.
- **Pas pour** : des nombres à comparer entre eux (c’est un graphique) ; un chiffre déjà cité dans le texte
  d’avant, qu’une slide entière ne ferait que redire.

## Structure de l’information

```text
┌────────────────────────────────────────────────────────────┐
│ eyebrow                                                    │
│ title : ce que ces chiffres disent ensemble                │
│                                                            │
│   70            │ 42            │ 38 M€                    │
│   Valeur        │ Valeur        │ Valeur                   │
│   Titre         │ Titre         │ Titre                    │
│   Description   │ Description   │ Description              │
└────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
chiffre
├── content     : une à quatre lignes « Valeur | Titre | Description »
│     ├── Valeur      : le nombre d’abord, l’unité ensuite (« 38 M€ ») ; écrit en très grand
│     ├── Titre       : ce que le nombre compte, deux à quatre mots
│     └── Description : une ligne de contexte, en gris (facultatif)
├── title       : ce que ces chiffres disent ensemble (facultatif)
├── eyebrow     : repère court (« Le programme en chiffres ») (facultatif)
├── disposition : `""` en ligne, `grille` deux par rangée, `vedette` le premier en très grand
└── notes       : ce que le présentateur dit et qui n’est pas écrit
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `content` | Les chiffres, une ligne chacun. | Obligatoire. Syntaxe ci-dessous ; un à quatre. |
| `title` | Le message : ce que ces chiffres disent ensemble, pas « Chiffres clés ». | Facultatif. Soixante caractères environ ; au-delà de 64 caractères il s’affiche plus petit. |
| `eyebrow` | Repère au-dessus du titre : « Le programme en chiffres », « Consommation d’énergie ». | Facultatif, deux ou trois mots. |
| `disposition` | `""` (en ligne), `grille` ou `vedette`. | Voir « Dispositions ». |

Ce type n’emploie ni `content2`, ni `content3`, ni `author`, ni `image`. `progressive` reste sans effet : les
chiffres entrent ensemble, décalés par l’animation. Les autres champs communs (`anim`, `transition`,
`notes`) : voir `references/format-json.md`.

## Syntaxe de `content`

Une ligne par chiffre, trois cellules séparées par ` | `, dans cet ordre.

| Cellule | Écriture | Rendu |
| --- | --- | --- |
| Valeur | `70`, `38 M€`, `−47 %`, `4,2 M€`, `2028` | Le nombre en très grand, à la couleur d’accent ; ce qui suit le dernier chiffre (l’unité) se détache, plus petit. |
| Titre | `écoles concernées` | Sous la valeur, en gras : ce que le nombre compte. |
| Description | `Toutes les écoles primaires publiques.` | Une ligne en petit et en gris, sous le titre (facultatif). |

- Les deux premières cellules sont attendues : **écris toujours au moins `Valeur | Titre`**, même pour un
  chiffre unique. Seule la description peut manquer.
- La valeur commence par le nombre : un signe éventuel (`+`, `−`), les chiffres avec leurs espaces, virgules
  ou points, puis l’unité (`%`, `M€`, `min`, `€/m²`, `/10`). Une valeur qui ne commence pas par un chiffre
  (`Top 10`, `n. c.`) s’affiche entière, sans unité détachée.
- Un à quatre chiffres. Au-delà, les cases s’étrécissent et la plupart des modèles n’en dessinent que quatre.
- `(nom)` en tête du titre pose une petite icône devant lui (`70 | (école) écoles concernées | …`) ; une par
  ligne au plus, seulement si elle aide à lire. Noms : `references/pictogrammes.md`.
- `**gras**`, `==surligné==`, ` // ` : voir `references/format-json.md`.

**Un chiffre, une idée.** La valeur frappe, le titre dit ce qu’elle compte, la description donne la source,
le périmètre ou la période en une ligne (soixante caractères environ).

## Dispositions

| `disposition` | Composition | La choisir quand |
| --- | --- | --- |
| `""` | Les chiffres côte à côte, séparés par un filet fin ; à trois puis à quatre, les nombres perdent de la taille. | Deux à quatre chiffres de même rang, lus d’un regard. |
| `grille` | Deux par rangée : à trois ou quatre chiffres, les nombres reprennent de la taille. À trois, le troisième reste sur la moitié gauche de la seconde rangée. À deux, le rendu ne change presque pas. | Des titres ou des descriptions longs, des valeurs larges (`1 120 €/m²`), ou quatre chiffres qu’on veut lire en deux paires. |
| `vedette` | Le premier chiffre sur toute la largeur, en très grand ; les autres en dessous, sur une rangée de trois colonnes. | Un chiffre commande et les autres l’éclairent : trois ou quatre chiffres. |

```text
grille                             vedette
┌──────────────────────────┐       ┌──────────────────────────┐
│  70          │ 42        │       │  4,2 M€                  │
│  Titre       │ Titre     │       │  Titre · Description     │
│              │           │       │                          │
│  38 M€       │           │       │ +1 an  │ 3     │ 12      │
│  Titre       │           │       │ Titre  │ Titre │ Titre   │
└──────────────────────────┘       └──────────────────────────┘
```

Un chiffre seul se dessine toujours ainsi, quelle que soit la disposition : le nombre au plus grand, son
titre dessous, puis sa description.

```text
┌────────────────────────────────────────────────────────────┐
│ eyebrow                                                    │
│ title (s’il y en a un)                                     │
│                                                            │
│   −47 %                                                    │
│   Titre                                                    │
│   Description                                              │
└────────────────────────────────────────────────────────────┘
```

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : tout s’applique.
- **Modèles complets** : tous redessinent ce type (`compose`), sauf `tampon`, qui habille le rendu Libre.
  Tous gardent `grille` et `vedette`, et lisent les mêmes trois cellules :
  - `anneau` : une valeur en pourcentage de 0 à 100 devient un anneau rempli d’autant, la valeur au centre ;
    les autres restent des chiffres. Corail, ambre puis céladon, quatre au plus.
  - `pastille` : valeur et titre dans une pastille de couleur, la description renvoyée en note sur la
    colonne de droite.
  - `aube` : le titre passe au-dessus de la valeur, en étiquette, et la première carte prend le dégradé.
  - `bdt` : une ligne par chiffre — le titre à gauche, des points de conduite, la valeur, la description ;
    six lignes au plus, et une ligne sans `|` devient la légende posée à droite.
  - `revue` (vignettes), `chantier` (une rangée de colonnes en bas de slide), `marqueur` (encadrés d’un
    filet), `bloc` (dernier chiffre en khaki), `crayon` (premier et dernier à l’encre), `cimaise` (premier
    en corail) et `opale` (cartes de verre dépoli) gardent l’ordre valeur, titre, description.
- **Plateforme** (`"modele": "plateforme"`) : des cases séparées par un filet, la valeur en très gras et
  l’unité plus petite. `grille` et `vedette` s’appliquent, et en `vedette` la rangée du bas s’ajuste au
  nombre de chiffres restants. Pas de pictogramme : le mot est retiré sans s’afficher.

## Pièges

- **Une ligne sans `|` parmi des lignes qui en ont** devient un chiffre à part entière : toute la ligne
  s’écrit à la place du nombre, en très grand. Chaque ligne porte au moins `Valeur | Titre`.
- **Aucun `|` dans tout le `content`** : il n’y a plus de chiffre du tout — en Libre la slide montre un
  « 42 » en gris pâle, ailleurs la zone reste vide — sauf si le `title` fait douze caractères au plus et
  contient un chiffre : il devient alors le grand nombre, la première ligne son titre, le reste sa
  description, et il disparaît comme titre. Garde toujours `Valeur | Titre`.
- **L’ordre est l’inverse de `kpi`** : ici la valeur d’abord (`70 | écoles`), là le libellé
  (`Rendement | 84,2 %`).
- Un pictogramme en tête de la **valeur** empêche l’unité de se détacher (`(école) 70 %` s’écrit en
  entier, parenthèses comprises si le nom est inconnu) : à un seul chiffre le nombre chute de taille, à
  plusieurs il déborde de sa case. Pose-le sur le titre.
- Une valeur qui ne commence pas par un chiffre (`Top 10`) s’écrit entière à la place du nombre ; une valeur
  longue (`12 450 000 €`) le fait chuter de taille : écris `12,45 M€`.
- `grille` et `vedette` ne changent rien à un chiffre seul ; en `vedette` à deux chiffres, le second
  n’occupe qu’un tiers de la largeur en Libre.

## JSON

Quatre chiffres en ligne, un réseau de lecture publique :

```json
{ "layout": "chiffre", "eyebrow": "Le réseau en chiffres", "title": "Douze bibliothèques, un seul catalogue.", "content": "12 | bibliothèques | Réunies dans le réseau depuis janvier 2026.\n180 000 | documents | Un catalogue commun, empruntable dans toutes les communes.\n1,9 M€ | de budget annuel | Dont 22 % consacrés aux acquisitions.\n2028 | fin du déploiement | Dernière commune raccordée au portail.", "notes": "Les 180 000 documents sont le catalogue après dédoublonnage ; le chiffre brut du rapport, 214 000, compte deux fois les fonds partagés. Insister sur « empruntable dans toutes les communes » : c’est la nouveauté pour les usagers." }
```

Un seul chiffre, sans titre, en `zoom` : il occupe la slide et laisse une pause au présentateur.

```json
{ "layout": "chiffre", "eyebrow": "Consommation d’énergie", "content": "−47 % | sur les douze écoles rénovées | Une année scolaire complète, à climat corrigé, pour un objectif fixé à −38 %.", "anim": "zoom", "notes": "Marquer une pause avant de commenter. Le chiffre vient du relevé des compteurs, pas de l’estimation du bureau d’études : le dire si la question vient." }
```

Trois chiffres en `vedette` : le besoin de financement commande, les deux autres l’éclairent.

```json
{ "layout": "chiffre", "eyebrow": "L’écart à combler", "title": "Le plan de financement n’est pas bouclé.", "disposition": "vedette", "content": "4,2 M€ | de besoin de financement | Écart entre le coût révisé des travaux et les subventions notifiées.\n+1 an | de décalage possible | Si le programme est tenu sans recourir à l’emprunt.\n3 | pistes ouvertes | Emprunt, phasage, révision du programme." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
