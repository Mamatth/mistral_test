# `section` · Section

> Ouverture de partie : un repère, le nom de la partie en très grand, une phrase d’accroche. Le fond « temps fort » la met sur la couleur d’accent, une ou deux fois par présentation.

## Quand l’employer

- **Dans la matière, tu as trouvé** : un plan en plusieurs parties (chapitres d’un rapport, rubriques d’un dossier, points d’un ordre du jour) ; un changement de sujet net entre deux blocs (après le cadre, les réalisations ; après le bilan, la suite) ; une question à poser à la salle, qui ouvre un temps d’échange ; des annexes à mettre à part ; un moment que la présentation doit marquer, la partie décisive.
- **Plutôt que** : `titre`, qui n’ouvre que la présentation, une seule fois, en première slide ; `sommaire`, qui annonce toutes les parties d’un coup, quand la section n’en ouvre qu’une, à sa place ; `image` quand la photo est le message et que le titre s’y incruste, alors que la section en `photo` garde son texte à gauche et fait de la photo l’annonce de ce qui suit.
- **Pas pour** : une présentation courte de six à huit slides, où les sections coupent le rythme ; porter du contenu : deux ou trois puces dans `content` en font un `contenu` déguisé.

Structure type d’une présentation : `titre` → `sommaire` (dès dix slides) → pour chaque partie, une `section` puis ses slides → `fin`. Surtitres des sections : `Partie 01`, `Partie 02`…

## Structure de l’information

```text
┌────────────────────────────────────────────────────────────┐
│                                                            │
│                                                            │
│   ── EYEBROW (PARTIE 02)                                   │
│   title : le nom de la partie,                             │
│   en très grand, une ou deux lignes                        │
│   content : la phrase d’accroche                           │
│                                                            │
│                                                            │
└────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
section
├── title      : le nom de la partie, deux à six mots
├── eyebrow    : le repère, « Partie 02 » ; c’est son nombre que `numero` agrandit
├── content    : l’accroche, une phrase ; deux paragraphes au plus
├── fond       : "rouge" pour le temps fort (facultatif)
└── notes      : ce que le présentateur dit ; la photo voulue, en `photo`
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `title` | Le nom de la partie, en très grand. `==mots==` possible. | Court : au-delà de 32 caractères le corps baisse, au-delà de 64 encore ; deux lignes au plus. |
| `eyebrow` | Le repère de la partie : `Partie 02`, `02`, `Annexes`. Écrit en capitales espacées, un filet devant. | Avec `numero`, il doit contenir un nombre, de deux chiffres de préférence. |
| `content` | L’accroche : ce que la partie va montrer. | Une ou deux phrases, chaque ligne un paragraphe. Sans puce ni `|`. |
| `fond` | `""` (fond du thème) ou `"rouge"` : le temps fort, sur la couleur d’accent, le texte dans celle des couleurs du thème qui s’y lit. La valeur s’appelle `rouge` quel que soit le thème. | Une ou deux sections par présentation. |
| `disposition` | `""`, `numero` ou `photo` (voir « Dispositions »). | |
| `image` | La photo de la disposition `photo` (et celle que `bloc`, `anneau`, `crayon` et `cimaise` posent d’office). | Laisse `""` et décris la photo dans `notes` : `Image à ajouter : …` (voir `references/images.md`). |
| `horsSommaire` | `true` tient la section hors d’un `sommaire` qui suit les sections : pour des annexes. | Sans guillemets. Absent sinon. |

Les champs communs (`anim`, `transition`, `notes`, `progressive`…) : voir `references/format-json.md`.

## Syntaxe de `content`

Pas de syntaxe structurée : du texte courant, une phrase par ligne, avec `**gras**` et `==surligné==` si utile.

- `Vingt-six écoles livrées en deux étés, et une méthode qui tient la route.` : l’accroche, en un paragraphe.
- `Tout ne s’est pas déroulé comme prévu.\nTrois difficultés appellent une décision du comité.` : deux paragraphes, la limite raisonnable.
- Une puce `- ` ou un intertitre `# ` perd sa marque en Libre et devient un paragraphe ; certains modèles complets en font autre chose (voir « Selon le modèle »). Écris des phrases.
- `(nom)` en tête de ligne est retiré sans s’afficher : l’accroche ne dessine pas de pictogramme.

## Dispositions

| `disposition` | Composition | La choisir quand |
| --- | --- | --- |
| `""` | Numéro discret : le surtitre en repère au-dessus du titre, le tout centré en hauteur, aligné à gauche. | Par défaut : une partie parmi d’autres. |
| `numero` | Le premier nombre du surtitre en très grand, tracé en contour dans la couleur d’accent ; le reste du surtitre au-dessus, le titre et l’accroche posés sur sa droite, en léger chevauchement. | Un plan numéroté, une partie qui doit marquer. Le surtitre porte un nombre : sans nombre, la section reste discrète. |
| `photo` | Le surtitre, le titre et l’accroche à gauche ; une photo à fond perdu sur la moitié droite (48 %). | Une image annonce ce qui suit : le chantier, le lieu, l’équipe. |

```text
numero
┌────────────────────────────────────────────────────────────┐
│   ── PARTIE                                                │
│   ┌──┐  ┌──┐                                               │
│   │  │  │  │                                               │
│   │0 │  │2 │   title : le nom de la partie, sur le nombre  │
│   └──┘  └──┘   content : l’accroche                        │
└────────────────────────────────────────────────────────────┘
```

```text
photo
┌──────────────────────────────┬─────────────────────────────┐
│                              │                             │
│   ── PARTIE 02               │                             │
│   title : le nom de la partie│      image, à fond perdu    │
│   content : l’accroche       │      (cadre vide sans photo)│
│                              │                             │
└──────────────────────────────┴─────────────────────────────┘
```

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : tout s’applique ; avec `marge`, le surtitre passe dans la gouttière, le repère et son filet disparaissent de la slide. `marqueur` habille ce rendu sans le redessiner : tout s’applique aussi.
- **Modèles complets** qui redessinent la section : `revue`, `chantier`, `tampon`, `pastille`, `bloc`, `anneau`, `crayon`, `cimaise`, `aube`, `opale`, `bdt`. Le temps fort (`fond`) vaut partout. Dispositions gardées :

  | Modèle | `numero` | `photo` | Écriture particulière |
  | --- | --- | --- | --- |
  | `revue` | ignorée (le grand chiffre de chapitre est déjà là) | oui | une ligne `- ` de `content` devient une sous-partie numérotée (1.1, 1.2…) ; les autres lignes font le chapeau |
  | `chantier` | oui | oui | une ligne `- Titre | texte` devient une fiche numérotée ; le premier mot du titre est posé en bloc |
  | `tampon` | ignorée | oui (la photo sur la bande de droite) | le rang de la section, suivi de sa pastille |
  | `pastille` | oui | oui (la photo prend le grand disque) | une ligne `Valeur | libellé` (valeur courte avec un chiffre) devient une statistique, trois au plus |
  | `bloc` | oui | ignorée (la photo est toujours posée) | le surtitre n’est pas affiché : « 02 / 05 » (rang / total) le remplace ; la liste des parties, celle-ci en cours |
  | `anneau` | oui | ignorée (la photo est toujours posée) | la frise des parties sous le titre |
  | `crayon` | oui | ignorée (la photo est toujours posée) | « 02 / 05 » au-dessus du titre, le surtitre écrit à la verticale à droite ; le premier paragraphe de `content` passe à l’encre |
  | `cimaise` | ignorée | ignorée | l’`image` remplit le numéro évidé ; un `eyebrow` de 18 caractères au plus s’empile en couleur sur le titre |
  | `aube` | ignorée | ignorée (pas de photo) | une icône en tête du titre, `(fusée) Notre cap`, est dessinée en grand ; sans icône, le numéro ; en temps fort, le dégradé prend toute la slide |
  | `opale` | ignorée | ignorée (pas de photo) | le numéro à l’encre sur les disques, qui prennent toute la slide |
  | `bdt` | ignorée | oui (la photo à droite de l’hexagone) | les sections prennent tour à tour les couleurs de chapitre |

  Avec `bloc`, `anneau`, `crayon` et `cimaise`, la section prend une photo sans changer de disposition : `image` vide et `Image à ajouter : …` dans `notes` ; sans photo, `bloc`, `anneau` et `cimaise` gardent leur forme vide, `crayon` n’en dessine aucune.
  Le grand numéro de `revue`, `tampon` et `bdt` est le rang de la section parmi les sections (01, 02…), pas le nombre du surtitre. `chantier`, `pastille`, `bloc`, `anneau` et `crayon` prennent au contraire le premier nombre du surtitre, et le rang seulement s’il n’y en a pas ; `cimaise`, `aube` et `opale` prennent ce nombre s’il a deux chiffres au plus, sinon le rang. Le « 02 / 05 » de `bloc` et de `crayon` reste, lui, le rang. Numérote donc les surtitres dans l’ordre des sections.
- **Plateforme** (`"modele": "plateforme"`) : `numero` et `photo` gardées ; la section est sur fond sombre, le logo en filigrane, et le temps fort la passe en rouge. Pas de pictogramme : `(nom)` est retiré sans s’afficher.

## Pièges

- `numero` sans nombre dans le surtitre : la section reste discrète. Écris `Partie 02` ou `02`. Une année (`2027`) fait un nombre long, dessiné plus petit en Libre ; `cimaise`, `aube` et `opale` lui substituent le rang, les autres modèles complets l’affichent en entier.
- `"fond": "rouge"` sur chaque section : plus de temps fort. Une ou deux, pour la partie décisive. Toute autre valeur que `rouge` est une erreur.
- Des puces dans `content` : en Libre elles deviennent des paragraphes ; `revue` en fait des sous-parties, `chantier` des fiches. La section n’est pas une slide de contenu : une accroche, et le détail dans les slides qui suivent.
- Un titre long : au-delà de 32 caractères il rétrécit, au-delà de 64 davantage. Le nom de la partie tient en deux à six mots ; pas de `|` dedans ; pour un temps d’échange, la question tient elle aussi en deux lignes.
- `photo` avec une adresse web dans `image` : hors ligne, la photo ne se charge pas et le cadre reste vide. Laisse `""` et décris la photo dans `notes`.
- Un surtitre qui contredit l’ordre (`Partie 03` sur la deuxième section) : `revue`, `tampon`, `bloc`, `crayon` et `bdt` affichent le rang, `02`, à côté de ton `03`. Avec `"suitSections": true` sur le `sommaire`, le titre de chaque section y est repris sans `==` ni point final ; une section en `horsSommaire` n’y figure pas.

## JSON

La disposition par défaut, avec des notes :

```json
{ "layout": "section", "eyebrow": "Partie 01", "title": "Le programme en bref.", "content": "Trois rivières, quarante-deux communes, soixante-dix écoles primaires : un patrimoine ancien, énergivore et mal adapté aux étés qui viennent.", "notes": "Poser le décor en une minute : l’échelle du territoire, l’âge du bâti, la contrainte des étés. Annoncer que les chiffres viennent dans la partie suivante." }
```

Le numéro en grand, sur fond « temps fort » :

```json
{ "layout": "section", "eyebrow": "Partie 04", "title": "Ce qui résiste.", "content": "Deux chantiers en retard, un surcoût à arbitrer.", "disposition": "numero", "fond": "rouge", "transition": "volet", "notes": "Changer de ton : c’est ici que le comité doit décider. Ne pas minimiser les retards, ils sont expliqués slide suivante." }
```

Avec photo, pour l’annexe d’une présentation dont le sommaire suit les sections :

```json
{ "layout": "section", "eyebrow": "Annexes", "title": "Pour aller plus loin.", "content": "Méthode de calcul et plan de financement détaillé.", "disposition": "photo", "image": "", "horsSommaire": true, "anim": "fondu", "notes": "Image à ajouter : une salle de classe rénovée, lumière du matin. Ne projeter cette partie que si des questions portent sur la méthode." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
