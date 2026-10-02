# Les onze graphiques

> À ouvrir dès qu’une slide doit porter un graphique : où l’écrire, la syntaxe commune, le type à choisir d’après la donnée, et les onze dessins que TalkNote sait faire.

## Où s’écrit un graphique

Un graphique se décrit en texte, dans le champ `content2`. TalkNote le dessine lui-même : tu n’écris jamais d’image, ni de code, ni d’adresse.

- `graph` : un à quatre graphiques, à côté d’une analyse écrite dans `content`. Dispositions `""` (texte à gauche), `inverse` (graphique à gauche), `large` (graphique sur deux tiers).
- `dashboard` : deux à quatre graphiques, sans `content`. Pas de disposition.
- Plusieurs graphiques se séparent par une **ligne vide** (`\n\n` en JSON) ; chacun recommence par sa ligne `type :`.
- `agencement` range les cartes : `""`, `ligne`, `colonne`, `grille`. Laissé vide, le moteur choisit : à côté d’un texte, deux graphiques se superposent et trois ou quatre passent en grille ; sur un tableau de bord, jusqu’à trois se rangent en ligne, quatre en grille. `grille` demandé pour deux graphiques les met côte à côte.
- Au-delà de quatre, les graphiques suivants ne sont pas dessinés.
- Les champs de ces deux types : voir `references/types/graph.md` et `references/types/dashboard.md`. L’enveloppe et les champs communs : voir `references/format-json.md`.

## La syntaxe

Une ligne par réglage, puis une ligne par série. Toujours `clé : valeur`.

```text
type : barres
titre : Demandes de logement social
sous-titre : Par trimestre, en 2026
axe : T1, T2, T3, T4
Déposées : 412, 468, 501, 455
Instruites : 380, 402, 470, 441
```

### Les réglages

| Réglage | Aussi écrit | Ce qu’il fait | Employé par |
| --- | --- | --- | --- |
| `type` | — | le dessin ; un nom inconnu donne des barres | tous |
| `titre` | `title` | la légende au-dessus du dessin | tous |
| `sous-titre` | `sub`, `légende` | la précision sous le titre : unité, période, source | tous |
| `axe` | `axes` | les libellés, séparés par des virgules | `barres`, `courbe`, `radar` ; nomme les points de `échelles` |
| `unité` | `unit` | l’unité collée à la valeur écrite dans le dessin | `anneaux`, `jauge`, `progression`, `entonnoir`, `bulles` |
| `description` | `alt` | la phrase lue par un lecteur d’écran à la place du dessin ; sans elle, TalkNote la compose d’après les données | tous |
| `max` | `maximum` | le haut de l’échelle, au lieu d’un maximum calculé | `barres`, `courbe`, `radar`, `anneaux`, `jauge`, `progression`, `échelles` |
| `centre` | `center` | le texte posé au milieu du dessin | `anneaux`, `jauge`, `secteurs`, `intersection` |
| `crans` | — | le nombre de graduations, de 8 à 200 (40 par défaut) | `jauge` |
| `options` | `option` | `empilé`, `horizontal` (ou `couché`), `aire`, `emboîtées`, séparées par des virgules | voir chaque type |

La clé se lit sans accent, sans casse et sans espaces : `Sous-titre`, `sous titre` et `soustitre` sont la même. Une clé inconnue est lue comme une série.

### Les séries

- Une ligne par série : `Nom : valeurs`. Le nom porte la légende.
- Autant de valeurs que l’axe a de libellés, séparées par des virgules.
- `Nom : 26 / 70` donne la valeur et sa cible propre, ligne par ligne (`anneaux`, `jauge`, `progression`, `échelles`).
- Les couleurs viennent du thème ou du modèle et suivent l’ordre des séries, huit couleurs puis on recommence ; tu ne les choisis pas.
- La légende s’affiche dès deux séries, et toujours pour `anneaux` (les noms seuls) et `secteurs` (les noms et leurs pourcentages, calculés sur le total). `progression`, `entonnoir`, `bulles`, `échelles` et `intersection` écrivent leurs noms dans le dessin : pas de légende, sauf `échelles` à plusieurs points, où elle nomme les points d’après `axe :`.

### Les nombres

- Point décimal : `12.5`. La virgule sépare les valeurs, jamais les décimales.
- Pas de séparateur de milliers : `1200`.
- Pas d’unité dans la valeur : elle va dans `unité :` ou dans `sous-titre :`.
- Une valeur illisible vaut zéro.

## Choisir le graphique d’après la donnée

| Ce que dit la donnée | Type | Ce qui départage |
| --- | --- | --- |
| Une évolution dans le temps, trois points ou plus | `courbe` | deux périodes seulement : `barres` |
| Comparer des catégories entre elles | `barres` | libellés longs : `options : horizontal` |
| Des postes qui s’additionnent, période par période | `barres` + `options : empilé` | un seul total à décomposer : `secteurs` |
| La part d’un tout, cinq parts au plus | `secteurs` | plus de cinq parts : `barres` |
| Deux à quatre progressions vers leur cible | `anneaux` | une seule : `jauge` ; plus de quatre : `progression` |
| Une valeur unique face à son objectif | `jauge` | sans objectif : plutôt une slide `chiffre` |
| Un avancement ligne à ligne, jusqu’à six lignes | `progression` | cibles différentes : `Nom : 41 / 48` |
| Des effectifs qui se réduisent d’étape en étape | `entonnoir` | sans perte entre les étapes : `barres` |
| Des ordres de grandeur très écartés | `bulles` | l’un contenu dans l’autre : `options : emboîtées` |
| Un profil sur cinq à huit critères | `radar` | critères non comparables : `barres` |
| Une position entre deux mots opposés | `échelles` | avant et après : deux valeurs par ligne |
| Ce qui est commun à deux ou trois ensembles | `intersection` | quatre ensembles : `colonnes` ou `matrice` |

Parfois le graphique n’est pas la bonne réponse : trois nombres sans évolution tiennent mieux en `chiffre`, des lignes homogènes à plusieurs colonnes en `tableau`. Voir `references/analyse.md`.

## `barres` — comparer des catégories

Aussi : `barre`, `histogramme`, `bar`, `bars`. `axe :` porte les catégories, puis une ligne par série, quatre au plus. `options : empilé` additionne les séries ; `options : horizontal` couche les barres, pour des libellés longs (coupés au-delà de 26 caractères). `max :` fixe le haut de l’échelle. Au-delà de sept catégories, les libellés se serrent.

```text
 60 |          ##
 40 |   ## ..   ## ..
 20 |   ## ..   ## ..
  0 +-------------------
      T1         T2
```

```text
type : barres
titre : Dépenses par poste
sous-titre : En millions d’euros
options : empilé
axe : 2025, 2026, 2027
Isolation : 4.2, 5.1, 6.6
Menuiseries : 2.1, 2.6, 3.3
```

```json
{ "layout": "graph", "title": "Les demandes affluent au printemps, l’instruction suit avec un trimestre de retard.", "content": "Le pic de mai n’est instruit qu’en juillet.\n- Deux agents renforcent le service depuis juin", "content2": "type : barres\ntitre : Demandes de logement social\nsous-titre : Par trimestre, en 2026\naxe : T1, T2, T3, T4\nDéposées : 412, 468, 501, 455\nInstruites : 380, 402, 470, 441", "notes": "Source : tableau de bord du service logement, septembre 2026." }
```

## `courbe` — une évolution dans le temps

Aussi : `courbes`, `ligne`, `lignes`, `line`. `axe :` porte les périodes, puis une ligne par série, quatre au plus. `options : aire` remplit sous la courbe, pour une seule série. `max :` fixe le haut de l’échelle. Le dernier point de chaque courbe est marqué plus gros.

```text
 300 |                      o--o
 200 |      o--o--o--o--o--'
 100 |  o--'
   0 +---------------------------
      2021  2022  2023  2024  2025
```

```text
type : courbe
titre : Entrées en médiathèque
sous-titre : En milliers, par an
axe : 2022, 2023, 2024, 2025
Réseau entier : 226, 241, 289, 312
```

```json
{ "layout": "graph", "disposition": "inverse", "title": "La fréquentation est repartie dès l’ouverture du dimanche.", "content": "L’ouverture dominicale date de janvier 2025.\n- Le prêt de documents suit la même pente\n- Les inscriptions des 15-25 ans doublent", "content2": "type : courbe\ntitre : Entrées en médiathèque\nsous-titre : En milliers, par an\naxe : 2021, 2022, 2023, 2024, 2025, 2026\nRéseau entier : 214, 226, 241, 238, 289, 312\nMédiathèque centrale : 96, 101, 108, 104, 132, 148", "notes": "Source : comptage des portiques, janvier 2027." }
```

## `radar` — un profil sur plusieurs critères

`axe :` porte les critères, cinq à huit (six est la bonne taille), puis une ligne par profil, trois au plus. Écris toujours `max :` : sans lui, l’échelle est calculée sur la plus forte valeur et deux graphiques voisins ne se comparent plus. Une valeur manquante vaut zéro et creuse la forme.

```text
        Accueil
      .    |    .
 Suivi ----+---- Clarté
      .   / \   .
  Délai      Accès
```

```text
type : radar
titre : Qualité du guichet
sous-titre : Note sur 10
max : 10
axe : Accueil, Clarté, Délai, Accessibilité, Suivi, Fiabilité
Guichet unique : 8.2, 7.6, 4.8, 8.8, 7.1, 8.4
```

```json
{ "layout": "graph", "title": "Le guichet unique tient ses promesses, sauf sur le délai.", "content": "Le délai moyen reste de dix-neuf jours.\n- Priorité 2027 : instruire en dix jours", "content2": "type : radar\ntitre : Qualité du guichet unique\nsous-titre : Note sur 10, enquête de juin\nmax : 10\naxe : Accueil, Clarté, Délai, Accessibilité, Suivi, Fiabilité\nGuichet unique : 8.2, 7.6, 4.8, 8.8, 7.1, 8.4\nAncien guichet : 6.1, 5.4, 5.2, 4.3, 4.9, 6.6", "notes": "Enquête auprès de 412 usagers, juin 2026." }
```

## `anneaux` — des progressions vers leur cible

Aussi : `anneau`, `donut`, `ring`. Une ligne par anneau, quatre au plus, écrite `Nom : 26 / 70` (sans `/`, la cible est 100). Le milieu porte la valeur du **premier** anneau ; `centre :` remplace le nom écrit dessous. `unité :` s’ajoute à cette valeur. La légende nomme tous les anneaux.

```text
    .-----------.
   /  .-------.  \      Raccordés
  |  |   84    |  |     En travaux
   \  '-Sites-'  /      À programmer
    '-----------'
```

```text
type : anneaux
titre : Raccordement des sites publics
centre : Sites
Raccordés : 84 / 126
En travaux : 27 / 126
```

```json
{ "layout": "graph", "disposition": "inverse", "title": "Deux tiers des sites publics sont raccordés, le reste attend le génie civil.", "content": "Les quinze sites à programmer sont tous en zone rurale.\n- Fin du déploiement visée en 2028", "content2": "type : anneaux\ntitre : Raccordement des sites publics\ncentre : Sites\nRaccordés : 84 / 126\nEn travaux : 27 / 126\nÀ programmer : 15 / 126", "notes": "Source : point d’avancement du syndicat numérique, août 2026." }
```

## `jauge` — une valeur face à son objectif

Aussi : `gauge`. **Une seule ligne**, écrite `Nom : 58 / 100`. Le nom passe sous le cadran. `centre :` remplace la valeur affichée par un texte parlant (`22 M€ sur 38 M€`) ; sinon la valeur est écrite, suivie de `unité :`. `crans :` change le nombre de graduations, de 8 à 200.

```text
    . ' ' ' ' ' ' .
  '       58 %      '
  .      Engagé      .
    .  ' ' ' ' '  .
```

```text
type : jauge
titre : Budget engagé
centre : 14 M€ sur 24 M€
unité : %
Engagé : 58 / 100
```

```json
{ "layout": "dashboard", "title": "Le plan vélo à mi-parcours.", "content2": "type : jauge\ntitre : Budget engagé\ncentre : 14 M€ sur 24 M€\ncrans : 48\nEngagé : 58 / 100\n\ntype : anneaux\ntitre : Kilomètres livrés\ncentre : Kilomètres\nLivrés : 38 / 90\nEn chantier : 22 / 90", "notes": "Chiffres arrêtés au 30 juin 2026." }
```

## `secteurs` — la part d’un tout

Aussi : `secteur`, `camembert`, `parts`, `répartition`, `pie`. Une ligne par part, cinq au plus ; les pourcentages sont calculés sur le total et écrits dans la légende. `centre :` pose le total au milieu de l’anneau. Des parts très inégales deviennent illisibles : regroupe sous « Autres ».

```text
     .------.
   /  .----.  \      Ordures    · 50 %
  |  : 48 kt : |     Emballages · 20 %
   \  '----'  /      Verre      · 13 %
     '------'
```

```text
type : secteurs
titre : Collecte 2026 par flux
sous-titre : En milliers de tonnes
centre : 48 kt
Ordures ménagères : 24.1
Emballages : 9.6
```

```json
{ "layout": "graph", "title": "L’ordure ménagère pèse encore la moitié de la collecte.", "content": "Le tri progresse, la masse totale baisse peu.\n- Objectif 2030 : ramener l’ordure ménagère sous 40 %", "content2": "type : secteurs\ntitre : Collecte 2026 par flux\nsous-titre : En milliers de tonnes\ncentre : 48 kt\nOrdures ménagères : 24.1\nEmballages : 9.6\nVerre : 6.2\nBiodéchets : 5.4\nEncombrants : 2.7", "notes": "Source : rapport annuel du service déchets, 2026." }
```

## `progression` — l’avancement ligne à ligne

Aussi : `progressions`, `avancement`, `progress`. Une barre par ligne, six au plus. Sans `/`, la barre se remplit vers 100 ; `Nom : 41 / 48` fixe la cible de la ligne et l’écrit à droite. `unité :` s’ajoute à la valeur. Une seule couleur, pas de légende ; un nom trop long est coupé. Range les lignes de la plus avancée à la moins avancée.

```text
 Bourg-Neuf                 72 / 72
 [#############################]
 Vaux                       22 / 39
 [################             ]
```

```text
type : progression
titre : Inventaire du patrimoine
sous-titre : Bâtiments relevés sur le total
Bourg-Neuf : 72 / 72
La Ferrière : 41 / 48
```

```json
{ "layout": "graph", "title": "Trois communes sur cinq ont terminé leur inventaire.", "content": "Les deux dernières manquent d’un agent formé au relevé.\n- Un appui mutualisé est proposé dès octobre", "content2": "type : progression\ntitre : Inventaire du patrimoine bâti\nsous-titre : Bâtiments relevés sur le total attendu\nBourg-Neuf : 72 / 72\nSaint-Amand : 54 / 54\nLa Ferrière : 41 / 48\nVaux : 22 / 39\nMontigny : 9 / 35", "notes": "Source : suivi de la mission patrimoine, septembre 2026." }
```

## `entonnoir` — des effectifs qui se réduisent

Aussi : `entonnoirs`, `funnel`. Une tranche par ligne, de la plus grande à la plus petite ; range-les toi-même dans cet ordre. À partir de la deuxième, sa part de la première est écrite à côté. `unité :` s’ajoute à chaque valeur. Quatre ou cinq étapes suffisent.

```text
 \=========================/   Déposés     1240
  \===================/        Recevables   980 · 79 %
   \=============/             Instruits    610 · 49 %
    \========/                 Aidés        412 · 33 %
```

```text
type : entonnoir
titre : Du dossier déposé à l’aide versée
unité : dossiers
Déposés : 1240
Recevables : 980
```

```json
{ "layout": "graph", "title": "Un dossier déposé sur trois aboutit à une aide versée.", "content": "La moitié des pertes vient d’une pièce manquante.\n- Un accusé de réception détaillé est testé depuis mai", "content2": "type : entonnoir\ntitre : Du dossier déposé à l’aide versée\nsous-titre : Aide à la rénovation, année 2026\nunité : dossiers\nDéposés : 1240\nRecevables : 980\nInstruits : 610\nAidés : 412", "notes": "Source : extraction du logiciel d’instruction, décembre 2026." }
```

## `bulles` — des ordres de grandeur

Aussi : `bulle`, `bubble`, `bubbles`. Une ligne par disque, quatre au plus ; l’aire suit la valeur. Par défaut les disques sont côte à côte, la valeur et le nom dessous, le premier à l’accent. `options : emboîtées` les pose l’un dans l’autre, du plus grand au plus petit, chaque valeur reliée à son anneau : pour un tout, sa part, et ce qu’on en tient. `unité :` s’ajoute aux valeurs.

```text
   .---------.
  /  .-----.  \-- 9400 logements au fioul
 |  |  (o)--+---- 640 aidés
  \  '-----'  /-- 3100 éligibles
   '---------'
```

```text
type : bulles
titre : Du gisement au réalisé
options : emboîtées
Logements chauffés au fioul : 9400
Éligibles à l’aide : 3100
```

```json
{ "layout": "graph", "disposition": "large", "title": "Sur 9 400 logements chauffés au fioul, 640 sont passés à la pompe à chaleur.", "content": "Le gisement reste très large devant le réalisé.", "content2": "type : bulles\ntitre : Du gisement au réalisé\nsous-titre : Logements du territoire, fin 2026\noptions : emboîtées\nLogements chauffés au fioul : 9400\nÉligibles à l’aide : 3100\nDossiers aidés : 640", "notes": "Source : observatoire de l’habitat, fin 2026." }
```

## `échelles` — une position entre deux mots opposés

Aussi : `échelle`, `curseur`, `curseurs`, `scale`, `scales`. Une ligne par axe, huit au plus, nommée par ses deux bouts : `Confus / Clair : 28`. Les séparateurs acceptés sont `/`, `->`, `→`, `<->`, `<>`, `↔` et la barre verticale. Le point va de 0 (mot de gauche) au maximum, 100 par défaut, changé par `max :` ou par la ligne elle-même (`Confus / Clair : 3 / 5`). Le mot du côté du point passe à l’encre. Deux valeurs posent deux points, nommés dans l’ordre par `axe :` : c’est la façon de montrer un avant et un après.

```text
 Confus      o--------|-------O   Clair
 Lent           o-----|--O        Rapide
 Rigide       o-------|------O    Souple
```

```text
type : échelles
titre : Le portail vu par les agents
axe : Ancien portail, Nouveau portail
Confus / Clair : 28, 79
Lent / Rapide : 31, 44
```

```json
{ "layout": "graph", "disposition": "large", "title": "Les agents jugent le nouveau portail plus clair, pas encore plus rapide.", "content": "La rapidité reste le seul axe sans progrès net.", "content2": "type : échelles\ntitre : Le portail vu par les agents\nsous-titre : Position moyenne, de 0 à 100\naxe : Ancien portail, Nouveau portail\nConfus / Clair : 28, 79\nLent / Rapide : 31, 44\nRigide / Souple : 24, 68\nIsolé / Bien relié : 35, 72", "notes": "Enquête interne, 186 réponses, mai 2026." }
```

## `intersection` — ce qui est commun à des ensembles

Aussi : `intersections`, `venn`, `recouvrement`. Une ligne par cercle, son **nom seul**, sans deux-points ni valeur ; deux ou trois cercles, les suivants sont ignorés. `centre :` écrit ce qui se joue là où tout se rejoint, dans un disque d’accent. Des noms courts : deux ou trois mots, coupés à trois lignes.

```text
        .---------.
       /  Sobriété \
  .---+---.     .---+----.
 / Confort |Retenu|  Usages \
 '---------'     '----------'
```

```text
type : intersection
titre : Ce qui fait un projet retenu
centre : Projet retenu
Sobriété
Usage partagé
Coût maîtrisé
```

```json
{ "layout": "graph", "disposition": "large", "title": "Un projet est retenu quand les trois critères se rejoignent.", "content": "Deux critères sur trois suffisent à passer en étude, jamais à passer en travaux.", "content2": "type : intersection\ntitre : Les critères de sélection\ncentre : Projet retenu\nSobriété énergétique\nUsage partagé\nCoût maîtrisé", "notes": "Grille de sélection votée en commission, mars 2026." }
```

## Pièges

- **Une virgule dans un libellé d’axe** le coupe en deux libellés. Écris `2027 (prév.)`, jamais `T4, 2027`.
- **Une unité devant la valeur** la met à zéro (`€ 58`). Écris la valeur seule et mets l’unité dans `unité :`.
- **Une série plus courte que l’axe** : en barres, les valeurs manquantes valent zéro ; en courbe, le tracé s’arrête. Compte les valeurs, une par libellé.
- **`type :` absent ou inconnu** : le graphique est dessiné en barres, sans prévenir.
- **Une ligne vide au milieu d’un graphique** le coupe en deux sur un tableau de bord. Ne laisse de ligne vide qu’entre deux graphiques.
- **Une ligne sans deux-points** est ignorée, sauf en `intersection` où elle est un cercle.
- **Une puce en tête de série** (`- Déposés : 412`) garde le tiret dans la légende : écris `Déposés : 412`.
- **Un `/` dans une valeur** sépare la valeur de sa cible : ne l’emploie nulle part ailleurs.
- **Accessibilité** : `description :` est la phrase que lit un lecteur d’écran à la place du dessin, une ou deux phrases sur ce que le graphique montre (l’évolution ou l’écart à retenir). Omise, TalkNote la compose seul d’après les données (type, départ, arrivée, sommet) ; écris-la quand le message du graphique va au-delà : `description : Les écoles rénovées consomment deux fois moins dès le premier hiver.` Un tableau des valeurs est ajouté automatiquement.
- **Un nom de série qui est un mot réglé** est lu comme un réglage, et la série disparaît : `Centre : 120, 130` devient le texte du milieu. Mots réservés : `type`, `titre`/`title`, `sous-titre`/`sub`/`légende`, `axe`/`axes`, `unité`/`unit`, `description`/`alt`, `max`/`maximum`, `centre`/`center`, `crans`, `options`/`option`. Renomme la série : `Secteur centre : 120, 130`.
- **Un deux-points dans un nom de série** est accepté ; la coupure se fait au dernier. Évite-le quand même.
- **Aucune série lisible** : la slide montre un cadre vide et le mode d’emploi de TalkNote. Relis toujours tes lignes.
