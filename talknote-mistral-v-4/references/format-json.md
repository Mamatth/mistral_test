# L’enveloppe et les champs

> Ouvre ce fichier au moment d’écrire le JSON : la structure du fichier, tous les champs d’une slide, la
> syntaxe commune du texte, la mise en scène, les notes, la livraison et la liste de contrôle.

Tu livres **un seul objet JSON**, que TalkNote ouvre tel quel. Lui s’occupe du rendu — couleurs, polices,
mise en page, animations, graphiques. Toi, tu écris la présentation : le plan, les messages, les données.
Tu n’écris jamais de HTML ni de CSS.

## 1. La structure du fichier

```json
{ "version": 2, "title": "Écoles sobres · Revue 2026", "theme": "papier", "modele": "", "transition": "glisse", "footer": true, "slides": [ { "layout": "titre", "eyebrow": "Comité de pilotage · Septembre 2026", "title": "Des écoles plus sobres, plus fraîches.", "content": "Bilan de la deuxième année du programme de rénovation.", "author": "24 septembre 2026 · Direction du patrimoine" }, { "layout": "fin", "title": "Merci. ==Place aux questions.==", "content": "Les fiches par école sont disponibles sur demande.\nAdresse | 4 place du Marché\nCourriel | ecoles@exemple.fr", "author": "Direction du patrimoine" } ] }
```

| Champ | Valeurs | Rôle |
| --- | --- | --- |
| `version` | `2` | Toujours `2`. Sans elle, TalkNote croit lire une présentation d’avant la version 2 et retouche les slides `chiffre`. |
| `title` | texte | Nom de la présentation. Repris dans le pied de page et dans le nom du fichier. |
| `theme` | `minuit` (défaut), `papier`, `braise`, `foret`, `neon`, `nuage`, ou l’identifiant d’un modèle complet | Couleurs et polices. Voir `references/styles.md`. |
| `modele` | `""` (défaut), `cadran`, `marge`, `palier`, `grille`, ou un modèle complet | Mise en page. Voir `references/styles.md`. |
| `transition` | `glisse` (défaut), `fondu`, `volet`, `zoom`, `aucune` | Le passage d’une slide à l’autre, pour toute la présentation. |
| `footer` | `true` (défaut), `false` | Le titre et le numéro en bas de slide. Dessinés avec `"modele": ""` seulement, et pas sur `titre`, `section`, `matrice`, `etapes`, `equipe`, `imagetexte`, `galerie`, `image` ni `fin`. |
| `icones` | `"duotone"`, `"gras"`, `"plein"` ou absent (défaut) | Style des icônes : absent, le trait ; `duotone`, le trait sur un fond léger à la couleur d’accent du thème ; `gras`, un trait épais ; `plein`, la forme remplie. Seulement si on le demande. |
| `mention` | texte | `bdt` et `plateforme` seulement : la mention de diffusion (`"Interne"`, `"Usage interne"`). Ailleurs, sans effet. |
| `docref` | texte | `bdt` et `plateforme` seulement : la référence portée en pied de chaque slide ; sans elle, le `title`. |
| `reglages` | objet | Couleurs, en-tête, pied, numéro et options d’un modèle, rangés par modèle. Seulement si on les demande : voir `references/styles.md`. |
| `slides` | tableau | Les slides, dans l’ordre. Une au moins ; la première est un `titre`, la dernière une `fin`. |

Une valeur inconnue n’arrête rien : TalkNote reprend le défaut. Un thème inconnu redevient `minuit`, un
modèle inconnu redevient `""`. Écris donc les identifiants exactement, en minuscules et sans accent.

## 2. Les champs d’une slide

N’écris que les champs utiles : TalkNote complète les autres avec leur valeur par défaut. Tout champ que
tu inventes est ignoré.

| Champ | Défaut | Rôle | Types concernés |
| --- | --- | --- | --- |
| `layout` | — | **Obligatoire.** L’un des 24 identifiants. Un identifiant inconnu devient `contenu`. | tous |
| `id` | posé par TalkNote | Identifiant interne de la slide. Ne l’écris pas. | tous |
| `eyebrow` | `""` | Surtitre : un repère court au-dessus du titre (`Partie 02`, `Contexte · 2026`). | tous sauf `image` et `fin`, qui n’en affichent pas |
| `title` | `""` | Le titre, c’est-à-dire le message. Pour `citation`, la citation elle-même. | tous |
| `content` | `""` | Le texte principal, dans la syntaxe du type. | tous |
| `content2` | `""` | Le second champ, selon le type : colonne droite, graphiques, lignes du tableau, titre du texte d’appui, chiffres du faux écran. | `colonnes`, `citation`, `graph`, `dashboard`, `tableau`, `maquette` |
| `content3` | `""` | La troisième colonne. | `colonnes` en `trois` |
| `author` | `""` | Selon le type : date et auteur, attribution, crédit, source ou contact. | `titre`, `citation`, `media`, `imagetexte`, `fin` |
| `notes` | `""` | Les notes du présentateur, visibles de lui seul (touche N). | tous |
| `disposition` | `""` | La variante de composition, propre à chaque type. Voir la fiche du type. | la plupart |
| `fond` | `""` | `"rouge"` passe la slide sur la couleur d’accent : le temps fort. Seule valeur admise. | `section` |
| `accent` | `false` | `true` met la colonne droite en avant. | `colonnes` |
| `cadre` | `"portable"` | `portable`, `bureau`, `mobile` ou `tablette`. | `maquette` |
| `ecrans` | `1` | Écrans côte à côte : jusqu’à 3 en `mobile`, 2 en `tablette`, 1 ailleurs. | `maquette` |
| `captures` | `[]` | Captures des écrans 2 et 3 (l’écran 1 prend `image`), six au plus. Laisse `[]`. | `maquette` |
| `image` | `""` | L’image intégrée à la slide. Laisse `""` : voir `references/images.md`. | les types à image |
| `photos` | `[]` | Une photo par ligne de `content`, dans l’ordre, six au plus. Laisse `[]`. | `galerie` |
| `portraits` | `[]` | Un portrait par personne, dans l’ordre des lignes, huit au plus. Laisse `[]`. | `equipe` |
| `imageAlt` | `""` | La description de l’image, lue par les lecteurs d’écran. Laisse `""` (voir `references/images.md`). | les types à image |
| `imageRight` | `false` | `true` place la photo à droite. | `imagetexte` |
| `imageWidth` | `"normale"` | `etroite`, `normale` ou `large`. | `imagetexte` |
| `anim` | `"montee"` | L’animation d’entrée des éléments. | tous |
| `transition` | `"defaut"` | La transition d’arrivée sur cette slide ; `defaut` = celle de la présentation. | tous |
| `progressive` | `true` | Les puces apparaissent une à une. `false` : toutes d’un coup. | les types à puces |
| `unParUn` | `false` | `true` fait apparaître les jalons un à un, comme des puces ; sinon le fil se trace d’un bout à l’autre dès l’entrée. | `jalons` |
| `agencement` | `""` | Dès deux graphiques : `ligne`, `colonne` ou `grille` (deux par rangée, à partir de trois). `""` : l’agencement automatique. | `graph`, `dashboard` |
| `suitSections` | absent | `true` : le sommaire suit les slides `section` de la présentation, et TalkNote tient sa liste à jour dans l’atelier. Écris quand même les parties dans `content`. | `sommaire` |
| `horsSommaire` | absent | `true` : cette section ne figure pas dans un sommaire qui suit les sections. | `section` |

`accent`, `imageRight`, `progressive`, `unParUn`, `suitSections`, `horsSommaire` et `footer` s’écrivent
`true` ou `false`, **sans guillemets**. `ecrans` est un nombre ; `photos`, `portraits` et `captures` sont
des tableaux, laissés à `[]`. Tous les autres champs sont des chaînes.

## 3. Écrire le texte

La même syntaxe vaut dans tous les champs de texte, quel que soit le type.

| Écriture | Effet |
| --- | --- |
| `\n` | Un retour à la ligne. Chaque ligne est un paragraphe, ou une ligne de données. **Un seul antislash** : `\\n` afficherait « \n » en toutes lettres, tout sur une ligne. |
| `- ` en tête de ligne | Une puce (`*` et `•` marchent aussi). |
| `1. ` en tête de ligne | Une puce numérotée : le nombre écrit remplace la puce. Numérote `1. `, `2. `, `3. ` dans l’ordre (`1)` marche aussi). |
| `# ` en tête de ligne | Un intertitre (`##` et `###` font la même chose). |
| `**gras**` | Du gras. |
| `*italique*` | De l’italique. |
| `==surligné==` | Le passage prend la couleur d’accent : un ou deux groupes de mots par slide, pas plus. |
| `(nom) ` en tête | Un pictogramme, dans la couleur d’accent. Voir `references/pictogrammes.md`. |
| ` // ` | Un retour à la ligne **dans une case**, sans changer de ligne du champ. |
| `\|` | Le séparateur de cellules des types structurés. |

Quelques règles qui évitent les surprises :

- **Ni HTML, ni lien, ni autre Markdown** : tout le reste s’affiche tel quel. Une balise écrite à
  la main, une adresse web, un tableau Markdown se liraient exactement comme tu les as écrits.
- Le pictogramme `(nom)` se pose en tête d’une ligne, d’une puce ou de n’importe quelle case : titre,
  surtitre, valeur d’un chiffre clé, cellule de tableau. Sur une puce, il remplace le losange
  (`- (éclair) Moins d’énergie`) — sauf dans une puce de comparaison (`colonnes`), où il se pose devant le
  texte sans le remplacer. Les repères d’un type restent devant : `x (loupe) Audit | …`,
  `> (cible) Standard`. Un seul par ligne, et seulement s’il aide à lire. Un nom inconnu, comme `(2027)`,
  reste du texte ; là où un modèle ne dessine pas de pictogramme, le mot est retiré sans s’afficher.
- ` // ` s’écrit avec **une espace de part et d’autre**. Chaque bout peut commencer par `- `, `1. ` ou
  `(nom) ` : une courte liste dans une description, une cellule, un titre. Deux à quatre bouts au plus.
  Dans une case d’une seule ligne, un repère suivi d’un nombre reste du texte : `- 2 j` et `1. 5`
  s’affichent tels quels. Dès qu’il y a un ` // `, chaque bout est lu comme une ligne.
- Le caractère `|` découpe les cellules : ne l’emploie jamais dans une phrase.
- Inutile d’ajouter des espaces insécables : TalkNote les pose devant `? ! : ;` et dans les guillemets.
- En JSON, un guillemet droit dans un texte s’échappe `\"` ; préfère les guillemets français `« »` et
  l’apostrophe typographique `’`, que TalkNote compose mieux.

```json
{ "layout": "contenu", "eyebrow": "Contexte", "title": "Pourquoi agir maintenant.", "content": "Les écoles pèsent la moitié de la consommation des bâtiments communaux.\n# Trois pressions qui se cumulent\n- (éclair) **Une obligation** : ==−40 % de consommation d’ici 2030==\n- (soleil) **Des étés plus chauds** : 34 °C relevés dans une classe en juin\n- (euro) **Des aides qui ferment** : le guichet régional s’arrête fin 2027", "notes": "[À vérifier] Le relevé de 34 °C vient du capteur de l’école du Pont-Neuf.\nSource : rapport annuel 2026, p. 12.\nEnchaîner sur ce qui a déjà été fait." }
```

Le même texte, dans une case, avec ` // ` et des pictogrammes en tête de cellule :

```json
{ "layout": "faits", "title": "Trois instances, un seul calendrier.", "content": "(groupe) Pilotage | Comité de pilotage | Élus et financeurs : // - deux séances par an // - un arbitrage budgétaire | Décider\n(outil) Technique | Cellule d’ingénierie | Quatre personnes mutualisées entre les communes | Conduire\n(école) Terrain | Conseils d’école | Enseignants et parents associés à chaque chantier | Associer" }
```

## 4. Mise en scène

Les valeurs par défaut conviennent presque toujours : ne règle `anim` et `transition` que pour un effet
voulu, sur une ou deux slides.

- `anim` : `montee` (défaut), `fondu`, `glisse`, `zoom`, `flou`, `machine`, `aucune`.
  `fondu` pour une photo pleine page, `zoom` pour un chiffre fort, `flou` pour une citation ;
  `machine` (machine à écrire) seulement sur un titre court.
- `transition` : `defaut` (défaut), `glisse`, `fondu`, `volet`, `zoom`, `aucune`. Une transition pour
  toute la présentation, réglée dans l’enveloppe ; au plus une slide avec la sienne.
- `progressive` : laisse `true` pour que les puces se découvrent une à une. Passe à `false` quand la
  liste se lit d’un bloc (un rappel, une légende).
- `unParUn` : sur `jalons`, `true` fait apparaître les dates une à une, pour les commenter.

```json
{ "layout": "citation", "title": "Avant, on ouvrait les fenêtres en janvier pour ==faire baisser le chauffage==.", "author": "Directrice d’une école pilote", "anim": "flou", "transition": "fondu" }
```

## 5. Les notes du présentateur

Écris des `notes` pour chaque slide de contenu : ce qu’il faut dire et qui n’est pas écrit sur la slide,
en deux à quatre phrases. La slide montre, les notes racontent.

- Le fil oral, un exemple concret, la transition vers la slide suivante.
- `[À vérifier]` **en tête** des notes dès qu’un fait, un chiffre ou une date n’a pas été confirmé.
- `Source : …` pour chaque chiffre repris de la matière (`Source : rapport 2025, p. 12`), afin que
  l’utilisateur retrouve d’où il vient.
- `Image à ajouter : …` pour décrire la photo attendue par la slide : voir `references/images.md`.

Les notes acceptent, en plus de la syntaxe du texte de la section 3, trois éléments que TalkNote met en forme.
Ne les écris que si l’utilisateur les demande ou si son texte les contient :

| Écriture | Effet dans les notes |
| --- | --- |
| `# Titre` et `## Sous-titre` en tête de ligne | Un titre et un sous-titre, avec un plan dans la console du présentateur. |
| `[tableau]` puis des lignes `Cellule \| Cellule` | Un tableau, première ligne en en-tête, `>` en tête d’une ligne pour la mettre en avant. Il s’arrête à la première ligne vide. |
| `[graphique]` puis les lignes d’un graphique (`type : barres`, `axe : …`, `Série : 1, 2, 3`) | Un graphique aux couleurs de la présentation. Il s’arrête à la première ligne vide. |

N’écris jamais `[@…]` ni `[→ …]` : TalkNote les pose lui-même depuis son atelier.

```json
{ "layout": "chiffre", "disposition": "vedette", "title": "Deux ans de travaux, en trois nombres.", "content": "12 | écoles rénovées | sur les 34 du territoire\n−38 % | de consommation | moyenne des douze écoles\n2,4 M€ | investis | dont 1,1 M€ de subventions", "notes": "[À vérifier] Les 2,4 M€ comprennent-ils les études ?\nSource : compte administratif 2026.\nDire que la barre des 40 % sera franchie avec la tranche 2027." }
```

## 6. Livrer le JSON

- **Un seul bloc de code `json`**, qui contient l’objet entier et rien d’autre : ni commentaire, ni
  virgule finale, ni `…`. Le fichier commence par `{` et finit par `}`.
- **Jamais coupé.** Une réponse tronquée ne s’ouvre pas. Au-delà de quinze slides, écris compact (une
  slide par ligne, sans indentation) pour tenir dans la réponse.
- **Jamais résumé, jamais partiel.** À chaque modification d’une présentation entière, redonne le JSON
  complet. Pour ajouter ou corriger seulement une slide, suis `references/coller-une-slide.md` : la slide se
  colle avec ⌘ V dans la présentation ouverte.
- Après le bloc, trois lignes au plus : les hypothèses prises, les chiffres à vérifier, les images à
  ajouter.

Côté utilisateur, dans TalkNote, sur l’accueil **Mes présentations** :

- **⌘ V** sur l’accueil, ou le bouton **Coller un JSON…** : il copie ta réponse et la colle. Le texte
  autour du JSON est ignoré, bloc de code compris.
- **⌘ V dans une présentation ouverte**, hors d’un champ de texte : il ajoute la slide collée après la slide
  courante (clic droit sur une vignette, puis **Coller après**). Il accepte une slide, une liste de slides ou
  les slides d’une présentation entière.
- **Ouvrir…** : il choisit un fichier `.json` (ou ta réponse enregistrée en texte brut, en UTF-8).
- Il peut aussi déposer le fichier dans le dossier `Présentations/` de TalkNote : il apparaît à l’accueil.

Si tu peux créer des fichiers, nomme-le `titre-de-la-presentation.json` : minuscules, tirets, sans accents.

## 7. Liste de contrôle avant de livrer

- [ ] Le plan a été validé, ou tes hypothèses sont listées sous le bloc.
- [ ] Chaque fait non confirmé porte `[À vérifier]` en tête des notes de sa slide.
- [ ] Le JSON est valide : il commence par `{`, finit par `}`, sans commentaire ni virgule finale.
- [ ] Les retours à la ligne des textes sont écrits `\n`, **avec un seul antislash** : ni `\\n`, ni vrai saut
  de ligne dans une chaîne.
- [ ] Un guillemet droit `"` dans un texte est échappé `\"`, ou remplacé par `« »`.
- [ ] `version` vaut `2`. `theme`, `modele` et `transition` sont pris dans leurs listes.
- [ ] Chaque `layout` est l’un des 24 identifiants, sans accent : `titre`, `section`, `sommaire`,
  `contenu`, `citation`, `colonnes`, `matrice`, `etapes`, `jalons`, `roadmap`, `portefeuille`, `kpi`,
  `chiffre`, `faits`, `equipe`, `graph`, `dashboard`, `tableau`, `maquette`, `media`, `imagetexte`,
  `galerie`, `image`, `fin`.
- [ ] Chaque `disposition`, `cadre`, `anim`, `transition` et `agencement` est pris dans la liste de son
  type ; `true` et `false` sont écrits sans guillemets.
- [ ] Chaque ligne structurée a ses cellules `|` dans le bon ordre, et le nombre de lignes tient la
  limite du type (voir sa fiche).
- [ ] Chaque graphique a sa ligne `type :` ; là où il y a un axe, chaque série a autant de valeurs
  que l’axe a de libellés (voir `references/graphiques.md`).
- [ ] `image`, `photos`, `portraits` et `captures` sont vides, et les images attendues sont décrites
  dans les `notes`.
- [ ] La première slide est un `titre`, la dernière une `fin` ; jamais plus de deux `contenu` d’affilée.
- [ ] Chaque slide de contenu a ses `notes`.
