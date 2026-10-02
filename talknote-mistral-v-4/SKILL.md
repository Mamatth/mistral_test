---
name: talknote-mistral-v-4
description: "Charger ce skill quand l’utilisateur demande une présentation, des slides, un diaporama, un deck ou un support de réunion, ou nomme TalkNote, ou veut ajouter, refaire ou corriger une seule slide, ou colle le JSON d’une slide, ou colle un message contenant la ligne --- PAGE D’ÉCRITURE ---. Il produit un JSON à coller dans TalkNote (24 types, 11 graphiques). Ne pas charger pour un fichier PowerPoint, PDF ou Word, ni pour une page web."
---

# Présentation TalkNote à partir de votre matière

Ce skill produit **un seul objet JSON** que l’utilisateur colle dans TalkNote, l’éditeur de slides hors ligne.
TalkNote fait le rendu (couleurs, polices, mise en page, animations, graphiques). Tu écris le plan, les
messages et les données, dans la syntaxe exacte de chaque type de slide.

## Ce skill ne fait pas

- Il n’écrit ni HTML, ni CSS, ni PowerPoint, ni PDF. Tu n’exécutes aucun script.
- Il ne cherche aucune image ni adresse d’image. Les images restent vides.
- Il n’invente ni chiffre, ni date, ni nom, ni citation.
- Il n’ajoute aucun champ, type, disposition, thème, modèle, graphique ni pictogramme qui n’est pas écrit dans
  ce fichier ou dans un fichier de `references/`.

## Choisir le mode

Teste les trois conditions **dans cet ordre** ; la première vraie décide. Ouvre alors le fichier indiqué, en entier.

| N° | Condition | Mode | Fichier à ouvrir |
| --- | --- | --- | --- |
| 1 | Le message contient la ligne `--- PAGE D’ÉCRITURE ---` | **Page d’écriture** | `references/page-ecriture.md` |
| 2 | La page d’écriture est un document partagé (canvas) que l’utilisateur peut modifier, ou dont il parle comme d’un document ouvert | **Canvas d’écriture** | `references/canvas.md`, puis `references/page-ecriture.md` pour la syntaxe |
| 3 | La demande vise **une ou quelques slides** d’une présentation déjà ouverte (ajouter, refaire, corriger), ou l’utilisateur colle un objet JSON qui commence par `{ "layout"` | **Slide à coller** | `references/coller-une-slide.md` |
| 4 | Toute autre demande de présentation | **Présentation entière** | les cinq étapes ci-dessous |

- Si les conditions 3 et 4 restent possibles toutes les deux, pose cette seule question : « Une slide à coller dans
  ta présentation ouverte, ou une présentation entière ? ».
- En mode **Page d’écriture**, **Canvas d’écriture** ou **Slide à coller**, le fichier indiqué **remplace** les cinq étapes. Les règles
  d’exécution ci-dessous restent valables, sauf deux : la règle « JSON complet » de l’étape 5 et les règles sur
  les `notes` de `references/format-json.md` (section 5), remplacées par celles de ce fichier.

## Règles d’exécution

Ces règles s’appliquent à chaque réponse. Aucune n’est facultative.

1. **Ouvre avant d’écrire.** Avant d’écrire la moindre slide, ouvre et lis en entier la fiche de son type
   (`references/types/<id>.md`) et `references/format-json.md`. Une slide écrite de mémoire est une erreur.
2. **Recopie, n’interprète pas.** Reprends les noms de champs, les identifiants, les séparateurs et les
   exemples JSON des fiches **à l’identique**. Pour écrire une slide, pars de l’exemple JSON de sa fiche et
   remplace uniquement les textes. Ne paraphrase pas une règle. Ne la « corrige » pas. Ne la généralise pas.
3. **Ce qui n’est pas écrit n’existe pas.** Si une fiche ne mentionne pas un champ, une valeur, une
   disposition ou une syntaxe, ne l’utilise pas. Si la fiche ne couvre pas ton besoin, choisis un autre type ;
   n’improvise jamais.
4. **En cas de doute, demande ou laisse vide.** Une information absente de la matière n’est pas devinée :
   pose la question à l’étape 3, ou laisse le champ vide et signale-le dans les `notes` par `[À vérifier]`.
5. **Un fichier de référence lu est un fichier appliqué.** Ne résume pas un fichier de `references/` et n’en
   cite pas de mémoire : relis-le à chaque fois que tu en as besoin. En mode **Canvas d’écriture**, l’état courant du canvas
   est une source de vérité au même titre : relis-le avant chaque réponse, et ne repars jamais d’une version antérieure.
6. **Format de sortie imposé.** Utilise les formats de l’étape 3 et de l’étape 4, sans ajouter de section,
   de commentaire, de conclusion ou de reformulation.

## Le déroulé de la présentation entière : cinq étapes, dans cet ordre

### Étape 1 — Lire la matière

1. Lis chaque document en entier. Ouvre chaque lien si tu le peux ; sinon demande le texte collé.
2. Ouvre `references/analyse.md`. Remplis sa fiche de lecture champ par champ : sujet, public, objectif,
   messages clés, chiffres et leur source, dates, étapes, comparaisons, personnes, citations, images
   disponibles, manques.
3. Un champ sans réponse dans la matière reste « non précisé ». Ne le remplis pas par supposition.

### Étape 2 — Choisir le type de chaque contenu

1. Pour chaque contenu retenu, prends le type dans la table « Choisir le type » ci-dessous. Si deux types
   se disputent le contenu, applique la table de décision de `references/analyse.md`.
2. Ouvre la fiche `references/types/<id>.md` de chaque type retenu. Vérifie ses sections « Quand l’employer »
   et « Pas pour ». Si la fiche exclut ton contenu, change de type.
3. Pour un graphique, ouvre `references/graphiques.md`. Pour le style, ouvre `references/styles.md`.
4. Respecte la structure : `titre`, puis `sommaire` (à partir de 10 slides), puis pour chaque partie une
   `section` suivie de ses slides, puis `fin`. Durées : 5 min = 6 à 8 slides ; 10 min = 10 à 14 ; 20 min =
   18 à 25 ; 45 min = 35 à 45. Maximum deux `contenu` d’affilée.

### Étape 3 — Faire valider, en un seul message

Ouvre `references/dialogue.md`. Envoie **un seul message**, dans cet ordre exact :

1. « Ce que j’ai lu » : 5 lignes.
2. Le plan, en tableau à six colonnes : N° · Type · Disposition · Titre · Contenu prévu · Pourquoi ce type.
3. Le style proposé : un thème ou un modèle pris dans `references/styles.md`.
4. Les questions que la matière ne tranche pas : 3 au plus, plus la validation du plan en dernière question.
5. Tout ce que tu as supposé est suivi de « *(proposition)* ».

Ne pose pas de question dont la matière donne la réponse. Ne pose pas de question sur le nombre de slides.
**Exception** : si l’utilisateur dit « fais directement », ou si aucun échange n’est possible, saute cette
étape, écris le JSON, et liste tes hypothèses sous le bloc.

### Étape 4 — Écrire le JSON

1. Enveloppe et champs : `references/format-json.md`. Chaque slide : sa fiche de type.
2. Images : `references/images.md`. Pictogrammes : `references/pictogrammes.md`.
3. Avant de livrer, applique **point par point** la liste de contrôle de `references/format-json.md`
   (section 7). Corrige ce qui échoue.
4. Livre, dans cet ordre exact : le JSON entier dans **un seul bloc de code** ; puis 3 lignes au plus
   (hypothèses · chiffres à vérifier · images à ajouter) ; puis la phrase d’import de la dernière section.
   Rien d’autre.

### Étape 5 — Ajuster

1. Termine par la dernière carte de choix de `references/dialogue.md`.
2. À chaque modification demandée, applique **uniquement** ce qui est demandé, laisse le reste identique, et
   redonne le JSON **complet**. Jamais un extrait. (Ne vaut que pour une présentation entière ; pour une
   slide à coller, voir `references/coller-une-slide.md` ; pour le canvas d’écriture, voir la section 4
   de `references/canvas.md` : seules les slides touchées sont redonnées, sauf demande du JSON entier.)

## Les quatre fautes qui ruinent le fichier

Chacune est interdite. Relis cette liste avant de livrer.

- **Aucun commentaire dans le JSON** (`// slide 1`) : le fichier ne s’ouvre plus. Pas de virgule finale, pas
  de texte hors des accolades.
- **Aucun champ inventé** (`subtitle`, `type`, `data`, `label`, `value`) : il est supprimé à l’ouverture. Les
  champs d’une slide forment la liste fermée de `references/format-json.md`.
- **Aucun graphique en objets JSON.** Un graphique s’écrit en texte dans `content2` : une ligne par réglage,
  puis une ligne par série. Syntaxe : `references/graphiques.md`.
- **Un seul antislash pour le retour à la ligne** : `\n`, jamais `\\n`. Écris le JSON tel qu’il doit être lu ;
  ne l’échappe pas une seconde fois parce qu’il est dans un bloc de code.

## Les références : quand ouvrir quoi

Seuls `SKILL.md` et les fichiers que tu ouvres sont connus de toi. Ouvre le fichier indiqué, en entier.

| Fiche | L’ouvrir quand |
| --- | --- |
| `references/coller-une-slide.md` | Dès que la demande porte sur une ou quelques slides à coller dans une présentation ouverte, ou qu’une slide est collée. |
| `references/page-ecriture.md` | Dès que le message contient `--- PAGE D’ÉCRITURE ---` : les repères `[SECTION]`, `[SLIDE]`, le plan à valider, les notes mot pour mot. |
| `references/canvas.md` | Dès que la page d’écriture est un document partagé (canvas) modifiable : relecture de l’état courant, qui écrit quoi, gestion des divergences, livraison des slides touchées. |
| `references/analyse.md` | Dès qu’il y a de la matière à lire ; pour la table de décision « signaux → types » et le format du message de réflexion. |
| `references/types/<id>.md` | Avant d’écrire une slide de ce type. Une fiche par type, nommée d’après son identifiant : `references/types/titre.md`, `references/types/section.md`, `references/types/sommaire.md`, `references/types/contenu.md`, `references/types/citation.md`, `references/types/colonnes.md`, `references/types/matrice.md`, `references/types/etapes.md`, `references/types/jalons.md`, `references/types/roadmap.md`, `references/types/portefeuille.md`, `references/types/kpi.md`, `references/types/chiffre.md`, `references/types/faits.md`, `references/types/equipe.md`, `references/types/graph.md`, `references/types/dashboard.md`, `references/types/tableau.md`, `references/types/maquette.md`, `references/types/media.md`, `references/types/imagetexte.md`, `references/types/galerie.md`, `references/types/image.md`, `references/types/fin.md`. |
| `references/graphiques.md` | Dès qu’une donnée chiffrée mérite un dessin : choisir parmi les onze graphiques et écrire leur syntaxe. |
| `references/styles.md` | Pour proposer un thème ou un modèle, savoir quelles dispositions un modèle applique, écrire des réglages. |
| `references/format-json.md` | Avant d’écrire le JSON : l’enveloppe, tous les champs d’une slide, la syntaxe du texte, les notes, la liste de contrôle, l’import dans TalkNote. |
| `references/images.md` | Dès qu’une slide attend une photo, un portrait, une capture ou un schéma. |
| `references/pictogrammes.md` | Pour poser un pictogramme `(nom)` : les noms reconnus. |
| `references/dialogue.md` | Au moment de faire valider : questions en choix à cliquer (Vibe) ou cartes de choix (Le Chat), puis les ajustements. |
| `references/exemple-complet.md` | Pour voir la méthode entière sur un cas : matière, fiche de lecture, plan justifié, JSON. |

## Choisir le type

| Ce que la matière contient | Type |
| --- | --- |
| De quoi ouvrir la présentation | `titre` |
| Le plan, en trois à six parties | `sommaire` |
| Le début d’une partie | `section` |
| Une explication, un argumentaire en quelques points | `contenu` |
| Deux options, un avant / après (trois options : disposition `trois`) | `colonnes` |
| Des choix à situer sur deux axes (effort et impact, urgence et importance) | `matrice` |
| Une méthode, un processus dans l’ordre, sans dates | `etapes` |
| Des dates clés, passées ou à venir | `jalons` |
| Des chantiers menés en parallèle sur l’année | `roadmap` |
| Des sujets répartis par état d’avancement | `portefeuille` |
| Trois ou quatre indicateurs suivis, avec leur évolution | `kpi` |
| Un à quatre chiffres marquants, sans évolution | `chiffre` |
| Trois ou quatre réalisations, décisions ou constats | `faits` |
| Les personnes qui portent le projet | `equipe` |
| Une tendance, une répartition, une comparaison chiffrée | `graph` |
| Une perception entre deux mots opposés · ce qui est commun à deux ou trois ensembles | `graph` (échelles · intersection) |
| L’état d’un programme en deux à quatre graphiques | `dashboard` |
| Des données ligne à ligne, des statuts, un cadre de référence | `tableau` |
| Un outil, une application à montrer | `maquette` |
| Un schéma ou une capture qui occupe la slide | `media` |
| Une photo et son contexte | `imagetexte` |
| Plusieurs photos à comparer ou à enchaîner | `galerie` |
| Une image forte, en plein cadre | `image` |
| Un témoignage, une phrase forte | `citation` |
| Conclure, demander la décision, donner un contact | `fin` |

Si une liste a une structure (un ordre, des dates, des chiffres, des catégories), utilise le type de la table,
pas `contenu`. `contenu` sert uniquement à un texte explicatif sans structure. Maximum deux `contenu` d’affilée.

## Mémo : ce que porte chaque type

Ce mémo est un filet de sécurité, pas une source. Le détail, les limites, les dispositions et les pièges sont dans
la fiche du type, que tu ouvres avant d’écrire ; en cas d’écart, la fiche l’emporte. Le caractère `|` sépare les cases ; un retour à la ligne s’écrit
`\n` et sépare les éléments.

| Type | Ce qu’il faut écrire |
| --- | --- |
| `titre` | `eyebrow` le repère, `title` le message, `content` le chapeau, `author` `Date · Auteur` |
| `section` | `eyebrow` `Partie 01`, `title` le nom de la partie, `content` une phrase |
| `sommaire` | `content` : une ligne par partie, `Titre \| Description` |
| `contenu` | `content` : des paragraphes, des puces `- `, des intertitres `# ` |
| `citation` | `title` la citation nue, `author` l’attribution |
| `colonnes` | `content` la colonne gauche, `content2` la droite (`content3` en disposition `trois`) ; par ligne `> Étiquette`, `# Titre`, `- puce`, une ligne nue en pied |
| `matrice` | `content` : `axes : Horizontal \| Vertical`, puis quatre lignes `Titre \| Description` |
| `etapes` | `content` : une ligne par étape, `Titre \| Description` ; `x ` franchie, `> ` en cours |
| `jalons` | `content` : une ligne par jalon, `Date \| Titre \| Description` ; `x ` réalisé |
| `roadmap` | `content` : `# Chantier \| sous-titre`, puis des barres `Libellé \| T2 \| en cours` |
| `portefeuille` | `content` : `# Colonne \| Étiquette \| actif`, puis un sujet par ligne |
| `kpi` | `content` : une ligne par indicateur, `Libellé \| Valeur \| Variation \| Commentaire` |
| `chiffre` | `content` : une ligne par chiffre, `Valeur \| Titre \| Description` |
| `faits` | `content` : une ligne par carte, `Catégorie \| Titre \| Description \| Étiquette` |
| `equipe` | `content` : une ligne par personne, `Nom \| Rôle \| Une ligne` |
| `graph` | `content` l’analyse, `content2` le graphique en texte : `type : courbe`, `axe : 2024, 2025`, `Série : 12, 18` |
| `dashboard` | `content2` seul : deux à quatre graphiques, séparés par une ligne vide |
| `tableau` | `content` une phrase, `content2` les rangées `Cellule \| Cellule`, la première ligne en en-tête |
| `maquette` | `content` le chapeau et des puces, `content2` trois lignes `Valeur \| Libellé`, `cadre` l’appareil |
| `media` | `title`, `content` la légende, `author` la source, `image` vide |
| `imagetexte` | `title`, `content` la légende, `author` le crédit, `image` vide |
| `galerie` | `content` : une ligne par photo, `Titre \| Légende` ; `photos` vide |
| `image` | `title` incrusté, `content` une ligne dessous, `image` vide |
| `fin` | `title` le message, `content` une phrase puis des lignes `Libellé \| Valeur`, `author` le contact |

## Pictogrammes

Un pictogramme s’écrit `(nom)` en tête de ligne, avec un nom relevé dans `references/pictogrammes.md`
(44 pictogrammes TalkNote et 1 512 icônes Phosphor, rangés par catégorie). La bibliothèque dessine des objets,
pas des idées : `gouvernance`, `territoire`, `mobilité` et `partenariat` n’existent pas. Si ton mot n’est dans
aucune table de ce fichier, **n’écris aucun pictogramme** : un nom inconnu s’affiche entre parenthèses sur la slide.

## L’enveloppe, pour mémoire

```json
{
  "version": 2,
  "title": "Titre de la présentation",
  "theme": "minuit",
  "modele": "",
  "transition": "glisse",
  "footer": true,
  "slides": [
    { "layout": "titre", "eyebrow": "…", "title": "…", "content": "…", "author": "…", "notes": "…" }
  ]
}
```

Chaque slide est un objet avec `"layout"` (l’un des 24 identifiants de la table, sans accent) et les champs de
sa fiche. Un retour à la ligne s’écrit `\n` ; le caractère `|` sépare les cellules des types structurés.

## Règles chiffrées

- **Données.** Chaque chiffre, date, nom et citation vient de la matière ; sa source va dans les `notes`
  (`Source : …`). Une valeur qui manque porte `[À vérifier]` en tête des `notes`. Aucune citation n’est
  attribuée à une personne réelle si l’utilisateur ne te l’a pas donnée.
- **Titre.** Une phrase qui énonce le message de la slide, 60 caractères au maximum. Le détail va dans les `notes`.
- **Images.** `image`, `photos`, `portraits` et `captures` valent `""` ou `[]`. Écris `Image à ajouter : …` dans
  les `notes`. Aucune adresse web d’image.
- **Livraison.** Le JSON est entier, en un seul bloc, sans « … » ni commentaire. Au-delà de 15 slides, écris-le
  compact (une slide par ligne). La première slide est un `titre`, la dernière une `fin`.

## Import côté utilisateur

Dans TalkNote, accueil **Mes présentations** : ⌘ V, ou « Coller un JSON… », ou « Ouvrir… » un fichier `.json`.
La présentation s’ouvre ; l’utilisateur ajoute ensuite ses images dans le panneau « Slide ». Termine ta
livraison par cette phrase : « Dans TalkNote, accueil Mes présentations : ⌘ V, ou Coller un JSON. »
