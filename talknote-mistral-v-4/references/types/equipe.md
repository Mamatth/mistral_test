# `equipe` · Équipe

> Trois à huit personnes qui portent le projet : un portrait rond, le nom, le rôle et une ligne chacune.

## Quand l’employer

- **Dans la matière, tu as trouvé** : une liste de noms avec leur fonction (équipe projet, cellule
  d’ingénierie, comité) ; un organigramme, un trombinoscope, une page « qui sommes-nous » ; une phrase du
  genre « le programme est porté par X, Y et Z », suivie de ce que chacun fait ; les interlocuteurs d’un
  marché ou d’un groupement (maîtrise d’ouvrage, assistance, titulaire) avec leur rôle ; une liste de
  contacts où chaque personne a son périmètre.
- **Plutôt que** : `faits` quand les cartes portent des instances ou des réalisations plutôt que des
  personnes nommées (un comité de pilotage est un fait ; ses membres sont une équipe) ; `citation` en
  `portrait` quand une seule personne parle et que c’est sa phrase qui compte, pas son rôle ; `galerie`
  quand ce sont les images qui font le propos (lieux, chantiers, avant et après) et non les personnes ;
  `fin` quand tu veux seulement laisser un contact.
- **Pas pour** : une liste de structures ou de partenaires sans personne nommée (`faits`, `contenu`) ;
  plus de huit personnes : au-delà, les suivantes ne sont pas affichées — présente alors les rôles.

## Structure de l’information

```text
┌────────────────────────────────────────────────────────────┐
│ eyebrow                                                    │
│ title : ce que l’équipe permet de dire                     │
│                                                            │
│   ( O )      ( O )      ( O )      ( O )                   │
│   le portrait rond, ou les initiales du nom                │
│                                                            │
│   Nom        Nom        Nom        Nom                     │
│   RÔLE       RÔLE       RÔLE       RÔLE                    │
│   Une ligne  Une ligne  Une ligne  Une ligne               │
└────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
equipe
├── title       : ce que l’équipe démontre, en une phrase (soixante caractères environ)
├── eyebrow     : repère court (« L’équipe », « Gouvernance ») (facultatif)
├── content     : une ligne par personne, trois à huit
│     ├── Nom      : prénom et nom, la première cellule
│     ├── Rôle     : sa fonction, en capitales d’accent (facultatif)
│     └── Ligne    : ce qu’elle fait sur ce projet (facultatif)
├── portraits   : un portrait par personne, dans l’ordre des lignes ; vide, les initiales
├── disposition : `""` en ligne, `grille` le portrait à gauche, `vedette` la première personne en grand
└── notes       : les portraits à ajouter, et ce que le présentateur dit de chacun
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `eyebrow` | Repère au-dessus du titre : « L’équipe », « Gouvernance », « Vos interlocuteurs ». | Facultatif, deux ou trois mots. |
| `title` | Le message : ce que l’équipe démontre, pas « L’équipe ». | Soixante caractères environ ; au-delà de 64, il s’affiche plus petit. |
| `content` | Une ligne par personne. | Trois à huit lignes ; la neuvième et les suivantes ne sont pas affichées. |
| `portraits` | Un portrait par personne, dans l’ordre des lignes. | Laisse `[]` : voir `references/images.md`. |
| `disposition` | `""` (en ligne), `grille`, `vedette`. | Voir plus bas. |

Ce type n’emploie ni `content2`, ni `content3`, ni `author`, ni `image`. `progressive` est sans effet :
les personnes entrent ensemble, en cascade. Champs communs (`anim`, `transition`, `notes`) :
`references/format-json.md`.

## Syntaxe de `content`

Une ligne par personne, trois cellules séparées par `|` : `Nom | Rôle | Une ligne`.

- **Nom**, première cellule : « Prénom Nom », écrit en grand sous le portrait. Seul obligatoire.
- **Rôle**, deuxième cellule, facultatif : la fonction, affichée en capitales espacées dans la couleur
  d’accent. Deux à quatre mots (« Directrice du programme », « Architecte conseil »).
- **Une ligne**, troisième cellule, facultative : ce que la personne fait ici, soixante à
  quatre-vingt-dix caractères. Tout ce qui suit le deuxième `|` en fait partie.
- Sans photo, TalkNote dessine les **initiales** : la première lettre du prénom et celle du dernier mot
  du nom, quand le nom tient en deux ou trois mots commençant tous par une majuscule. Sinon, seule la
  première lettre s’affiche.
- ` // ` coupe une ligne dans une case, `**gras**` et `==surligné==` s’écrivent partout : voir
  `references/format-json.md`. Un pictogramme `(nom)` se pose en tête d’une cellule, mais le portrait
  rond tient déjà ce rôle : garde-le pour d’autres types.

## Dispositions

| `disposition` | Composition | La choisir quand |
| --- | --- | --- |
| `""` | En ligne : les personnes côte à côte, le portrait au-dessus du nom ; autant de colonnes que de personnes. | Trois ou quatre personnes. Dès cinq, portraits et textes se resserrent ; dès sept, tout devient petit. |
| `grille` | Le portrait à gauche du texte, deux par rangée (trois au-delà de quatre personnes, quatre au-delà de six). | Cinq personnes et plus, ou des lignes de description un peu longues. |
| `vedette` | La première personne en grand à gauche, les autres en liste à droite, petit portrait devant leur texte. | Une personne porte le projet et les autres l’entourent. |

```text
┌────────────────────────────── grille ──────────────────────┐
│ title                                                      │
│                                                            │
│   ( O )  Nom                  ( O )  Nom                   │
│          RÔLE                        RÔLE                  │
│          Une ligne                   Une ligne             │
│   ( O )  Nom                  ( O )  Nom                   │
│          RÔLE                        RÔLE                  │
│          Une ligne                   Une ligne             │
└────────────────────────────────────────────────────────────┘
```

```text
┌────────────────────────────── vedette ─────────────────────┐
│ title                                                      │
│   (        )           ( o )  Nom                          │
│   (  GRAND )                  RÔLE                         │
│   (PORTRAIT)                  Une ligne                    │
│   (        )           ( o )  Nom                          │
│   Nom                         RÔLE                         │
│   RÔLE                        Une ligne                    │
│   Une ligne                                                │
└────────────────────────────────────────────────────────────┘
```

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : tout
  s’applique. Le portrait est un rond cerné d’un filet d’accent ; sans photo, les initiales sont à
  l’accent, et le rôle s’écrit en capitales espacées, à l’accent lui aussi.
- **Modèles complets** qui redessinent ce type (`compose`) : `opale` seulement. Les portraits deviennent
  des disques posés sur la vitre, cernés d’un filet fin, les initiales à l’encre ; le rôle reste en bas
  de casse, dans le gris des repères. Il garde `grille` et `vedette` ; en vedette, dès sept personnes,
  les autres se rangent sur deux colonnes. Les autres modèles complets (`revue`, `chantier`, `marqueur`,
  `tampon`, `pastille`, `bloc`, `anneau`, `crayon`, `cimaise`, `aube`, `bdt`) habillent le rendu Libre
  avec leurs polices, leur accent et leurs repères, et gardent les trois dispositions.
- **Plateforme** (`"modele": "plateforme"`) : pas d’équipe dans le catalogue officiel. La slide reprend
  les cartes des faits — une carte blanche par personne, un portrait rond (les initiales en rouge sans
  photo), une ligne de repère « — 01 · Rôle », le nom en titre, la ligne de description en dessous.
  `grille` et `vedette` s’appliquent, avec le même compte de colonnes qu’en Libre ; dès six personnes les
  cartes se resserrent, et en `vedette` les autres se rangent sur deux colonnes. Pas de pictogramme : le
  mot est retiré sans s’afficher.

## Pièges

- L’ordre des cellules est fixe : nom, rôle, ligne. `Claire Vasseur | Pilote le calendrier | Directrice
  du programme` met « Pilote le calendrier » en capitales d’accent, à la place du rôle.
- Une quatrième cellule ne crée pas de champ : elle se recolle à la ligne de description, avec un `|`
  qui s’affiche tel quel. Trois cellules par personne, pas plus, et pas de `|` dans une phrase.
- Au-delà de huit lignes, les personnes en trop disparaissent sans avertissement.
- Huit personnes en disposition par défaut font huit colonnes très étroites : passe en `grille`.
- Une virgule ou une parenthèse dans le nom ampute les initiales (« Vasseur, Claire » donne « V »), et
  un nom de plus de trois mots, ou dont un mot est en bas de casse (« Claire de Vasseur »), n’en donne
  qu’une. Écris le nom seul, en deux ou trois mots, et mets le reste dans le rôle.
- « L’équipe » en titre ne dit rien : mets-le en `eyebrow` et garde le titre pour le message.
- N’invente jamais d’adresse de portrait : laisse `"portraits": []` et note dans `notes` les photos à
  ajouter.

## JSON

Quatre personnes, la disposition par défaut :

```json
{ "layout": "equipe", "eyebrow": "L’équipe", "title": "Quatre personnes pour soixante-dix écoles.", "content": "Claire Vasseur | Directrice du programme | Pilote le calendrier et le budget des soixante-dix écoles\nNadir Belkacem | Architecte conseil | Suit les chantiers et les entreprises\nInès Rocher | Cheffe de projet numérique | L’application et les capteurs de consommation\nThéo Marchal | Chargé de concertation | Écoles, parents d’élèves et communes", "notes": "Portraits à ajouter : les quatre. Sans photo, la slide affiche leurs initiales. Dire que l’équipe est mutualisée entre les douze communes, et qu’aucun poste n’a été créé." }
```

Six personnes, en grille (trois par rangée, le portrait à gauche du texte) :

```json
{ "layout": "equipe", "eyebrow": "Gouvernance", "title": "Six métiers autour d’un même plan de charge.", "disposition": "grille", "content": "Sophie Vermeulen | Direction générale adjointe | Arbitre les priorités et porte le plan devant les élus\nKarim Ouali | Systèmes d’information | Infrastructure, sécurité et hébergement des services\nÉlodie Pasquier | Cheffe de projet données | Ouvre les données et outille les tableaux de bord\nMathieu Roussel | Référent achats | Marchés, notifications et suivi des titulaires\nAnaïs Kerbrat | Cheffe de projet usages | Forme les agents et recueille les retours des guichets\nPierre Lemoine | Contrôle de gestion | Suit les dépenses et l’avancement des engagements", "notes": "Portraits à ajouter pour les six. Insister sur le fait que ces six personnes ne sont pas six postes : quatre d’entre elles interviennent à temps partiel." }
```

Une personne en vedette, les appuis à côté :

```json
{ "layout": "equipe", "eyebrow": "Maîtrise d’ouvrage", "title": "Une cheffe de projet à plein temps, trois appuis.", "disposition": "vedette", "content": "Inès Rocher | Cheffe de projet | Seule à plein temps : calendrier, budget, comité mensuel et relation aux écoles\nNadir Belkacem | Architecte conseil | Deux jours par mois sur les chantiers\nThéo Marchal | Concertation | Un jour par semaine auprès des écoles\nClaire Vasseur | Direction du programme | Arbitrages et présentation devant les élus", "notes": "Portraits à ajouter : les quatre. La vedette sert ici à dire la réalité des moyens : une seule personne à plein temps sur soixante-dix écoles." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
