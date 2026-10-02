# `colonnes` · Comparaison

> Deux colonnes à confronter, un avant et un après ou deux options, chacune avec son étiquette, son titre,
> ses points et son pied ; la colonne de droite peut être mise en avant.

## Quand l’employer

- **Dans la matière, tu as trouvé** : un avant et un après (une organisation, un coût, un délai, avant et
  après le projet) ; deux options ou deux scénarios décrits point par point ; deux offres, deux niveaux de
  service, deux publics à distinguer ; trois formules ou trois scénarios côte à côte (disposition `trois`) ;
  une recommandation parmi ces choix, à mettre en avant.
- **Plutôt que** : `matrice` si les choix se situent sur deux axes (effort et impact) plus qu’ils ne
  s’opposent ; `tableau` dès que la comparaison porte sur plus de trois options ou se lit par critères, ligne à
  ligne ; `faits` si les trois ou quatre éléments se juxtaposent sans s’opposer (réalisations, décisions) ;
  `contenu` si un seul camp a quelque chose à dire : un argumentaire, pas une confrontation.
- **Pas pour** : une suite dans le temps (`etapes`, `jalons`) ni deux séries de chiffres (`graph` en barres).

## Structure de l’information

```text
┌────────────────────────────────────────────────────────────┐
│ eyebrow                                                    │
│ title : ce que l’écart entre les colonnes montre           │
│                                                            │
│ ▬                            ╭─▬─────────────────────────╮ │
│ > ÉTIQUETTE                  │ > ÉTIQUETTE  (en avant)   │ │
│ # Titre de colonne           │ # Titre de colonne        │ │
│ • Puce                       │ • Puce                    │ │
│ • Puce                       │ • Puce                    │ │
│ • Puce                       │ • Puce                    │ │
│ PIED DE COLONNE              │ PIED DE COLONNE           │ │
│                              ╰───────────────────────────╯ │
└────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
colonnes
├── title      : ce que l’écart montre, en une phrase (soixante caractères environ)
├── eyebrow    : repère court (« Principe », « Arbitrage ») (facultatif)
├── content    : colonne gauche, une ligne par élément
│     ├── > Étiquette : le nom du camp (« Avant », « Scénario A »), un ou deux mots
│     ├── # Titre     : l’idée de la colonne en quelques mots
│     ├── - Puce      : un point de comparaison ; trois à cinq, courts
│     └── Pied        : une ligne sans préfixe, posée en bas (facultatif)
├── content2   : colonne droite, même syntaxe
├── content3   : troisième colonne, seulement en disposition `trois`
├── accent     : `true` met la dernière colonne en avant
└── notes      : ce que le présentateur dit et qui n’est pas écrit
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `eyebrow` | Repère au-dessus du titre : « Principe », « Arbitrage », « Programme type ». | Facultatif, deux ou trois mots. |
| `title` | Le message : ce que l’écart entre les colonnes montre. | Soixante caractères environ, deux lignes au plus ; au-delà de 64 caractères il s’affiche plus petit. |
| `content` | La colonne gauche. | Syntaxe ci-dessous. |
| `content2` | La colonne droite. | Même syntaxe. Vide, la colonne reste vide : ne l’oublie pas. |
| `content3` | La troisième colonne. | Lue seulement avec `"disposition": "trois"`, et alors indispensable : sans elle, la troisième colonne reste vide. Ignorée sinon. |
| `accent` | `true` met la dernière colonne en avant (la droite, ou la troisième). | `true` ou `false` sans guillemets ; défaut `false`. |
| `disposition` | `""` (deux colonnes) ou `trois`. | Voir « Dispositions ». |

Les champs communs (`anim`, `transition`, `notes`, `progressive`) : voir `references/format-json.md`.

## Syntaxe de `content`

Une ligne par élément, dans cet ordre : l’étiquette, le titre, les puces, le pied.

| Ligne | Écriture | Rendu |
| --- | --- | --- |
| Étiquette | `> Avant` | Petites capitales au-dessus du titre ; en couleur d’accent si la colonne est en avant. |
| Étiquette en avant | `>> Avec le programme` | La même, et la colonne est mise en avant. |
| Titre de colonne | `# Chacun pour soi` | Le titre de la colonne, en grand. |
| Puce | `- Un diagnostic par commune` | Un point de comparaison. `* ` et `• ` valent `- `. |
| Pied | `Coût moyen : 1 450 € / m²` (sans préfixe) | Une ligne courte en petites capitales, posée en bas de la colonne. |

- Le pied descend toujours en bas de la colonne, où qu’il soit écrit ; plusieurs lignes sans préfixe se
  rejoignent en un seul pied, séparées par « · ».
- Une ligne `1. ` devient une puce ordinaire : le numéro ne s’affiche pas. Une suite ordonnée va dans `etapes`.
- Un pictogramme `(nom)` se pose après le repère : `> (cible) Standard`, `# (éclair) Réglages et LED`. Dans
  une puce, il s’ajoute devant le texte sans remplacer la puce. Noms : `references/pictogrammes.md`.
- `**gras**`, `==surligné==`, ` // ` : voir `references/format-json.md`.
- `content2` s’écrit de la même façon ; `content3` aussi, en disposition `trois`.

**Mise en avant.** Deux moyens : `"accent": true` met en avant la dernière colonne (la droite, ou la
troisième), `>> ` devant l’étiquette met en avant n’importe quelle colonne. Une seule colonne en avant par
slide. Pour un avant / après, mets la solution à droite et en avant ; pour deux options à égalité, n’en mets
aucune : la slide laisse le choix au public.

**Point par point.** Même nombre de puces dans chaque colonne, dans le même ordre (le coût en face du coût,
le délai en face du délai) : la comparaison se lit ligne à ligne. Trois à cinq puces d’une ligne chacune.

## Dispositions

| `disposition` | Composition | La choisir quand |
| --- | --- | --- |
| `""` | Deux colonnes égales : `content` à gauche, `content2` à droite. | Un avant / après, deux options, deux scénarios. |
| `trois` | Trois colonnes, la troisième dans `content3` ; textes plus petits. | Trois niveaux, offres, formules ou scénarios ; souvent celui du milieu en avant avec `>> `. |

```text
┌────────────────────────────────────────────────────────────┐
│ title : ce que l’écart entre les colonnes montre           │
│                                                            │
│ ▬                  ╭─▬───────────────╮  ▬                  │
│ > ÉTIQUETTE        │ >> ÉTIQUETTE    │  > ÉTIQUETTE        │
│ # Titre            │ # Titre         │  # Titre            │
│ • Puce             │ • Puce          │  • Puce             │
│ • Puce             │ • Puce          │  • Puce             │
│ PIED               │ PIED            │  PIED               │
│                    ╰─────────────────╯                     │
└────────────────────────────────────────────────────────────┘
```

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : tout s’applique.
  Le filet d’accent en tête de colonne n’existe qu’en Libre : les mises en page ne le posent pas, et
  cernent la colonne en avant d’un simple cadre, sans fond.
- **Modèles complets** qui redessinent ce type (`compose`) : `tampon` seulement. Il pose le numéro de la
  partie en grand, avec son disque vermillon, au-dessus du titre ; dans chaque colonne, l’étiquette en
  capitales sur un filet, puis le titre, les puces et le pied. Il garde `trois`, mais ignore la mise en
  avant (`accent` comme `>> `) : ses colonnes restent égales ; sans étiquette, le titre prend sa place. Il ne
  dessine pas de pictogramme. Une colonne vide n’y est pas dessinée du tout : avec `trois`, un `content3`
  vide ne laisse que deux colonnes. Les autres modèles complets (`revue`, `chantier`, `marqueur`, `pastille`,
  `bloc`, `anneau`, `crayon`, `cimaise`, `aube`, `opale`, `bdt`) habillent le rendu Libre : `trois` et la
  mise en avant s’appliquent, le filet d’accent en tête de colonne n’y est pas dessiné, la colonne en avant
  est cernée d’un filet (`aube` la pose sur une carte blanche ; `opale` pose chaque colonne sur une carte
  de verre et cerne celle en avant d’une de ses teintes), les pictogrammes se dessinent.
- **Plateforme** (`"modele": "plateforme"`) : chaque colonne devient une carte blanche ; la colonne en avant
  porte un filet rouge en tête et son étiquette en rouge. `trois` s’applique. Pas de pictogramme : le mot
  est retiré sans s’afficher.

## Pièges

- `"layout": "contenu"` avec `"disposition": "colonnes"` n’est pas une comparaison : c’est un texte coulé sur
  deux colonnes. La comparaison, c’est `"layout": "colonnes"`.
- **Les deux colonnes écrites dans le seul `content`**, séparées par un `|` : c’est la faute la plus coûteuse.
  Ici le `|` ne sépare pas des cases, il s’affiche tel quel ; `content2` reste vide, donc la moitié droite de
  la slide aussi. La colonne gauche est à écrire dans `content`, la droite dans `content2`, jamais les deux
  dans le même champ.
- **Une colonne faite de lignes sans préfixe** part en entier au pied de colonne : capitales espacées, corps
  de 16 px, en gris. Ce pied est fait pour une phrase de clôture, pas pour un paragraphe. Donne un titre
  `# ` à la colonne et des puces `- ` à son contenu.
- Une phrase sans préfixe glissée entre deux puces file au pied de la colonne, jointe aux autres par « · ».
- `"disposition": "trois"` sans `content3` laisse une troisième colonne vide ; `content3` rempli sans cette
  disposition n’apparaît pas.
- `"accent": true` et `>> ` sur une autre colonne mettent deux colonnes en avant : choisis-en une.
- Avec `progressive` à sa valeur par défaut, les puces se dévoilent une à une, toute la colonne gauche avant
  la droite. Pour une comparaison lue d’un coup d’œil, `"progressive": false`.
- Un titre neutre (« Comparaison », « Avant / après ») ne dit rien : écris ce que l’écart montre.
- Deux colonnes de longueurs très différentes se lisent mal : résume la plus longue ou complète la plus courte.

## JSON

Un avant / après, la colonne droite en avant :

```json
{ "layout": "colonnes", "eyebrow": "Principe", "title": "Un guichet unique plutôt que six accueils.", "content": "> Avant\n# Chaque service son accueil\n- Six adresses, six horaires différents\n- Le même justificatif demandé plusieurs fois\n- Un dossier sur trois réorienté\nDélai moyen : 21 jours", "content2": "> Avec le guichet unique\n# Un seul point d’entrée\n- Une adresse, des horaires élargis le samedi\n- Un dossier partagé entre les services\n- Une réorientation sur vingt\nDélai moyen : 9 jours", "accent": true, "notes": "La colonne de droite est mise en avant : c’est la cible. Les délais viennent du bilan du guichet pilote, un an après l’ouverture." }
```

Trois scénarios, celui du milieu en avant avec `>> `, un pictogramme devant chaque étiquette :

```json
{ "layout": "colonnes", "eyebrow": "Déploiement", "title": "Trois rythmes pour passer à la nouvelle messagerie.", "disposition": "trois", "content": "> (loupe) Pilote\n# Une direction d’abord\n- 120 agents volontaires\n- Trois mois d’essai\n- Retours avant généralisation\nBascule complète : fin 2027", "content2": ">> (calendrier) Par vagues\n# Une direction par mois\n- 400 agents par vague\n- Formation la semaine précédente\n- Ancienne messagerie coupée après un mois\nBascule complète : juin 2027", "content3": "> (fusée) D’un coup\n# Tout le monde le même jour\n- 1 900 agents\n- Un week-end de bascule\n- Assistance renforcée deux semaines\nBascule complète : mars 2027", "notes": "La colonne du milieu est mise en avant : c’est le rythme recommandé par la direction du numérique. Le pilote existe déjà et sert de première vague." }
```

Deux scénarios à égalité, sans mise en avant, tout affiché d’un coup :

```json
{ "layout": "colonnes", "eyebrow": "Arbitrage", "title": "Deux scénarios pour financer la dernière vague.", "content": "> Scénario A\n# Tenir le calendrier\n- Les 26 écoles restantes rénovées d’ici 2028\n- **Emprunt complémentaire de 4,2 M€**\n- Programme allégé, sans cour végétalisée\nAchèvement : été 2028", "content2": "> Scénario B\n# Tenir le programme\n- 18 écoles en 2028, les 8 dernières en 2029\n- **Aucun emprunt supplémentaire**\n- Programme complet, cours comprises\nAchèvement : été 2029", "progressive": false, "notes": "Aucune colonne mise en avant : la cellule ne recommande pas de scénario, c’est au comité de choisir." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
