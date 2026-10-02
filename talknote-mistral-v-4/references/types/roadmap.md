# `roadmap` · Roadmap

> Des chantiers menés en parallèle sur l’année, chacun en barres posées sur quatre trimestres : ce qui est
> réalisé, en cours, à venir.

## Quand l’employer

- **Dans la matière, tu as trouvé** : un planning par trimestre ou par semestre, un diagramme de Gantt ; une
  feuille de route ou un calendrier prévisionnel où plusieurs chantiers se chevauchent ; des actions avec un
  début, une fin et un état d’avancement ; un bilan d’étape (« ce qui est fait, ce qui reste ») daté sur
  l’année ; des lots de travaux ou des vagues de déploiement qui se suivent et se recouvrent.
- **Plutôt que** : `jalons` si la matière donne des dates ponctuelles (une signature, une livraison), non des
  durées ; `etapes` si c’est une suite ordonnée sans calendrier ; `portefeuille` si les sujets sont rangés par
  état (à cadrer, en cours, livré) sans axe du temps ; `tableau` au-delà de quatre chantiers, ou quand chaque
  action porte plus qu’une période et un état (un budget, un pilote, un statut détaillé).
- **Pas pour** : le déroulé d’un seul chantier (une `etapes` ou des `jalons` le disent mieux) ; une stratégie
  pluriannuelle à vingt actions (un `tableau`, ou une roadmap par année).

## Structure de l’information

```text
┌──────────────────────────────────────────────────────────────┐
│ eyebrow                                                      │
│ title : le message du plan                                   │
│                                                              │
│             ● T1 janv – mars ● T2 avr – juin ● T3 …  ● T4 …  │
│ Chantier    ▐ Libellé (réalisé) ▌                            │
│ sous-titre              ▐ Libellé (en cours) ▌               │
│ ───────────────────────────────────────────────────────────  │
│ Chantier                ▐ Libellé (réalisé) ▌                │
│ sous-titre                          ┌ Libellé (à venir) ┐    │
│ ───────────────────────────────────────────────────────────  │
│ ■ Réalisé    ■ En cours    ┈ À venir                         │
└──────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
roadmap
├── title      : le message du plan, une phrase courte (« Une année, trois chantiers en parallèle. »)
├── eyebrow    : le repère de période (« Feuille de route · 2027 ») (facultatif)
├── content    : le plan, ligne à ligne
│     ├── colonnes : A, B, C, D   : la ligne des colonnes, une seule, en tête (facultatif : T1 à T4)
│     ├── # Chantier | sous-titre : ouvre un chantier ; trois ou quatre par slide
│     │     └── Libellé | position | état : une barre par ligne, trois au plus par chantier
│     │           ├── Libellé  : ce qui est fait pendant la barre, court
│     │           ├── position : une colonne (T2), une étendue (T1-T3) ou des pourcentages (24-47)
│     │           └── état     : réalisé, en cours ou à venir
└── notes      : ce que le présentateur dit et qui n’est pas écrit
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `title` | Le message du plan : ce que l’année montre, pas le mot « Roadmap » (il va dans `eyebrow`). | Une phrase courte ; au-delà de 64 caractères, le corps du titre baisse. |
| `eyebrow` | Le surtitre : la période ou le nom du plan, `Feuille de route · 2027`, `Roadmap · Octobre 2026 → septembre 2027`. | Facultatif. |
| `content` | Les colonnes, puis les chantiers et leurs barres. | Syntaxe ci-dessous ; trois ou quatre chantiers, trois barres au plus chacun. |

`content2`, `content3`, `author`, `image` et `disposition` ne servent pas ici : ce type n’a pas de
disposition, et le rendu ignore toute valeur écrite. `progressive` est sans effet : les chantiers entrent
avec l’animation de la slide, l’un après l’autre. Les champs communs (`anim`, `transition`, `notes`) :
voir `references/format-json.md`.

## Syntaxe de `content`

- **La ligne des colonnes**, facultative, en tête : `colonnes : ` puis les colonnes séparées par des virgules.
  Dans chaque colonne, le premier mot est le repère (en gras, précédé d’un point de couleur), la suite le
  sous-titre en petit. Sans cette ligne, TalkNote pose `T1` à `T4`.
  `colonnes : T1 · janv – mars, T2 · avril – juin, T3 · juil – sept, T4 · oct – déc`
  `colonnes : 2026 · S2, 2027 · S1, 2027 · S2, 2028 · S1`
  Quatre colonnes d’ordinaire : elles se partagent la largeur à égalité, si bien que chaque colonne de plus
  resserre les en-têtes. Garde des repères d’un mot.
- **Un chantier** : `# Chantier | sous-titre` ouvre une ligne du plan. Le nom se pose en gras dans la colonne
  de gauche, étroite (deux ou trois mots, il se replie au-delà) ; le sous-titre, facultatif, dessous en petit.
  Une troisième cellule n’est pas affichée.
  `# Travaux | Vague 2027`
- **Une barre** : sous son chantier, une ligne `Libellé | position | état`.
  - Libellé : court, sur une ligne, sans ` // ` ; une barre d’une colonne tient une trentaine de caractères,
    le reste est coupé par des points de suspension.
  - Position : `T2` la 2ᵉ colonne ; `T1-T3` de la 1ʳᵉ à la 3ᵉ. `Tn` désigne le **rang** de la colonne, pas le
    trimestre civil : avec des colonnes qui commencent à `T4 · oct – déc 2026`, `T1` tombe sur ce T4. Ou en
    pourcentage de la largeur : `24-47` (de 24 % à 47 %), `0-100` (toute l’année) ; `24` seul va de 24 à 34.
  - État, exactement : `réalisé` (barre pleine, couleur d’accent), `en cours` (barre sombre, à l’encre),
    `à venir` (contour en pointillé). La légende se compose seule, avec les seuls états présents.
  `Attribution des marchés | T1 | en cours`
  `Capteurs posés | T1-T2 | réalisé`
  `Diagnostics amiante | 26-70 | à venir`
- **Pictogramme** : `(nom)` en tête du nom d’un chantier (`# (chantier) Travaux | Vague 2027`) se dessine
  devant lui en Libre et dans les modèles complets, Plateforme le retire. Dans une barre, il se dessine
  aussi, mais la barre ne fait que 24 px de haut : n’en mets pas. Noms reconnus :
  `references/pictogrammes.md`.
- **Limites** : trois ou quatre chantiers, trois barres au plus par chantier ; à douze barres la slide est
  pleine. Au-delà, deux slides (une par semestre, ou par famille de chantiers).
- Gras et surligné valent dans les libellés (`references/format-json.md`) ; reste sobre, les barres se lisent
  de loin.

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : tout s’applique.
  Les mises en page équarrissent les barres et donnent aux barres réalisées leur couleur de repère.
- **Modèles complets** : aucun ne redessine ce type. Tous (`revue`, `chantier`, `marqueur`, `tampon`,
  `pastille`, `bloc`, `anneau`, `crayon`, `cimaise`, `aube`, `opale`, `bdt`) habillent le rendu Libre : la
  même grille et les mêmes barres, à angles droits, dans la palette et les polices du modèle ; `opale` pose la
  grille sur son verre, arrondit les barres et prend son premier ton pour le réalisé. Le pictogramme en tête
  d’un chantier se dessine.
- **Plateforme** (`"modele": "plateforme"`) : son propre gabarit, la même grille dans la charte : réalisé en
  rouge, en cours en anthracite, à venir en pointillé ; le titre se replie vers 28 caractères par ligne, la
  colonne des chantiers est plus étroite. Pas de pictogramme : le mot entre parenthèses est retiré.

## Pièges

- Un état que le moteur ne reconnaît pas (`bloqué`, `en retard`, `à risque`, `annulé`, ou la cellule laissée
  vide) : la barre est dessinée pleine, comme un « réalisé », et dit le contraire du plan. Écris les trois
  mots attendus : `réalisé`, `en cours`, `à venir`.
- Une position absente ou illisible (`mars`, `T2 à T3`) : la barre prend toute la largeur.
- Un `Tn` au-delà du nombre de colonnes (`T5` sur quatre colonnes, `T4` sur trois) ou `T0` : la barre est
  posée hors de la grille, à 101 % de la largeur ou à −25 %, et sort de la slide ou retombe sur la colonne
  des chantiers. Compte les colonnes avant d’écrire la position.
- Un pourcentage plus petit que le nombre de colonnes (`2-4`) est lu comme des rangs de colonnes ; écris `2%-4%`,
  ou reste en rangs.
- Des colonnes qui ne sont pas T1 à T4 dans l’ordre : vérifie chaque `Tn` par son rang, ou nomme les colonnes
  sans T (`2026 · S2`) pour ne pas confondre.
- Un `|` dans un libellé : la deuxième cellule devient la position, la troisième l’état. La barre s’étale
  sur toute la largeur et repasse en « réalisé ». Écris « ou », un tiret, deux points.
- Une ligne de barre avant le premier `# ` : elle ouvre un chantier sans nom.
- Un nom de chantier long (`Modernisation du système d’information`) : la colonne de gauche le replie sur trois
  lignes. Deux ou trois mots, le reste en sous-titre.
- Plus de quatre chantiers, ou plus de trois barres dans l’un d’eux : le bas de la slide déborde.

## JSON

La composition courante : les quatre trimestres nommés, trois chantiers, les trois états.

```json
{ "layout": "roadmap", "eyebrow": "Feuille de route · 2027", "title": "Une année, trois chantiers menés de front.", "content": "colonnes : T1 · janv – mars, T2 · avril – juin, T3 · juil – sept, T4 · oct – déc\n# Guichet unique | Portail et accueil\nCahier des charges | T1 | réalisé\nDéveloppement du portail | T2-T3 | en cours\nOuverture au public | T4 | à venir\n# Données | Socle et qualité\nInventaire des bases | T1 | réalisé\nRéférentiel des adresses | T2-T4 | en cours\n# Agents | Formation et accompagnement\nFormateurs relais | T2 | en cours\nSessions dans les mairies | T3-T4 | à venir", "notes": "Insister sur le troisième trimestre : le portail et les sessions de formation se chevauchent, c’est la période tendue pour la DSI." }
```

Des colonnes à soi (quatre semestres), des positions en pourcentage et un pictogramme par chantier ; ici `T1`
désigne la colonne `2026 · S2` :

```json
{ "layout": "roadmap", "eyebrow": "Réseau de chaleur · 2026-2028", "title": "Dix-huit mois de travaux, la concertation en continu.", "content": "colonnes : 2026 · S2, 2027 · S1, 2027 · S2, 2028 · S1\n# (chantier) Travaux | Chaufferie et réseau\nChaufferie bois | T1-T2 | en cours\nPose des 9 km de réseau | 30-80 | à venir\nRaccordement des 40 bâtiments | T4 | à venir\n# (euro) Financement | Subventions et emprunt\nFonds chaleur notifié | T1 | réalisé\nEmprunt signé | 20-45 | en cours\n# (groupe) Concertation | Habitants et copropriétés\nRéunions de quartier | 0-100 | en cours", "notes": "Les copropriétés du secteur sud n’ont pas encore voté : la barre de raccordement peut glisser d’un semestre." }
```

Sans ligne `colonnes` (T1 à T4), deux chantiers : le cas le plus court, qui convient aussi à Plateforme.

```json
{ "layout": "roadmap", "title": "Le déploiement de la vidéoprotection, trimestre par trimestre.", "content": "# Caméras | 24 sites\nMarché attribué | T1 | réalisé\nPose, secteur centre | T2 | en cours\nPose, secteurs nord et sud | T3-T4 | à venir\n# Supervision | Locaux et agents\nTravaux d’aménagement | T1-T2 | réalisé\nRecrutement des opérateurs | T3 | à venir", "notes": "Préciser que les secteurs nord et sud dépendent du raccordement à la fibre, prévu à l’automne." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
