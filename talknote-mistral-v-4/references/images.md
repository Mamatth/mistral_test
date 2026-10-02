# Images, photos, portraits, captures

> Ouvre ce fichier dès qu’une slide attend une photo, un portrait, une capture d’écran ou un schéma. Il dit
> ce que tu écris dans le JSON — rien —, ce que tu écris dans les `notes` à la place, et ce que l’utilisateur
> fera ensuite dans TalkNote.

## La règle, en une ligne

Tu laisses `image`, `photos`, `portraits` et `captures` **vides**, et tu décris chaque image voulue dans les
`notes` de sa slide. La slide montre alors un cadre vide ; l’utilisateur y dépose sa photo en deux clics.

Tu n’écris **jamais** une adresse web (`https://…`), un chemin de fichier (`/Users/…`, `photos/halle.jpg`),
un nom d’image ni une chaîne `data:` fabriquée. Une image inventée ne s’affiche pas : elle disparaît.

## Pourquoi

TalkNote travaille hors ligne : la présentation est un seul fichier, et l’image doit y être **intégrée**.
Une adresse web ne s’afficherait pas chez l’utilisateur, et elle dirait à un serveur extérieur qui ouvre le
fichier. À l’import, TalkNote ne garde donc que les données `data:image/…` ; tout le reste devient une
chaîne vide, sans message. Mieux vaut un cadre vide assumé, avec sa consigne dans les notes, qu’un champ
rempli de travers.

## Les quatre champs, et la description

| Champ | Défaut | Qui l’emploie | Ce que tu écris |
| --- | --- | --- | --- |
| `image` | `""` | `media`, `imagetexte`, `image`, `maquette`, `section` en `photo`, `citation` en `portrait` | `""` |
| `photos` | `[]` | `galerie` : une photo par ligne de `content`, dans l’ordre (six au plus) | `[]` |
| `portraits` | `[]` | `equipe` : un portrait par personne, dans l’ordre des lignes (huit au plus) | `[]` |
| `captures` | `[]` | `maquette` à plusieurs écrans : les écrans 2 et 3 (l’écran 1 prend `image`) | `[]` |

**`imageAlt`** est la description de l’image pour les lecteurs d’écran. Laisse `""` tant que `image` est vide.
Quand tu fournis vraiment une image, décris ce qu’elle montre en une phrase (« Une classe rénovée, vue depuis
le fond, lumière du sud »), jamais son nom de fichier. TalkNote propose le nom du fichier à l’import d’une
image dans l’atelier ; l’utilisateur le corrige. Ne renseigne pas `imageAltAuto` (champ interne).

Ces champs ont tous une valeur par défaut : tu peux simplement ne pas les écrire. Le reste des champs d’une
slide est dans `references/format-json.md`.

## Écrire la note

Une ligne de `notes`, en tête, qui dit **ce que l’image doit montrer** — pas « ajouter une photo ».

```text
Image à ajouter : la halle vue de l’intérieur, en journée, avec du public.
Photos à ajouter, dans l’ordre des lignes : le terrassement, la chaudière, la chaufferie terminée.
Portraits à ajouter : Claire Vasseur, Nadir Belkacem, Inès Rocher.
Capture à ajouter : l’écran d’accueil de l’application, avec la courbe du mois.
```

Puis, sous le bloc JSON, reprends la liste des images attendues en une ou deux lignes : l’utilisateur sait
tout de suite ce qu’il doit rassembler avant sa réunion.

## Les types qui attendent une image

| Type | Champ | Ce que l’image occupe | Sans image |
| --- | --- | --- | --- |
| `media` | `image` | un cadre 16:9 au centre, sous le titre | Un cadre vide : « Déposez ici la capture, le schéma ou l’image (16:9) ». |
| `imagetexte` | `image` | la moitié de la slide (`imageRight` la passe à droite, `imageWidth` la resserre ou l’élargit) | Un cadre vide, le texte tient sa place. |
| `image` | `image` | toute la slide, titre en incrustation | Un grand cadre en pointillés ; le titre passe sur le fond du thème, toujours lisible. |
| `galerie` | `photos` | une vignette par ligne de `content` (trois à six) | Chaque vignette porte « Photo 1 », « Photo 2 »… |
| `equipe` | `portraits` | un rond par personne, dans l’ordre des lignes | Les initiales du nom, dessinées par TalkNote. |
| `maquette` | `image`, `captures` | l’écran de l’appareil | Un faux écran, dessiné avec les chiffres de `content2`. |
| `section` en `photo` | `image` | la moitié droite, à fond perdu | Un cadre vide, le texte garde la moitié gauche. |
| `citation` en `portrait` | `image` | un rond à gauche de la citation | Les initiales de l’attribution, sinon un grand guillemet. |

Deux précisions qui évitent une déception :

- **`equipe` sans portraits reste une bonne slide.** Les initiales viennent du nom quand il fait deux ou
  trois mots commençant chacun par une majuscule (`Claire Vasseur` → `CV`). Un nom d’un seul mot donne sa
  première lettre.
- **`citation` en `portrait` sans photo** montre les initiales seulement si l’attribution commence par un
  nom (`Claire Vasseur, directrice du programme` → `CV`) ; sinon, le guillemet. Une attribution du genre
  `Une directrice d’école` ne donne pas d’initiales : la disposition `""` est alors plus simple.

## Les modèles qui posent une photo d’eux-mêmes

Cinq modèles complets réservent une place à la photo de la slide dans des types qui n’ont d’ordinaire pas de
champ Image. Même règle : `image` vide, la consigne dans les `notes`.

| Modèle | Types concernés | Ce qu’il en fait | Sans photo |
| --- | --- | --- | --- |
| `pastille` | `titre` | La couverture porte la photo. | La couverture garde ses pastilles. |
| `bloc` | `titre`, `section` | La couverture et l’ouverture de partie portent la photo. | Le rail et l’aplat suffisent. |
| `anneau` | `titre`, `section` | La photo se découpe en demi-lune. | Les anneaux restent seuls. |
| `crayon` | `titre`, `section` | Une photo sur le côté du titre. | Le tracé à l’encre tient la slide. |
| `cimaise` | `titre`, `section`, `faits` | La couverture découpe la photo en bandes, la section l’emploie à évider son numéro, les points clés la posent en colonne. | Des gris alternés, un numéro plein. |

`bloc`, `anneau`, `crayon` et `cimaise` posant déjà la photo de leur `section`, la disposition `photo` n’y
ajoute rien ; `aube` et `opale` l’ignorent aussi, leur fond leur appartenant. Elle sert avec `revue`,
`chantier`, `marqueur`, `tampon`, `pastille`, `bdt`, `plateforme` et avec Libre. Le détail des modèles
est dans `references/styles.md`.

## Combien de slides à image

Sans photos fournies par l’utilisateur, **deux ou trois slides au plus** parmi `image`, `imagetexte` et
`media` : au-delà, la présentation devient une suite de cadres vides. Une `galerie` compte pour trois à six
photos à elle seule : n’en mets qu’une, et seulement si les photos existent vraiment.

Quand l’utilisateur annonce qu’il a des photos, l’inverse est vrai : propose-lui une `imagetexte` par partie
et une `image` pleine page au moment fort. Demande-le une fois, dans le message de validation du plan
(`references/dialogue.md`), et n’y reviens pas.

## La maquette et son faux écran

`maquette` n’a **pas besoin** de capture : sans image, TalkNote dessine un faux écran dans l’appareil, à
partir des lignes de `content2` (`812 | Utilisateurs`, trois lignes au plus — deux seulement en `bureau` et
en `tablette`). C’est le seul type à image qui rend bien vide : emploie-le sans hésiter pour montrer un
outil.

- `cadre` choisit l’appareil : `portable` (défaut), `bureau`, `mobile`, `tablette`.
- `ecrans` met plusieurs appareils côte à côte : jusqu’à 3 en `mobile`, 2 en `tablette`, 1 ailleurs. Les
  écrans suivants reprennent les mêmes chiffres, décalés d’un rang.
- L’écran 1 prend `image`, les écrans 2 et 3 prennent `captures`. Laisse les deux vides.
- Si `content2` est vide, TalkNote met des chiffres d’illustration : écris plutôt les tiens, tirés de la
  matière. Le détail du type est dans `references/types/maquette.md`.

## Si tu as vraiment le fichier

`image`, `photos`, `portraits` et `captures` acceptent une donnée intégrée `data:image/jpeg;base64,…` (ou
`png`, `webp`). Ne t’en sers que si tu disposes réellement du fichier et d’un outil qui l’encode, et reste
sous 500 Ko par image : le JSON se colle à la main, une image lourde le rend impossible à copier. Dans le
doute, laisse vide. Une chaîne base64 approchée n’existe pas.

## Ce que l’utilisateur fait ensuite

Dans TalkNote, panneau **Slide**, section **Contenu** :

- le champ **Image** — son libellé suit le type : Photo, Portrait, Capture d’écran, Capture de l’écran 1 —
  avec le bouton « Choisir une image… » et un aperçu cliquable ;
- le champ **Portraits** (équipe), **Photos** (galerie) ou **Autres écrans** (maquette), une ligne par
  personne, par photo ou par écran, dans l’ordre du texte ;
- un fichier se glisse aussi sur le champ, ou directement sur la slide ; un clic sur une image de la slide
  ouvre le champ correspondant.

L’image est alors intégrée à la présentation : le fichier d’origine n’est plus nécessaire, et l’export
fonctionne hors ligne. Dis-le à l’utilisateur en une ligne à la livraison, avec la liste des images attendues.

## Deux exemples

Une photo et sa légende, photo à droite :

```json
{ "layout": "imagetexte", "eyebrow": "Tiers-lieu des Halles", "title": "Six mois d’ouverture, mille cartes signées.", "content": "Un marché couvert de 1911 devenu atelier partagé, salle de travail et café associatif.\n- Ouvert six jours sur sept\n- Trente-deux associations accueillies\n- 1 040 cartes de membre signées", "author": "Photo · Service communication", "imageRight": true, "image": "", "notes": "Image à ajouter : la halle vue de l’intérieur, en journée, avec du public.\nSource : bilan d’activité du premier semestre 2026, p. 4." }
```

Trois photos dans l’ordre du chantier :

```json
{ "layout": "galerie", "eyebrow": "Réseau de chaleur", "title": "La chaufferie bois, en trois temps.", "content": "Octobre 2025 | Terrassement de la parcelle, derrière le gymnase\nFévrier 2026 | Pose de la chaudière et du silo à plaquettes\nJuin 2026 | Mise en service, avant la première saison de chauffe", "photos": [], "notes": "Photos à ajouter, dans l’ordre des lignes : le terrassement, la chaudière en cours de pose, la chaufferie terminée.\nSource : comptes rendus de chantier, lot 3." }
```
