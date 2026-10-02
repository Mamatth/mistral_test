# `graph` · Graphique

> Une analyse d’un côté, un graphique dessiné à partir de tes données de l’autre : la slide qui montre
> une tendance, une répartition ou une comparaison chiffrée.

## Quand l’employer

- **Dans la matière, tu as trouvé** : une suite de nombres relevés dans le temps (cinq années de
  consommation) ; une répartition en parts d’un tout (un budget par poste) ; une comparaison chiffrée
  entre deux ou trois groupes sur les mêmes critères ; des effectifs qui se réduisent d’étape en étape ;
  une perception mesurée entre deux mots opposés ; deux ou trois ensembles dont le croisement compte.
- **Plutôt que** : `chiffre` quand un à quatre nombres suffisent à frapper et que la forme du tracé
  n’ajoute rien ; `kpi` pour trois ou quatre indicateurs suivis, chacun avec sa variation et son
  commentaire ; `dashboard` quand il n’y a plus d’analyse à écrire à côté et que deux à quatre graphiques
  donnent l’état d’un programme ; `tableau` quand ce sont les valeurs exactes qui comptent.
- **Pas pour** : une frise de dates (`jalons`), un calendrier de chantiers (`roadmap`), un schéma
  d’organisation ; ni pour une image de graphique déjà rendue, qui relève de `media`.

## Structure de l’information

```text
┌──────────────────────────────────────────────────────────┐
│ eyebrow                                                  │
│ title : le message que porte le graphique                │
│                                                          │
│ content : l’analyse,      ┌───────────────────────────┐  │
│ deux ou trois phrases,    │ titre du graphique        │  │
│ puis une ou deux puces    │ sous-titre                │  │
│                           │  ·__                      │  │
│                           │      ‾‾·__   ‾‾·          │  │
│                           │ 2023  2024  2025  2026    │  │
│                           └───────────────────────────┘  │
└──────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
graph
├── title       : le message que porte le graphique (soixante caractères environ)
├── content2    : un à quatre graphiques, séparés par une ligne vide
│     ├── type :        : la sorte de graphique, en tête de chacun (obligatoire)
│     └── réglages et séries : voir `references/graphiques.md`
├── content     : l’analyse — deux ou trois phrases, ou quelques puces
├── eyebrow     : repère court, « Énergie · 2022 → 2026 » (facultatif)
├── disposition : `""` texte à gauche, `inverse`, `large`
├── agencement  : dès deux graphiques, `ligne`, `colonne` ou `grille`
└── notes       : ce que le présentateur dit et qui n’est pas écrit
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `content2` | Le ou les graphiques. | Obligatoire. Un à quatre, séparés par une ligne vide ; au-delà, les suivants sont abandonnés. |
| `title` | Le message que le graphique démontre, pas l’intitulé du graphique (celui-ci va dans `titre :`). | Soixante caractères environ ; au-delà de 64, il s’affiche plus petit. |
| `content` | L’analyse : ce qu’il faut lire dans le tracé, et ce qu’on en conclut. | Deux ou trois phrases, ou deux à quatre puces. Le détail va dans `notes`. |
| `eyebrow` | Repère au-dessus du titre : le domaine, la période, la source. | Facultatif, deux ou trois mots. |
| `disposition` | `""`, `inverse` ou `large`. | Voir « Dispositions ». |
| `agencement` | La forme de la grille, dès deux graphiques. | `""` (défaut), `ligne`, `colonne` ou `grille`. |

`content3` et `author` ne sont pas employés par ce type. Les champs communs (`anim`, `transition`,
`notes`, `progressive`) : voir `references/format-json.md`.

## Syntaxe de `content` et de `content2`

`content` est du texte courant : un paragraphe par ligne, `- ` pour une puce, `# ` pour un intertitre,
`(nom) ` pour un pictogramme, `**gras**` et `==surligné==` — voir `references/format-json.md`.

`content2` décrit le ou les graphiques : une ligne par réglage `clé : valeur`, puis une ligne par série
`Nom : valeurs`. La syntaxe complète — les onze `type`, les réglages, l’écriture des nombres — est dans
`references/graphiques.md`. Seul `type :` est obligatoire, en tête de chaque graphique ; `barres`, `courbe`
et `radar` demandent en plus une ligne `axe :`, et chaque série y a autant de valeurs que l’axe a de
libellés.

**Plusieurs graphiques.** Jusqu’à quatre, séparés par une ligne vide, chacun ouvert par sa ligne `type :`.
Leur rangement vient d’`agencement` : `ligne` côte à côte, `colonne` l’un sur l’autre, `grille` deux par
rangée (à deux graphiques, `grille` revient à `ligne`). Sans `agencement`, à côté du texte, deux
graphiques se superposent et trois ou quatre se rangent en grille ; là où le modèle les pose sur toute la
largeur (Bloc, Crayon, Plateforme ; Anneau et Pastille sans chiffres), ils vont en ligne jusqu’à trois,
puis en grille.

## Dispositions

| `disposition` | Composition | La choisir quand |
| --- | --- | --- |
| `""` | L’analyse à gauche, le graphique à droite, un peu plus large. | Le cas courant : un tracé à commenter en deux ou trois phrases. |
| `inverse` | Le graphique à gauche, l’analyse à droite. | Le tracé enchaîne avec la slide précédente, ou l’analyse se lit après coup. |
| `large` | Le graphique prend les deux tiers ; le titre et l’analyse sont dessinés plus petits. | Un tracé dense : beaucoup de libellés, des barres horizontales, une intersection, des échelles. Garde alors un texte court. |

```text
inverse                      large
┌────────────┐ eyebrow       eyebrow  ┌──────────────────────┐
│ graphique  │ title         title    │      graphique       │
│            │ analyse       analyse  │                      │
└────────────┘ - une puce    courte   └──────────────────────┘
```

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : tout
  s’applique ; le graphique est posé sur une carte, aux couleurs du thème.
- **Modèles complets** qui redessinent ce type (`compose`) : `chantier`, `marqueur`, `pastille`, `bloc`,
  `anneau`, `crayon`, `aube`, `opale`, `bdt`. Tous gardent `inverse` et `large`, sauf `bloc` et `crayon`
  qui posent déjà le graphique à gauche et ne gardent que `large`. Écritures particulières :
  - une ligne de `content` dont la **première case tient en seize caractères et contient un chiffre**
    (`4,2 M€ | de besoin de financement`, sans `- `, `# ` ni `> ` en tête) devient une statistique du
    modèle : chiffres (`chantier`, `bloc`), pastille chiffrée (`pastille`), anneau si la valeur est un
    pourcentage (`anneau`), chiffre sur filet (`crayon`), encadré surligné (`marqueur`, le premier
    seulement), repère à côté de l’analyse (`aube`) ; quatre au plus, et `opale` ne l’affiche pas ;
  - un graphique `barres` à une seule série est redessiné par le modèle : histogramme à la dernière
    colonne en accent (`chantier`, `bloc`, `anneau`, `crayon` — jusqu’à huit valeurs et hors
    `options : horizontal` ; au-delà, ou en horizontal, c’est le graphique ordinaire qui est tracé),
    barres de proportion (`pastille`, six valeurs au plus), barres surlignées (`marqueur`) ;
  - `chantier`, `marqueur`, `pastille`, `anneau` et `crayon` réduisent l’analyse à des paragraphes (ni
    puces, ni pictogrammes) ; les trois derniers posent le surtitre, ou à défaut le `sous-titre :` du
    graphique, en pied de slide ;
  - `aube` pose le graphique sur une carte blanche, `opale` à même le verre ; `bdt` sort le `titre :` du
    graphique et le pose en rouge, centré, au-dessus du tracé (seulement quand la slide n’a qu’un
    graphique) et lit le premier paragraphe de `content` comme un chapeau en italique.
- Les autres modèles complets (`revue`, `tampon`, `cimaise`) habillent le rendu Libre.
- **Plateforme** (`"modele": "plateforme"`) : surtitre, titre et analyse à gauche, le graphique dans une
  carte blanche à droite ; `inverse` et `large` s’appliquent. Plusieurs graphiques en ligne font passer
  l’en-tête au-dessus, sur toute la largeur. Pas de pictogramme : le mot est retiré sans s’afficher.

## Pièges

- **Les pièges d’écriture des graphiques** — virgule décimale, unité dans la valeur, virgule dans un
  libellé d’axe, série plus courte que l’axe — sont dans `references/graphiques.md`.
- **Un nom de série ne doit pas être un réglage.** Une ligne `Max : 120`, `Centre : 38`, `Unité : %` ou
  `Axe : …` est lue comme un réglage, et la série disparaît : renomme-la (`Plafond`, `Total`).
- **Chaque graphique commence par `type :`** : sans elle, le bloc rejoint le précédent.
- **Une slide `graph` sans `content` laisse une colonne vide** : s’il n’y a rien à analyser, prends
  `dashboard` ; s’il y a peu à dire, `large`.
- **`Valeur | libellé` n’est lu que par les modèles qui redessinent ce type**, et seulement si la première
  case tient en seize caractères et contient un chiffre : sinon la barre s’affiche dans le texte.

## JSON

Le cas courant : une courbe à droite, l’analyse à gauche.

```json
{ "layout": "graph", "eyebrow": "Énergie · 2022 → 2026", "title": "La consommation des gymnases a décroché dès le premier hiver.", "content": "Les trois gymnases rénovés consomment deux fois moins que les autres, à surface égale.\n- Écart stable depuis dix-huit mois\n- Aucun effet rebond observé", "content2": "type : courbe\ntitre : Consommation de chauffage\nsous-titre : kWh par m² et par saison\naxe : 2022, 2023, 2024, 2025, 2026\nGymnases rénovés : 182, 176, 171, 104, 96\nGymnases en attente : 179, 181, 174, 177, 172", "notes": "Le décrochage suit la mise en service des chaufferies, en octobre 2024. Deux gymnases rénovés ont aussi changé d’horaires : préciser que la correction climatique est faite." }
```

Des libellés longs : barres horizontales et disposition `large`, avec un texte court.

```json
{ "layout": "graph", "eyebrow": "Canicule · 12 juillet 2026", "title": "Sept degrés séparent les écoles rénovées des autres.", "disposition": "large", "content": "Température relevée à 16 h, dans la classe la plus exposée de chaque école.", "content2": "type : barres\ntitre : Température maximale en classe\nsous-titre : 12 juillet 2026, à 16 h\nunité : °C\noptions : horizontal\naxe : La Vergne (rénovée), Pasteur (rénovée), Les Coteaux (rénovée), Les Sources (en attente), Le Moulin (en attente)\nTempérature : 26.1, 26.8, 27.4, 33.9, 34.6" }
```

Trois graphiques en grille : deux par rangée, le troisième sur toute la largeur.

```json
{ "layout": "graph", "eyebrow": "Enquête · Juin 2026", "title": "Le nouveau guichet tient ses promesses, sauf sur les délais.", "agencement": "grille", "content": "412 réponses recueillies en mairie et en ligne, un an après l’ouverture.\n- Les démarches longues restent celles de l’urbanisme", "content2": "type : secteurs\ntitre : Satisfaction générale\nsous-titre : En % des réponses\nSatisfaits : 71\nSans avis : 22\nMécontents : 7\n\ntype : jauge\ntitre : Démarches abouties du premier coup\nunité : %\nRéussies : 76 / 100\n\ntype : barres\ntitre : Attente au guichet\nsous-titre : En minutes, moyenne du mois\nunité : min\naxe : Avant, Après\nAttente : 18, 7", "notes": "Les 24 % de démarches reprises deux fois sont presque toutes des demandes d’urbanisme : c’est le chantier de l’an prochain, à annoncer ici." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
