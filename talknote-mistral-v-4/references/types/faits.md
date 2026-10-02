# `faits` · Faits

> Trois ou quatre réalisations, décisions ou constats, chacun sur sa carte numérotée d’office : une
> catégorie, un titre, une phrase de contexte, une étiquette.

## Quand l’employer

- **Dans la matière, tu as trouvé** : trois ou quatre réalisations achevées, chacune dans un domaine
  différent (usages, emploi, santé) ; les instances d’une gouvernance, avec ce que chacune décide ; des
  décisions de comité, chacune avec son effet ; des constats qualitatifs tirés d’un bilan — ce qui a
  changé, sans nombre pour le mesurer ; un « ce que cela change » en fin de partie.
- **Plutôt que** : `contenu` dès que les points partagent une structure (un domaine, un titre, une phrase)
  qu’une liste à puces aplatirait ; `chiffre` si c’est le nombre qui frappe et que le texte n’en est que la
  légende ; `colonnes` quand les blocs s’opposent deux à deux (avant et après, deux options) au lieu de
  s’additionner ; `etapes` quand l’ordre compte et que chaque point mène au suivant.
- **Pas pour** : plus de quatre cartes (scinde la slide, ou passe à `tableau`) ; un texte suivi coupé en
  morceaux — chaque carte doit se lire seule.

## Structure de l’information

```text
┌────────────────────────────────────────────────────────────┐
│ eyebrow                                                    │
│ title : ce que les cartes disent ensemble                  │
│                                                            │
│ ╭────────────────╮ ╭────────────────╮ ╭────────────────╮   │
│ │ [icône]        │ │ [icône]        │ │ [icône]        │   │
│ │ — 01 · CATÉG.  │ │ — 02 · CATÉG.  │ │ — 03 · CATÉG.  │   │
│ │ Titre de la    │ │ Titre de la    │ │ Titre de la    │   │
│ │ carte          │ │ carte          │ │ carte          │   │
│ │ Description    │ │ Description    │ │ Description    │   │
│ │ (Étiquette)    │ │ (Étiquette)    │ │ (Étiquette)    │   │
│ ╰────────────────╯ ╰────────────────╯ ╰────────────────╯   │
└────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
faits
├── title       : ce que les cartes disent ensemble, en une phrase (soixante caractères environ)
├── eyebrow     : repère court (« Bilan · Première année ») (facultatif)
├── content     : trois à quatre lignes « Catégorie | Titre | Description | Étiquette »
│     ├── Catégorie   : le domaine, un ou deux mots ; en petites capitales, après le numéro (facultatif)
│     ├── Titre       : l’idée de la carte, quatre à huit mots
│     ├── Description : une ou deux lignes de contexte (facultatif)
│     └── Étiquette   : un ou deux mots, en pastille au bas de la carte (facultatif)
├── disposition : `""` en ligne, `grille` deux par rangée
└── notes       : ce que le présentateur dit et qui n’est pas écrit
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `eyebrow` | Repère au-dessus du titre : « Bilan · Première année », « Gouvernance ». | Facultatif, deux ou trois mots. |
| `title` | Le message : ce que les cartes disent ensemble, pas « Nos réalisations ». | Soixante caractères environ ; au-delà de 64 il s’affiche plus petit. |
| `content` | Les cartes, une ligne chacune. | Obligatoire. Syntaxe ci-dessous ; trois à quatre lignes. |
| `disposition` | `""` (en ligne) ou `grille`. | Voir « Dispositions ». |
| `image` | Seulement avec le modèle `cimaise` : une photo haute posée au-dessus des cartes. | Laisse-la vide (voir `references/images.md`). |

Ce type n’emploie ni `content2`, ni `content3`, ni `author`. `progressive` reste sans effet : les cartes
entrent ensemble, décalées par l’animation. Les autres champs communs (`anim`, `transition`, `notes`) :
voir `references/format-json.md`.

## Syntaxe de `content`

Une ligne par carte, quatre cellules séparées par ` | `, dans cet ordre.

| Cellule | Écriture | Rendu |
| --- | --- | --- |
| Catégorie | `Horaires`, `Numérique` | Petites capitales en couleur d’accent, après le numéro : « — 01 · HORAIRES ». |
| Titre | `Ouvert le samedi après-midi` | L’idée de la carte, en gras et en grand. |
| Description | `Les trois sites ferment à 18 h.` | Une ou deux lignes en petit, sous le titre. |
| Étiquette | `Accueil` | Pastille cerclée, en capitales, au bas de la carte. |

- **Le numéro est posé par TalkNote** (`01`, `02`, `03`…), dans l’ordre des lignes : ne l’écris pas.
- Seules les deux premières cellules sont attendues. La catégorie peut être vide, avec sa barre :
  ` | Une carte unique sur le téléphone | Un seul compte pour les onze communes.` ; la description et
  l’étiquette peuvent simplement manquer. Une cinquième cellule est ignorée.
- `(nom)` en tête de la catégorie pose l’icône de la carte, au-dessus du numéro
  (`(horloge) Horaires | Ouvert le samedi après-midi | …`) ; un par ligne au plus, et seulement s’il aide
  à lire. Plusieurs modèles remplacent alors le numéro par cette icône. Noms : `references/pictogrammes.md`.
- `**gras**`, `==surligné==`, ` // ` : voir `references/format-json.md`.

**Une seule idée par carte.** La catégorie classe, le titre dit, la description explique en une ligne
(cent vingt caractères environ) : le reste va dans `notes`.

## Dispositions

| `disposition` | Composition | La choisir quand |
| --- | --- | --- |
| `""` | Les cartes côte à côte, hautes, une par réalisation. | Trois ou quatre cartes de même rang, lues d’un regard. |
| `grille` | Deux cartes par rangée, plus larges et moins hautes ; avec trois cartes, la troisième prend toute la largeur. | Des titres ou des descriptions longs, ou quatre cartes qu’on veut lire en deux paires. |

```text
┌────────────────────────────────────────────────────────────┐
│ title                                                      │
│ ╭───────────────────────────╮ ╭───────────────────────────╮│
│ │ — 01 · CATÉG.  Titre      │ │ — 02 · CATÉG.  Titre      ││
│ │ Description   (Étiquette) │ │ Description   (Étiquette) ││
│ ╰───────────────────────────╯ ╰───────────────────────────╯│
│ ╭─────────────────────────────────────────────────────────╮│
│ │ — 03 · CATÉG.  Titre · Description        (Étiquette)   ││
│ ╰─────────────────────────────────────────────────────────╯│
└────────────────────────────────────────────────────────────┘
```

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : tout s’applique.
- **Modèles complets** qui redessinent ce type (`compose`) : `chantier`, `pastille`, `bloc`, `anneau`,
  `cimaise`, `aube`, `opale`. Tous gardent `grille`, tous lisent les mêmes quatre cellules, et tous
  dessinent l’icône de la catégorie — sauf `opale` en `grille`, qui n’affiche ni icône ni numéro. Dans
  `pastille`, `anneau`, `bloc`, `cimaise`, `aube` et `opale`, **une ligne sans `|` ne fait pas une carte :
  elle forme le chapeau posé près du titre.**
  - `chantier` : des fiches bordées d’un filet épais en haut, coloré pour les deux premières ; l’icône, le
    numéro et la catégorie en tête, puis le titre, la description et l’étiquette.
  - `pastille` : des cartes à grand rayon, quatre couleurs tour à tour ; une pastille carrée porte l’icône,
    sinon le numéro ; la catégorie et l’étiquette se rejoignent en bas, jointes par « · ».
  - `bloc` : des tuiles sombres, la catégorie en étiquette en tête. Une ligne de deux cellules dont la
    première est courte (seize caractères au plus) et contient un chiffre devient une statistique posée
    sous les tuiles, quatre au plus.
  - `anneau` : des cartes en corail, ambre et céladon ; une puce ronde porte l’icône ou le numéro, la
    catégorie et l’étiquette à côté ; deux ou quatre cartes passent sur deux colonnes. La carte n’affiche
    que la deuxième cellule comme titre : écris-la toujours.
  - `cimaise` : les points clés sous une photo haute quand `image` est remplie ; l’icône, le titre, la
    catégorie dessous, la description, l’étiquette. Six cartes au plus.
  - `aube` : des cartes blanches, l’icône évidée en grand (sinon le numéro) ; six au plus. En `grille`,
    jusqu’à quatre cartes forment une mosaïque à côté du titre, la première en large si le compte est impair.
  - `opale` : quatre cartes au plus. Par défaut des cercles qui portent l’icône, sinon le numéro, le titre
    à gauche ; en `grille`, des colonnes où un filet sépare le titre de la description, sans icône ni
    numéro. L’étiquette n’y est pas dessinée : n’y mets rien d’indispensable.
  Les autres modèles complets (`revue`, `marqueur`, `tampon`, `crayon`, `bdt`) habillent le rendu Libre.
- **Plateforme** (`"modele": "plateforme"`) : des cartes blanches, « — 01 · CATÉGORIE », le titre, la
  description, l’étiquette en pastille ; `grille` s’applique, et la troisième carte y prend toute la
  largeur. Pas de pictogramme : le mot est retiré sans s’afficher.

## Pièges

- Le numéro est automatique : `1. Horaires | …` ou `01 | Horaires | …` ferait doublon.
- L’ordre des cellules se lit à l’envers de l’intuition : la catégorie d’abord, le titre ensuite.
  `Comité de pilotage | Pilotage | …` met « Comité de pilotage » en petites capitales et « Pilotage » en titre.
- Une ligne sans `|` ne donne pas la même chose partout : dans `pastille`, `anneau`, `bloc`, `cimaise`,
  `aube` et `opale` elle devient le chapeau ; partout ailleurs — en Libre, avec Plateforme, avec
  `chantier` et avec les modèles qui habillent le rendu Libre — elle fabrique une carte au titre vide.
  Décide laquelle des deux tu veux.
- Un `|` dans une phrase coupe la cellule : la description est tronquée et le reste part dans l’étiquette.
- Cinq cartes ou plus : en Libre elles s’étrécissent, `opale` n’en garde que quatre, `aube` et `cimaise` six.
  Trois ou quatre, pas plus ; au-delà, scinde la slide.
- L’étiquette est une pastille en capitales : un ou deux mots (« Décider », « Qualité de l’air »). Une
  phrase y déborde.
- Un mot très long dans une carte étroite fait baisser toute la rangée : préfère des mots courts. Et un
  titre neutre (« Nos réalisations ») ne dit rien : écris ce que les cartes montrent ensemble.

## JSON

Trois cartes en ligne, avec leurs icônes et leurs étiquettes :

```json
{ "layout": "faits", "eyebrow": "Bilan · Première année", "title": "Trois décisions qui ont changé le service.", "content": "(horloge) Horaires | Ouvert le samedi après-midi | Les trois médiathèques ferment à 18 h le samedi, au lieu de 12 h 30. | Accueil\n(mobile) Numérique | Une carte unique sur le téléphone | Un seul compte pour emprunter, réserver et prolonger dans les onze communes. | Simplifier\n(groupe) Publics | Deux médiateurs itinérants | Ils tiennent une permanence dans les quatre villages sans équipement. | Aller vers", "notes": "Les horaires du samedi sont l’engagement le plus visible : c’est celui que les élus citent en conseil. La carte unique a demandé dix-huit mois de convention entre les onze communes, ne pas s’étendre dessus ici." }
```

Quatre chantiers en grille, deux par rangée :

```json
{ "layout": "faits", "eyebrow": "Plan de sobriété", "title": "Quatre chantiers menés dans les bâtiments communaux.", "disposition": "grille", "content": "(thermomètre) Chauffage | Cent trente-quatre sondes posées | Chaque bâtiment est réglé à 19 °C, crèches et résidences autonomie exceptées. | Confort\n(soleil) Éclairage | Toutes les salles en LED | Les gymnases et les écoles ont été traités les premiers, avant les bureaux. | Travaux\n(feuille) Toitures | Huit toitures isolées | Deux écoles, un centre technique et cinq logements communaux. | Isolation\n(euro) Marchés | Un groupement d’achat d’énergie | Vingt-deux communes achètent ensemble depuis janvier. | Mutualiser", "notes": "Chiffres arrêtés au 30 juin. Le groupement d’achat est le seul chantier qui produira ses effets l’an prochain : le dire, sinon on l’attendra dès cet hiver." }
```

Trois constats sans catégorie ni étiquette : la première cellule reste vide, seule sa barre subsiste.

```json
{ "layout": "faits", "title": "Ce que les habitants nous ont dit en concertation.", "content": " | Les horaires comptent plus que les lieux | Quatre contributions sur dix demandent une ouverture en soirée plutôt qu’un guichet de plus.\n | Le téléphone reste la première porte | Une personne sur trois n’a pas de démarche en ligne aboutie sans appeler d’abord.\n | Les jeunes parlent d’abord de transport | Dans les ateliers en lycée, la mobilité arrive avant l’emploi et le logement.", "notes": "Concertation de mars à mai : 612 contributions en ligne, sept ateliers. Le troisième constat a surpris le comité de pilotage, prendre le temps de l’expliquer." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
