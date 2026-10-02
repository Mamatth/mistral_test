# `galerie` · Galerie

> Trois à six photos rangées côte à côte, chacune avec son titre et sa légende : ce qu’une suite
> d’images raconte — avant, pendant, après.

## Quand l’employer

- **Dans la matière, tu as trouvé** : une même chose photographiée à plusieurs moments (avant travaux,
  chantier, livraison) ; un reportage ou un album de visite, d’inauguration, de terrain ; trois à six
  lieux, sites ou équipements d’un même réseau, chacun avec une ligne de description ; une comparaison
  qui ne tient qu’en images (deux aménagements, deux matériaux, deux implantations) ; une page où
  plusieurs visuels portent chacun leur courte légende.
- **Plutôt que** : `imagetexte` quand il n’y a qu’une photo et que le texte à côté se développe en
  plusieurs lignes ou en puces ; `image` quand une seule photo doit occuper toute la slide, le titre
  incrusté dessus ; `faits` quand ce sont les constats qui portent le propos et que les images
  n’ajouteraient rien — `faits` fait des cartes de texte, `galerie` fait des cadres photo.
- **Pas pour** : une seule photo (prends `imagetexte`, `image` ou `media`) ; des captures d’une
  application, qui ont leur cadre avec `maquette` ; plus de six photos, les suivantes n’étant pas
  affichées.

## Structure de l’information

```text
┌────────────────────────────────────────────────────────────┐
│ eyebrow                                                    │
│ title : ce que la suite d’images démontre                  │
│                                                            │
│  ┌──────────┐   ┌──────────┐   ┌──────────┐                │
│  │ Photo 1  │   │ Photo 2  │   │ Photo 3  │                │
│  └──────────┘   └──────────┘   └──────────┘                │
│   Titre          Titre          Titre                      │
│   Légende        Légende        Légende                    │
└────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
galerie
├── title      : ce que la suite d’images démontre (soixante caractères environ)
├── eyebrow    : le lieu, le projet, la date (facultatif)
├── content    : une ligne par photo, trois à six
│     ├── Titre   : le moment ou le lieu, deux ou trois mots
│     └── Légende : ce qu’on voit, une ligne (facultatif)
├── photos     : une photo par ligne, dans l’ordre ; sans photo, un cadre « Photo 1 »
└── notes      : les photos à ajouter, dans l’ordre, et ce que le présentateur en dit
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `eyebrow` | Repère au-dessus du titre : le lieu, le projet (« École des Tilleuls », « Réseau des tiers-lieux »). | Facultatif, deux ou trois mots. |
| `title` | Le message que la suite d’images démontre, pas « Quelques photos ». | Soixante caractères environ ; au-delà de 64, il s’affiche plus petit. |
| `content` | Une ligne par photo : son titre, puis sa légende. | Trois à six lignes ; la septième et les suivantes ne sont pas affichées. |
| `photos` | Une photo par ligne, dans l’ordre des lignes. | Laisse `[]` : voir `references/images.md`. |
| `disposition` | `""` (en rangée), `grille`, `vedette`. | Voir plus bas. |

Ce type n’emploie ni `content2`, ni `content3`, ni `author`, ni `image` : la galerie prend ses images
dans `photos`. `progressive` est sans effet, les photos entrant ensemble, en cascade. Champs communs
(`anim`, `transition`, `notes`) : `references/format-json.md`.

## Syntaxe de `content`

Une ligne par photo, deux cellules séparées par une barre verticale : `Titre | Légende`.

- **Titre**, première cellule : le moment ou le lieu, en gros caractères de titrage sous l’image
  (« Avant », « Pendant », « Après », « La cour », « Marnay »). Deux ou trois mots. Seul obligatoire.
- **Légende**, deuxième cellule, facultative : ce que montre l’image, quarante à quatre-vingts
  caractères, dans le gris des repères. Tout ce qui suit la première barre en fait partie : une
  deuxième barre ne crée pas de troisième cellule, elle revient dans la légende et s’y affiche telle
  quelle.
- Sans image déposée, chaque photo devient un **cadre en pointillé** portant « Photo 1 », « Photo 2 »…
  La slide se lit quand même : c’est l’état dans lequel tu la livres.
- Une ligne sans titre ni légende laisse un cadre muet, sans aucune ligne sous lui.
- ` // ` coupe une case en deux lignes, `**gras**` et `==surligné==` s’écrivent partout : voir
  `references/format-json.md`. Un pictogramme `(nom)` se pose en tête d’une cellule, mais la photo
  tient déjà ce rôle : garde-le pour d’autres types.

## Dispositions

| `disposition` | Composition | La choisir quand |
| --- | --- | --- |
| `""` | En rangée : autant de colonnes que de photos, toutes sur une seule ligne, chaque image dans un cadre au format 4/3, titre et légende empilés dessous. | Trois ou quatre photos, une chronologie qui se lit de gauche à droite. |
| `grille` | En grille : trois par rangée, deux seulement quand il y a exactement quatre photos. Les images remplissent la hauteur restante ; sous chacune, le titre et la légende se rangent côte à côte, en plus petit. | Cinq ou six photos, ou quatre qu’on veut voir en grand. |
| `vedette` | La première photo en grand à gauche, les autres empilées à droite dans une colonne étroite, titres et légendes réduits. | Une image porte le propos et les autres la complètent. |

```text
┌────────────────────────────── grille ──────────────────────┐
│ title                                                      │
│  ┌────────┐  ┌────────┐  ┌────────┐                        │
│  │Photo 1 │  │Photo 2 │  │Photo 3 │                        │
│  └────────┘  └────────┘  └────────┘                        │
│   Titre · Légende   Titre · Légende   Titre · Légende      │
│  ┌────────┐  ┌────────┐  ┌────────┐                        │
│  │Photo 4 │  │Photo 5 │  │Photo 6 │                        │
│  └────────┘  └────────┘  └────────┘                        │
└────────────────────────────────────────────────────────────┘
```

```text
┌────────────────────────────── vedette ─────────────────────┐
│ title                                                      │
│  ┌───────────────────────┐   ┌──────────┐                  │
│  │                       │   │ Photo 2  │                  │
│  │       Photo 1         │   └──────────┘                  │
│  │                       │    Titre                        │
│  └───────────────────────┘    Légende                      │
│   Titre                      ┌──────────┐                  │
│   Légende                    │ Photo 3  │                  │
│                              └──────────┘                  │
│                               Titre                        │
│                               Légende                      │
└────────────────────────────────────────────────────────────┘
```

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : les trois
  dispositions s’appliquent. En Libre, le cadre photo a les coins légèrement arrondis ; avec une mise
  en page, il redevient carré.
- **Modèles complets** qui redessinent ce type (`compose`) : `cimaise` seulement. Il numérote les
  photos (01, 02, 03…) devant leur titre et pose un filet corail sous chaque image ; il garde `grille`
  mais ignore `vedette`, qui retombe alors sur la rangée. Les autres modèles complets (`revue`,
  `chantier`, `marqueur`, `tampon`, `pastille`, `bloc`, `anneau`, `crayon`, `aube`, `opale`, `bdt`)
  habillent le rendu Libre de leurs polices, de leur accent et de leurs repères, et gardent les trois
  dispositions ; les cadres passent à angle droit, sauf avec `aube` et `opale`, qui les arrondissent
  largement.
- **Plateforme** (`"modele": "plateforme"`) : pas de galerie au catalogue officiel. La slide reprend
  les cadres photo et les légendes de la charte, en rangée. `grille` et `vedette` s’appliquent ; en
  `vedette`, les petites photos n’affichent que leur titre, leur légende est masquée. Pas de
  pictogramme : le mot entre parenthèses est retiré sans s’afficher.

## Pièges

- L’ordre des cellules est fixe : titre, puis légende. Une phrase entière en première cellule s’écrit
  en gros caractères de titrage et déborde du cadre.
- Une deuxième barre verticale ne crée pas de troisième cellule : elle se recolle à la légende et
  s’affiche telle quelle. Deux cellules par ligne, et jamais de `|` dans une phrase.
- Au-delà de six lignes, les photos en trop disparaissent sans avertissement.
- Six photos en disposition par défaut font six colonnes très étroites : passe en `grille`.
- `photos` suit l’ordre des lignes : une ligne insérée décale toutes les images. Laisse `[]` et décris
  les photos dans `notes`, dans l’ordre exact des lignes — tout est dans `references/images.md`, y
  compris la question de savoir si tu dois proposer une galerie du tout.
- Une galerie sans images reste une rangée de cadres vides : ne la propose que si l’utilisateur a
  vraiment des photos, et dis-le-lui. N’invente jamais d’adresse d’image.
- « Quelques photos » en titre ne dit rien : mets le lieu en `eyebrow` et garde le titre pour ce que
  les images démontrent.

## JSON

Trois photos, la disposition par défaut :

```json
{ "layout": "galerie", "eyebrow": "École des Tilleuls", "title": "Le chantier en trois temps.", "content": "Avant | Façade de 1974, simple vitrage et chaudière au fioul\nPendant | Été 2026, huit semaines d’échafaudage\nAprès | Rentrée 2026, cour plantée et classes fraîches", "notes": "Photos à ajouter, dans l’ordre : la façade avant travaux, l’échafaudage monté en juillet, la cour plantée le jour de la rentrée. Dire que tout a tenu dans les vacances : aucune classe déplacée." }
```

Six lieux, en grille (trois par rangée) :

```json
{ "layout": "galerie", "eyebrow": "Réseau des tiers-lieux", "title": "Six lieux ouverts en dix-huit mois.", "disposition": "grille", "content": "Marnay | Ancienne poste, 90 m², ouverte en mars 2025\nVerneuil | Salle des fêtes partagée, deux jours par semaine\nLa Vergne | Préau de l’école, hors temps scolaire\nSaint-Clar | Local commercial repris avec la commune\nBoissy | Bâtiment agricole réhabilité en chantier d’insertion\nAulnoy | Bureau mobile, quatre communes en tournée", "notes": "Photos à ajouter : une par lieu, dans l’ordre des lignes. Préciser que seuls Marnay et Saint-Clar ont demandé des travaux lourds." }
```

Une image en vedette, deux vues d’appui :

```json
{ "layout": "galerie", "eyebrow": "Médiathèque du Val", "title": "Un bâtiment, trois usages que le programme n’avait pas prévus.", "disposition": "vedette", "anim": "fondu", "content": "La halle | Le hall ouvert sert de salle d’attente aux permanences sociales\nLe patio | Occupé tous les midis par les lycéens du lycée voisin\nL’atelier | Réservé quatre soirs sur cinq par les associations", "notes": "Photos à ajouter : la halle en grand, puis le patio et l’atelier. Insister : ces trois usages ne figuraient pas au programme, et aucun n’a demandé de travaux." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
