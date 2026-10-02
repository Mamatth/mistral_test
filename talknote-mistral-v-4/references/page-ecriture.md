# Mode « Page d’écriture » : faire la présentation d’un texte écrit dans TalkNote

> L’utilisateur a rédigé son propos dans la page d’écriture de TalkNote, puis l’a exporté. Tu en fais une
> présentation : **les slides résument, les notes gardent son texte mot pour mot**. Dans ce mode, ce fichier
> remplace le déroulé en cinq étapes de `SKILL.md` et la section 5 (notes) de `references/format-json.md`.

## 1. Lire la tête du message

Le message a deux parties : la **tête** (avant la ligne `--- PAGE D’ÉCRITURE ---`) et le **texte** (entre cette
ligne et la ligne `--- FIN ---`). La tête donne quatre choix, déjà faits. Ne pose aucune question à leur sujet.

| Ligne de la tête | Ce que tu en fais |
| --- | --- |
| `Titre : …` | C’est le `title` de l’enveloppe JSON. Si c’est « Sans titre », propose un titre dans le plan et écris-le dans `title`. |
| `Modèle : … (modele "x", theme "x")` ou `Thème : … (theme "x") · Mise en page : … (modele "y")` | Recopie les valeurs entre guillemets dans `theme` et `modele` de l’enveloppe, **caractère pour caractère**. Ne choisis pas d’autre style. |
| `Nombre de slides : N à M` | Le JSON compte entre N et M slides, `titre`, `section` et `fin` comprises, bornes incluses (section 4). |
| `Nombre de slides : à toi de voir` | Tu décides. Annonce le total dans le plan. |

## 2. Lire les repères du texte

Le texte est écrit dans la syntaxe de TalkNote (une ligne par paragraphe, `- ` puce, `1. ` numéro, `# ` titre,
`## ` sous-titre, `(icône)` en tête de ligne, `**gras**`, `*italique*`, `==surligné==`). Trois repères, chacun sur
sa propre ligne, imposent le découpage :

| Repère | Ce que tu en fais |
| --- | --- |
| `[SECTION] Titre de la partie` | Une slide `section`. Son `title` est ce titre, recopié tel quel. |
| `[SLIDE]` … `[/SLIDE]` | **Exactement une slide**, tirée des lignes comprises entre les deux repères. Ni deux, ni zéro. |
| `[SLIDE · Libellé]` … `[/SLIDE]` | Exactement une slide, **de ce type** : prends l’identifiant dans la table de la section 9. |
| Tout le reste (texte libre) | À toi de le découper, en une slide ou plus, avec la table « Choisir le type » de `SKILL.md`. |

L’ordre des slides suit l’ordre du texte. Tu peux ajouter une slide `titre` en tête (son `title` : le titre du
message) et une slide `fin` si le texte se termine par une conclusion, une demande ou un remerciement. Tu n’ajoutes
aucune autre slide.

Deux blocs gardent leur forme exacte dans le texte :
- `[tableau]` puis des lignes `Cellule | Cellule` : un tableau, la première ligne en en-tête. Il s’arrête à la
  première ligne vide.
- `[graphique]` puis des lignes `type : barres`, `axe : …`, `Série : 1, 2, 3` : un graphique. Il s’arrête à la
  première ligne vide.

## 3. Le déroulé, en trois temps

1. **Lire** le texte entier. Repère les slides imposées (`[SECTION]`, `[SLIDE]`) et les passages libres.
2. **Proposer le plan**, dans **un seul message**, en tableau à cinq colonnes :
   N° · Type · Titre · Passage repris (ses cinq premiers mots) · Pourquoi ce type.
   Une slide imposée porte « imposée » dans la dernière colonne. Sous le tableau : le nombre total de slides, puis
   une seule question : « Ce plan te convient-il ? ». **Attends la réponse.** N’écris pas le JSON avant.
3. **Écrire le JSON** quand le plan est validé. Si l’utilisateur demande un changement, applique **uniquement** ce
   changement, réécris la ligne du plan qui bouge, puis écris le JSON sans redemander.

Si l’utilisateur écrit « fais directement », saute le temps 2.

## 4. Le nombre de slides

- Compte : chaque slide du JSON (`titre`, `section`, `fin` et slides de contenu).
- Les slides imposées par `[SECTION]` et `[SLIDE]` sont **toutes conservées**, même si leur nombre dépasse M. Dans ce
  cas, ne découpe aucun passage libre (une slide par passage libre, au plus) et écris sous le plan : « Les slides
  imposées dépassent M. »
- Sinon, ajuste le nombre de slides issues du texte libre pour rester entre N et M. Regroupe deux passages libres
  voisins pour baisser, coupe un passage libre pour monter.

## 5. Écrire les notes : le texte, mot pour mot

1. Chaque ligne du texte, sauf les repères `[SECTION]`, `[SLIDE…]` et `[/SLIDE]`, va dans les `notes` d’**une et
   une seule** slide : celle qui en parle. Les lignes d’un bloc `[SLIDE]` vont toutes dans les notes de sa slide.
2. Recopie chaque ligne **à l’identique** : mêmes mots, même ponctuation, mêmes marques (`- `, `# `, `**`, `(icône)`).
   Ne reformule pas, ne corrige pas l’orthographe, ne coupe pas, ne fusionne pas deux lignes.
3. Garde l’ordre. Les lignes se séparent par `\n` ; une ligne vide du texte s’écrit `\n\n`.
4. Les blocs `[tableau]` et `[graphique]` vont dans les notes **en entier**, ligne `[tableau]` ou `[graphique]`
   comprise, suivis d’une ligne vide (`\n\n`) s’il reste du texte après eux.
5. Une note est une chaîne JSON : un guillemet droit `"` du texte s’écrit `\"` et un antislash `\\`. Cela ne change
   pas le texte, qui reste mot pour mot.
6. **N’ajoute rien** aux notes : ni `[À vérifier]`, ni `Source :`, ni phrase de transition. Tes hypothèses, les
   chiffres à vérifier et les images à ajouter vont dans les trois lignes sous le bloc JSON.
7. Une slide qui ne reprend aucune ligne (la `section`, la `titre` ou la `fin` que tu as ajoutées) a `"notes": ""`.
8. N’écris jamais de repère `[@…]` ni `[→ …]` dans les notes : TalkNote les pose lui-même.

**Contrôle avant de livrer** : mises bout à bout dans l’ordre des slides, les notes redonnent le texte entier, sans
ses trois repères. Aucune ligne ne manque, aucune n’est en double. Sinon, corrige. TalkNote fait le même contrôle à
la fusion et signale toute ligne absente.

## 6. Écrire les slides : ce qu’elles montrent

- Ouvre la fiche `references/types/<id>.md` de chaque type, comme dans les autres modes.
- La slide **résume** son passage dans la syntaxe de son type : un titre-message, quelques puces, des chiffres, des
  étapes. Elle ne recopie pas le paragraphe.
- Un bloc `[graphique]` peut devenir une slide `graph` : recopie ses lignes, **sans** la ligne `[graphique]`, dans
  `content2`. Un bloc `[tableau]` peut devenir une slide `tableau` : ses lignes, sans la ligne `[tableau]`, dans
  `content2`. Dans les deux cas, le bloc reste aussi en entier dans les notes.
- N’invente aucun chiffre, nom ou date absents du texte. Un pictogramme `(nom)` sur une slide vient de
  `references/pictogrammes.md` ; les `(icône)` du texte restent dans les notes, tels quels.
- Les images restent vides (`references/images.md`).
- Enveloppe : `references/format-json.md`, avec `version` 2, `title`, `theme` et `modele` de la section 1.

## 7. Livrer

Applique la liste de contrôle de `references/format-json.md` (section 7), sauf ses points sur les `notes`, remplacés
par la section 5. Livre, dans cet ordre exact et sans rien d’autre :

1. Le JSON entier dans **un seul bloc de code**. Au-delà de 15 slides, écris-le compact.
2. Trois lignes au plus : hypothèses · chiffres à vérifier · images à ajouter.
3. La phrase : « Copie ce bloc et colle-le dans la page d’écriture de TalkNote (dans une note, si la présentation
   a déjà des slides) : il fera la présentation. »

Si l’utilisateur demande ensuite une modification, applique **uniquement** ce qui est demandé, garde les `notes`
identiques, et redonne le JSON **entier**.

## 8. Un exemple complet

Texte reçu (tête : `Titre : Écoles sobres`, `Thème : Papier (theme "papier") · Mise en page : Classique (modele "")`,
`Nombre de slides : 5 à 8`) :

```text
[SECTION] Le constat
[SLIDE · Chiffres clés]
Douze écoles rénovées sur 34.
Une baisse de 38 % de la consommation.
[/SLIDE]
Les étés sont plus chauds : 34 °C relevés dans une classe en juin.
```

Slides livrées (extrait de la liste `slides`) : la `section` n’a pas de notes, la slide `chiffre` reprend les deux
lignes du bloc, la slide `contenu` reprend la ligne libre. Les notes redonnent les trois lignes, dans l’ordre.

```json
{ "version": 2, "title": "Écoles sobres", "theme": "papier", "modele": "", "slides": [
  { "layout": "titre", "title": "Écoles sobres", "content": "", "notes": "" },
  { "layout": "section", "eyebrow": "Partie 01", "title": "Le constat", "notes": "" },
  { "layout": "chiffre", "title": "Deux ans de travaux, deux résultats.", "content": "12 | écoles rénovées | sur les 34\n−38 % | de consommation | depuis 2024", "notes": "Douze écoles rénovées sur 34.\nUne baisse de 38 % de la consommation." },
  { "layout": "contenu", "title": "Les étés deviennent trop chauds.", "content": "- ==34 °C== relevés en classe en juin", "notes": "Les étés sont plus chauds : 34 °C relevés dans une classe en juin." },
  { "layout": "fin", "title": "Merci.", "content": "", "notes": "" }
] }
```

## 9. Les libellés de type → l’identifiant à écrire dans `layout`

| Libellé dans `[SLIDE · …]` | `layout` |
| --- | --- |
| Couverture | `titre` |
| Sommaire | `sommaire` |
| Texte | `contenu` |
| Citation | `citation` |
| Comparaison | `colonnes` |
| Matrice | `matrice` |
| Étapes | `etapes` |
| Jalons | `jalons` |
| Roadmap | `roadmap` |
| Portefeuille | `portefeuille` |
| Indicateurs | `kpi` |
| Chiffres clés | `chiffre` |
| Faits | `faits` |
| Équipe | `equipe` |
| Graphique | `graph` |
| Tableau de bord | `dashboard` |
| Tableau | `tableau` |
| Maquette d’écran | `maquette` |
| Média | `media` |
| Photo + légende | `imagetexte` |
| Galerie | `galerie` |
| Photo pleine page | `image` |
| Fin | `fin` |

Un libellé absent de cette table : choisis le type toi-même, et signale-le sous le bloc JSON.
