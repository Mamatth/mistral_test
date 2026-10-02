# `imagetexte` · Photo + légende

> Une photo et son contexte, côte à côte : ce que montre l’image, ce qu’il faut en retenir, et son crédit.

## Quand l’employer

- **Dans la matière, tu as trouvé** : une photo de terrain (un site, un chantier, un équipement) et le
  paragraphe qui l’explique ; une réalisation à montrer et à commenter en deux ou trois points ; une visite,
  une inauguration, une expérimentation racontée par l’image ; un lieu dont il faut donner le contexte avant
  d’en tirer des chiffres ; une image dont la source ou l’auteur doivent être affichés.
- **Plutôt que** : `media` quand le visuel est un schéma, une capture ou une infographie qu’il faut lire de
  près — il occupe alors la slide entière, la légende dessous ; `image` quand la photo doit être immersive et
  le texte réduit à un titre en incrustation ; `galerie` dès trois photos à comparer ou à enchaîner (avant,
  pendant, après) ; `citation` quand c’est la parole rapportée qui porte, et non l’image.
- **Pas pour** : une slide de texte à laquelle on ajouterait une photo d’illustration — prends `contenu` ; une
  capture d’interface, qui appelle `maquette` (elle la pose dans un cadre d’appareil) ou `media`.

## Structure de l’information

```text
┌────────────────────────────────────────────────────────────┐
│░░░░░░░░░░░░░░░░░░░░░░░░░░ eyebrow                          │
│░░░░░░░░░░░░░░░░░░░░░░░░░░                                  │
│░░░░░░░ image ░░░░░░░░░░░░ title : le message               │
│░░░░ 46 % de la largeur ░░ ────                             │
│░░░░░░░░░░░░░░░░░░░░░░░░░░ content : la légende             │
│░░░░░░░░░░░░░░░░░░░░░░░░░░ - puce                           │
│░░░░░░░░░░░░░░░░░░░░░░░░░░ - puce                           │
│░░░░░░░░░░░░░░░░░░░░░░░░░░ AUTHOR : LE CRÉDIT               │
└────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
imagetexte
├── image      : la photo, à gauche, sur presque la moitié de la slide
├── title      : le message que dit la photo, une phrase
├── content    : la légende — un paragraphe, puis deux ou trois puces
├── author     : le crédit ou la source, une ligne (facultatif)
├── eyebrow    : repère court au-dessus du titre (facultatif)
├── imageRight : true pose la photo à droite (facultatif)
├── imageWidth : etroite, normale ou large (facultatif)
└── notes      : la photo à ajouter, et ce que le présentateur raconte
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `image` | La photo elle-même. | Laisse `""` et écris `Photo à ajouter : …` dans `notes` (voir `references/images.md`). Sans photo, un cadre en pointillés tient la place. |
| `title` | Le message que porte la photo, pas son étiquette. | Une phrase. Au-delà de 64 caractères, le corps du titre est réduit ; les modèles complets le tassent par paliers. |
| `content` | La légende : ce que montre l’image, puis ce qu’on en retient. | Un paragraphe et deux ou trois puces au plus : le texte n’a que la moitié de la slide. |
| `author` | Le crédit ou la source de la photo. | Facultatif, une ligne. S’affiche en petites capitales sous la légende : `Photo · Mairie de La Vergne`. |
| `eyebrow` | Surtitre : le lieu, la date, le volet du programme. | Facultatif, court (`École pilote · La Vergne`). |
| `imageRight` | Place la photo à droite au lieu de la gauche. | `true` ou `false`, sans guillemets. Alterner d’une slide photo à l’autre évite la monotonie. |
| `imageWidth` | Largeur de la photo. | `etroite` (34 % de la slide), `normale` (46 %, le défaut) ou `large` (58 %). Sans accent : `etroite`. Aucune autre valeur. |

Ce type n’a ni `disposition`, ni `content2`, ni `content3` : ils ne seraient pas lus. Les champs communs
(`anim`, `transition`, `notes`, `progressive`) : voir `references/format-json.md`. Les puces de la légende
apparaissent une à une, sauf `"progressive": false`.

Avec `"imageRight": true` et `"imageWidth": "large"`, la même slide :

```text
┌────────────────────────────────────────────────────────────┐
│ eyebrow                  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░│
│ title : le message       ░░░░░░░░░░░ image ░░░░░░░░░░░░░░░░│
│ ────                     ░░ 58 % de la largeur ░░░░░░░░░░░░│
│ content : la légende     ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░│
│ AUTHOR                   ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░│
└────────────────────────────────────────────────────────────┘
```

## Syntaxe de `content`

- La syntaxe commune du texte (voir `references/format-json.md`) : une ligne par paragraphe (`\n` dans le
  JSON), `- ` pour une puce, `1. ` pour un numéro, `# ` pour un intertitre, `**gras**`, `*italique*`,
  `==surligné==`, `(nom)` en tête de ligne pour un pictogramme.
- La forme qui marche : un paragraphe qui décrit la scène, puis deux ou trois puces qui en tirent les
  enseignements. Exemple :
  `Isolation en fibre de bois et ventilation double flux.\n- Consommation divisée par deux\n- 26 °C au plus fort de juillet`
- Pas de cellules ici : n’emploie pas `|` dans la légende. Une exception utile, dans une présentation en
  `revue` : une ligne comme `72 % | des écoles équipées` — une valeur de 16 caractères au plus contenant un
  chiffre, sans puce ni intertitre en tête — est retirée du texte et dessinée en statistique sous la légende,
  quatre au plus. Avec tout autre modèle, la barre s’afficherait telle quelle.
- Le crédit va dans `author`, pas en dernière ligne de `content` : il a son propre dessin.

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : la composition
  ci-dessus, la photo à fond perdu d’un bord à l’autre de sa colonne ; `imageRight` et `imageWidth`
  s’appliquent. En `large`, le titre et la légende passent en plus petit corps.
- **Modèles complets qui redessinent ce type** (`compose`) : `revue`, `chantier`, `cimaise`, `aube`, `opale`,
  `bdt`. Ce type n’ayant pas de disposition, il n’y a rien à retenir de ce côté ; les écritures particulières :
  - `revue` : la photo d’un côté, le texte de l’autre, comme en Libre — photo à gauche par défaut, à droite
    avec `imageRight`, la colonne de texte restant la plus large. Sous la photo, une ligne de repère : le
    numéro de figure (`Fig. 03`, le rang de la slide parmi les slides `imagetexte`, `media` et `image` de la
    présentation) à gauche, le crédit d’`author` à droite. Une ligne `Valeur | libellé` de la légende devient
    une statistique, posée en bas de la colonne de texte.
  - `chantier` : la photo pleine hauteur d’un côté, le texte de l’autre ; `imageRight` la place à droite ;
    chaque puce prend un carré de couleur, où se dessine son pictogramme.
  - `cimaise` : la photo d’abord, un filet corail sous le titre, le crédit dessous ; `imageRight` et
    `imageWidth` s’appliquent ; un `eyebrow` de 18 caractères au plus s’empile en couleur sur le titre.
  - `aube` : la photo dans le dégradé du modèle, le crédit posé dessus ; `imageRight` et `imageWidth`
    s’appliquent.
  - `opale` : la photo remplit la slide, floutée derrière le verre, et une fenêtre nette s’y ouvre ;
    `imageRight` et `imageWidth` n’y changent rien.
  - `bdt` : le titre en tête de slide, le surtitre dessous, la photo dans son cadre et la légende à côté ;
    `imageRight` et `imageWidth` sont sans effet, les puces deviennent de simples paragraphes et aucun
    pictogramme n’est dessiné.
  Les autres modèles complets (`marqueur`, `tampon`, `pastille`, `bloc`, `anneau`, `crayon`) habillent le
  rendu Libre : `imageRight` et `imageWidth` s’y comportent comme en Libre.
- **Plateforme** (`"modele": "plateforme"`) : la photo et le pavé de texte côte à côte, surtitre, titre,
  légende puis crédit ; `imageRight` s’applique, la largeur non — le modèle impose ses proportions. Aucun
  pictogramme n’y est dessiné.

## Pièges

- Une légende de huit lignes : le texte tient sur moins de la moitié de la slide. Un paragraphe et deux ou
  trois puces ; le reste va dans les `notes`.
- Un `|` dans une phrase de la légende : il s’affiche tel quel, et avec `revue` il transforme la ligne en
  statistique. Écris la phrase sans barre.
- `imageWidth` mal écrit (`étroite`, `normal`, `larges`) : TalkNote retombe sur `normale` sans rien dire.
  Les trois valeurs sont `etroite`, `normale`, `large`.
- `"imageRight": "true"` entre guillemets : la valeur n’est gardée que si c’est un booléen `true`.
- Une `disposition` écrite sur cette slide : ce type n’en a pas, elle serait ignorée. La composition se règle
  par `imageRight` et `imageWidth`.
- `"image"` rempli d’une adresse ou d’un nom de fichier, ou trop de slides à photo : les deux règles sont
  dans `references/images.md`. Ici : `"image": ""`, et la photo attendue décrite dans `notes`.

## JSON

La composition par défaut : photo à gauche, largeur normale.

```json
{ "layout": "imagetexte", "eyebrow": "École pilote · La Vergne", "title": "L’école de la Vergne, un an après.", "content": "Isolation par l’extérieur en fibre de bois, menuiseries remplacées, ventilation double flux et panneaux solaires en toiture.\n- Consommation divisée par deux\n- 26 °C au plus fort de la canicule de juillet\n- Neuf semaines de travaux, rentrée à la date prévue", "author": "Photo · Cellule d’ingénierie, juin 2026", "notes": "Photo à ajouter : la façade sud rénovée, prise depuis la cour. Première école livrée, en 2025 : elle sert de référence pour toutes les suivantes. Enchaîner sur le calendrier de chantier." }
```

Photo à droite et large, une légende en prose seule : l’image porte le propos.

```json
{ "layout": "imagetexte", "eyebrow": "Chantier · Été 2026", "title": "Neuf semaines entre deux rentrées.", "content": "Tout le programme repose sur une contrainte : libérer l’école le 1er juillet, la rendre le 31 août. Les lots sont préparés dès l’hiver et les matériaux stockés avant la fin des cours.", "author": "Photo · Groupe scolaire des Tilleuls", "imageRight": true, "imageWidth": "large", "notes": "Photo à ajouter : l’échafaudage monté sur la façade, cour vide, plein été." }
```

Photo étroite, texte en avant, pictogrammes en tête des puces.

```json
{ "layout": "imagetexte", "eyebrow": "Réseau de chaleur", "title": "Une chaufferie bois pour ==quatre équipements== du bourg.", "content": "Mise en service en novembre 2026, elle alimente l’école, la salle des fêtes, la mairie et le gymnase.\n- (feuille) 210 tonnes de CO₂ évitées chaque année\n- (euro) Facture de chauffage divisée par trois\n- (arbre) Bois issu des forêts du département", "author": "Photo · Syndicat d’énergie", "imageWidth": "etroite", "anim": "fondu", "notes": "Photo à ajouter : le silo à plaquettes et la chaufferie, vue extérieure. Rappeler que le réseau peut accueillir deux bâtiments de plus." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
