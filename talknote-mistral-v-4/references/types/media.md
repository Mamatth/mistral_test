# `media` · Média

> Une capture, un schéma ou une image occupe la slide, montré en entier, avec sa légende et sa source.

## Quand l’employer

- **Dans la matière, tu as trouvé** : une figure déjà dessinée dans le document source (schéma, organigramme,
  carte, plan d’implantation, « Figure 3 ») ; une copie d’écran d’un outil, d’un portail, d’un courriel type,
  à montrer telle quelle ; une infographie ou une planche dont on ne peut rien couper sans la fausser ; une
  photographie d’un document, d’un panneau, d’une affiche ; un visuel accompagné d’une source à citer
  (bureau d’études, institut, service producteur).
- **Plutôt que** : `maquette` quand c’est une application à présenter, avec un argumentaire à côté (elle pose
  l’écran dans un appareil et sait se passer de capture) ; `imagetexte` quand la photo n’illustre qu’un texte
  à lire à côté (elle recadre la photo et lui laisse la moitié de la slide) ; `image` quand l’image est une
  ambiance en plein cadre (elle la recadre pour remplir la slide et incruste le titre dedans). `media` est le
  seul des quatre qui montre le visuel **en entier**, jamais recadré, avec une légende et une source.
- **Pas pour** : un graphique dont tu as les données, que `graph` dessinera net et lisible ; un tableau
  photographié, que `tableau` rendra ligne à ligne ; une image d’ambiance sans rien à démontrer.

## Structure de l’information

```text
┌────────────────────────────────────────────────────────────┐
│ eyebrow                                                    │
│ title : ce que l’image démontre                            │
│ ┌────────────────────────────────────────────────────────┐ │
│ │                                                        │ │
│ │     image : le schéma ou la capture, entière (16:9)    │ │
│ │                                                        │ │
│ └────────────────────────────────────────────────────────┘ │
│ content : la légende                              AUTHOR   │
└────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
media
├── image      : le schéma ou la capture, montré en entier ; laisse-le vide
├── title      : ce que l’image démontre, une phrase
├── content    : la légende, une ou deux lignes simples sous le cadre
├── author     : la source, à droite de la légende, en petites capitales
├── eyebrow    : repère court au-dessus du titre (facultatif)
└── notes      : « Image à ajouter : … », puis ce que le présentateur commente
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `image` | Le schéma, la capture ou la photographie. Montré en entier, centré, sans recadrage. | Laisse `""` : la slide montre un cadre en pointillés et l’utilisateur y dépose son fichier. Écris `Image à ajouter : …` dans `notes` (voir `references/images.md`). Jamais d’adresse web. |
| `title` | Ce que l’image démontre, pas son étiquette. | Une phrase. Au-delà de 64 caractères, le corps du titre est réduit. |
| `content` | La légende, sous le cadre, à gauche. Ce qu’il faut lire dans l’image. | Une ou deux lignes simples. Chaque ligne mange la hauteur du cadre. |
| `author` | La source ou le producteur du visuel, à droite de la légende, en petites capitales. | Facultatif. Court : il ne passe jamais à la ligne. `Schéma · Cellule d’ingénierie`, `Capture · Portail des aides`. |
| `eyebrow` | Surtitre : le repère au-dessus du titre. | Facultatif, quelques mots. |

`media` n’a pas de disposition : `disposition` y est sans effet, comme `content2`, `content3`, `cadre`,
`ecrans`, `imageRight`, `imageWidth` et `accent`. Les champs communs (`anim`, `transition`, `notes`,
`progressive`) : voir `references/format-json.md`. `fondu` convient à un visuel qui doit s’installer.

## Syntaxe de `content`

- Des lignes simples, séparées par `\n` : elles s’empilent dans la légende. `**gras**`, `*italique*`,
  `==surligné==` s’appliquent (syntaxe du texte : voir `references/format-json.md`).
  Exemple : `Dix-huit mois en moyenne entre le diagnostic et la réception.`
- **Pas de ligne à puce ni numérotée** : `- `, `* `, `• `, `1. ` ou `1) ` en tête font une puce, et la
  légende de Libre écarte ces lignes — elles disparaîtraient sans trace ; Plateforme, lui, les dessinerait
  en puces. Écris une phrase par ligne, et jamais de numéro en tête.
- **Pas d’intertitre `# `** : Libre en retirerait le dièse, Plateforme l’afficherait tel quel.
- Pas de pictogramme `(nom)` dans la légende : aucun gabarit n’en dessine ici, le mot serait retiré sans
  s’afficher. En tête du `title`, en revanche, il est dessiné (sauf avec Plateforme).
- Une ou deux lignes suffisent : le cadre de l’image occupe toute la place qui reste sous le titre et
  au-dessus de la légende.
- `author` est une ligne à part, pas une ligne de `content` : ne l’écris pas « Source : … » dans la légende.

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : tout s’applique.
  Les mises en page gardent la composition et posent leur décor autour (chiffre géant, gouttière, trame) ;
  le cadre de l’image y perd son arrondi et son fond, réduit à un filet du thème.
- **Modèles complets** : aucun ne redessine `media`. `revue`, `chantier`, `marqueur`, `tampon`, `pastille`,
  `bloc`, `anneau`, `crayon`, `cimaise`, `aube`, `opale` et `bdt` habillent tous le rendu Libre — la même
  composition, la palette et les polices du modèle, sa tête et son pied. Le cadre devient un simple filet,
  sauf avec `aube` et `opale`, qui lui gardent un grand arrondi et une carte claire.
- **Plateforme** (`"modele": "plateforme"`) : composition propre au modèle, mais de même ordre — surtitre,
  titre, cadre blanc à filet fin, puis la légende à gauche et la source à droite en capitales. Aucun
  pictogramme n’y est dessiné.

## Pièges

- Une ligne à puce ou numérotée dans `content` (`- `, `* `, `• `, `1. `, `1) `) : invisible en Libre, en
  puce sous Plateforme. La légende s’écrit en lignes simples, sans numéro en tête.
- Une source longue dans `author` : elle ne se coupe pas et déborderait sur la légende. Deux ou trois mots.
- Une légende de cinq lignes : le cadre de l’image rétrécit d’autant. Ce qui doit être dit va dans `notes`.
- Un titre qui nomme l’image (« Schéma du parcours ») : dis plutôt ce qu’elle démontre. Le nom du visuel,
  s’il faut le donner, tient dans `author`.
- Attendre un recadrage : l’image est montrée entière, centrée, avec des marges si elle n’est pas en 16:9.
  Pour une image qui doit remplir la slide, prends `image`.
- Écrire `disposition` : `media` n’en a aucune, la valeur est ignorée.
- Multiplier les slides sans visuel fourni : au-delà de deux ou trois `media`, `image` et `imagetexte` dans
  la présentation, l’utilisateur se retrouve devant une suite de cadres vides.

## JSON

Un schéma, avec son surtitre, sa légende et sa source :

```json
{ "layout": "media", "eyebrow": "Méthode", "title": "Le parcours d’une école, du diagnostic au suivi.", "content": "Dix-huit mois en moyenne entre le diagnostic et la réception des travaux, dont neuf semaines de chantier.", "author": "Schéma · Cellule d’ingénierie", "notes": "Image à ajouter : le parcours en cinq étapes, du diagnostic à la réception. Le chantier est la partie la plus courte : tout se joue dans la préparation." }
```

Une copie d’écran, légende sur deux lignes, entrée en fondu :

```json
{ "layout": "media", "title": "Une demande d’aide se dépose désormais ==en quatre écrans==.", "content": "Le formulaire en ligne, ouvert aux 42 communes depuis mars 2026.\nLes pièces justificatives sont reprises d’un dossier à l’autre.", "author": "Capture · Portail des aides", "anim": "fondu", "notes": "Image à ajouter : capture du formulaire, écran 2 sur 4. Montrer que le numéro SIRET est déjà rempli." }
```

Une carte, sans légende : le titre porte tout, la source reste seule sous le cadre.

```json
{ "layout": "media", "eyebrow": "Déploiement 2026", "title": "Les trente-deux écoles retenues couvrent ==les quatre bassins de vie==.", "author": "Carte · Service SIG", "notes": "Image à ajouter : carte du territoire, écoles retenues en plein, écoles candidates en creux. Citer les deux communes encore en attente d’arbitrage." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
