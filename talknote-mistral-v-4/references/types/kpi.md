# `kpi` · Indicateurs

> Trois ou quatre indicateurs suivis, chacun sur sa carte : le libellé, la valeur en grand, sa variation
> fléchée et un commentaire.

## Quand l’employer

- **Dans la matière, tu as trouvé** : trois ou quatre indicateurs suivis dans le temps, chacun avec sa
  valeur du moment et son évolution (« +12 % sur un an », « −3 points par rapport à l’objectif ») ; un bilan
  annuel, une revue de programme, un rapport d’activité où chaque chiffre est accompagné d’un écart ; des
  objectifs chiffrés à un an, avec le chemin qui reste à faire ; un « objectif / réalisé ».
- **Plutôt que** : `chiffre` si les nombres n’ont pas d’évolution à montrer, ou si un seul chiffre doit
  frapper (un à quatre chiffres très grands, peu de texte) ; `graph` au-delà de quatre valeurs, ou quand
  c’est la courbe qui compte (une série dans le temps, une répartition) ; `tableau` dès qu’il y a plus de
  quatre indicateurs ou plusieurs colonnes par indicateur (une valeur par année, par site, par service) ;
  `dashboard` si l’état du programme se lit mieux en deux ou trois graphiques qu’en quatre nombres.
- **Pas pour** : des chiffres sans suivi (un budget, une surface, une population : `chiffre`) ni des
  réalisations sans nombre (`faits`).

## Structure de l’information

```text
┌────────────────────────────────────────────────────────────┐
│ eyebrow                                                    │
│ title : ce que les indicateurs montrent, ensemble          │
│                                                            │
│ ╭────────────────╮ ╭────────────────╮ ╭────────────────╮   │
│ │ LIBELLÉ        │ │ LIBELLÉ        │ │ LIBELLÉ        │   │
│ │ 84,2 %         │ │ 412            │ │ 2,4 j          │   │
│ │ ↑ +3,1 pts     │ │ ↑ +18 %        │ │ ↓ −0,9 j       │   │
│ │                │ │                │ │                │   │
│ │ Commentaire    │ │ Commentaire    │ │ Commentaire    │   │
│ ╰────────────────╯ ╰────────────────╯ ╰────────────────╯   │
└────────────────────────────────────────────────────────────┘
```

Ce que porte la slide, du plus au moins important :

```text
kpi
├── title       : ce que les indicateurs montrent, en une phrase (soixante caractères environ)
├── eyebrow     : repère court (« Indicateurs · Bilan 2026 ») (facultatif)
├── content     : trois à quatre lignes « Libellé | Valeur | Variation | Commentaire »
│     ├── Libellé     : le nom de l’indicateur, deux à quatre mots, en petites capitales
│     ├── Valeur      : le nombre puis son unité (« 84,2 % », « 2,4 j ») ; en très grand
│     ├── Variation   : l’écart, signe en tête (« +3,1 pts », « −0,9 j ») ; flèche ajoutée (facultatif)
│     └── Commentaire : une ligne de contexte, posée en bas de la carte (facultatif)
├── disposition : `""` en ligne, `grille` deux par rangée
└── notes       : ce que le présentateur dit et qui n’est pas écrit
```

## Champs

| Champ | Rôle ici | Contrainte |
| --- | --- | --- |
| `eyebrow` | Repère au-dessus du titre : « Indicateurs · Bilan 2026 », « Objectifs · Fin 2027 ». | Facultatif, deux ou trois mots. |
| `title` | Le message : ce que les indicateurs montrent ensemble, pas « Indicateurs ». | Soixante caractères environ, deux lignes au plus ; au-delà de 64 caractères il s’affiche plus petit. |
| `content` | Les indicateurs, une ligne chacun. | Obligatoire. Syntaxe ci-dessous ; trois à quatre lignes. |
| `disposition` | `""` (en ligne) ou `grille`. | Voir « Dispositions ». |

`content2`, `content3`, `author` et `image` ne servent pas ici. Les champs communs (`anim`,
`transition`, `notes`, `progressive`) : voir `references/format-json.md`.

## Syntaxe de `content`

Une ligne par indicateur, quatre cellules séparées par ` | `, dans cet ordre.

| Cellule | Écriture | Rendu |
| --- | --- | --- |
| Libellé | `Rendement du réseau` | Petites capitales en gris, au-dessus de la valeur. |
| Valeur | `84,2 %`, `2,4 j`, `1 120 €/m²`, `412` | Le premier groupe de chiffres en très grand ; tout ce qui suit (l’unité) se détache, plus petit et en gris — y compris un second nombre : `6 jours / 7` donne « 6 » en grand et « jours / 7 » en petit. |
| Variation | `+3,1 pts`, `−0,9 j`, `+9 pts vs objectif` | Sur sa ligne, une flèche en tête : `↑` en couleur d’accent pour une hausse, `↓` en retrait pour une baisse. |
| Commentaire | `Objectif 85 % en 2027.` | Une ligne en petit, alignée en bas de la carte. |

- Les deux premières cellules sont attendues ; la variation et le commentaire peuvent manquer. Une variation
  vide s’écrit avec sa barre : `Accueil physique | 6 jours / 7 | | Le guichet reste ouvert.`
- La valeur commence par le nombre : un signe éventuel (`+`, `−`), des chiffres avec leurs espaces, virgules
  ou points, puis l’unité (`%`, `M€`, `°C`, `/10`, `€/m²`). Une valeur qui ne commence pas par un chiffre
  (`n. c.`, `AAA`) s’affiche entière, sans unité détachée.
- La variation est une baisse si elle commence par `-`, `−` ou `↓` ; sinon c’est une hausse, et `↑` est
  ajouté, même devant un texte sans signe (`Objectif atteint` devient `↑ Objectif atteint`). Une flèche
  déjà écrite est gardée telle quelle : `↓ −7,1 °C`.
- `(nom)` en tête du libellé dessine une petite icône devant lui (`(goutte) Rendement du réseau | …`) ;
  un par ligne au plus, seulement s’il aide à lire. Noms : `references/pictogrammes.md`.
- `**gras**`, `==surligné==`, ` // ` : voir `references/format-json.md`.

**Une seule idée par carte.** Le libellé nomme, la valeur dit, la variation situe, le commentaire explique
en une ligne (soixante caractères environ) : la source, la période, ce à quoi l’écart se compare.

## Dispositions

| `disposition` | Composition | La choisir quand |
| --- | --- | --- |
| `""` | Les cartes côte à côte, une par indicateur ; à quatre, les valeurs sont un peu plus petites. | Trois ou quatre indicateurs de même rang, lus d’un regard. |
| `grille` | Deux cartes par rangée, plus larges et moins hautes ; avec trois indicateurs, la troisième carte prend toute la largeur ; à quatre, les valeurs retrouvent leur grande taille. | Des libellés ou des commentaires longs, des valeurs larges (`1 120 €/m²`), ou quatre indicateurs qu’on veut lire en deux paires. |

```text
┌────────────────────────────────────────────────────────────┐
│ ╭───────────────────────────╮ ╭───────────────────────────╮│
│ │ LIBELLÉ    84,2 %  ↑ +3,1 │ │ LIBELLÉ    412     ↑ +18 %││
│ │ Commentaire               │ │ Commentaire               ││
│ ╰───────────────────────────╯ ╰───────────────────────────╯│
│ ╭─────────────────────────────────────────────────────────╮│
│ │ LIBELLÉ    2,4 j   ↓ −0,9 j   Commentaire               ││
│ ╰─────────────────────────────────────────────────────────╯│
└────────────────────────────────────────────────────────────┘
```

## Selon le modèle

- **Libre** (`"modele": ""`) et ses mises en page (`cadran`, `marge`, `palier`, `grille`) : tout s’applique.
- **Modèles complets** qui redessinent ce type (`compose`) : `marqueur`, `anneau`, `crayon`, `bdt`. Tous
  gardent `grille`. Chacun lit les mêmes quatre cellules, mais les dessine à sa façon :
  - `marqueur` : un indicateur dont la valeur est un pourcentage de 0 à 100 devient une jauge en anneau
    (trois au plus), la valeur au centre, le libellé, la variation et le commentaire à côté ; les autres
    deviennent des encadrés (valeur, libellé, commentaire) qui ne montrent pas la variation. Jauges à
    gauche, encadrés à droite ; `grille` les empile.
  - `anneau` : quatre indicateurs au plus ; un pourcentage de 0 à 100 devient un anneau, les autres un
    chiffre ; libellé, variation fléchée et commentaire sous chacun, en corail, ambre et céladon tour à tour.
  - `crayon` : quatre figures au plus, la première et la dernière à l’encre bleue ; la variation suit le
    libellé, le commentaire vient dessous.
  - `bdt` : une ligne par indicateur, comme un tableau à points de conduite : le libellé, les points, la
    valeur, puis la variation et le commentaire joints par « · » ; six lignes au plus ; une ligne sans `|`
    devient la légende, à droite.
  Les autres modèles complets (`revue`, `chantier`, `tampon`, `pastille`, `bloc`, `cimaise`, `aube`, `opale`)
  habillent le rendu Libre : les cartes, `grille` et les icônes s’appliquent ; `revue` donne à la baisse une
  couleur dédiée.
- **Plateforme** (`"modele": "plateforme"`) : des cartes blanches ; le libellé en capitales grises, la valeur
  en très gras, la variation en vert (hausse) ou en rouge (baisse), le commentaire en bas. `grille`
  s’applique. Pas de pictogramme : le mot est retiré sans s’afficher.

## Pièges

- L’ordre est l’inverse de `chiffre` : ici le libellé vient d’abord, la valeur ensuite. `84,2 % | Rendement`
  affiche « 84,2 % » en petites capitales et « Rendement » en très grand, sans unité.
- Une baisse est toujours dessinée en retrait, même quand c’est une bonne nouvelle (moins de fuites, moins
  de réclamations). Pour la mettre en valeur, écris la baisse dans la valeur et l’écart à l’objectif, positif,
  dans la variation : `Consommation d’énergie | −47 % | +9 pts vs objectif | Objectif de −38 % dépassé.`
- Une variation sans signe reçoit une flèche vers le haut : « stable » devient « ↑ stable ». Laisse la
  cellule vide et dis-le dans le commentaire.
- Un `|` dans le commentaire le coupe : ce qui suit la barre est perdu.
- Cinq indicateurs ou plus : en Libre, les cartes s’étrécissent ; `anneau` et `crayon` n’en gardent que
  quatre, `bdt` six, `marqueur` ne dessine que trois jauges. Scinde en deux slides ou passe à `tableau`.
- Une valeur large (`12 450 000 €`) est réduite pour tenir sur sa ligne : écris `12,45 M€`. Un libellé de
  plus de quatre mots risque de passer sur deux lignes en petites capitales : raccourcis-le.
- Un titre neutre (« Indicateurs », « Chiffres 2026 ») ne dit rien : écris ce que les indicateurs montrent.

## JSON

Quatre indicateurs en ligne, le bilan d’un réseau d’eau :

```json
{ "layout": "kpi", "eyebrow": "Indicateurs · Bilan 2026", "title": "Le réseau perd moins d’eau et répare plus vite.", "content": "Rendement du réseau | 84,2 % | +3,1 pts | Objectif 85 % en 2027, fixé par le schéma directeur.\nFuites réparées | 412 | +18 % | Grâce aux capteurs posés sur les 60 km les plus anciens.\nDélai moyen d’intervention | 2,4 j | −0,9 j | Contre 3,3 jours en 2025.\nRéclamations | 138 | −22 % | Sur 41 000 abonnés.", "notes": "Le rendement conditionne la subvention de l’agence de l’eau en 2027 : c’est l’indicateur à commenter en premier. Les 412 réparations viennent du rapport annuel du délégataire." }
```

Trois objectifs en grille, la troisième carte sur toute la largeur, une variation vide pour l’indicateur
qui ne bouge pas :

```json
{ "layout": "kpi", "eyebrow": "Objectifs · Fin 2027", "title": "Ce que nous visons dans un an.", "disposition": "grille", "content": "Démarches en ligne | 38 | +12 | Sur les 52 démarches recensées à l’accueil.\nDossiers traités sous dix jours | 91 % | +14 pts | Contre 77 % aujourd’hui.\nAccueil physique | 6 jours / 7 | | Stable : le guichet reste ouvert à ceux qui n’ont pas Internet.", "notes": "L’accueil physique ne bouge pas : c’est un engagement pris devant le conseil, à rappeler avant de passer aux chiffres de la dématérialisation." }
```

Dans une présentation en `marqueur` (`"modele": "marqueur"` dans l’enveloppe), les deux pourcentages
deviennent des jauges en anneau et la facture un encadré, sans sa variation ; en Libre, trois cartes :

```json
{ "layout": "kpi", "eyebrow": "Sobriété · Hiver 2026-2027", "title": "Trois indicateurs suivis chaque semaine.", "content": "Bâtiments chauffés à 19 °C | 92 % | +11 pts | 134 bâtiments équipés d’une sonde.\nBaisse de la consommation | 14 % | +3 pts vs hiver 2025 | À climat corrigé, gaz et électricité.\nFacture d’énergie | 3,8 M€ | −0,6 M€ | Malgré la hausse des tarifs de janvier.", "notes": "Les 19 °C sont la consigne nationale : rappeler que les crèches et les EHPAD en sont exemptés. La facture baisse malgré les tarifs, grâce au volume." }
```

Cet objet se place dans le tableau `slides` de l’enveloppe décrite dans `references/format-json.md`.
