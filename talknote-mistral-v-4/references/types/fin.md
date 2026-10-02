# `fin` · Fin

> La dernière slide : elle clôt la présentation par un message, ses coordonnées et un contact.

## Quand l’employer

- **Dans la matière, tu as trouvé** : une formule de clôture ou une invitation aux questions ; un bloc de
  contacts en fin de document ou en pied de page (adresse, téléphone, courriel, site) ; le nom d’un service
  référent et son courriel ; une phrase qui dit où trouver le détail (« les fiches sont disponibles sur
  demande ») ; le mot de la fin, la phrase à retenir.
- **Plutôt que** : `titre`, qui ouvre la présentation et porte la date et l’auteur ; `section`, qui ouvre
  une partie, même la dernière ; `contenu`, si la conclusion s’argumente en plusieurs points — la `fin` ne
  porte qu’un message et des coordonnées, elle ne récapitule rien.
- **Pas pour** : récapituler les décisions ou les prochaines étapes (une slide `etapes`, `jalons` ou
  `contenu` juste avant) ; remercier au milieu du déroulé.

Une seule `fin` par présentation, toujours en dernière position.

## Structure de l’information

```text
┌──────────────────────────────────────────────────────────────┐
│                                                              │
│   title    Merci. ==Place aux questions.==                   │
│   ▬▬▬▬     (filet dans la couleur d’accent)                  │
│   content  Les fiches détaillées sont disponibles.           │
│                                                              │
│   ADRESSE           TÉLÉPHONE        SITE                    │
│   4 place du Marché 02 40 00 00 00   ecoles.exemple.fr       │
│   Libellé           Libellé          Libellé                 │
│   Valeur            Valeur           Valeur                  │
│                                                              │
│   author   ▬▬ CELLULE.ECOLES@EXEMPLE.FR                      │
│   (par défaut, le tout est centré dans la slide)             │
└──────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
fin
├── title    : le message de clôture, une ligne ou deux
├── content  : la phrase de clôture, puis une ligne par coordonnée
│     ├── une ligne sans « | » : le message, où trouver le détail
│     └── « Libellé | Valeur » : adresse, téléphone, courriel, site
├── author   : le contact, en petites capitales sous un filet (facultatif)
└── notes    : ce que le présentateur dit en refermant
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `title` | Le message de clôture : un remerciement, une invitation aux questions, la phrase à retenir. `==mots==` met des mots en couleur ; `(nom)` en tête pose un pictogramme. | Une ou deux lignes, soixante caractères environ. En Libre le corps baisse au-delà de 32 puis de 64 caractères. |
| `content` | La phrase de clôture, puis les coordonnées, une par ligne. | Facultatif. Syntaxe ci-dessous : une ou deux phrases, puis deux à quatre coordonnées. |
| `author` | Le contact : un courriel, un service. Rendu en petites capitales, précédé d’un filet d’accent. | Une ligne courte. Le modèle `bdt` ne l’affiche pas (voir « Selon le modèle »). |
| `disposition` | `""` (centrée) ou `gauche`. | Voir « Dispositions ». |

Ce type n’emploie ni `eyebrow`, ni `image`, ni `content2`, ni `content3` : aucun gabarit de `fin` ne les
dessine. Seul `revue`, qui ne redessine pas ce type, reprend le surtitre au milieu de son en-tête courant.
`progressive` est sans effet : une `fin` n’a pas de puce à découvrir. Les champs communs (`anim`,
`transition`, `notes`) : voir `references/format-json.md`.

## Syntaxe de `content`

Une ligne sans `|` reste du message ; une ligne qui contient un `|` devient une coordonnée. Les deux
peuvent se mêler, mais écris toujours le message d’abord, les coordonnées ensuite : le rendu les regroupe
de toute façon sous le message, dans leur ordre d’écriture.

- **Le message** : une ligne = un paragraphe, sous le titre et son filet. Une phrase suffit, deux au plus.
- **Une coordonnée** : `Libellé | Valeur`. Le libellé s’écrit en petites capitales de couleur, la valeur
  en dessous. Exemple : `Téléphone | 02 40 00 00 00`.
- Libellés courts, d’un mot : `Adresse`, `Téléphone`, `Courriel`, `Site`, `Contact`.
- Trois cellules ou plus : la première est le libellé, les suivantes sont recollées avec ` | ` dans la
  valeur. N’écris donc que deux cellules par ligne.
- En Libre, les coordonnées se rangent côte à côte et passent à la ligne quand elles ne tiennent plus
  (trois par rangée environ) : deux à quatre coordonnées, pas davantage.
- `**gras**`, `*italique*` et `==surligné==` s’appliquent au titre comme au message (syntaxe générale :
  `references/format-json.md`).
- Pas de `- ` ni de `# ` : la marque est retirée et la ligne devient un simple paragraphe.

Exemple de champ complet :
`"content": "Les fiches détaillées sont disponibles sur demande.\nAdresse | 4 place du Marché, Nantes\nTéléphone | 02 40 00 00 00"`

## Dispositions

| `disposition` | Composition | La choisir quand |
| --- | --- | --- |
| `""` | Titre, filet, message, coordonnées et contact centrés au milieu de la slide. | Par défaut : la slide de clôture qu’on laisse affichée pendant les questions. |
| `gauche` | Le même bloc aligné à gauche, comme la couverture. | Pour répondre à la couverture, ou quand le message et les coordonnées sont longs. |

```text
gauche
┌──────────────────────────────────────────────┐
│  Merci. Place aux questions.                 │
│  ▬▬▬▬                                        │
│  Les fiches détaillées sont disponibles.     │
│  ADRESSE            TÉLÉPHONE                │
│  4 place du Marché  02 40 00 00 00           │
│  ▬▬ CELLULE.ECOLES@EXEMPLE.FR                │
└──────────────────────────────────────────────┘
```

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : tout s’applique.
  Ces quatre mises en page gardent le rendu Libre de la `fin` et y posent seulement leur repère (le grand
  numéro de `cadran`, la gouttière de `marge`, la trame de `grille`, le compteur). Elles ne réduisent jamais
  un texte trop long : écris court.
- **Modèles complets qui redessinent ce type** : `aube`, `opale` et `bdt`. Tous les trois gardent la
  disposition `gauche`. Écritures particulières :
  - `aube` : une icône en tête du `title` (`(fusée) On commence lundi.`) devient le grand signe évidé de la
    slide ; en `gauche`, sans icône, une flèche prend sa place. La `fin` y prend le dégradé en pleine page.
  - `opale` : le message se pose sur le panneau de verre, les disques de couleur y sont amples ; tout
    s’écrit à l’encre.
  - `bdt` : le titre tient dans une zone étroite du gabarit officiel — deux ou trois mots par ligne. Les
    coordonnées s’écrivent en une colonne, le libellé en rouge devant la valeur. **Ce modèle n’affiche pas
    `author`** : mets le contact en coordonnée (`Contact | …`).
  - Les autres modèles complets (`revue`, `chantier`, `marqueur`, `tampon`, `pastille`, `bloc`, `anneau`,
    `crayon`, `cimaise`) habillent le rendu Libre de leur palette et de leurs polices.
- **Plateforme** (`"modele": "plateforme"`) : `gauche` s’applique. La slide passe sur fond sombre, la marque
  de la charte est posée en grand au-dessus du titre, et chaque coordonnée devient une ligne
  `Libellé : Valeur`. Pas de pictogramme : un `(nom)` en tête du titre est retiré sans s’afficher.

## Pièges

- Un `|` dans une phrase du message : la phrase entière devient une coordonnée, coupée en libellé et
  valeur. Réserve ce caractère aux lignes de coordonnées.
- Un libellé long (`Adresse postale du service instructeur`) : il s’affiche en petites capitales, sur
  plusieurs lignes. Un mot suffit.
- Six ou huit coordonnées : elles se serrent et perdent leur force. Deux à quatre, les plus utiles.
- Un `eyebrow` écrit sur une `fin` : sauf dans l’en-tête courant de `revue`, aucun gabarit ne le dessine,
  le texte est perdu.
- Un contact placé dans `author` avec le modèle `bdt` : il ne s’affiche pas. Écris-le en coordonnée.
- « Merci de votre attention. » seul : le titre est la dernière chose qu’on lit, fais-lui dire quelque
  chose (`Merci. ==Place aux questions.==`).
- Une seule slide de la présentation peut porter sa propre `transition` : la `fin` est une bonne
  candidate (`"transition": "zoom"`).

## JSON

La disposition par défaut, avec ses coordonnées, son contact et les notes de clôture :

```json
{ "layout": "fin", "title": "Merci. ==Place aux questions.==", "content": "Les fiches détaillées, école par école, sont disponibles auprès de la cellule d’ingénierie.\nAdresse | Maison des Trois Rivières, 4 place du Marché\nTéléphone | 02 40 00 00 00\nSite | ecoles-sobres.exemple.fr", "author": "cellule.ecoles@exemple.fr", "notes": "Laisser la slide affichée pendant les questions. Rappeler que le prochain comité se tient en mars, et que les diagnostics sont attendus pour février." }
```

Alignée à gauche, avec une icône en tête du titre (petit pictogramme en Libre, grand signe avec `aube`) et
sa propre transition :

```json
{ "layout": "fin", "disposition": "gauche", "title": "(fusée) On commence ==lundi==.", "content": "Le compte rendu et le calendrier partent ce soir à tous les participants.", "author": "mission.numerique@exemple.fr", "transition": "zoom", "notes": "Nommer les deux personnes qui pilotent la première semaine. Annoncer le point d’étape à quinze jours." }
```

Pour une présentation en `bdt`, le contact passe en coordonnée, puisque ce modèle est le seul à ne pas
afficher `author` :

```json
{ "layout": "fin", "title": "Merci de votre attention.", "content": "Les annexes détaillées sont jointes au dossier de séance.\nContact | Direction de l’appui territorial\nCourriel | appui.territorial@exemple.fr\nTéléphone | 01 00 00 00 00" }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
