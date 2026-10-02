# `contenu` · Texte

> Un titre qui affirme, puis un texte structuré : paragraphes, puces, intertitres. Les puces apparaissent une à une.

## Quand l’employer

- **Dans la matière, tu as trouvé** : un argumentaire en trois à cinq points, sans ordre imposé ; un contexte à
  poser (une ou deux phrases, puis les raisons) ; une explication ou une méthode que rien ne structure (ni
  chiffres, ni dates, ni catégories) ; deux ou trois questions à poser à la salle ; un passage qu’il faut
  résumer plutôt que montrer.
- **Plutôt que** : `faits` si chaque point a un titre, une description et mérite sa carte (trois ou quatre
  réalisations, décisions, constats) ; `colonnes` dès qu’il y a deux camps (avant / après, deux options) ;
  `chiffre` dès que ce qui compte est un nombre (un à quatre) ; `citation` si la matière est la phrase de
  quelqu’un, un témoignage.
- **Pas pour** : une liste qui a un ordre (`etapes`), des dates (`jalons`), des lignes et des colonnes
  (`tableau`) ; un pavé recopié du document : la slide montre, les notes racontent. Jamais plus de deux
  `contenu` d’affilée.

## Structure de l’information

```text
┌────────────────────────────────────────────────────────────┐
│ eyebrow                                                    │
│ title : le message de la slide, deux lignes au plus        │
│                                                            │
│ Paragraphe d’ouverture, une ou deux phrases.               │
│ ◆ **Premier point** : sa précision                         │
│ ◆ **Deuxième point** : sa précision                        │
│ ◆ **Troisième point** : sa précision                       │
│ INTERTITRE                                                 │
│ Paragraphe de conclusion.                                  │
└────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
contenu
├── title      : le message, soixante caractères environ
├── content    : le texte, une ligne par élément
│     ├── paragraphe : une ligne sans préfixe, une ou deux phrases
│     ├── puce       : « - » ou « 1. » en tête ; cinq au plus, une idée par puce
│     └── intertitre : « # » en tête, pour séparer deux groupes de puces
├── eyebrow    : le repère au-dessus du titre (« Contexte », « Partie 02 · Constat ») (facultatif)
└── notes      : ce que le présentateur dit et qui n’est pas écrit
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `title` | Le message de la slide, une affirmation. | Soixante caractères environ ; au-delà de 64, Libre le réduit. |
| `eyebrow` | Le repère : contexte, partie, date. | Deux ou trois mots. Facultatif. |
| `content` | Le texte : paragraphes, puces, intertitres. | Cinq puces au plus ; huit à dix lignes en tout. |
| `disposition` | La composition. | `""`, `colonnes` ou `cote` (voir « Dispositions »). |

Les champs communs (`anim`, `transition`, `notes`, `progressive` — `false` affiche toutes les puces d’un coup) :
voir `references/format-json.md`.

## Syntaxe de `content`

Une ligne du champ = un élément ; les lignes se séparent par `\n`. Ce type n’a pas de cellules `|`.

| En tête de ligne | Élément | Exemple |
| --- | --- | --- |
| rien | Un paragraphe. | `Les écoles pèsent la moitié de l’énergie des bâtiments communaux.` |
| `- ` | Une puce : un losange à la couleur d’accent. | `- **Une obligation** : −40 % d’ici 2030` |
| `1. ` | Une puce numérotée : le nombre écrit s’affiche, numérote dans l’ordre. | `2. Correction climatique par les degrés-jours` |
| `# ` | Un intertitre : capitales, petit corps, couleur d’accent. | `# Des prix orientés à la hausse` |
| `- (nom) ` | Un pictogramme à la place du losange (ou du numéro). | `- (horloge) **Neuf jours** d’accusé de réception` |

- `**gras**` pour le mot-clé d’une puce, `*italique*` pour une réserve, `==surligné==` une fois par slide :
  voir `references/format-json.md`. Les noms de pictogrammes : `references/pictogrammes.md`.
- Un rythme qui marche : un paragraphe d’ouverture, trois à cinq puces, un paragraphe de conclusion. Ou deux
  intertitres `# ` avec deux ou trois puces chacun.
- Les puces apparaissent une à une (`progressive` vaut `true` par défaut) ; les paragraphes et les intertitres
  sont là dès l’entrée de la slide.

## Dispositions

| `disposition` | Composition | La choisir quand |
| --- | --- | --- |
| `""` | Le surtitre, le titre, puis le texte sur une colonne. | Le défaut : un argumentaire de trois à cinq points. |
| `colonnes` | Le titre sur toute la largeur, le texte réparti sur deux colonnes ; un élément ne se coupe pas. | Une longue liste (six à huit puces courtes) ou deux groupes sous intertitres. |
| `cote` | Le surtitre et le titre à gauche, sur deux cinquièmes ; le texte à droite, sur trois cinquièmes. | Un titre court et un texte qui se lit d’un bloc : méthode, annexe, définition. |

```text
colonnes
┌────────────────────────────────────────────────────────────┐
│ title                                                      │
│ INTERTITRE A               │ INTERTITRE B                  │
│ ◆ puce                     │ ◆ puce                        │
│ ◆ puce                     │ ◆ puce                        │
│ ◆ puce                     │ Paragraphe                    │
└────────────────────────────────────────────────────────────┘
```

```text
cote
┌────────────────────────────────────────────────────────────┐
│ eyebrow                │ Paragraphe d’ouverture.           │
│ title, à gauche        │ 1. première étape de la méthode   │
│                        │ 2. deuxième                       │
│                        │ 3. troisième                      │
│                        │ *Réserve en italique.*            │
└────────────────────────────────────────────────────────────┘
```

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : tout s’applique.
  Chaque mise en page compose le texte à sa manière (`cadran` numérote les puces 01, 02… ; `palier` n’éclaire
  que la puce courante et atténue les autres — la première si `progressive` vaut `false`) et ne réduit jamais
  un texte trop long : écris plus court, surtout avec `palier`.
- **Modèles complets** qui redessinent ce type (`compose`) : `revue`, `chantier`, `cimaise`, `aube`, `opale`,
  `bdt`. Dispositions gardées : `colonnes` et `cote` avec `revue`, `chantier` et `bdt` ; `colonnes` seulement
  avec `cimaise`, `aube` et `opale`, qui posent déjà le titre à gauche du texte. Écritures particulières :
  - `revue` : une ligne `Valeur | libellé` (`72 % | des sites équipés` : une valeur courte qui contient un
    chiffre) devient une statistique sous le texte, quatre au plus ;
  - `aube` et `opale` : ce qui précède la liste fait le chapeau, sous le titre ; la liste part à droite (dans
    une carte blanche avec `aube`) ; un ou deux courts paragraphes après la liste — 260 caractères au plus,
    sans intertitre — s’en détachent en conclusion, mise en avant ;
  - `bdt` : le premier paragraphe est le chapeau, en italique ; les intertitres `# ` sont numérotés ;
  - `chantier` : les deux premières puces portent un carré vermillon puis anthracite, les suivantes un carré gris.

  Ces six modèles dessinent les pictogrammes. Les autres modèles complets (`marqueur`, `tampon`, `pastille`,
  `bloc`, `anneau`, `crayon`) habillent le rendu Libre : dispositions et pictogrammes s’appliquent, mais une
  ligne `Valeur | libellé` s’y affiche telle quelle.
- **Plateforme** (`"modele": "plateforme"`) : `colonnes` gardée ; `cote` ignorée, le titre est déjà à gauche
  du texte. Pas de pictogramme : le mot `(nom)` est retiré sans s’afficher.

## Pièges

- Le caractère `|` dans une phrase : en Libre il s’affiche ; avec `revue`, si ce qui précède le `|` fait
  16 caractères au plus et contient un chiffre, la ligne devient une statistique. Écris « ou », un tiret,
  deux points.
- Plus de cinq puces : passe en `colonnes`, scinde en deux slides, ou prends le type qui montre la structure
  (`etapes`, `faits`, `tableau`).
- Un titre de plus de 64 caractères se réduit en Libre ; les mises en page `cadran`, `marge`, `palier` et
  `grille` ne réduisent rien, ni le titre ni le texte.
- Une numérotation s’écrit dans l’ordre, `1. `, `2. `, `3. ` : c’est le nombre écrit qui s’affiche, TalkNote
  ne recompte pas. Un pictogramme sur une ligne numérotée remplace le numéro.
- Un pictogramme inconnu, `(2025)` ou `(rénovation)`, reste du texte : n’écris que des noms de
  `references/pictogrammes.md`.
- Le détail va dans `notes`, pas dans un sixième paragraphe : la slide se lit en dix secondes.
- `cote` est ignorée par `plateforme`, `cimaise`, `aube` et `opale` : la slide prend leur composition, rien
  ne casse.

## JSON

Disposition par défaut : un paragraphe d’ouverture, trois puces avec pictogrammes, une conclusion.

```json
{ "layout": "contenu", "eyebrow": "Constat", "title": "Le guichet unique ne tient pas encore sa promesse.", "content": "Ouvert en janvier, le guichet reçoit un tiers des demandes de subvention ; les autres arrivent encore par courrier ou par courriel.\n- (document) **Des formulaires trop longs** : 42 champs, dont 15 déjà connus du service\n- (horloge) **Neuf jours d’accusé de réception**, contre deux annoncés\n- (groupe) **Des agents sollicités deux fois** : au guichet, puis dans l’outil métier\nTrois chantiers, présentés ensuite, visent à tenir la promesse d’ici l’été.", "notes": "Source : bilan du service instruction, mars 2026. Insister sur la troisième puce : c’est elle qui use les équipes. Enchaîner sur les trois chantiers." }
```

Deux colonnes sous intertitres, toutes les puces affichées d’un coup :

```json
{ "layout": "contenu", "eyebrow": "Ce qui change", "title": "Le nouveau règlement engage la Région sur deux fronts.", "disposition": "colonnes", "progressive": false, "content": "# Pour les demandes\n- Un dossier unique, quel que soit le dispositif\n- Des pièces justificatives fournies une seule fois\n- Un accusé de réception sous deux jours\n# Pour le suivi\n- Un tableau de bord partagé avec la commune\n- Un référent nommé pour chaque dossier\n- Un versement dans les trente jours après décision", "notes": "Les deux colonnes se lisent l’une après l’autre : d’abord ce que la commune envoie, ensuite ce qu’elle reçoit. Le délai de versement est l’engagement le plus attendu des maires." }
```

Titre à gauche, une méthode numérotée à droite :

```json
{ "layout": "contenu", "eyebrow": "Annexe 1", "title": "Comment les économies d’énergie sont calculées.", "disposition": "cote", "content": "Les consommations sont comparées à l’année de référence, la dernière année scolaire complète avant travaux.\n1. Relevé mensuel des compteurs de gaz, de fioul et d’électricité\n2. Correction climatique par les degrés-jours de la station la plus proche\n3. Ramené au mètre carré chauffé, hors logements de fonction\n4. Comparaison avec un groupe témoin d’écoles en attente de travaux\n*Les chiffres de 2026 seront consolidés en juin 2027, après un hiver complet.*", "notes": "Slide d’annexe : ne la montrer que si la question de la méthode est posée." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
