# `portefeuille` · Portefeuille

> Des sujets répartis en colonnes selon leur état d’avancement, chaque colonne comptant ses sujets, la
> colonne en cours mise en avant : où en est chaque chose, d’un coup d’œil.

## Quand l’employer

- **Dans la matière, tu as trouvé** : une liste de projets, de dossiers, de sites ou d’actions dont chacun
  porte un état (« à cadrer », « en cours », « livré », « retenu », « écarté ») ; un tableau de suivi ou un
  kanban ; un « portefeuille de projets » dans un rapport d’activité ; des actions réparties en réalisé, en
  cours et à venir, sans dates ; la question « où en est-on ? » posée sur plusieurs sujets à la fois.
- **Plutôt que** : `roadmap` si chaque sujet a un début et une fin dans l’année, des chantiers à placer sur
  des trimestres ; `tableau` si chaque sujet porte plusieurs informations (commune, budget, statut) à lire
  ligne à ligne ; `faits` si les sujets sont trois ou quatre et que chacun mérite une description ;
  `matrice` si les sujets se rangent sur deux axes (effort et impact) et non sur la seule progression.
- **Pas pour** : une suite d’étapes dans l’ordre (`etapes`), des dates (`jalons`), deux options à opposer
  (`colonnes`).

## Structure de l’information

```text
┌──────────────────────────────────────────────────────────────┐
│ eyebrow                                                      │
│ title : ce que l’état du portefeuille montre                 │
│ ╭─────────────────╮ ┏━━━━━━━━━━━━━━━━━┓ ╭─────────────────╮  │
│ │ ÉTIQ. · 3 SUJETS│ ┃ ÉTIQ. · 4 SUJETS┃ │ ÉTIQ. · 2 SUJETS│  │
│ │ Titre           │ ┃ Titre   (actif) ┃ │ Titre           │  │
│ │ ▪ Sujet         │ ┃ ▪ Sujet         ┃ │ ▪ Sujet         │  │
│ │ ▪ Sujet         │ ┃ ▪ Sujet         ┃ │ ▪ Sujet         │  │
│ │ ▪ Sujet         │ ┃ ▪ Sujet         ┃ │                 │  │
│ │                 │ ┃ ▪ Sujet         ┃ │                 │  │
│ ╰─────────────────╯ ┗━━━━━━━━━━━━━━━━━┛ ╰─────────────────╯  │
└──────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
portefeuille
├── title      : ce que l’état du portefeuille montre, en une phrase (soixante caractères environ)
├── eyebrow    : repère court (« Avancement », « Suivi · Juin 2026 ») (facultatif)
├── content    : deux à quatre colonnes, chacune ouverte par une ligne « # »
│     ├── # Titre | Étiquette | actif
│     │     ├── Titre     : l’état, en un ou deux mots (« À cadrer », « En cours », « Livrés »)
│     │     ├── Étiquette : un complément court ; TalkNote y ajoute « · n sujets » (facultatif)
│     │     └── actif     : marque la colonne en cours, mise en avant ; une seule (facultatif)
│     └── Sujet   : une ligne par sujet, son nom seul ; cinq par colonne au plus
└── notes      : ce que le présentateur dit et qui n’est pas écrit
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `eyebrow` | Repère au-dessus du titre : « Avancement », « Portefeuille 2027 », « Suivi · Juin 2026 ». | Facultatif, deux ou trois mots. |
| `title` | Le message : ce que l’état du portefeuille montre. | Soixante caractères environ, deux lignes au plus ; au-delà de 64 caractères il s’affiche plus petit. |
| `content` | Les colonnes et leurs sujets. | Obligatoire, syntaxe ci-dessous ; vide, la slide affiche à sa place le rappel de saisie de TalkNote. |

Ce type n’a pas de disposition : laisse `disposition` à `""`, le rendu ignore toute autre valeur. `content2`,
`content3`, `author` et `image` ne servent pas. Les champs communs (`anim`, `transition`, `notes`, `progressive`) :
voir `references/format-json.md`.

## Syntaxe de `content`

Une ligne `# ` ouvre une colonne ; les lignes qui suivent, jusqu’au `# ` suivant, sont ses sujets.

| Ligne | Écriture | Rendu |
| --- | --- | --- |
| Colonne | `# En cours \| Chantiers` | Une carte : l’étiquette en petites capitales de couleur, complétée du compte (« Chantiers · 3 sujets »), puis le titre en grand. |
| Colonne en avant | `# En cours \| Chantiers \| actif` | La même, inversée : fond de la couleur du texte, texte de la couleur du fond. |
| Colonne sans étiquette | `# Livrés`, ou `# En cours \| \| actif` pour la mettre en avant | Le compte seul en étiquette (« 3 sujets ») ; la cellule vide garde `actif` à sa place. |
| Sujet | `Refonte du socle` | Une ligne de la colonne, précédée d’un petit carré de couleur. |

- **Titre** : l’état, en un ou deux mots. Range les colonnes de gauche à droite dans le sens de la
  progression, de ce qui reste à faire vers ce qui est fait (ou l’inverse), et garde ce sens d’une slide à
  l’autre.
- **Étiquette** : un complément (« Vague 2027 », « En production »). N’y écris pas le nombre de sujets,
  TalkNote l’ajoute. Un ou plusieurs `#` valent pareil.
- **`actif`** : en troisième cellule, tel quel (`active` et `courant` marchent aussi, majuscules
  indifférentes). Le mot est cherché dans la cellule : n’y écris pas `inactif`, la colonne serait mise en
  avant. Une seule colonne en avant par slide : celle où le travail se fait.
- **Sujets** : une ligne, un nom. Un `- `, `* `, `• `, `1. ` ou `1) ` en tête est accepté et retiré : le carré est dessiné
  par TalkNote, le numéro ne s’affiche pas. Toute la ligne est le sujet : un `|` s’y afficherait tel quel.
  Trente à quarante caractères, moins à quatre colonnes.
- **Limites** : deux à quatre colonnes (la cinquième et les suivantes ne s’affichent pas), cinq sujets par
  colonne ; au-delà, résume ou scinde en deux slides.
- **Pictogramme** : `(nom)` en tête du titre (`# (chantier) En cours | Chantiers | actif`) ou d’un sujet
  (`(école) École du Moulin`). Noms : `references/pictogrammes.md`.
- `**gras**`, `==surligné==`, ` // ` (un sujet sur deux lignes) : voir `references/format-json.md`.

## Selon le modèle

- **Libre** (`"modele": ""`) : tout s’applique : des cartes à fond léger cernées d’un filet fin, la colonne
  en avant inversée. Ses mises en page (`cadran`, `marge`, `palier`, `grille`) retirent le fond et les angles
  arrondis des cartes, qu’un simple filet cerne ; la colonne en avant reste inversée.
- **Modèles complets** : aucun ne redessine ce type (`compose`) ; les douze (`revue`, `chantier`, `marqueur`,
  `tampon`, `pastille`, `bloc`, `anneau`, `crayon`, `cimaise`, `aube`, `opale`, `bdt`) habillent le rendu
  Libre : cartes sans fond, cernées d’un filet, angles droits, la colonne en avant inversée aux couleurs du
  modèle, les pictogrammes dessinés. `opale` fait de chaque colonne une carte de verre à grand rayon et cerne
  la colonne en avant d’un trait de son premier ton au lieu de la peindre.
- **Plateforme** (`"modele": "plateforme"`) : son propre gabarit : surtitre, titre en grand replié sur une
  colonne étroite (dix-huit caractères par ligne environ : garde-le court), puis des cartes blanches à filet
  gris, l’étiquette en rouge ; la colonne en avant en anthracite, son texte en blanc, son étiquette rouge. Pas
  de pictogramme : le mot est retiré sans s’afficher.

## Pièges

- `actif` en deuxième cellule (`# En cours | actif`) est lu comme l’étiquette : la colonne n’est pas mise en
  avant et affiche « actif · 3 sujets ». Écris `# En cours | | actif`. Deux colonnes `actif` donnent deux
  colonnes inversées et plus aucun repère : une seule.
- Un sujet écrit avant la première ligne `# ` ouvre une colonne sans titre ni étiquette, qui n’affiche que
  son compte.
- Le nombre dans l’étiquette (« 3 projets ») fait doublon : TalkNote l’ajoute lui-même (« 3 projets · 3
  sujets »).
- Cinq colonnes : la cinquième disparaît sans prévenir, regroupe deux états. Une colonne sans sujet affiche
  « 0 sujet » : garde-la seulement si ce vide est le message (rien n’est encore livré).
- Un sujet qui est une phrase déborde de sa colonne, surtout à quatre colonnes : le nom seul sur la slide,
  le détail dans les notes.
- Toute `disposition` est ignorée ; `progressive` ne change rien : les colonnes entrent l’une après l’autre
  avec l’animation de la slide, sujets compris.

## JSON

Trois états, la colonne du milieu en avant :

```json
{ "layout": "portefeuille", "eyebrow": "Avancement", "title": "Où en sont les projets numériques de la collectivité.", "content": "# À cadrer | Idées retenues\nPortail des associations\nPaiement en ligne de la cantine\nDémarches d’urbanisme en ligne\n# En cours | Chantiers | actif\nRefonte du site de la ville\nNouvelle messagerie des agents\nSupervision du réseau\n# Livrés | En production\nPrise de rendez-vous en mairie\nSignalement des incidents de voirie", "notes": "La colonne du milieu est mise en avant : c’est là que se joue l’année. Le budget de chaque chantier est détaillé en annexe." }
```

Quatre états, un pictogramme en tête de chaque titre, un sujet en gras :

```json
{ "layout": "portefeuille", "eyebrow": "Plan climat · Suivi 2027", "title": "Quarante actions, quatre états.", "content": "# (ampoule) Proposées | Ateliers citoyens\nVélos en libre-service\nMarché bio hebdomadaire\nMonnaie locale\n# (validé) Retenues | Vote du conseil\nForêt urbaine du canal\nCantines à 50 % de bio\nPrime vélo cargo\n# (chantier) En cours | Lancées en 2027 | actif\n**Rénovation de cinq écoles**\nPistes cyclables, tranche 2\nRéseau de chaleur du centre\n# (trophée) Réalisées | Depuis 2025\nExtinction nocturne de l’éclairage\nComposteurs de quartier\nToitures solaires des gymnases", "notes": "Quarante actions au total, trois par colonne ici : la liste complète est dans le rapport annuel. La rénovation des écoles est en gras, c’est le plus gros budget." }
```

Deux colonnes sans étiquette, la première en avant, les sujets écrits avec des puces :

```json
{ "layout": "portefeuille", "title": "Le déploiement de la fibre, commune par commune.", "content": "# Raccordées | | actif\n- Montjoux\n- Lurcy\n- Brémont\n- Vaux-le-Haut\n- Saint-Ours\n# À raccorder\n- Castelvieil\n- La Vergne", "anim": "fondu", "notes": "Sans étiquette, chaque colonne n’affiche que son compte : « 5 sujets » et « 2 sujets ». Les deux dernières communes seront raccordées avant l’été." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
