# `titre` · Couverture

> La première slide : elle ouvre la présentation avec un surtitre, un titre, un chapeau, puis la date ou l’auteur.

## Quand l’employer

- **Dans la matière, tu as trouvé** : le titre du document ou de la réunion ; le nom de l’instance et sa date
  (« comité de pilotage du 24 septembre ») ; une version, une mention, un service auteur ; la phrase qui dit
  l’objet du document (souvent dans l’introduction ou le résumé) : c’est le chapeau.
- **Plutôt que** : `section` si tu ouvres une partie et non la présentation (le surtitre porte « Partie 01 »,
  le fond « temps fort » existe) ; `fin` si la slide clôt et donne un contact. Une seule couverture par
  présentation, toujours en première position.
- **Pas pour** : ouvrir un chapitre ou des annexes (une `section`) ; poser un message au milieu du déroulé
  (`contenu` ou `citation`).

## Structure de l’information

```text
┌──────────────────────────────────────────────────────────────┐
│                                                              │
│   eyebrow  COMITÉ DE PILOTAGE · SEPTEMBRE 2026               │
│   title    Des écoles plus sobres,                           │
│            plus fraîches.                                    │
│   ▬▬▬▬     (filet dans la couleur d’accent)                  │
│   content  Bilan de la deuxième année du programme de        │
│            rénovation, et feuille de route 2027.             │
│   author   24 SEPTEMBRE 2026 · DIRECTION DU PATRIMOINE       │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
titre
├── title      : le message de la présentation ; deux lignes au plus, soixante caractères environ
├── eyebrow    : nature du document, instance, date ou version (facultatif)
├── content    : le chapeau, une ou deux phrases ; une ligne = un paragraphe (facultatif)
├── author     : « Date · Auteur », ou le service qui présente (facultatif)
└── notes      : ce que le présentateur dit en ouvrant, et qui n’est pas écrit
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `title` | Le titre de la présentation : une phrase qui dit le message, pas une étiquette. `==mots==` met des mots en couleur ; `(nom)` en tête pose un pictogramme. | Deux lignes au plus, soixante caractères environ. En Libre, le corps baisse au-delà de 32 puis de 64 caractères. |
| `eyebrow` | Surtitre en petites capitales de couleur : la nature du document, l’instance, la date ou la version. | Une ligne courte. Avec `cimaise`, 18 caractères au plus pour qu’il s’empile sur le titre. |
| `content` | Le chapeau : ce que la présentation va montrer, en une ou deux phrases. | Une ligne = un paragraphe ; ni puces ni intertitres. |
| `author` | Date et auteur, `Date · Auteur`, ou l’organisation qui présente. | Une ligne ; le ` · ` sépare les parties, que `bloc` et `crayon` répartissent. |
| `disposition` | `""`, `centre` ou `bas`. | Voir « Dispositions ». |
| `image` | Photo de couverture, posée seulement par `pastille`, `bloc`, `anneau`, `crayon` et `cimaise`. | Laisse `""` ; décris la photo dans `notes` (`Image à ajouter : …`), voir `references/images.md`. |

Les champs communs (`anim`, `transition`, `notes`, `progressive`) : voir `references/format-json.md`.

## Syntaxe de `content`

- Chaque ligne du champ (`\n` dans le JSON) est un paragraphe, rendu sous le titre en corps moyen et en couleur
  atténuée. Une ligne suffit ; deux au plus.
- `**gras**`, `*italique*` et `==surligné==` s’appliquent (syntaxe générale : `references/format-json.md`).
- Pas de `- ` ni de `# ` : la couverture n’a pas de liste. En Libre et dans les modèles complets, la marque est
  retirée et la ligne devient un simple paragraphe.
- Pas de `|` : la couverture n’a pas de cellules ; le caractère resterait dans le texte.
- Pas de `(nom)` : le chapeau ne dessine pas de pictogramme, le mot entre parenthèses est retiré sans
  s’afficher. L’icône de la couverture s’écrit en tête du `title`.

Exemple : `"content": "Bilan de la deuxième année du programme, et feuille de route 2027."`

## Dispositions

| `disposition` | Composition | La choisir quand |
| --- | --- | --- |
| `""` | Surtitre, titre, filet, chapeau et date alignés à gauche, au milieu de la hauteur. | Par défaut : la lecture la plus naturelle. |
| `centre` | Le même bloc, centré en largeur comme en hauteur. | Un titre court et symétrique ; une couverture d’événement, de conférence. |
| `bas` | Le bloc posé en bas de la slide, le haut laissé vide. | Pour laisser respirer, ou quand un logo ou un fond occupe le haut. |

```text
centre
┌──────────────────────────────────────────────┐
│           COMITÉ DE PILOTAGE · 2026          │
│         Des écoles plus sobres.              │
│                  ▬▬▬▬                        │
│      Bilan de la deuxième année.             │
│                                              │
└──────────────────────────────────────────────┘
```

```text
bas
┌──────────────────────────────────────────────┐
│                                              │
│   COMITÉ DE PILOTAGE · 2026                  │
│   Des écoles plus sobres.                    │
│   ▬▬▬▬                                       │
│   Bilan de la deuxième année.                │
│   24 SEPTEMBRE 2026 · DIRECTION DU PATRIMOINE│
└──────────────────────────────────────────────┘
```

## Selon le modèle

- **Libre** (`"modele": ""`) : tout s’applique. Ses mises en page `cadran`, `marge`, `palier` et `grille`
  dessinent leur propre couverture, le titre déjà posé en bas : `centre` s’applique, `bas` est ignorée. Avec
  `marge`, le surtitre et l’auteur passent dans la gouttière ; avec `grille`, le surtitre indique les colonnes
  qu’occupe le titre. Ces quatre mises en page ne réduisent jamais le texte : écris un titre court, surtout
  avec `palier`.
- **Modèles complets** : tous redessinent la couverture (`revue`, `chantier`, `marqueur`, `tampon`, `pastille`,
  `bloc`, `anneau`, `crayon`, `cimaise`, `aube`, `opale`, `bdt`). Dispositions gardées : `centre` et `bas` avec
  `revue`, `pastille`, `bloc`, `anneau` et `crayon` ; `centre` seulement avec `chantier`, `marqueur`, `tampon` et
  `bdt` (leur titre est déjà en bas, l’hexagone de `bdt` cadre le texte) ; aucune avec `cimaise`, `aube` et
  `opale`. Écritures particulières :
  - `pastille`, `bloc`, `anneau`, `crayon` et `cimaise` posent une photo sur la couverture : `image` vide et
    `Image à ajouter : …` dans `notes` ; sans photo, `pastille`, `bloc`, `anneau` et `cimaise` gardent leur
    forme vide, `crayon` n’en dessine aucune.
  - `aube` : une icône en tête du `title` (`(fusée) Notre cap`) devient le grand signe évidé de la couverture ;
    sans icône, une flèche. Pas de photo, ni avec `opale` (son fond est fait de disques de couleur).
  - `cimaise` : un `eyebrow` de 18 caractères au plus s’empile en couleur sur le titre, au même corps ; plus
    long, il reste une ligne de petites capitales.
  - `bloc` et `crayon` répartissent l’`author` autour de ` · ` : `bloc` met la première partie à gauche et le
    reste à droite de l’en-tête, `crayon` empile une ligne par partie. `crayon` monte aussi le premier
    paragraphe du chapeau en haut, en bleu, et garde les suivants en bas.
  - `revue` isole le dernier mot du titre sur sa propre ligne, en géant ; un chapeau d’un seul paragraphe de
    48 caractères au plus devient la ligne mono sous le titre, sinon il passe en colonnes.
  - `chantier` fait précéder l’`author` de « Présenté par » ; `marqueur` le pose en pastille.
- **Plateforme** (`"modele": "plateforme"`) : `centre` et `bas` s’appliquent ; la marque de la charte (ou le
  logo réglé) tient la droite de la slide, en grand — avec `centre`, elle passe au-dessus du texte, en petit.
  Pas de pictogramme : un `(nom)` en tête du titre est retiré sans s’afficher.

## Pièges

- Un titre-étiquette (« Revue annuelle 2026 ») : la nature et la date vont dans `eyebrow` ; `title` porte le
  message (« Des écoles plus sobres, plus fraîches. »).
- Un titre de trois lignes : Libre réduit le corps, les modèles complets se resserrent, les mises en page
  `cadran`, `marge`, `palier` et `grille` ne réduisent jamais. Soixante caractères environ.
- La date écrite deux fois, dans `eyebrow` et dans `author` : choisis une place ; `eyebrow` pour le mois et
  l’instance, `author` pour le jour et le service.
- Des puces dans `content` : la marque est retirée, la liste devient des paragraphes. Un chapeau, c’est une ou
  deux phrases.
- `anim: "machine"` (le titre s’écrit lettre à lettre) seulement pour un titre court.
- Une disposition que le modèle ignore ne casse rien : la slide prend la composition du modèle.
- Deux couvertures dans un même fichier : la deuxième partie s’ouvre par une `section`, pas par un `titre`.

## JSON

La disposition par défaut, avec les notes d’ouverture :

```json
{ "layout": "titre", "eyebrow": "Comité de pilotage · Septembre 2026", "title": "Des écoles plus sobres, plus fraîches.", "content": "Bilan de la deuxième année du programme de rénovation, et feuille de route 2027.", "author": "24 septembre 2026 · Direction du patrimoine", "notes": "Remercier les élus présents. Rappeler que la séance dure une heure : quarante minutes de présentation, vingt minutes de décisions." }
```

Centrée, avec des mots mis en couleur et une icône en tête du titre (petit pictogramme en Libre, grand signe
avec `aube`) :

```json
{ "layout": "titre", "disposition": "centre", "eyebrow": "Journée des agents · 12 mars 2027", "title": "(fusée) Un guichet unique, ==ouvert à tous==.", "content": "Ce que change le nouvel accueil de la mairie, et comment chaque service y contribue.", "author": "Direction de la relation aux usagers", "notes": "Ouvrir sur l’histoire d’une habitante qui devait faire trois guichets pour une seule démarche." }
```

Pour une présentation en `cimaise` (`modele` et `theme` valent `cimaise`) : surtitre court, qui s’empile sur le
titre, et photo de couverture décrite dans les notes :

```json
{ "layout": "titre", "eyebrow": "Portfolio 2026", "title": "Dix chantiers qui ont changé le quartier.", "content": "Retour en images sur trois ans de rénovation urbaine.", "author": "Service urbanisme · Octobre 2026", "notes": "Image à ajouter : vue aérienne du quartier rénové, en fin de journée. Laisser la photo parler dix secondes avant de commencer." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
