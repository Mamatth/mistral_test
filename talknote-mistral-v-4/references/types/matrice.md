# `matrice` · Matrice

> Quatre cases posées sur deux axes nommés, effort et impact ou urgence et importance, pour décider par où
> commencer ; une case peut être mise en avant.

## Quand l’employer

- **Dans la matière, tu as trouvé** : une liste d’actions, de projets ou de mesures que l’auteur classe selon
  deux critères (coût et bénéfice, effort et impact, urgence et importance, risque et probabilité) ; une
  priorisation, un arbitrage sur ce qu’il faut lancer d’abord, des « gains rapides » opposés à des chantiers
  lourds ; quatre familles qui se rangent naturellement dans un carré (atouts, fragilités, opportunités,
  menaces) ; des publics ou des sites répartis selon deux caractéristiques.
- **Plutôt que** : `colonnes` si les options s’opposent l’une à l’autre (avant / après, deux scénarios) plus
  qu’elles ne se situent sur deux échelles ; `portefeuille` si les sujets sont classés par état d’avancement
  (à cadrer, en cours, livré), en colonnes, sans second critère ; `faits` si les trois ou quatre éléments se
  juxtaposent sans position relative (réalisations, décisions, constats) ; `tableau` dès que les critères
  dépassent deux ou que chaque élément porte des valeurs à comparer ligne à ligne.
- **Pas pour** : une suite dans le temps (`etapes`, `jalons`) ni des éléments chiffrés avec précision : quatre
  cases disent « plutôt fort » ou « plutôt faible », pas 38 % contre 41 % (`graph`).

## Structure de l’information

```text
┌────────────────────────────────────────────────────────────┐
│ eyebrow                                                    │
│ title : la décision que la matrice éclaire                 │
│                                                            │
│ ▲  ╭────────────────────────╮ ╭────────────────────────╮   │
│ │  │ > Titre     (en avant) │ │ Titre                  │   │
│ I  │ Description            │ │ Description            │   │
│ M  ╰────────────────────────╯ ╰────────────────────────╯   │
│ P  ╭────────────────────────╮ ╭────────────────────────╮   │
│ A  │ Titre                  │ │ Titre                  │   │
│ C  │ Description            │ │ Description            │   │
│ T  ╰────────────────────────╯ ╰────────────────────────╯   │
│    EFFORT FAIBLE                             EFFORT FORT   │
└────────────────────────────────────────────────────────────┘
```

L’axe vertical se lit de bas en haut, l’axe horizontal à ses deux bouts ; la case en avant prend l’accent.

Ce que porte la slide, du plus au moins important :

```text
matrice
├── title      : la décision que la matrice éclaire, en une phrase (soixante caractères environ)
├── eyebrow    : repère court (« Priorités 2027 », « Arbitrage ») (facultatif)
├── content    : une ligne d’axes, puis quatre lignes « Titre | Description »
│     ├── axes : horizontal | vertical, chacun du plus faible au plus fort (facultatif)
│     ├── haut gauche  : Titre | Description   (« > » en tête : la case mise en avant)
│     ├── haut droite  : Titre | Description
│     ├── bas gauche   : Titre | Description
│     └── bas droite   : Titre | Description
└── notes      : ce que le présentateur dit et qui n’est pas écrit
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `eyebrow` | Repère au-dessus du titre : « Priorités 2027 », « Arbitrage », « Plan d’action ». | Facultatif, deux ou trois mots. |
| `title` | Le message : ce que la matrice décide, pas son nom. | Soixante caractères environ, deux lignes au plus ; au-delà de 64 caractères il s’affiche plus petit. |
| `content` | Les axes et les quatre cases. | Syntaxe ci-dessous. Cinq lignes au plus. |

Ce type n’emploie ni `content2`, ni `author`, ni `image`, et n’a pas de `disposition`. Les quatre cases
entrent ensemble : `progressive` est sans effet. Champs communs (`anim`, `transition`, `notes`) : `references/format-json.md`.

## Syntaxe de `content`

**La ligne des axes**, facultative, en première ligne : `axes : Effort faible → fort | Impact faible → fort`.

- La première cellule est l’axe horizontal, lu de gauche à droite ; la seconde, l’axe vertical, lu de bas en
  haut. Chaque axe va **du plus faible au plus fort**, avec la flèche `→` (`->` vaut aussi).
- TalkNote coupe l’axe horizontal sur la flèche et pose un bout à chaque extrémité de la grille : « Effort
  faible » à gauche, « Effort fort » à droite (le premier mot n’est repris que si le bout gauche tient en
  deux mots et le bout droit en un seul ; écris donc l’axe en deux mots, sinon le bout droit s’affiche seul).
  Sans flèche, le texte s’affiche seul, centré sous la grille. L’axe vertical s’affiche entier, flèche
  comprise, écrit de bas en haut à gauche de la grille.
- `axes : Effort faible → fort` sans seconde cellule : pas d’axe vertical, la grille prend toute la largeur.
  Sans ligne d’axes : quatre cases nues, pour un carré dont les familles se comprennent d’elles-mêmes.

**Les quatre cases**, une par ligne, `Titre | Description`, dans cet ordre fixe :

| Ligne | Case | Avec les axes de l’exemple | Ce qu’on y range |
| --- | --- | --- | --- |
| 1 | haut gauche | Effort faible · Impact fort | Ce qu’il faut faire en premier. |
| 2 | haut droite | Effort fort · Impact fort | Ce qui se planifie : ça vaut le coût. |
| 3 | bas gauche | Effort faible · Impact faible | Ce qu’on fait quand on peut. |
| 4 | bas droite | Effort fort · Impact faible | Ce qu’on écarte. |

- Le titre est la première cellule : deux à quatre mots, un verbe ou une consigne (« À lancer maintenant »,
  « À planifier »). La description est tout ce qui suit le premier `|` : les éléments rangés dans la case, en
  une ligne ou deux (soixante à quatre-vingt-dix caractères) ; elle est facultative.
- `> ` en tête de ligne met la case en avant : `> À lancer maintenant | Réglage des chaufferies, éclairage
  LED`. Une seule case en avant par slide, celle où se prend la décision.
- Un pictogramme `(nom)` se pose en tête du titre d’une case, après le repère : `> (éclair) À lancer
  maintenant | …`. Noms : `references/pictogrammes.md`. ` // ` fait une courte liste dans une description
  (`À planifier | - Pompes à chaleur // - Reprise des façades`). `**gras**`, `==surligné==` : voir
  `references/format-json.md`.
- Quatre lignes de cases, ni plus ni moins : une cinquième n’est pas affichée, une case manquante reste vide.

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : tout s’applique.
  En Libre, la case en avant est un aplat de la couleur d’accent ; avec une mise en page, elle garde un fond
  neutre, cernée d’un filet d’accent, son titre à l’accent.
- **Modèles complets** qui redessinent ce type (`compose`) : `opale` seulement. Il pose la grille sur sa
  vitre : chaque case est une carte de verre dépoli, coiffée de sa position sur les deux axes (« Effort
  faible · Impact fort », déduite de la ligne des axes) ; deux lignes fléchées se croisent au milieu de la
  grille, l’axe vertical est écrit à gauche, les deux bouts de l’axe horizontal en dessous. La case en avant
  est cernée d’une de ses teintes, son titre dans cette teinte. Un pictogramme en tête de case s’y dessine.
  Les autres modèles complets (`revue`, `chantier`, `marqueur`, `tampon`, `pastille`, `bloc`, `anneau`,
  `crayon`, `cimaise`, `aube`, `bdt`) habillent le rendu Libre : cartes sans aplat, la case en avant cernée
  d’un filet d’accent avec son titre à l’accent, comme la colonne en avant d’une comparaison ; les
  pictogrammes se dessinent.
- **Plateforme** (`"modele": "plateforme"`) : pas de matrice dans le catalogue officiel. La slide reprend
  les cartes des faits, une par case, dans l’ordre écrit ; moins de quatre lignes donnent moins de cartes,
  sans case vide : chaque carte porte son numéro suivi de sa position sur les deux axes
  (« — 01 · Effort faible · Impact fort »), puis le titre et la description. Ni grille, ni
  axes dessinés ; la mise en avant `> ` ne se voit pas ; sans ligne d’axes, les cartes n’ont que leur numéro.
  Pas de pictogramme : le mot est retiré sans s’afficher.

```text
┌────────────────────────────────────────────────────────────┐
│ title                                                      │
│ ╭──────────╮ ╭──────────╮ ╭──────────╮ ╭──────────╮        │
│ │ — 01 ·   │ │ — 02 ·   │ │ — 03 ·   │ │ — 04 ·   │        │
│ │ Effort   │ │ Effort   │ │ Effort   │ │ Effort   │        │
│ │ faible · │ │ fort ·   │ │ faible · │ │ fort ·   │        │
│ │ Impact   │ │ Impact   │ │ Impact   │ │ Impact   │        │
│ │ fort     │ │ fort     │ │ faible   │ │ faible   │        │
│ │ Titre    │ │ Titre    │ │ Titre    │ │ Titre    │        │
│ │ Descr.   │ │ Descr.   │ │ Descr.   │ │ Descr.   │        │
│ ╰──────────╯ ╰──────────╯ ╰──────────╯ ╰──────────╯        │
└────────────────────────────────────────────────────────────┘
```

## Pièges

- L’ordre des lignes est celui des cases, pas celui de l’importance : haut gauche, haut droite, bas gauche,
  bas droite. Si tu veux « faire en premier » en haut à gauche, écris cette case en première ligne.
- Un axe écrit du plus fort au plus faible (`Impact fort → faible`) inverse la lecture des cases sans que
  TalkNote le sache : va toujours du plus faible au plus fort. Sans `→`, l’axe horizontal ne se coupe pas :
  tout son texte s’affiche d’un bloc, centré sous la grille.
- Un `|` dans un titre de case le coupe : le titre est la première cellule seulement. Dans une description,
  il reste du texte.
- Deux lignes avec `> ` donnent deux cases en avant : garde-en une.
- Le type n’a pas de disposition : `"disposition": "grille"` est ignoré, et n’a donc rien à faire dans le
  JSON. Le carré est toujours deux par deux.
- Des descriptions longues font grandir la grille, et la slide entière rétrécit pour la contenir : deux lignes
  par case au plus. Un titre neutre (« Matrice effort / impact ») ne dit rien : écris la décision.

## JSON

La priorisation par défaut, la case « à faire en premier » en avant :

```json
{ "layout": "matrice", "eyebrow": "Priorités 2027", "title": "Trois services en ligne avant l’été, le reste ensuite.", "content": "axes : Effort faible → fort | Impact faible → fort\n> À lancer maintenant | Prise de rendez-vous en ligne, paiement de la cantine, alertes par SMS\nÀ planifier | Portail famille unique : un an de développement, un marché à passer\nQuand on peut | Reprise des formulaires PDF en formulaires en ligne\nÀ écarter | Application mobile dédiée : coût élevé, usage incertain", "notes": "La case en haut à gauche est celle du comité de mars : peu d’effort, beaucoup d’impact. Le portail famille reste la cible à deux ans ; l’application mobile est écartée tant que le portail n’existe pas." }
```

Urgence et importance, un pictogramme en tête de chaque case :

```json
{ "layout": "matrice", "eyebrow": "Plan de charge", "title": "Ce que l’équipe traite, planifie, confie ou abandonne.", "content": "axes : Urgence faible → forte | Importance faible → forte\n(calendrier) À planifier | Refonte de l’intranet, formation des nouveaux agents\n> (alerte) À traiter maintenant | Panne de la messagerie, mise à jour de sécurité du portail\n(document) À faire quand on peut | Tri des archives, mise à jour de l’annuaire\n(groupe) À confier ou à abandonner | Demandes hors périmètre, relances sans objet", "notes": "Ici l’urgence est l’axe horizontal : la case en avant est donc en haut à droite, urgent et important. Les exemples viennent du relevé des tickets du premier trimestre." }
```

Quatre familles sans axes, pour un carré atouts / fragilités / opportunités / menaces :

```json
{ "layout": "matrice", "eyebrow": "Diagnostic", "title": "Un réseau de lecture solide, qui vieillit avec ses lecteurs.", "content": "Atouts | Douze bibliothèques, une carte unique, 31 000 inscrits\nFragilités | Bâtiments anciens, horaires réduits le samedi, catalogue non consultable en ligne\nOpportunités | Le portail numérique de la région, deux écoles neuves à proximité\nMenaces | Baisse des inscrits de moins de 25 ans, deux départs en retraite non remplacés", "notes": "Sans ligne d’axes ni case en avant : les quatre familles se lisent comme un carré, à parcourir avec le public. Les chiffres viennent du rapport d’activité 2026." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
