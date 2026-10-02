# `image` · Photo pleine page

> Une photo occupe toute la slide et le titre s’incruste dedans : l’image porte le propos, le texte le nomme.

## Quand l’employer

- **Dans la matière, tu as trouvé** : une photographie forte qui vaut à elle seule un argument (un territoire,
  un site, un chantier, des usagers) ; un moment de respiration à ménager entre deux parties denses ; une
  phrase de cadrage que l’on peut lire sur une image, sans rien de plus ; deux ou trois repères de contexte
  qui tiennent sur une ligne (« 42 communes · 58 000 habitants ») ; l’ouverture ou la clôture d’une séquence,
  quand la photo est le sujet et le texte le commentaire.
- **Plutôt que** : `section` quand il s’agit d’ouvrir une partie numérotée, avec son surtitre et son plan
  (`image` n’a pas de surtitre en rendu Libre) ; `imagetexte` quand la photo n’occupe que la moitié de la
  slide et qu’il y a une légende, des puces et un crédit à lire à côté ; `titre` pour la couverture, qui porte
  la date et l’auteur ; `media` quand le visuel doit être montré en entier, jamais recadré.
- **Pas pour** : un schéma, une capture ou une infographie, que le recadrage plein cadre amputerait ; une
  photo accompagnée d’un commentaire de plusieurs lignes, illisible en blanc sur une image.

## Structure de l’information

```text
┌────────────────────────────────────────────────────────────┐
│                                                            │
│            image : la photo, recadrée plein cadre          │
│                                                            │
│                                                            │
│  ░░░░░░░░░░░░  voile sombre, du bas vers le haut  ░░░░░░░  │
│  title : le message, en blanc sur la photo                 │
│  content : une ligne de contexte                           │
└────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
image
├── image      : la photo, recadrée pour remplir la slide ; laisse-la vide
├── title      : le message incrusté, une phrase courte
├── content    : une ou deux lignes de contexte, sous le titre
└── notes      : « Image à ajouter : … », puis ce que le présentateur dit
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `image` | La photo. Recadrée pour remplir la slide, centrée : les bords sont rognés. | Laisse `""` : la slide montre un cadre en pointillés et l’utilisateur y dépose son fichier. Écris `Image à ajouter : …` dans `notes` (voir `references/images.md`). Jamais d’adresse web. |
| `title` | Le message, incrusté en blanc sur la photo. `==surligné==` possible. | Une phrase courte. Au-delà de 64 caractères il passe de 68 à 50 px ; avec Plateforme il se replie sur 18 caractères de large et descend vite. |
| `content` | Le contexte, sous le titre, en blanc plus discret. | Une ou deux lignes simples. Chaque ligne s’empile sous le titre, sur la photo. |
| `notes` | Ce que montre l’image voulue, puis ce que le présentateur ajoute. | La seule place où décrire la photo à fournir. |

`image` n’emploie ni `eyebrow` ni `author` : le rendu Libre et Plateforme les laissent de côté. Seul le
modèle `bdt` les reprend — le surtitre sous le titre de la tête ou au centre du voile, le crédit à la fin de
la légende — et un surtitre y suffit à empêcher la photo pleine page. `content2`, `content3`, `accent`, `imageRight`, `imageWidth`, `cadre` et `ecrans`
n’y servent à rien. `progressive` non plus : une photo pleine page n’a pas de puce à faire apparaître. Les
champs communs (`anim`, `transition`, `notes`) : voir `references/format-json.md`. `"anim": "fondu"` convient
à une image qui doit s’installer.

## Syntaxe de `content`

- Des lignes simples, séparées par `\n` : elles s’empilent sous le titre. `**gras**`, `*italique*`,
  `==surligné==` s’appliquent (syntaxe du texte : voir `references/format-json.md`).
  Exemple : `Vallée des Trois Rivières · 42 communes · 58 000 habitants`.
- **Pas de puce `- `** : en Libre le tiret est retiré et la ligne devient un paragraphe ordinaire ; sous
  Plateforme elle devient une vraie puce, un point dans la couleur d’accent posé sur la photo. Un chiffre
  juste après le tiret (`- 26 °C`) reste du texte partout. Écris une phrase par ligne, ou un seul fil de
  repères séparés par des points médians.
- **Pas d’intertitre `# `** : en Libre le dièse est retiré sans que la ligne change d’allure ; sous
  Plateforme il s’affiche tel quel, au début de la ligne.
- Pas de pictogramme `(nom)` dans `content` : aucun gabarit n’en dessine ici, le mot serait retiré sans
  s’afficher. En tête du `title`, en revanche, il est dessiné (sauf avec Plateforme).
- Une ligne suffit presque toujours : deux au plus. Le texte est posé sur la photo, chaque ligne de plus
  masque l’image et perd en lisibilité.
- Pas de `|` : `image` n’a pas de cellule.

## Dispositions

| `disposition` | Composition | La choisir quand |
| --- | --- | --- |
| `""` | Titre et contexte en bas, sur un dégradé sombre qui monte du bas. | Par défaut. La photo reste lisible en haut : le sujet peut y être cadré. |
| `centre` | Photo assombrie d’un voile uni, titre et contexte centrés au milieu. | La phrase prime sur l’image, ou la photo n’a pas de zone calme. |
| `haut` | Titre et contexte en haut, le dégradé sombre descend du haut. | Le sujet de la photo occupe le bas du cadre. |

```text
centre                         haut
┌───────────────────────────┐  ┌───────────────────────────┐
│░░░░░░░ voile uni ░░░░░░░░░│  │ title                     │
│░░░░░░░░░ title ░░░░░░░░░░░│  │ content                   │
│░░░░░░░ content ░░░░░░░░░░░│  │        photo              │
└───────────────────────────┘  └───────────────────────────┘
```

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : les trois
  dispositions s’appliquent. Sur une photo pleine page, les mises en page effacent leur décor (numéro géant,
  gouttière, trame) et laissent l’image aller bord à bord.
- **Modèles complets qui redessinent ce type** : `cimaise` (la photo pâlie en fond de slide, reprise nette
  dans une fenêtre à droite, le titre, un filet corail et le contexte à gauche, à l’encre du thème : le texte
  n’est donc pas incrusté sur la photo ; il ignore `centre` et `haut`) et `bdt` (il garde
  `centre`, ignore `haut` ; en `centre`, la photo occupe la slide et le titre, le surtitre, le contexte et
  `author` se centrent sur un voile ; sans titre, sans surtitre et sans texte, la photo occupe seule la
  slide ; sinon elle se range sous la tête du modèle, avec sa légende à côté). Les autres modèles complets
  habillent le rendu Libre : le dégradé devient un voile uni sur toute la photo, le titre perd son ombre
  portée et le décor du modèle disparaît.
- **Plateforme** (`"modele": "plateforme"`) : garde `centre` et `haut`. Le titre s’incruste en bas à gauche
  et `content` devient un crédit en petites capitales, à droite du titre (centré sous lui en `centre`). La
  marque et le numéro de page restent en haut ; pas de pictogramme.

## Pièges

- Une puce `- ` dans `content` : le tiret disparaît en Libre, mais Plateforme la dessine en vraie puce
  colorée sur la photo ; un `# ` fait l’inverse, invisible en Libre et visible sous Plateforme. Des lignes
  simples, toujours.
- Un `eyebrow` ou un `author` écrit par habitude : ils ne s’affichent pas, sauf avec `bdt`. Ce qu’ils
  portaient va dans `title`, dans `content` ou dans `notes`.
- Un titre long : au-delà de 64 caractères il rétrécit, et sous Plateforme il se replie sur quatre ou cinq
  lignes qui couvrent la photo.
- Trois lignes de contexte : le texte devient un pavé blanc posé sur l’image, et l’image ne sert plus.
- Oublier que l’image est recadrée : un visuel en hauteur, un schéma ou une capture y perdent leurs bords.
  Pour montrer un visuel entier, prends `media`.
- Laisser `image` vide sans le dire : la slide affiche un cadre en pointillés, sans voile, le titre revenant
  en bas à gauche dans la couleur du thème, même en `centre` ou en `haut`. Décris toujours la photo attendue
  dans `notes` — et vois `references/images.md` pour le nombre de slides à photo que supporte une
  présentation.

## JSON

La disposition par défaut : une image d’ouverture, le titre et les repères en bas.

```json
{ "layout": "image", "title": "Un territoire rural, ==des écoles au cœur des villages==.", "content": "Vallée des Trois Rivières · 42 communes · 58 000 habitants", "anim": "fondu", "notes": "Image à ajouter : vue aérienne d’un village et de son école, en fin de journée. Laisser l’image quelques secondes : la plupart des communes n’ont qu’une seule école." }
```

`centre` : la phrase prime, la photo passe derrière un voile.

```json
{ "layout": "image", "title": "Trois cours d’école devenues ==des îlots de fraîcheur==.", "content": "Désimperméabilisation, arbres et noues : jusqu’à 8 °C de moins au sol l’après-midi.", "disposition": "centre", "anim": "fondu", "notes": "Image à ajouter : une cour plantée, en plein été, avec des enfants à l’ombre. Les trois cours ont été dessinées avec les élèves." }
```

`haut` : le sujet occupe le bas de la photo, le titre s’installe au-dessus.

```json
{ "layout": "image", "title": "Le chantier de la Vergne, ==livré en neuf semaines==.", "content": "Juillet et août 2026, école ouverte dès la rentrée.", "disposition": "haut", "transition": "fondu", "notes": "Image à ajouter : la façade en cours d’isolation, échafaudage monté, vue depuis la cour." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
