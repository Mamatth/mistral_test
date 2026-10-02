# `etapes` · Étapes

> Trois à six étapes dans l’ordre, numérotées d’office : la suite des choses, sans dates. Une étape franchie
> se marque comme réalisée, celle en cours se met en avant.

## Quand l’employer

- **Dans la matière, tu as trouvé** : une méthode ou une procédure décrite en phases (« d’abord…, puis…,
  enfin… ») ; le parcours d’un dossier ou d’un usager, de la demande à la décision ; le déroulé d’un projet
  sans dates (diagnostic, programme, travaux, évaluation) ; une boucle qui recommence chaque année (mesurer,
  prioriser, agir, vérifier) ; une liste numérotée de trois à six points dont l’ordre compte.
- **Plutôt que** : `jalons` si chaque étape a une date (la frise des jalons lui fait une place) ; `roadmap` si
  plusieurs chantiers avancent en parallèle sur une période ; `sommaire` si les points sont les parties de
  l’exposé, non celles du sujet ; `faits` si les cartes n’ont pas d’ordre (des réalisations, des constats).
- **Pas pour** : plus de six étapes (regroupe, ou scinde en deux slides) ; des étapes à expliquer longuement,
  chaque chevron tient un titre et une phrase ; deux options à opposer (`colonnes`).

## Structure de l’information

```text
┌────────────────────────────────────────────────────────────┐
│ eyebrow                                                    │
│ title : ce que la suite des étapes montre                  │
│                                                            │
│ ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐        │
│ │ (picto)   >│ (picto)   >│ (picto)   >│ (picto)   >       │
│ │ 01        >│ 02        >│ 03        >│ 04        >       │
│ │ Titre     >│ Titre     >│ Titre     >│ Titre     >       │
│ │ Descript. >│ Descript. >│ Descript. >│ Descript. >       │
│ └──────────┘ └──────────┘ └──────────┘ └──────────┘        │
│  x = franchie (fond accent)   > = en cours (titre accent)  │
└────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
etapes
├── title      : ce que l’enchaînement montre, une phrase courte (« Comment une école est rénovée. »)
├── eyebrow    : le repère, « Méthode », « Chaque année » (facultatif)
├── content    : 3 à 6 lignes « Titre | Description », une par étape, dans l’ordre
│     ├── repère : « x » étape franchie, « > » étape en cours (facultatif, en tête de ligne)
│     ├── (nom)  : un pictogramme dans le chevron (facultatif, après le repère)
│     ├── Titre  : le nom de l’étape, un ou deux mots ; TalkNote pose le numéro 01, 02…
│     └── Description : ce qui se passe à cette étape, une phrase courte
└── notes      : ce que le présentateur dit et qui n’est pas écrit
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `title` | Le message : ce que l’enchaînement montre, pas « Les étapes ». | Une phrase courte. En `cycle`, au-delà de 64 caractères, le corps du titre baisse. |
| `eyebrow` | Le surtitre : `Méthode`, `Processus`, `Chaque année`. | Facultatif. |
| `content` | Les étapes, une par ligne, dans l’ordre. | Trois à six lignes. Syntaxe ci-dessous. |
| `disposition` | `""` ou `cycle`. | Voir « Dispositions ». |

`content2`, `content3`, `author` et `image` ne servent pas ici. Les champs communs (`anim`, `transition`,
`notes`, `progressive`) : voir `references/format-json.md`.

## Syntaxe de `content`

- Une ligne par étape, dans l’ordre : `Titre | Description`. La description est attendue ; un titre seul
  s’affiche quand même, mais le chevron reste creux sous son numéro.
  `Audit énergétique | Trois semaines de relevés, hiver compris.`
- Le numéro (`01`, `02`…) est posé par TalkNote dans l’ordre des lignes : n’écris ni `1.` ni `Étape 1` dans
  le titre.
- `x ` en tête de ligne, suivi d’une espace : l’étape est franchie (le chevron passe sur la couleur d’accent,
  texte en clair). `> ` en tête : l’étape en cours (le titre en couleur d’accent). Un seul repère par ligne ;
  les `x ` avant la `> `, une seule `> `, puis les étapes à venir sans repère. Sans aucun repère, la slide
  se lit comme une méthode, pas comme un avancement.
  `x Audit | Trois semaines de relevés.`
  `> Chantier | Huit semaines, l’été.`
- `(nom)` après le repère, avant le titre : un pictogramme en tête du chevron, au-dessus du numéro
  (`x (loupe) Audit | …`). En `cycle`, il remplace le numéro dans la pastille. Noms reconnus :
  `references/pictogrammes.md`.
- Deux cellules : ce qui suit un deuxième `|` n’est pas affiché.
- Gras, surligné, ` // ` : la syntaxe commune de `references/format-json.md`. Reste sobre, un chevron se lit
  d’un coup.
- Limites : trois à six étapes. Dès cinq, les chevrons se resserrent (titre et description en plus petit) :
  titres d’un ou deux mots, descriptions d’une dizaine de mots. Au-delà de six, ils se resserrent encore
  et ne se lisent plus.

## Dispositions

| `disposition` | Composition | La choisir quand |
| --- | --- | --- |
| `""` | Les étapes en chevrons égaux, de gauche à droite : numéro, titre et description dans chaque chevron. | Une méthode linéaire, un processus qui a un début et une fin. |
| `cycle` | Les étapes en pastilles sur un cercle fléché, à droite ; à gauche, le titre puis la liste numérotée avec les descriptions. | Ce qui recommence : un cycle annuel, une boucle d’amélioration, une routine. |

```text
┌────────────────────────────────────────────────────────────┐
│ eyebrow                                    ╭──(01)──╮      │
│ title                                     ╱   Titre  ╲     │
│                                         (04)        (02)   │
│ 01  Titre   Description                 Titre       Titre  │
│ 02  Titre   Description                   ╲        ╱       │
│ 03  Titre   Description                    ╰──(03)──╯      │
│ 04  Titre   Description                       Titre        │
└────────────────────────────────────────────────────────────┘
```

En `cycle`, chaque pastille ne porte que son numéro (ou son pictogramme) et son titre ; la liste de gauche
n’apparaît que si une étape au moins a une description. Le cercle tourne dans le sens des aiguilles d’une
montre, la première étape en haut.

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : tout s’applique.
- **Modèles complets qui redessinent ce type** (`compose`) : `anneau`, `crayon`, `opale`.
  - `anneau` : des ronds sur un filet, colorés corail, ambre puis céladon à tour de rôle ; le titre en
    capitales dessous, puis la description. Le rond porte le pictogramme, et pas de numéro. Sans `x ` ni
    `> `, tous les ronds sont pleins (une suite) ; avec des repères, les étapes à venir passent en anneau
    d’encre et l’étape en cours est cernée. `cycle` s’applique, les pastilles gardant leurs trois couleurs.
  - `crayon` : des colonnes sur un filet (trois par rangée, quatre côte à côte pour quatre étapes) ;
    « étape 01 » en bleu, « · faite » après un `x `, le pictogramme devant le titre, la description dessous.
    Sans repère, la dernière étape prend l’encre bleue : l’aboutissement. `cycle` s’applique.
  - `opale` : une file de cartes de verre, une flèche entre chaque, avec numéro, titre et description ; le
    pictogramme en tête de carte ; `x ` et `> ` se lisent sur la carte. Six étapes au plus, les suivantes
    ne sont pas affichées. `cycle` est ignoré.
- Les autres modèles complets (`revue`, `chantier`, `marqueur`, `tampon`, `pastille`, `bloc`, `cimaise`,
  `aube`, `bdt`) habillent le rendu Libre : chevrons ou `cycle`, pictogrammes dessinés.
- **Plateforme** (`"modele": "plateforme"`) : les étapes reprennent la frise des jalons, des points sur une
  ligne, « Étape 01 » tenant lieu de date, titre et description sous chaque point ; `x ` marque l’étape
  réalisée, `> ` n’y change rien. `cycle` s’applique (le numéro dans chaque pastille). Pas de pictogramme : le
  mot entre parenthèses est retiré.

## Pièges

- Un numéro écrit à la main (`1. Audit`, `Étape 1 · Audit`) : il double celui que TalkNote pose.
- Des dates en tête des titres (`2025 · Audit`) : c’est une `jalons`, qui a une cellule pour la date.
- Un `|` dans une description : tout ce qui le suit disparaît. Remplace-le par une virgule ou un point.
- Deux lignes `> `, ou un `x ` après la `> ` : l’avancement ne se lit plus. Les `x ` d’abord, une seule `> `.
- Un titre de trois mots, ou un mot très long, dans un chevron : la case est étroite, plus encore à cinq ou
  six étapes ; TalkNote baisse alors le corps de toute la rangée pour faire tenir le mot le plus long. Un ou
  deux mots par titre.
- `cycle` avec des titres longs : la pastille est petite, et la description ne se lit que dans la liste de
  gauche, jamais sur le cercle. Un ou deux mots courts par titre.
- `cycle` à deux étapes : un cercle qui ne dit rien ; il en faut trois au moins.
- Sept étapes ou plus : les chevrons ne se lisent plus, et `opale` coupe à six. Regroupe, ou scinde en deux
  slides.

## JSON

Une méthode en cours, en chevrons : deux étapes franchies, une en cours, un pictogramme par étape :

```json
{ "layout": "etapes", "eyebrow": "Méthode", "title": "Comment une demande de subvention est instruite.", "content": "x (document) Dépôt | Le dossier est déposé sur le portail, pièces jointes comprises.\nx (loupe) Recevabilité | Dix jours pour vérifier la complétude et l’éligibilité.\n> (groupe) Instruction | Le service et la commission thématique rendent leur avis.\n(validé) Décision | Notification sous trois mois, puis versement en deux fois.", "notes": "Six dossiers sur dix de l’année sont à l’instruction : dire que le délai de trois mois est tenu." }
```

Ce qui recommence chaque année, en `cycle`, l’étape en cours en avant :

```json
{ "layout": "etapes", "eyebrow": "Chaque année", "title": "La même boucle, tronçon après tronçon.", "disposition": "cycle", "content": "> (loupe) Mesurer | Relevés de fuites de l’hiver et enquête auprès des abonnés.\n(cible) Prioriser | Le comité de mars choisit les tronçons à renouveler.\n(outil) Renouveler | Chantiers d’été, sans coupure d’eau prolongée.\n(validé) Vérifier | Un an de rendement mesuré avant de conclure.", "notes": "Insister sur « Vérifier » : c’est la mesure qui décide de la vague suivante, pas le calendrier." }
```

Une suite neutre en cinq étapes, sans repère ni pictogramme : les chevrons se resserrent, les textes sont
courts à dessein (avec `anneau`, les cinq ronds sont pleins ; avec `crayon`, la dernière étape prend l’encre
bleue) :

```json
{ "layout": "etapes", "eyebrow": "Parcours usager", "title": "De la demande au titre, cinq gestes en ligne.", "content": "Compte | Identification en ligne, une fois pour toutes.\nDemande | Formulaire prérempli, dix minutes.\nPièces | Photo et justificatif depuis le téléphone.\nSuivi | Un courriel à chaque changement d’état.\nRetrait | Rendez-vous en mairie, ou envoi à domicile.", "notes": "Le parcours a été testé avec douze usagers en juin : deux n’ont pas trouvé le suivi par courriel." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
