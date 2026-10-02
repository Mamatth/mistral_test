# `citation` · Citation

> Une phrase forte et qui l’a dite, seule au centre de la slide ou à côté d’un court texte d’appui.

## Quand l’employer

- **Dans la matière, tu as trouvé** : un verbatim d’entretien ou d’enquête (« ce que disent les usagers ») ;
  une phrase entre guillemets dans un rapport, un discours, un éditorial ; le témoignage d’une personne
  nommée, avec son rôle ; une formule qui résume à elle seule un constat ou une ambition ; la phrase d’un
  participant à un test utilisateur.
- **Plutôt que** : `contenu` quand la phrase n’est pas une parole rapportée mais un argument à développer en
  points ; `imagetexte` quand c’est la photo qui compte et que le texte n’en est que la légende ; `equipe`
  quand plusieurs personnes sont à présenter avec leur rôle, sans phrase à mettre en avant.
- **Pas pour** : un chiffre marquant en une phrase (`chiffre`) ; une série de verbatims : garde-en un ou
  deux, une citation par slide, et mets les autres dans les `notes`.

## Structure de l’information

```text
┌────────────────────────────────────────────────────────────┐
│ eyebrow                                                    │
│                                                            │
│ “                                                          │
│ title : la citation, en grand et en italique,              │
│ ==les mots soulignés== dans la couleur d’accent            │
│                                                            │
│ — AUTHOR : L’ATTRIBUTION, EN CAPITALES                     │
│                                                            │
└────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
citation
├── title      : la citation, une ou deux phrases ; au-delà de 64 caractères, le corps baisse
├── author     : qui l’a dite, « Prénom Nom, rôle » ou un rôle seul (attendu, mais facultatif)
├── eyebrow    : repère court au-dessus, « Témoignage », « Vague 2025 » (facultatif)
├── content    : le texte d’appui, un à trois paragraphes courts (facultatif)
├── content2   : le titre du texte d’appui, une ligne (facultatif, avec content)
└── notes      : la source du verbatim, son contexte, le portrait à ajouter
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `title` | La citation elle-même. | Sans guillemets : TalkNote les dessine. `==mots==` pour en souligner une partie, un groupe de mots au plus. Une ou deux phrases ; au-delà de 64 caractères, le corps est réduit. |
| `author` | L’attribution. | Sans tiret en tête : Libre en dessine un (« — »), comme les modèles qui l’habillent ; Aube et Opale posent un point ; Marqueur, Tampon, BDT et Plateforme, rien. `Prénom Nom, rôle` quand la personne est nommée ; sinon le rôle seul, `Directrice d’une école pilote`. |
| `eyebrow` | Surtitre, repère court au-dessus de la citation. | Facultatif. |
| `content` | Le texte d’appui : le contexte de la citation, d’où elle vient, ce qu’elle illustre. | Facultatif. Paragraphes courts ; la citation passe alors à côté. |
| `content2` | Le titre du texte d’appui. | Facultatif, une ligne ; ne l’écris qu’avec `content`. |
| `disposition` | `""` ou `portrait`. | Voir « Dispositions ». |
| `image` | Le portrait, en disposition `portrait`. | Laisse `""` et écris `Portrait à ajouter : …` dans `notes` (voir `references/images.md`). |

Les champs communs (`anim`, `transition`, `notes`, `progressive`) : voir `references/format-json.md`.
L’animation `flou` convient à une citation.

## Syntaxe de `content`

- `title`, `author`, `eyebrow` et `content2` sont des lignes simples, sans retour à la ligne : `**gras**`,
  `*italique*`, `==surligné==` (syntaxe du texte : voir `references/format-json.md`).
- `content` suit la syntaxe commune : une ligne par paragraphe (`\n`), `- ` pour une puce, `# ` pour un
  intertitre. Un à trois paragraphes courts suffisent : ce texte s’affiche en petit, à côté ou sous la
  citation. Préfère la prose aux puces : Marqueur et Tampon posent chaque ligne en simple paragraphe.
  Exemple : `Douze directions d’école interrogées un an après les travaux.\nTrois sujets reviennent partout.`
- `content2` : une ligne, le titre de ce texte, `Ce que disent les équipes`.
- Sans `content` ni `content2`, la citation est seule, centrée. Dès que l’un des deux est écrit, la slide
  passe en deux colonnes, le texte d’appui à gauche, la citation à droite :

```text
┌────────────────────────────────────────────────────────────┐
│ eyebrow                        “                           │
│ content2 : titre de l’appui    title : la citation,        │
│ content : le contexte,         ==mots soulignés==          │
│ un ou deux paragraphes                                     │
│                                — AUTHOR                    │
└────────────────────────────────────────────────────────────┘
```

## Dispositions

| `disposition` | Composition | La choisir quand |
| --- | --- | --- |
| `""` | La citation seule, centrée ; ou à droite de son texte d’appui. | Par défaut ; une phrase anonyme, un rôle sans nom, aucune photo à attendre. |
| `portrait` | Un portrait rond à gauche, la citation à droite avec son attribution, puis le texte d’appui sous un filet. Sans photo, le cercle montre les initiales de l’attribution, sinon un guillemet. | La personne est nommée et une photo existe ou peut être ajoutée : un témoignage incarné. |

```text
┌────────────────────────────────────────────────────────────┐
│             eyebrow                                        │
│   ╭─────╮   “                                              │
│   │ CV  │   title : la citation, ==mots soulignés==        │
│   ╰─────╯   — AUTHOR                                       │
│             ─────────────────────────────                  │
│             content2 · content : le texte d’appui          │
└────────────────────────────────────────────────────────────┘
```

Les initiales viennent de ce qui précède la première virgule (ou `·`, `(`, `–`, `—`) dans `author` : deux ou
trois mots commençant chacun par une majuscule, dont TalkNote prend la première lettre du premier et du
dernier. `Claire Vasseur, directrice du programme` donne CV ; `Jean-Marc Dupont · maire` donne JD ;
`Marie de Lattre` (un mot en minuscule) ou `Directrice d’une école pilote` (quatre mots) donnent un
guillemet à la place.

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : tout s’applique.
- **Modèles complets qui redessinent la citation** (`compose`) : `marqueur`, `tampon`, `aube`, `opale`,
  `bdt`. Tous les cinq gardent `portrait`. Leurs écritures :
  - `marqueur` : les guillemets « » sont ajoutés autour de la citation ; l’attribution est coupée sur la
    virgule (ou `·`, `—`), le nom en avant, le rôle dessous ; en `portrait`, un disque jaune porte les
    initiales tant que la photo manque, ou un guillemet quand l’attribution n’en donne pas ;
    `content2` puis `content` forment un bloc d’appui sous la citation.
  - `tampon` : guillemets « » ajoutés, attribution coupée sur la virgule comme Marqueur ; `portrait` pose
    une bande photo sur toute la droite de la slide, qui porte le mot « PORTRAIT » et jamais d’initiales
    tant que la photo manque ; `content` passe en chapô sous l’attribution, et `content2` n’est pas
    affiché.
  - `aube` : la citation dans une carte au dégradé, avec un grand guillemet ou, en `portrait`, un portrait
    rond (initiales sans photo) ; `content2` en libellé et `content` dessous, dans la carte.
  - `opale` : des disques de couleur amples derrière le verre ; en `portrait`, le portrait rond (initiales
    sans photo) se pose à côté du panneau ; `content2` puis `content` sous l’attribution.
  - `bdt` : la citation en rouge gras avec l’hexagone du modèle, le texte d’appui dans la colonne de
    droite (`content2` en chapô, `content` à la suite) ; en `portrait`, le portrait prend la place de
    l’hexagone et la citation passe dans la colonne de droite.
  Les autres modèles complets (`revue`, `chantier`, `pastille`, `bloc`, `anneau`, `crayon`, `cimaise`)
  habillent le rendu Libre : `portrait` et le texte d’appui s’y comportent comme en Libre.
- **Plateforme** (`"modele": "plateforme"`) : garde `portrait` (un cadre photo à gauche, sans initiales tant
  que la photo manque) ; sinon le texte d’appui à gauche, la citation à droite sur un filet rouge ; aucun
  pictogramme n’est dessiné.

## Pièges

- Des guillemets écrits dans `title` (`« … »` ou `\"…\"`) : TalkNote dessine les siens, et les tiens s’y
  ajouteraient en Libre comme en Plateforme. Écris la phrase nue.
- Un tiret en tête de `author` (`— Claire Vasseur`) : Libre et les modèles complets le retirent, Plateforme
  l’afficherait devant l’attribution. Écris-la nue.
- Une citation de trois phrases : le corps baisse dès 64 caractères et les modèles complets la tassent par
  paliers. Coupe-la, ou mets la suite dans `content`.
- `content2` sans `content` : la slide passe en deux colonnes pour un simple titre. Donne-le seulement avec
  un texte d’appui.
- `portrait` sur une attribution sans nom (`Directrice d’une école pilote`) : le cercle ne montre qu’un
  guillemet. Garde `""`, sauf si la photo sera fournie.
- Une phrase inventée pour une personne réelle : jamais. Sans verbatim dans la matière, attribue-la à un
  rôle (`Un agent d’accueil`) et signale-la « (proposition) » dans les `notes`.
- Un pictogramme `(nom)` n’a pas sa place ici : Marqueur et Tampon le retirent du texte d’appui, Plateforme
  n’en dessine aucun.

## JSON

La citation seule, centrée, avec l’animation `flou` :

```json
{ "layout": "citation", "eyebrow": "Retour d’usage", "title": "Je trouve ma fiche de paie et mes congés ==sans appeler personne==.", "author": "Technicienne de maintenance, site de Lyon", "anim": "flou", "notes": "Verbatim du test utilisateur du 12 mai 2026. Source : compte rendu des tests, p. 3. Enchaîner sur les indicateurs d’usage de la slide suivante." }
```

Avec portrait : la personne est nommée, la photo viendra plus tard.

```json
{ "layout": "citation", "disposition": "portrait", "eyebrow": "Le programme vu de l’intérieur", "title": "Une école rénovée, c’est ==deux degrés de plus== en janvier et douze pour cent de budget en moins.", "author": "Claire Vasseur, directrice du programme", "notes": "Portrait à ajouter : photo de Claire Vasseur. Sans photo, le cercle montre ses initiales, CV. Source : entretien du 3 juin 2026." }
```

Avec un texte d’appui : le contexte à gauche, la citation à droite.

```json
{ "layout": "citation", "eyebrow": "Témoignage", "title": "Le plus grand changement, c’est que ==plus personne ne parle de la température== en conseil d’école.", "author": "Directeur d’école, vague 2025", "content2": "Ce que disent les équipes", "content": "Nous avons interrogé les directrices et directeurs des douze écoles de la première vague, un an après leur retour dans les murs.\nTrois sujets reviennent partout : la fraîcheur en juin, le silence de la ventilation, et le temps passé à apprendre les nouveaux réglages.", "notes": "Douze entretiens de trente minutes, menés en mai 2026. Source : synthèse des entretiens de la vague 1." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
