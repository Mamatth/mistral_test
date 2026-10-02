# `dashboard` · Tableau de bord

> Deux à quatre graphiques, chacun dans sa carte, sans texte d’analyse : l’état d’un programme d’un
> coup d’œil.

## Quand l’employer

- **Dans la matière, tu as trouvé** : un point d’avancement qui mêle plusieurs mesures de nature différente
  (un volume livré, un budget engagé, un calendrier) ; un comité de pilotage où trois chiffres reviennent à
  chaque séance, chacun avec sa cible ; un « où en est-on ? » qui demande deux ou trois angles à la fois ;
  des tableaux de suivi qu’on lit ensemble, pas l’un après l’autre.
- **Plutôt que** : `graph` quand une seule question est posée et qu’il faut l’analyser — le texte y tient la
  moitié gauche de la slide, et il accepte aussi jusqu’à quatre graphiques ; `kpi` quand les mesures sont
  des nombres avec leur variation, pas des figures (quatre cartes chiffrées se lisent plus vite que quatre
  dessins) ; `chiffre` quand deux ou trois nombres doivent frapper, sans progression ni répartition à
  montrer.
- **Pas pour** : un seul graphique (c’est `graph`) ; un tableau de valeurs ligne à ligne (c’est `tableau`) ;
  une démonstration qui a besoin de phrases, puisque ce type n’affiche aucun texte courant.

## Structure de l’information

```text
┌────────────────────────────────────────────────────────────┐
│ eyebrow                                                    │
│ title : l’état du programme, en une phrase                 │
│                                                            │
│ ╭──────────────╮ ╭──────────────╮ ╭──────────────╮         │
│ │ Titre        │ │ Titre        │ │ Titre        │         │
│ │ sous-titre   │ │ sous-titre   │ │ sous-titre   │         │
│ │    ◍ ◍       │ │    ▮▮▮       │ │   ▁▄▆█       │         │
│ │ Légende      │ │              │ │ Légende      │         │
│ ╰──────────────╯ ╰──────────────╯ ╰──────────────╯         │
└────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
dashboard
├── content2   : deux à quatre graphiques, séparés par une ligne vide
│     ├── type :        le format du graphique — première ligne de chaque bloc
│     ├── titre :       le nom de l’indicateur, posé sur la carte
│     ├── sous-titre :  l’unité, la période, la source (facultatif)
│     └── Nom : valeurs une ligne par série
├── title      : ce que les graphiques disent ensemble (soixante caractères environ)
├── eyebrow    : repère de pilotage (« Pilotage · Septembre 2026 ») (facultatif)
├── agencement : `""`, `ligne`, `colonne` ou `grille`
└── notes      : par où commencer la lecture, ce que les chiffres ne disent pas
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `content2` | Les graphiques eux-mêmes. | Obligatoire. Deux à quatre, séparés par une ligne vide ; au-delà de quatre, les suivants sont abandonnés. |
| `title` | Le message : ce que le tableau de bord montre, pas « Tableau de bord ». | Soixante caractères environ ; au-delà de 64 il s’affiche plus petit. |
| `eyebrow` | Repère au-dessus du titre : « Pilotage · Septembre 2026 », « Comité de suivi · T3 ». | Facultatif, deux ou trois mots. |
| `agencement` | La forme de la grille de cartes. | `""` (défaut), `ligne`, `colonne` ou `grille`. |

`content` et `author` ne sont pas employés par ce type. Les champs communs (`anim`, `transition`, `notes`) :
voir `references/format-json.md`.

## Syntaxe de `content2`

Un bloc par graphique, **séparés par une ligne vide** (`\n\n` dans le JSON). Chaque bloc commence par sa
ligne `type :`, puis ses réglages, puis ses séries — une ligne par série, `Nom : valeurs`.

```text
type : anneaux
titre : Pistes livrées
centre : km
Livrés : 42 / 120
En travaux : 31 / 120
```

- La syntaxe complète des graphiques (les onze `type`, les réglages `axe`, `unité`, `max`, `centre`,
  `crans`, `options`, l’écriture des nombres) est dans `references/graphiques.md`. Ici, seules deux règles
  changent : il en faut **deux au moins**, et **chaque bloc porte sa ligne `type :`**.
- Préfère les formats compacts, qui restent lisibles dans un quart de slide : `anneaux`, `jauge`,
  `secteurs`, `progression`, `entonnoir`, et des `barres` à trois ou quatre catégories. Garde `courbe` et
  `radar` pour un tableau de bord de deux cartes.
- Les titres courts valent mieux : `titre : Budget engagé` plutôt qu’une phrase. `titre :` et
  `sous-titre :` acceptent `**gras**`, `==surligné==` et un pictogramme `(nom)` en tête ; les noms de série
  s’affichent tels quels dans la légende.
- Un pictogramme `(nom)` en tête du `title` ou de l’`eyebrow` de la slide est dessiné devant le texte.
  Noms : `references/pictogrammes.md`.

## Agencement

Ce type n’a pas de disposition : c’est `agencement` qui compose les cartes.

| `agencement` | Composition | La choisir quand |
| --- | --- | --- |
| `""` | Le défaut : en ligne jusqu’à trois graphiques, en grille à quatre. | Presque toujours. |
| `ligne` | Toutes les cartes côte à côte, même à quatre. | Quatre figures très compactes (jauges, anneaux) qu’on veut lire d’un seul balayage. |
| `colonne` | Les cartes empilées, chacune large et basse ; le titre et la légende passent à gauche du tracé, qui est aplati pour remplir la largeur. | Des `barres` horizontales, une `progression` ou un `entonnoir`, qui gagnent à être larges. |
| `grille` | Deux cartes par rangée ; à trois, la troisième prend toute la largeur. Avec deux graphiques, revient à `ligne`. | Trois ou quatre graphiques carrés (anneaux, secteurs, radar). |

```text
colonne (deux cartes)                grille (trois cartes)
┌────────────────────────────────┐   ┌─────────────┐ ┌─────────────┐
│ Titre    ▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄   │   │  graphique  │ │  graphique  │
│ Légende  ▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄     │   └─────────────┘ └─────────────┘
└────────────────────────────────┘   ┌─────────────────────────────┐
┌────────────────────────────────┐   │          graphique          │
│ Titre    ▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄   │   └─────────────────────────────┘
└────────────────────────────────┘   à quatre : deux rangées de deux
```

## Selon le modèle

- **Libre** (`"modele": ""`) : tout s’applique. Les cartes prennent le fond et le filet du thème, les
  graphiques sa palette. Ses mises en page (`cadran`, `marge`, `palier`, `grille`) gardent les quatre
  agencements, mais leurs cartes perdent fond et arrondi : il ne reste qu’un filet, et le décor du modèle
  (chiffre géant, gouttière, trame) se pose autour.
- **Modèles complets** : aucun ne redessine ce type. `revue`, `chantier`, `marqueur`, `tampon`, `pastille`,
  `bloc`, `anneau`, `crayon`, `cimaise`, `aube`, `opale` et `bdt` habillent le rendu Libre — leur palette de
  graphiques, leur typographie, leurs cartes — et gardent les quatre agencements.
- **Plateforme** (`"modele": "plateforme"`) : le modèle compose lui-même le tableau de bord, cartes blanches
  et graphiques aux couleurs de la charte, surtitre et titre en tête. Les quatre agencements s’appliquent.
  Le titre y est plus court : environ vingt-deux caractères par ligne, trente-deux quand quatre graphiques
  passent en grille. Pas de pictogramme : le mot entre parenthèses est retiré sans s’afficher.

## Pièges

- **La ligne vide sépare deux graphiques.** Une ligne vide oubliée au milieu d’un bloc le coupe en deux, et
  le morceau orphelin, privé de `type :`, devient un histogramme sans axe. Contrairement à `graph`, un bloc
  sans `type :` ne continue pas le précédent : n’écris aucune ligne vide à l’intérieur d’un graphique.
- `content` n’est jamais affiché ici. Si l’analyse compte autant que les figures, prends `graph` : il pose le
  texte à gauche et accepte lui aussi jusqu’à quatre graphiques. Sinon, mets la lecture dans `notes`.
- Un seul graphique lisible : la slide le dessine seul, mais c’est `graph` qu’il fallait. Aucun graphique
  lisible : la slide n’affiche qu’un message d’aide.
- Au-delà de quatre blocs, les suivants sont abandonnés sans rien dire. Scinde en deux tableaux de bord.
- Quatre figures denses (courbe à huit points, radar, barres empilées à quatre séries) deviennent illisibles
  dans un quart de slide. À quatre cartes, ne garde que des formats compacts.
- `agencement: "grille"` avec deux graphiques donne une ligne : la grille ne commence qu’à trois.
- Pas d’unité dans les valeurs (`58` et `unité : %`, jamais `58 %`), et une série a autant de valeurs que
  l’axe a de libellés : voir `references/graphiques.md`.

## JSON

Trois graphiques, l’agencement par défaut : en ligne.

```json
{ "layout": "dashboard", "eyebrow": "Pilotage · Septembre 2026", "title": "Le plan vélo, trois mesures suivies chaque trimestre.", "content2": "type : anneaux\ntitre : Pistes livrées\ncentre : km\nLivrés : 42 / 120\nEn travaux : 31 / 120\n\ntype : jauge\ntitre : Budget engagé\nsous-titre : Sur 18 M€ votés\nunité : %\nEngagé : 64 / 100\n\ntype : barres\ntitre : Kilomètres par an\naxe : 2024, 2025, 2026\nPrévus : 28, 34, 40\nLivrés : 28, 14, 0", "notes": "Commencer par l’anneau : 42 km livrés sur 120. Les 14 km de 2025 s’expliquent par le report du pont de la Loire, arbitré en juin." }
```

Deux graphiques larges et bas, empilés : `agencement` en `colonne`.

```json
{ "layout": "dashboard", "eyebrow": "Restauration scolaire", "title": "Le bio progresse, mais pas au même rythme partout.", "content2": "type : progression\ntitre : Part du bio par cantine\nsous-titre : En pourcentage des repas servis\nunité : %\nCentre-ville : 62\nLes Coteaux : 48\nLa Prairie : 35\n\ntype : entonnoir\ntitre : Des marchés aux assiettes\nunité : repas par jour\nRepas commandés : 2400\nRepas servis : 2180\nRepas bio : 1050", "agencement": "colonne", "notes": "L’écart entre les trois cantines tient aux cuisines : La Prairie est en liaison froide. Le marché de 2027 doit le corriger." }
```

Quatre graphiques : le tableau de bord passe en grille, deux par rangée.

```json
{ "layout": "dashboard", "eyebrow": "Guichet numérique · Bilan 2026", "title": "Le service en ligne tient ses promesses.", "content2": "type : anneaux\ntitre : Communes raccordées\ncentre : Communes\nRaccordées : 38 / 52\nEn test : 9 / 52\n\ntype : jauge\ntitre : Demandes traitées sous dix jours\ncentre : 78 % en 2025\nunité : %\nTraitées : 86 / 100\n\ntype : courbe\ntitre : Demandes déposées en ligne\nsous-titre : Par trimestre\naxe : T1, T2, T3, T4\n2025 : 1240, 1380, 1410, 1620\n2026 : 1590, 1810, 2040, 2210\n\ntype : secteurs\ntitre : Origine des demandes\ncentre : 2026\nSite de la collectivité : 54\nFrance Connect : 31\nAccueil accompagné : 15", "notes": "Les 9 communes en test basculent en janvier. L’accueil accompagné reste ouvert : c’est l’engagement pris devant le conseil." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
