# `tableau` · Tableau

> Des données ligne à ligne, colonne par colonne, les statuts en pastilles de couleur : le détail précis
> qu’aucun graphique ne montrerait.

## Quand l’employer

- **Dans la matière, tu as trouvé** : un extrait de tableur, une annexe de rapport ; une liste d’objets qui
  portent tous les mêmes informations (un nom, une commune, un budget, un statut) ; un suivi d’actions avec
  leur état et leur échéance ; un plan de financement, une grille tarifaire, un comparatif d’offres ; un
  référentiel ou un cadre commun (finalité, méthode, exigences) — ce dernier appelle la disposition `cadre`.
- **Plutôt que** : `graph` si la question est une tendance ou une part, et que le lecteur doit retenir une
  forme plutôt que des nombres ; `portefeuille` si chaque sujet n’a qu’un nom et un état d’avancement ;
  `colonnes` si deux ou trois options s’opposent en texte, sans informations communes à aligner ; `kpi` si
  trois ou quatre indicateurs suivis suffisent, avec leur variation et un commentaire.
- **Pas pour** : trois nombres marquants (`chiffre`), l’état d’un programme à lire de loin (`dashboard`),
  une annexe de trente lignes (elle reste dans le document remis).

## Structure de l’information

```text
┌──────────────────────────────────────────────────────────────┐
│ eyebrow              ÉCOLE       COMMUNE   BUDGET   STATUT   │
│                      ─────────────────────────────────────   │
│ title : ce que le    Cellule     Cellule   Cellule   [Livré] │
│ tableau montre       Cellule     Cellule   Cellule   [Cours] │
│                      Cellule     Cellule   Cellule   [Retard]│
│ content : comment    Cellule     Cellule   Cellule   [Livré] │
└──────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
tableau
├── content2   : le tableau ; une ligne par rangée, cellules séparées par « | »
│     ├── 1re ligne : l’en-tête, un intitulé par colonne
│     ├── suivantes : les données ; « > » en tête met la rangée en avant
│     └── cellule   : un statut connu (« Livré », « En cours ») devient une pastille
├── title      : ce que le tableau montre, en une phrase (soixante caractères environ)
├── content    : une ou deux phrases qui disent comment le lire, ce qu’il ne montre pas
├── eyebrow    : repère court (« Détail · Vague 2026 », « Annexe 2 ») (facultatif)
└── notes      : les lignes à commenter, ce que le présentateur ajoute de vive voix
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `eyebrow` | Repère au-dessus du titre : « Détail · Vague 2026 », « Annexe 2 ». | Facultatif, deux ou trois mots. |
| `title` | Le message que le tableau démontre, pas son intitulé (« Les chantiers de l’été », non « Tableau de suivi »). | Soixante caractères environ ; au-delà de 64 il s’affiche plus petit. |
| `content` | L’introduction : la période, l’unité, ce qui est exclu du tableau. | Une ou deux phrases. Des puces `- ` sont possibles, elles apparaissent une à une. |
| `content2` | Le tableau lui-même. | Obligatoire, syntaxe ci-dessous ; vide, la slide s’ouvre quand même mais n’affiche que son texte, à côté d’un tableau sans une seule ligne. |
| `disposition` | `""`, `plein` ou `cadre`. | Voir ci-dessous. |

`content3`, `author` et `image` ne servent pas. Les champs communs (`anim`, `transition`, `notes`,
`progressive`) : voir `references/format-json.md`.

## Syntaxe de `content2`

Une ligne par rangée, les cellules séparées par `|`. **La première ligne est l’en-tête** : ne la fais jamais
commencer par `>`, le signe y resterait affiché.

```text
École | Commune | Budget | Statut
Groupe scolaire des Tilleuls | Montjoux | 2,4 M€ | Livré
> École Jules-Ferry | Vaux-le-Haut | 2,1 M€ | En retard
```

- **Statuts** : une cellule qui *commence* par un de ces mots devient une pastille, avec tout son texte
  (« En cours de validation » tient dans la pastille). Accents et majuscules sont indifférents.

  | Pastille | La cellule commence par | Sens |
  | --- | --- | --- |
  | Neutre | `Livré`, `Terminé`, `Réalisé`, `Déployé`, `Validé`, `En production`, `En prod`, `Fait`, `OK` | c’est fait |
  | Cernée d’accent | `En cours`, `En test`, `En progression`, `À venir`, `Planifié` | c’est engagé |
  | Pleine d’accent | `En retard`, `À risque`, `Bloqué`, `À cadrer`, `À faire`, `Abandonné` | c’est à surveiller |

- **`> ` en tête de la première cellule** d’une rangée de données : la rangée est mise en avant (un total,
  une projection). Le signe est toujours retiré ; il ne se **voit** qu’avec `bloc` (rangée peinte), `bdt`
  (rouge gras) et, en `cadre`, partout (cases cernées d’accent). Ailleurs, mets la rangée en `**gras**`.
- **Limites** : cinq colonnes et huit rangées de données au plus. Au-delà, scinde en deux slides ou résume.
- **Pictogramme** : `(nom)` en tête d’une cellule (`(école) Les Tilleuls`). Un seul par rangée suffit ; noms
  dans `references/pictogrammes.md`.
- `**gras**`, `*italique*`, `==surligné==` et ` // ` (deux lignes dans une case) : voir
  `references/format-json.md`. Le caractère `|` n’existe pas dans une phrase, il coupe la cellule.

## Dispositions

| `disposition` | Composition | La choisir quand |
| --- | --- | --- |
| `""` | Surtitre, titre et texte à gauche ; le tableau à droite, sur un peu moins des deux tiers. | Trois ou quatre colonnes, et un texte d’introduction qui compte. |
| `plein` | Titre à gauche, texte à droite ; le tableau dessous, sur toute la largeur et en plus gros. | Cinq colonnes, des cellules longues, un tableau qu’on vient vraiment lire. |
| `cadre` | Même en-tête, mais un tableau **sans ligne d’en-tête** : des cases encadrées, chaque rangée nommée par sa première cellule. | Un référentiel, une charte, un cadre commun : des rubriques, pas des données. |

```text
plein :  title .............   content .........................
         EN-TÊTE   EN-TÊTE   EN-TÊTE   EN-TÊTE   EN-TÊTE
         ───────────────────────────────────────────────────────
         Cellule   Cellule   Cellule   Cellule   Cellule
```

En `cadre`, une rangée plus courte que la plus longue étend sa dernière cellule jusqu’au bord ; une cellule
qui commence par un mot en gras pose ce mot en titre, la suite dessous. Six rangées, cinq colonnes au plus.

```text
cadre :  ┌───────────┬────────────┬────────────┬─────────────┐
         │ Finalité  │ Une phrase étendue jusqu’au bord      │
         ├───────────┼────────────┼────────────┼─────────────┤
         │ Exigences │ **Énergie**│ **Confort**│ **Chantier**│
         └───────────┴────────────┴────────────┴─────────────┘
```

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : les trois
  dispositions s’appliquent ; en-tête souligné d’un trait franc, filets fins, pastilles arrondies (au carré
  dans les mises en page).
- **Modèles complets qui redessinent ce type** (`compose`) : `bloc` et `bdt`.
  - `bloc` garde `cadre` et ignore `plein` (son tableau occupe déjà toute la largeur sous le titre) :
    bandeau d’en-tête noir en capitales, une rangée sur deux teintée, statut marqué d’un carré — plein pour
    ce qui est fait, khaki pour ce qui est engagé, évidé pour ce qui est à surveiller —, rangée `>` peinte
    en khaki, colonne entièrement chiffrée alignée à droite, tout resserré au-delà de six rangées.
  - `bdt` garde `plein` et `cadre` : cases grises séparées de blanc, en-tête en capitales, statuts colorés
    sans pastille, rangée `>` en rouge gras ; le `content` y devient une légende, à droite du tableau ou
    au-dessus en `plein` et en `cadre`.
  - Les autres modèles complets (`revue`, `chantier`, `marqueur`, `tampon`, `pastille`, `anneau`, `crayon`,
    `cimaise`, `aube`, `opale`) habillent le rendu Libre : les trois dispositions s’appliquent. `opale` pose
    les pastilles en verre et arrondit la première case d’un `cadre`.
- **Plateforme** (`"modele": "plateforme"`) : son propre gabarit — titre replié sur une colonne étroite
  (quatorze caractères par ligne : garde-le court ; en `plein` et en `cadre` il reprend toute la largeur,
  sous le surtitre), texte dessous, tableau à droite, pastilles vertes,
  orange et rouges ; il garde `plein` et `cadre` (cases centrées, rangée `>` barrée de rouge). Pas de
  pictogramme : le mot entre parenthèses est retiré sans s’afficher.

## Pièges

- Un `|` écrit dans une phrase (« énergie | eau ») coupe la cellule en deux et décale toute la rangée.
- Le `>` posé sur la première ligne : elle est l’en-tête, le signe y reste affiché. Et compter sur le `>`
  en thème Libre : dans un tableau ordinaire il ne se voit pas, le `**gras**` se voit partout.
- Une cellule ordinaire qui commence par un mot de statut devient une pastille sans qu’on l’ait voulu
  (« Faits marquants » commence par `Fait`) ; à l’inverse, un pictogramme devant un statut
  (`(validé) Livré`) annule la pastille.
- Une cellule qui commence par `- `, `* `, `• ` ou `1. ` suivi d’un mot devient une puce ou un numéro dans
  sa case ; un tiret suivi d’un nombre (`- 2 j`) et un tiret seul restent du texte. Pour une valeur absente,
  `—` reste plus lisible que `-`.
- Plus de cinq colonnes ou plus de huit rangées : illisible en projection. En `cadre`, la colonne des
  intitulés prend un peu plus d’un cinquième de la largeur et les autres se partagent le reste à parts
  égales, garde donc des cellules de longueur comparable — et sa première cellule est un intitulé, ni
  `**gras**` en titre ni pastille ne s’y appliquent.
- `content2` vide : rien n’est refusé, la slide s’affiche avec son seul texte et un tableau sans une seule
  ligne. Le tableau ne se met pas dans `content`.

## JSON

La disposition par défaut, quatre colonnes et des statuts :

```json
{ "layout": "tableau", "eyebrow": "Détail · Vague 2026", "title": "Les chantiers de l’été, école par école.", "content": "Quatorze écoles programmées ; les cinq plus importantes sont détaillées ici.", "content2": "École | Commune | Budget | Statut\nGroupe scolaire des Tilleuls | Montjoux | 2,4 M€ | Livré\nÉcole des Tanneurs | Lurcy | 1,7 M€ | En cours\nÉcole Jules-Ferry | Vaux-le-Haut | 2,1 M€ | En retard\nÉcole du Pré-Vert | Castelvieil | 0,9 M€ | Livré\nÉcole Paul-Bert | La Vergne | 1,0 M€ | Livré", "notes": "Les Tanneurs et Jules-Ferry sont détaillés en partie 04 : le retard vient du diagnostic amiante." }
```

Cinq colonnes et un total : `plein`, et la rangée de total en gras plutôt qu’en `>` :

```json
{ "layout": "tableau", "eyebrow": "Annexe 2", "title": "Le plan de financement, financeur par financeur.", "content": "En millions d’euros. Les montants 2027 sont prévisionnels.", "content2": "Financeur | 2025 | 2026 | 2027 | Total\nÉtat | 2,1 | 2,6 | 3,4 | 8,1\nRégion | 1,4 | 1,7 | 2,2 | 5,3\nDépartement | 0,6 | 0,8 | 1,0 | 2,4\nCommunes | 1,9 | 2,3 | 3,0 | 7,2\n**Total** | **6,0** | **7,4** | **9,6** | **23,0**", "disposition": "plein", "notes": "Les montants 2027 seront arrêtés au comité de mars ; le détail par commune est en annexe 3." }
```

Un cadre de référence : `cadre`, une rangée courte étendue jusqu’au bord, des mots en gras en titres de case
et la dernière rangée mise en avant :

```json
{ "layout": "tableau", "eyebrow": "Référentiel", "title": "Le cadre commun à tous les chantiers.", "content": "Voté par les quarante-deux communes, révisé en mars 2026.", "content2": "Finalité | Des écoles sobres, fraîches l’été et agréables toute l’année.\nMéthode | Un diagnostic partagé, puis des marchés groupés par vague d’été.\nExigences | **Énergie** −40 % de consommation au moins. | **Confort** 26 °C au plus en classe. | **Chantier** L’été, sans fermer l’école.\n> Révision | À rouvrir en comité, au plus tard en mars 2027.", "disposition": "cadre" }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
