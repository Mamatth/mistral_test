# `jalons` · Jalons

> Une frise de quatre à cinq dates structurantes, dans l’ordre du temps ; ce qui est passé se marque comme réalisé et remplit son point.

## Quand l’employer

- **Dans la matière, tu as trouvé** : l’historique d’un projet avec ses dates (un lancement, des vagues, une livraison) ; un calendrier des prochains mois en quatre ou cinq rendez-vous datés (comité, attribution des marchés, début des travaux) ; du passé et de l’avenir mêlés, où il faut montrer où l’on en est aujourd’hui ; des dates disséminées dans un récit (« depuis 2024 », « d’ici 2028 ») ; un rétroplanning à quelques échéances.
- **Plutôt que** : `etapes` quand l’ordre compte mais pas les dates (une méthode, un processus : audit, programme, chantier, mesure) ; `roadmap` quand plusieurs chantiers avancent en parallèle sur l’année et qu’il faut des durées (des barres de T1 à T3) et des états ; `tableau` quand le calendrier dépasse six lignes ou porte d’autres colonnes (responsable, budget, statut), ou que les statuts sont variés (en retard, à risque, bloqué).
- **Pas pour** : une seule date (une `section` ou un `chiffre` la dit mieux) ; des échéances qui durent ou se chevauchent (`roadmap`) ; une liste d’actions sans date (`etapes`, `contenu`).

## Structure de l’information

```text
┌──────────────────────────────────────────────────────────────┐
│ EYEBROW                                                      │
│ title : le message de la frise, une ligne                    │
│                                                              │
│ ●────────────●────────────○────────────○───────────────────  │
│ DATE         DATE         DATE         DATE                  │
│ Titre        Titre        Titre        Titre                 │
│ Description  Description  Description  Description           │
│                                                              │
│ titre de la présentation                            4 / 12   │
└──────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
jalons
├── title       : le message de la frise, soixante caractères environ
├── eyebrow     : le repère au-dessus du titre (« Chronologie », « Calendrier ») (facultatif)
├── content     : 4 à 5 lignes « Date | Titre | Description », dans l’ordre du temps
│     ├── x en tête   : jalon réalisé, son point se remplit (facultatif)
│     ├── Date        : courte ; en Libre, en capitales et en couleur (« Sept. 2024 », « T3 2027 »)
│     ├── Titre       : deux ou trois mots courts, le nom du jalon
│     └── Description : une phrase, ce qui s’est passé ou se passera
├── disposition : "" (en ligne) ou "escalier"
├── unParUn     : true révèle les jalons un à un (facultatif)
└── notes       : ce que le présentateur dit et qui n’est pas écrit
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `title` | Le message de la frise : ce que les dates racontent. `==mots==` possible. | Une ligne, soixante caractères environ ; au-delà de 64 caractères le corps baisse. |
| `eyebrow` | Le repère au-dessus du titre : `Chronologie`, `Calendrier`, `Partie 03 · Et après`. | Court. Facultatif. |
| `content` | Les jalons, une ligne chacun : `Date \| Titre \| Description`, `x ` devant les jalons réalisés. | Quatre à cinq lignes, six au plus ; trois cellules par ligne ; dans l’ordre chronologique. |
| `disposition` | `""` (en ligne) ou `escalier` (voir « Dispositions »). | |
| `unParUn` | `true` : les jalons apparaissent un à un, à chaque appui sur →, comme des puces. `false` (défaut) : le fil se trace d’un jalon à l’autre dès l’entrée de la slide. | Sans guillemets. Absent sinon. |

`content2`, `content3` et `author` ne servent pas ici. Les champs communs (`anim`, `transition`, `notes`, `progressive`…) : voir `references/format-json.md`.

## Syntaxe de `content`

- Une ligne par jalon, trois cellules séparées par `|`, dans cet ordre : `Date | Titre | Description`.
  `Été 2025 | Première vague | 12 écoles rénovées pendant les vacances scolaires.`
- `x ` en tête (un x, puis une espace) : jalon réalisé. Son point se remplit de la couleur d’accent ; sans `x`, le point reste un anneau vide. Marque le passé, jamais l’avenir.
  `x Sept. 2024 | Lancement | Convention signée par 42 communes.`
- Dans l’ordre du temps, de gauche à droite : les jalons réalisés d’abord, puis ceux à venir. Il n’y a pas de marque « en cours » : le présent se lit au premier jalon sans `x` (Anneau et Marqueur le mettent en couleur).
- La date : un texte libre et court, écrit tel quel : `Sept. 2024`, `T3 2027`, `24 sept. 2026`, `Été 2025`, `2028`. En Libre, elle s’affiche en capitales.
- Le titre : deux ou trois mots courts. La case est étroite, un cinquième de la largeur pour cinq jalons.
- La description : une phrase de dix à quinze mots. ` // ` y passe à la ligne (deux à quatre lignes au plus) ; `**gras**` et `==surligné==` valent dans chaque cellule, voir `references/format-json.md`.
- Quatre à cinq jalons ; six au plus, au-delà les colonnes s’étranglent. Trois cellules par ligne : une cellule manquante laisse sa zone vide sur la frise, une quatrième cellule n’est pas affichée.
- `(nom)` en tête d’une cellule y pose un pictogramme (`Sept. 2024 | (école) Lancement | …`) ; noms dans `references/pictogrammes.md`. Rarement utile sur une frise : la date et le point suffisent.

## Dispositions

| `disposition` | Composition | La choisir quand |
| --- | --- | --- |
| `""` | En ligne : les jalons côte à côte, à égale largeur, sur une frise horizontale ; un fil va du premier point au dernier et se prolonge jusqu’au bord droit ; sous chaque point, la date, le titre, la description. | Par défaut : une chronologie, un calendrier. |
| `escalier` | La frise monte de gauche à droite : chaque jalon est posé une marche plus haut que le précédent, et le fil va en diagonale d’un point au suivant. La marche fait 72 px au plus et se réduit avec le nombre de jalons ; la montée totale ne dépasse pas 240 px. | Une progression, une montée en charge, un déploiement qui s’étend : ce qui se lit aussi comme un gain. Deux jalons au moins. |

```text
escalier
┌──────────────────────────────────────────────────────────────┐
│ title : le message de la frise                               │
│                                              ○ DATE          │
│                                 ○ DATE     ╱   Titre         │
│                    ● DATE    ╱   Titre  ╱                    │
│       ● DATE    ╱   Titre  ╱                                 │
│         Titre ╱                                              │
└──────────────────────────────────────────────────────────────┘
```

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : tout s’applique, les deux dispositions et `unParUn`. Le fil se trace d’un jalon à l’autre en 1,5 s environ ; chaque point se pose quand le fil l’atteint, un jalon réalisé se remplit, puis sa date, son titre et sa description apparaissent.
- **Modèles complets** qui redessinent les jalons : `revue`, `marqueur`, `anneau`, `opale`. `unParUn` vaut partout. Dispositions gardées :

  | Modèle | `escalier` | Écriture particulière |
  | --- | --- | --- |
  | `revue` | oui | une frise éditoriale : le filet du haut se trace colonne après colonne, puis chaque jalon entre ; date et titre sur une ligne, la description dessous |
  | `marqueur` | oui | les jalons deviennent des chevrons numérotés 01, 02… : le titre dans le chevron, la date en tête de la description en dessous ; le premier jalon sans `x` est surligné en jaune (le dernier, si tous sont réalisés) |
  | `anneau` | oui | une frise de pastilles rondes, corail, ambre et céladon tour à tour : un jalon réalisé en pastille pleine, le premier sans `x` cerné d’un halo de sa couleur, les suivants en anneau d’encre sur le fond |
  | `opale` | ignorée | une file de cartes de verre, la date en tête de chaque carte suivie d’une flèche, le rang 01, 02… ; un jalon réalisé se distingue à la densité ; six cartes au plus |

  Les autres modèles complets (`chantier`, `tampon`, `pastille`, `bloc`, `crayon`, `cimaise`, `aube`, `bdt`) habillent le rendu Libre de leurs couleurs et de leurs polices : tout s’applique.
- **Plateforme** (`"modele": "plateforme"`) : `escalier` gardée ; la frise reprend la construction Libre aux mesures de la charte. Pas de pictogramme : `(nom)` est retiré sans s’afficher. Une slide `etapes` y prend d’ailleurs la même frise, le numéro tenant lieu de date.

## Pièges

- La date d’abord : `Lancement | Sept. 2024 | …` met le titre en capitales colorées et la date en gros. L’ordre est `Date | Titre | Description`.
- `> ` en tête n’existe pas pour les jalons : en Libre, le chevron reste dans la date (« > ÉTÉ 2027 »). Seul `x ` marque quelque chose ; le présent se lit au premier jalon sans `x`.
- Un `|` dans une description coupe la phrase : la quatrième cellule est ignorée. Écris « ou », un tiret, deux points.
- Six jalons, ou des titres de quatre mots : les colonnes s’étranglent, et un mot très long fait baisser toute la rangée. Quatre à cinq jalons, des titres de deux ou trois mots courts, une date brève (`Du 12 septembre au 3 octobre 2026` déborde).
- Un `x` sur un jalon à venir, ou un jalon réalisé après un jalon à venir : la frise dit le contraire du calendrier, et Anneau ou Marqueur colorent le mauvais jalon « en cours ». Les réalisés en tête, puis les autres.
- `"unParUn": "true"` entre guillemets : erreur, c’est un booléen. `escalier` avec `opale` est ignorée sans rien casser : la file de cartes reste en ligne.

## JSON

La disposition par défaut, une chronologie aux trois premiers jalons réalisés, avec des notes :

```json
{ "layout": "jalons", "eyebrow": "Chronologie", "title": "Les étapes franchies depuis le lancement.", "content": "x Sept. 2024 | Lancement | Convention signée par 42 communes, cellule d’ingénierie recrutée.\nx Été 2025 | Première vague | 12 écoles rénovées pendant les vacances scolaires.\nx Été 2026 | Deuxième vague | 14 écoles livrées, dont 3 avec une cour végétalisée.\nÉté 2027 | Troisième vague | 18 écoles programmées, marchés en cours d’attribution.\n2028 | Achèvement | Les 26 dernières écoles, puis l’évaluation finale.", "notes": "Trois jalons réalisés sur cinq : insister sur le rythme tenu, une vague par été. Annoncer que la troisième vague est l’objet de la décision du jour." }
```

En escalier, pour une montée en charge :

```json
{ "layout": "jalons", "eyebrow": "Déploiement", "title": "Un guichet numérique étendu à tout le département en trois ans.", "content": "x Janv. 2025 | Pilote | Deux intercommunalités, 3 000 usagers, un seul service : l’inscription périscolaire.\nx Sept. 2025 | Extension | Douze services en ligne, 40 000 usagers, le compte citoyen unique.\nMars 2026 | Généralisation | Toutes les communes volontaires, 180 000 usagers.\n2027 | Vitesse de croisière | Le guichet devient l’entrée par défaut ; l’accueil physique reste ouvert.", "disposition": "escalier", "notes": "La frise monte : chaque jalon multiplie le nombre d’usagers. Dire que l’accueil physique n’est pas supprimé, c’est la question qui revient à chaque réunion." }
```

Un calendrier révélé un jalon à la fois, en fondu :

```json
{ "layout": "jalons", "eyebrow": "Calendrier", "title": "Quatre rendez-vous d’ici l’été prochain.", "content": "x 15 sept. 2026 | Comité de pilotage | Choix du scénario de financement de la dernière vague.\nDéc. 2026 | Marchés attribués | Cinq lots, dix-huit écoles, ouverture aux entreprises locales.\nMars 2027 | Conseils d’école | Présentation des travaux aux équipes et aux parents.\nJuillet 2027 | Début des chantiers | Neuf semaines de travaux, rentrée garantie le 2 septembre.", "unParUn": true, "anim": "fondu", "notes": "Les jalons apparaissent un à un : présenter chaque rendez-vous avant de passer au suivant. Le comité de septembre est déjà derrière nous, les trois autres engagent la salle." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
