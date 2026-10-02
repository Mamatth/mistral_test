# Styles : thèmes, modèles, réglages

> Ouvre cette fiche pour proposer un style, savoir ce qu’un modèle dessine lui-même et quelles dispositions
> il garde, ou écrire des réglages de charte.

Deux champs de l’enveloppe décident de tout le rendu : `theme` (les couleurs et les polices) et `modele`
(la mise en page). Tu ne choisis jamais une couleur dans une slide : le style est global. Les autres champs
de l’enveloppe : voir `references/format-json.md`.

## 1. Les six thèmes

Ils s’emploient avec le modèle Libre (`"modele": ""` ou l’une de ses mises en page).

| `theme` | Couleurs et typographie | Caractère | Quand le proposer |
| --- | --- | --- | --- |
| `minuit` | Bleu nuit et or, sans empattement | Sobre, posé | Le défaut, sans consigne : comité, revue de projet, bilan |
| `papier` | Crème et encre, accent vermillon, empattements | Éditorial, institutionnel | Rapport, note de cadrage, conseil d’administration |
| `braise` | Bordeaux sombre et orange, titres Didot | Dramatique, chaleureux | Lancement, événement, clôture de programme |
| `foret` | Vert profond et doré | Naturel, ancré | Environnement, territoire, énergie, agriculture |
| `neon` | Noir et vert fluo, chasse fixe | Technique, tranchant | Sécurité, infrastructure, public de développeurs |
| `nuage` | Gris bleuté clair et corail, formes arrondies | Pédagogique, accueillant | Formation, grand public, usagers, scolaire |

Sans consigne : `minuit`. Propose deux thèmes au plus, et dis en une ligne pourquoi.

## 2. Libre et ses mises en page

Libre se règle en deux temps : la mise en page dans `modele`, le thème dans `theme`.

| `modele` | Ce que la mise en page change | Quand |
| --- | --- | --- |
| `""` | La composition d’origine : titre en haut, texte dessous, pied de page. | Le défaut : toujours sûr. |
| `cadran` | Le numéro de la slide, en très grand, structure la page. | Une suite d’étapes, un déroulé qu’on suit. |
| `marge` | Une gouttière à gauche porte le surtitre et le numéro. | Un document de travail, annoté. |
| `palier` | Un titre immense, des repères minuscules. | Peu de mots, des affirmations fortes. |
| `grille` | Huit colonnes tracées sur la slide. | Un propos graphique, assumé, technique. |

Longueur du texte : en Libre classique, un contenu trop long est réduit par paliers plutôt que de déborder.
Avec `cadran`, `marge`, `palier` et `grille`, la couverture et le texte ne sont **jamais** réduits : écris
court, surtout avec `palier` (les autres types, eux, gardent la réduction).

Le pied de page (`"footer": true`, le titre et le numéro en bas) n’existe qu’en Libre classique : les quatre
mises en page et les modèles complets posent leur propre repère, et `footer` n’y change rien. En Libre
classique, il ne se pose pas non plus sur `titre`, `section`, `matrice`, `etapes`, `equipe`, `imagetexte`,
`galerie`, `image` ni `fin`.

```json
{
  "version": 2,
  "title": "Rénover les groupes scolaires",
  "theme": "papier",
  "modele": "palier",
  "transition": "fondu",
  "footer": true,
  "slides": [
    { "layout": "titre", "eyebrow": "Comité de pilotage · Octobre 2026", "title": "Rénover sans fermer.", "content": "Trois ans de travaux dans douze groupes scolaires, sans déplacer une classe.", "author": "8 octobre 2026 · Direction du patrimoine" },
    { "layout": "fin", "title": "Merci. ==Vos questions ?==", "content": "Le calendrier détaillé est joint au compte rendu.", "author": "patrimoine@exemple.fr" }
  ]
}
```

## 3. Les modèles complets

Un modèle complet apporte sa palette, ses polices, sa grille et redessine une partie des types. Il ne se
croise pas avec un thème : **écris le même identifiant dans `modele` et dans `theme`**.

| `modele` = `theme` | Caractère | Quand le choisir |
| --- | --- | --- |
| `revue` | Noir et blanc éditorial, chiffres de chapitre géants | Bilan annuel, dossier long, ton de magazine |
| `chantier` | Vermillon et anthracite, aplats pleins | Travaux, programme opérationnel, ton direct |
| `marqueur` | Jaune surligneur, barres et jauges | Revue de projet, point d’avancement |
| `tampon` | Blanc suisse, graisse maigre, disque vermillon | Propos net et court : trois lignes de titre au plus |
| `pastille` | Crème, outremer et ambre, formes rondes | Grand public, usagers, service accueillant |
| `bloc` | Capitales très grasses, khaki et noir | Rapport technique, propos affirmé |
| `anneau` | Anneaux fins corail, ambre et céladon | Frises, jauges, suivi d’indicateurs |
| `crayon` | Mono bas de casse, une encre bleue tracée à la main | Atelier, note de travail, hypothèses |
| `opale` | Verre dépoli : des disques nets diffusés derrière une vitre | Produit, marque, présentation soignée |
| `cimaise` | La photo d’abord : papier gris perle, titres très gras, filet corail | Portfolio, rapport illustré, belles photos |
| `aube` | Ciel de lever du jour : dégradé, cartes blanches, grande icône évidée | Présentation d’entreprise, pitch, produit |
| `bdt` | Le gabarit PowerPoint de la Banque des Territoires : Arial, hexagones rouges | Seulement si on le demande |
| `plateforme` | L’identité Plateforme de la Banque des Territoires | Seulement si on le demande |

Ce qu’il faut savoir avant de choisir :

- **Photos.** `pastille`, `bloc`, `anneau`, `crayon` et `cimaise` posent la photo de la couverture ; `bloc`,
  `anneau`, `crayon` et `cimaise` celle de la `section` ; `cimaise` aussi celle d’une slide `faits`. `opale`
  et `aube` n’en posent ni sur `titre` ni sur `section` : leur fond leur appartient. Laisse `image` vide et
  décris la photo dans `notes` : voir `references/images.md`.
- **`aube`.** Commence le `title` de `titre`, de chaque `section` et de la `fin` par une icône,
  `"(fusée) Notre cap pour 2027"` : le modèle la dessine en grand.
- **`cimaise`.** Un `eyebrow` de 18 caractères au plus s’empile en couleur sur le titre ; plus long, il reste
  un surtitre ordinaire.
- **`bdt` et `plateforme`.** Ajoute `"mention"` (la diffusion) et `"docref"` (le nom du document et sa date) :
  ce sont les deux seuls modèles qui les affichent, en pied de page.

```json
{
  "version": 2,
  "title": "Notre cap 2027",
  "theme": "aube",
  "modele": "aube",
  "slides": [
    { "layout": "titre", "eyebrow": "Séminaire annuel", "title": "(fusée) Notre cap pour 2027", "content": "Trois priorités, un budget, une équipe.", "author": "12 janvier 2027 · Direction générale" },
    { "layout": "fin", "title": "(cible) À vous de jouer.", "content": "Les fiches priorités partent demain matin.", "author": "direction@exemple.fr" }
  ]
}
```

```json
{
  "version": 2,
  "title": "Programme Petites Villes",
  "theme": "bdt",
  "modele": "bdt",
  "mention": "Interne",
  "docref": "Programme Petites Villes · Octobre 2026",
  "slides": [
    { "layout": "titre", "eyebrow": "Revue de portefeuille", "title": "Petites Villes : deux ans d’appui aux centres-bourgs.", "content": "Quarante communes accompagnées, dix-huit opérations engagées.", "author": "15 octobre 2026" },
    { "layout": "fin", "title": "Merci.", "content": "La revue détaillée est jointe.\nContact | appui.territoires@exemple.fr", "author": "Direction de l’appui aux territoires" }
  ]
}
```

## 4. Choisir un style d’après la matière

| Ce que dit la matière | Deux propositions |
| --- | --- |
| Rapport annuel, bilan long, ton institutionnel | `papier` en Libre · `revue` |
| Comité de pilotage, suivi d’un programme | `minuit` en Libre · `marqueur` |
| Travaux, voirie, énergie, chantier opérationnel | `chantier` · `foret` en Libre |
| Environnement, eau, biodiversité, territoire | `foret` en Libre · `anneau` |
| Usagers, familles, scolaire, médiation | `nuage` en Libre · `pastille` |
| Produit, service numérique, marque | `opale` · `aube` |
| Pitch, séminaire, cap stratégique | `aube` · `braise` en Libre |
| Sécurité, infrastructure, public technique | `neon` en Libre · `bloc` |
| Beaucoup de photos, visites, réalisations | `cimaise` · `nuage` en Libre |
| Atelier, hypothèses, document de travail | `crayon` · `marge` en Libre |
| Lancement, événement, clôture | `braise` en Libre · `tampon` |
| Banque des Territoires, demandé explicitement | `bdt` · `plateforme` |

## 5. Dispositions et modèles

Une disposition ne change que la composition de la slide, jamais ses couleurs. Le modèle décide s’il
l’applique : les types qu’il dessine lui-même ont déjà leur composition, et certaines variantes n’y ont plus
de sens. Tout ce qui n’est pas dans la dernière colonne s’applique.

| Modèle | Types qu’il dessine lui-même | Dispositions ignorées |
| --- | --- | --- |
| Libre `""` | aucun | aucune |
| `cadran`, `marge`, `palier`, `grille` | `titre`, `contenu` | `bas` de `titre` |
| `revue` | titre, section, contenu, imagetexte, chiffre, jalons | `numero` de `section` |
| `chantier` | titre, contenu, imagetexte, section, faits, graph, chiffre | `bas` de `titre` |
| `marqueur` | titre, graph, chiffre, jalons, kpi, citation | `bas` de `titre` |
| `tampon` | titre, section, sommaire, citation, colonnes | `bas` de `titre` ; `numero` de `section` |
| `pastille` | titre, section, faits, chiffre, graph | aucune |
| `bloc` | titre, section, sommaire, faits, chiffre, graph, tableau | `photo` de `section` ; `inverse` de `graph` ; `plein` de `tableau` |
| `anneau` | titre, section, faits, etapes, jalons, kpi, chiffre, graph | `photo` de `section` |
| `crayon` | titre, section, etapes, kpi, chiffre, graph | `photo` de `section` ; `inverse` de `graph` |
| `cimaise` | titre, section, contenu, imagetexte, image, faits, galerie, chiffre | `centre` et `bas` de `titre` ; `cote` de `contenu` ; les deux de `section` ; `centre` et `haut` d’`image` ; `vedette` de `galerie` |
| `aube` | titre, section, contenu, faits, chiffre, graph, imagetexte, citation, fin | `centre` et `bas` de `titre` ; `cote` de `contenu` ; les deux de `section` |
| `opale` | titre, sommaire, section, contenu, faits, chiffre, graph, imagetexte, citation, equipe, maquette, matrice, etapes, jalons, fin | `centre` et `bas` de `titre` ; `cote` de `contenu` ; les deux de `section` ; les deux de `sommaire` ; `cycle` d’`etapes` ; `escalier` de `jalons` |
| `bdt` | titre, sommaire, section, contenu, citation, graph, tableau, kpi, chiffre, imagetexte, image, fin | `bas` de `titre` ; `numero` de `section` ; `colonnes` de `sommaire` ; `haut` d’`image` |
| `plateforme` | tous | `cote` de `contenu` |

- La disposition `grand` de `maquette` est réservée à `opale` : partout ailleurs, elle est ignorée.
- Une disposition ignorée ne casse rien : la slide prend simplement la composition du modèle. Mais évite de
  l’écrire, elle ne dit plus rien au lecteur du JSON.
- Les dispositions elles-mêmes sont décrites dans la fiche de chaque type, `references/types/<id>.md`.
- **Pictogrammes.** Dans un type qu’il dessine lui-même, le modèle ne pose le pictogramme `(nom)` que là où
  son gabarit en prévoit un : `revue` dans `contenu` et `imagetexte` ; `chantier` dans `contenu`, `imagetexte`
  et `faits` ; `tampon` dans `sommaire` ; `pastille` dans `faits` ; `bloc` dans `sommaire`, `faits` et `graph` ;
  `anneau` dans `etapes` et `faits` ; `crayon` dans `etapes` ; `cimaise` dans `contenu`, `imagetexte` et
  `faits` ; `aube` dans `contenu`, `faits`, `graph` et `imagetexte`, plus la grande icône en tête du titre d’une
  couverture, d’une section ou d’une fin ; `opale` dans `contenu`, `graph` et `imagetexte` ; `bdt` dans
  `contenu`, `citation`, `graph` et `sommaire` ; `marqueur` dans aucun. `plateforme` n’en dessine nulle part.
  Dans les types qu’il ne dessine pas, le pictogramme s’affiche comme en Libre. Voir
  `references/pictogrammes.md`.

## 6. Écritures que les modèles complets reconnaissent

Dans les types qu’un modèle dessine lui-même (colonne du milieu ci-dessus), certaines lignes prennent un
sens de plus. Ailleurs, et en Libre, elles le perdent : au mieux elles s’affichent telles quelles, au pire
la slide devient bancale. Ne les écris que si le modèle est choisi.

- Une ligne `Valeur | libellé` (`72 % | des sites équipés`) dans le texte d’un `contenu`, d’un `imagetexte`
  ou d’un `graph` devient une statistique (`revue`, `chantier`, `bloc`), un encadré surligné (`marqueur`),
  une pastille chiffrée (`pastille`), une jauge annulaire si la valeur est en `%` (`anneau`) ou un chiffre
  sur filet (`crayon`). La valeur doit être courte (seize caractères au plus) et contenir un chiffre ; une
  ligne qui commence par une puce, un intertitre `# ` ou un repère `> ` garde son sens. `pastille` lit aussi
  ces lignes dans une `section`.
- Un graphique `barres` à une seule série est redessiné par le modèle (histogramme, barres de proportion) ;
  dans `marqueur`, un indicateur `kpi` en `%` devient une jauge.
- `chantier` : dans une `section`, une puce `- Titre | texte` devient une fiche ; le reste du texte fait le
  chapeau.
- `pastille`, `bloc`, `anneau`, `cimaise` et `aube` : dans `faits`, les lignes sans `|` forment le chapeau,
  à côté du titre ou au-dessus des cartes. N’en écris que là : en Libre, dans `chantier` et dans
  `plateforme`, une ligne sans `|` fait une carte sans titre ni texte, et `opale` ne l’affiche pas du tout.
- `aube` : dans un `contenu`, un court paragraphe placé après la liste devient la conclusion, mise en avant.
- `bdt` : le premier paragraphe d’un `contenu` est le chapeau, ses intertitres `# ` sont numérotés, et les
  sections prennent tour à tour les couleurs de chapitre.

## 7. Réglages

À écrire **seulement si on te le demande** (une couleur de charte, un texte d’en-tête ou de pied, une
option). Un objet `reglages` au niveau de la présentation, rangé par identifiant de modèle.

| Modèle | Couleurs | Autres clés |
| --- | --- | --- |
| `revue` | `fond` (le papier), `encre` (la typo ; sans elle, assortie au papier) | `tete`, `teteTexte`, `numero` (il est dans l’en-tête) ; pas de pied |
| `chantier` | `accent` (le vermillon), `inverse` (l’anthracite) | `tete`, `teteTexte`, `pied`, `piedTexte`, `numero` |
| `marqueur` | `accent` (le surligneur) | `tete`, `teteTexte`, `pied`, `piedTexte`, `numero`, `repere`, `repereIcone`, `repereRond` |
| `tampon` | `accent` (le disque) | `tete` (sans texte), `pied`, `piedTexte`, `numero` |
| `pastille` | `bleu`, `ambre` | `pied`, `piedTexte`, `numero` |
| `bloc` | `khaki` | `tete`, `teteTexte` (le rail), `pied`, `piedTexte`, `numero` |
| `anneau` | `corail`, `ambre`, `celadon` | `pied`, `piedTexte`, `numero` |
| `crayon` | `bleu` (l’encre) | `pied`, `piedTexte`, `numero` |
| `cimaise` | `corail` (le filet) | `nb`, `pied`, `piedTexte`, `numero` |
| `aube` | `aube` (le côté chaud, plutôt clair), `brume` (le côté froid) | `pied`, `piedTexte`, `numero` |
| `opale` | `ton-1`, `ton-2` (les deux tons des disques, plutôt clairs) | `formes`, `fondTeinte`, `pied`, `piedTexte`, `numero` |
| `bdt` | — | `aplat` |
| `plateforme` | — | `logoNom`, `logoSignature` |

- **Couleurs** : un objet `couleurs`, chaque valeur en six chiffres hexadécimaux (`"#1f4fd8"`). Sauf `tampon`,
  `opale` et les deux modèles Banque des Territoires, tous acceptent en plus `fond` (le papier) et `encre`
  (le texte) pour une variante complète. Une couleur trop proche du fond est relevée d’office : le contraste
  est garanti, la teinte exacte n’est pas promise.
- **Parties** : `"tete": false`, `"pied": false`, `"numero": false` masquent l’en-tête, le pied, le numéro.
  `teteTexte` et `piedTexte` posent un texte court (nom de l’organisme, mention de diffusion).
- **Options** : elles ne valent que `true`. `nb` (`cimaise`) passe toutes les photos en noir et blanc ;
  `fondTeinte` (`opale`) teinte le fond gris par les deux tons ; `aplat` (`bdt`) passe au design Aplat,
  couverture et fin rouges, ouvertures de chapitre à leur couleur.
- **`formes`** (`opale`) : la forme des disques du fond, `galets`, `carres`, `losanges`, `gouttes`,
  `anneaux`, `rubans` ou `melange` ; sans la clé, des disques.
- **`repere`** (`marqueur`) : le petit carré de l’en-tête devient `rond`, `losange`, `triangle`, `trait`,
  `equerre`, `demi` ou `aucun` ; ou `"repere": "icone"` avec `"repereIcone": "p:graduation-cap"` (le nom
  anglais d’une icône Phosphor précédé de `p:`) ou `"repereIcone": "eclair"` (l’identifiant d’un
  pictogramme de TalkNote, sans accent), posée dans le carré, ou dans le rond avec `"repereRond": true`.
- Un logo ou un SVG importé ne s’écrit jamais dans le .json : l’utilisateur les dépose dans l’atelier.
- Un réglage écrit pour un modèle qui n’est pas celui de la présentation est simplement ignoré.

```json
{
  "version": 2,
  "title": "Revue de projet · Mobilités",
  "theme": "marqueur",
  "modele": "marqueur",
  "reglages": {
    "marqueur": {
      "couleurs": { "accent": "#1f4fd8", "fond": "#f6f5f1", "encre": "#16181d" },
      "teteTexte": "Agence des mobilités",
      "piedTexte": "Diffusion restreinte",
      "repere": "rond",
      "numero": false
    }
  },
  "slides": [
    { "layout": "titre", "eyebrow": "Revue trimestrielle · T3 2026", "title": "Le réseau tient ses promesses.", "content": "Fréquentation, ponctualité, satisfaction : les trois courbes montent.", "author": "2 octobre 2026 · Direction des mobilités" },
    { "layout": "fin", "title": "Merci.", "content": "Prochain point le 14 janvier 2027.", "author": "mobilites@exemple.fr" }
  ]
}
```
