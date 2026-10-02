# Lire la matière et monter la réflexion

> Ouvre ce fichier dès qu’on te donne de la matière — un document, un lien, un texte collé, quelques
> phrases — et avant d’écrire la moindre slide. Il dit comment lire, ce qu’il faut en retenir, quels types
> de slides en découlent, et comment présenter ta réflexion avant le JSON.

Tu n’es pas un formulaire : tu lis, tu comprends, tu décides. La présentation n’est pas la matière mise en
pages, c’est un **chemin de démonstration** construit à partir d’elle. Trois temps : lire, trier, monter le
plan. Le JSON ne vient qu’après.

## 1. Lire la matière

| Ce qu’on te donne | Ce que tu fais |
| --- | --- |
| Un document joint (rapport, note, compte rendu, tableur, support existant) | Tu le lis **en entier**, pas seulement le résumé. Les chiffres, les dates et les noms sont dans le corps du texte et dans les annexes. |
| Un lien | Tu l’ouvres si ton outil de navigation le permet. Sinon, tu le dis en une ligne et tu demandes le texte, un copier-coller ou le résumé — sans jamais deviner le contenu d’une page que tu n’as pas lue. |
| Un texte collé | Tu le traites comme un document : même lecture, mêmes relevés. |
| Une consigne en quelques phrases, sans document | Tu travailles avec ce que tu sais du sujet, et tu **marques comme proposition** tout ce que tu apportes toi-même. |
| Plusieurs sources | Tu repères ce qui se recoupe et ce qui se contredit. Une contradiction se signale, elle ne se moyenne pas. |

En lisant, note **la source de chaque fait** : de quel document, de quelle page, de quelle section il vient.
Ces sources vont dans les `notes` de la slide, au format `Source : rapport 2025, p. 12`. Un fait dont tu ne
retrouves pas la source est un fait à vérifier.

Ne recopie pas la matière. Tu cherches ce qu’elle **prouve**, ce qu’elle **demande** et ce qui **manque**.

## 2. La fiche de lecture

Avant de proposer quoi que ce soit, remplis cette fiche — dans ta tête pour une matière courte, dans ton
message pour un dossier. Elle sert deux fois : à choisir les types, puis à écrire les slides.

```text
Sujet          : de quoi parle la matière, en une phrase
Public         : qui regardera la présentation, ce qu’il sait déjà
Objectif       : informer / convaincre / faire décider / former
Décision       : ce qu’on attend du public à la fin (un vote, un arbitrage, une action, rien)
Messages clés  : 3 à 5 phrases affirmatives — une par partie de la présentation
Chiffres       : valeur · unité · source · évolution (le chiffre sans son évolution ne se traite pas pareil)
Dates          : jalons passés et à venir, échéances, décisions datées
Processus      : étapes ordonnées, avec ou sans dates ; ce qui recommence
Comparaisons   : avant / après, options à trancher, critères de comparaison
Personnes      : noms, rôles, une ligne chacun ; contacts de fin
Citations      : phrases réellement rapportées, avec leur auteur tel qu’il est écrit
Images         : photos, captures, schémas disponibles (ou aucun)
Tableaux       : lignes homogènes, colonnes, statuts
Avancement     : ce qui est réalisé, en cours, à venir ; par sujet ou par chantier
Manques        : ce que la matière ne dit pas et qui change la présentation
```

Deux relevés méritent d’être faits avec soin, parce que ce sont eux qui décident du type de slide :

- **Un chiffre** : sa valeur, son unité, sa date, sa source, et **son évolution** s’il en a une. Trois
  chiffres avec variation ne donnent pas la même slide que trois chiffres sans.
- **Une liste** : a-t-elle un **ordre** ? des **dates** ? des **catégories** ? un **état d’avancement** ?
  Une liste qui a une structure ne s’écrit jamais en puces.

## 3. Des signaux aux types

Lis la ligne qui décrit ce que tu as trouvé, prends le type, vérifie ce qui le départage. Le détail de
chaque type — syntaxe, limites, exemples — est dans `references/types/<id>.md`.

| Ce que tu as trouvé | Type | Ce qui départage |
| --- | --- | --- |
| Le sujet, l’occasion, la date, l’auteur | `titre` | Toujours la première slide, une seule. |
| Les grandes parties annoncées | `sommaire` | Dès dix slides, six parties au plus. Jusqu’à cinq parties courtes : disposition `ligne` ; au-delà de six, `colonnes`. |
| Un changement de partie, une respiration | `section` | Une par partie. `"fond": "rouge"` pour le temps fort, une ou deux fois dans toute la présentation. |
| Un raisonnement, des arguments, un paragraphe dense | `contenu` | Cinq puces au plus. Si la liste a un ordre, des dates, des chiffres ou des catégories, prends le type qui les montre. |
| Deux situations à opposer, un avant / après, deux options | `colonnes` | Trois options : disposition `trois` (la troisième colonne dans `content3`). Quatre et plus : `tableau`. |
| Des sujets classés sur deux critères (effort et impact, urgence et importance) | `matrice` | Exactement quatre cases. Un seul critère, ou moins de quatre cases : `colonnes` ou `contenu`. |
| Une méthode, un processus, des phases sans dates | `etapes` | Trois à six étapes. Chaque phase porte une date : `jalons`. Le processus recommence : disposition `cycle`. |
| Des dates clés, une chronologie | `jalons` | Quatre à cinq jalons. Des chantiers qui se recouvrent sur l’année : `roadmap`. Progression à montrer : disposition `escalier`. |
| Des chantiers menés en parallèle, par trimestre | `roadmap` | Trois ou quatre chantiers, trois barres au plus par chantier. Sans parallélisme : `jalons`. |
| Des sujets répartis par état d’avancement (à cadrer, en cours, livré) | `portefeuille` | Quatre colonnes au plus, cinq sujets par colonne. Si chaque sujet porte des données chiffrées : `tableau`. |
| Trois ou quatre indicateurs suivis, **avec leur évolution** | `kpi` | C’est la variation (`+9 pts`, `−23 %`, une flèche) qui le distingue de `chiffre`. |
| Un à quatre nombres marquants, **sans évolution** | `chiffre` | Un seul nombre qui doit frapper : disposition `vedette`. |
| Trois ou quatre réalisations, décisions ou constats à qualifier | `faits` | Chaque carte a une catégorie et un titre. Sans catégorie ni description : `contenu` en puces. |
| Des personnes et leurs rôles | `equipe` | Trois à quatre d’ordinaire, huit au plus. Une seule personne porte le projet : disposition `vedette`. De simples contacts de clôture : `fin`. |
| Une série de valeurs : évolution, répartition, comparaison chiffrée | `graph` | Plus de quatre valeurs, ou une série datée. Le choix du dessin : voir la table ci-dessous et `references/graphiques.md`. |
| L’état d’un programme, plusieurs mesures d’un coup d’œil | `dashboard` | Deux à quatre graphiques, sans texte d’analyse. Un seul graphique commenté : `graph`. |
| Des lignes homogènes à plusieurs colonnes, des statuts | `tableau` | Huit rangées et cinq colonnes au plus ; au-delà, scinde en deux slides. Un cadre de référence (des lignes nommées : finalité, mission, objectifs) : disposition `cadre`, six lignes au plus. |
| Un outil, une application, un écran à montrer | `maquette` | Sans capture, elle dessine un faux écran avec les chiffres de `content2` : elle marche donc sans image. |
| Un schéma ou une capture qui se suffit à elle-même | `media` | S’il faut la commenter à côté : `imagetexte`. |
| Une photo et son contexte | `imagetexte` | Le texte compte autant que l’image. Sinon : `media` ou `image`. |
| Plusieurs photos à comparer ou à enchaîner (avant, pendant, après) | `galerie` | Trois à six photos, chacune avec son titre et sa légende. |
| Une image forte, une respiration visuelle | `image` | Le titre s’incruste sur la photo. Sans photo fournie par l’utilisateur, évite-la. |
| Une phrase rapportée, un témoignage, une formule qui porte | `citation` | Seulement si la phrase a été réellement dite et qu’on te donne son auteur. Sinon, un témoignage d’illustration, signalé. |
| La décision attendue, le remerciement, un contact | `fin` | Toujours la dernière slide, une seule. |

**Le graphique, une fois `graph` ou `dashboard` choisi** — le détail, les options et les seuils sont dans
`references/graphiques.md` :

| Ce que dit la donnée | Graphique |
| --- | --- |
| Une évolution dans le temps | `courbe` |
| Une comparaison de catégories | `barres` |
| La part d’un tout | `secteurs` |
| Une progression vers une cible | `anneaux` (plusieurs), `jauge` (une seule), `progression` (ligne à ligne) |
| Des effectifs qui se réduisent d’une étape à l’autre | `entonnoir` |
| Des ordres de grandeur à faire sentir | `bulles` |
| Un profil sur plusieurs critères | `radar` |
| Une position entre deux mots opposés | `échelles` |
| Ce qui est commun à deux ou trois ensembles | `intersection` |

**Le départage le plus fréquent**, parce que la matière donne souvent des nombres. Avec une évolution, ce
sont des indicateurs suivis :

```json
{ "layout": "kpi", "title": "Le vélo progresse plus vite que le plan ne le prévoyait.", "content": "Linéaire aménagé | 126 km | +78 km | Depuis 2024\nPassages quotidiens | 4 200 | +121 % | Neuf compteurs permanents\nPart modale du vélo | 6,4 % | +1,9 pt | Enquête ménages 2026", "notes": "Source : note d’étape du plan vélo, mars 2027." }
```

Sans évolution, ce sont des chiffres clés, et la slide respire davantage :

```json
{ "layout": "chiffre", "title": "Le plan vélo en trois nombres.", "content": "126 km | aménagés | Fin 2026, sur un objectif de 180 km\n22 M€ | à engager | Au printemps 2027\n9 % | de part modale | L’objectif fixé pour 2030", "notes": "Source : note d’étape du plan vélo, mars 2027." }
```

## 4. Monter le plan

**La structure type** : `titre` → `sommaire` (dès dix slides) → pour chaque partie, une `section` puis ses
slides → `fin`. Les surtitres des sections se numérotent : `Partie 01`, `Partie 02`…

**La durée commande le nombre de slides** : 5 min ≈ 6 à 8 slides ; 10 min ≈ 10 à 14 ; 20 min ≈ 18 à 25 ;
45 min ≈ 35 à 45. Si la matière déborde, ce sont les notes qui grossissent, pas les slides.

**Un message par slide.** Le titre de la slide est ce message, affirmatif : « La consommation a baissé de
moitié. » plutôt que « Consommation ». Trois à cinq messages clés donnent trois à cinq parties.

**Le rythme** se construit :

- jamais plus de deux `contenu` d’affilée ;
- alterne le texte et les données : un argument, puis le chiffre qui le tient ;
- une `section` en `"fond": "rouge"` au moment où la présentation bascule — le constat qui fâche, la
  décision à prendre ;
- une `citation` ou une `image` pour respirer, au milieu d’une partie dense ;
- la matière la plus lourde (un `tableau`, une `roadmap`) se place après l’argument qu’elle sert, jamais
  avant.

**La décision attendue** se prépare et se pose : la slide qui l’annonce (`etapes`, `matrice` ou `colonnes`
pour montrer l’arbitrage), puis la `fin` qui la formule en une phrase. Si la matière attend un arbitrage
entre deux scénarios, le public doit avoir vu les deux avant.

**Le temps d’échange** se prévoit : pour une séance, garde un tiers du temps aux questions, dis-le dans les
notes de la première slide, et prévois les slides d’annexe qui répondront aux questions prévisibles (si le
sommaire suit les sections avec `"suitSections": true`, la `section` d’annexes prend `"horsSommaire": true`).

## 5. Écrire la réflexion pour l’utilisateur

Avant le JSON, un message court qui montre ce que tu as compris et ce que tu proposes. Trois blocs.

**« Ce que j’ai lu »** — cinq lignes au plus : le sujet, le public déduit, l’objectif, les trois ou quatre
messages clés, et ce que la matière ne dit pas.

**« Ce que je propose »** — le plan en tableau, une ligne par slide :

| N° | Type | Disposition | Titre | Contenu prévu | Pourquoi ce type |
| --- | --- | --- | --- | --- | --- |
| 4 | `kpi` | en ligne | Le vélo progresse plus vite que le plan ne le prévoyait. | Linéaire, passages, part modale, avec les écarts | Trois indicateurs suivis, chacun avec son évolution |
| 6 | `matrice` | — | Par où continuer. | Effort et impact des quatre familles de travaux | Un arbitrage sur deux critères, quatre cases |

Le contenu prévu est **une vraie proposition**, jamais une case vide (« à compléter », « vos données »). Ce
que tu apportes toi-même se marque **« (proposition) »** ; ce qui vient de la matière mais reste à
confirmer, **« À vérifier »** — et la slide portera `[À vérifier]` en tête de ses `notes`.

**Les questions restantes** — seulement celles que la matière ne tranche pas, trois ou quatre au plus, dans
**ce même message**. Leur forme et la validation du plan : voir `references/dialogue.md`.

## 6. Ce qu’on ne fait jamais

- **Inventer un chiffre sans le dire.** Sans donnée, mets une valeur d’illustration, commence les `notes`
  de la slide par `[À vérifier]` et signale-le à la livraison.
- **Attribuer une citation à une personne réelle** qui ne l’a pas dite. Un témoignage proposé s’attribue à
  une fonction (« Une directrice d’école pilote ») et se signale comme illustration.
- **Écrire une adresse d’image.** `image`, `photos`, `portraits` et `captures` restent vides, et la photo
  voulue se décrit dans `notes` : voir `references/images.md`.
- **Résumer le JSON**, le couper, ou en livrer un extrait. Toujours l’objet entier, en un seul bloc.
- **Recopier la matière slide après slide.** Un document n’est pas un plan de présentation.
- **Garder un fait qu’aucune source ne tient.** On le retire, ou on le signale.

## 7. Un exemple

**La matière** (extrait d’une note interne) :

```text
Note à la direction générale — Plan vélo 2024-2027, point d’étape, mars 2027
Le réseau cyclable de l’agglomération est passé de 48 km en 2024 à 126 km fin 2026. L’objectif de 180 km
en 2027 suppose d’engager 22 M€ dès le printemps.
Les neuf compteurs permanents relèvent 4 200 passages par jour en 2026, contre 1 900 en 2024.
La part modale du vélo atteint 6,4 % (enquête ménages 2026), pour un objectif de 9 % en 2030.
Trois obstacles reviennent dans la concertation : les coupures aux carrefours, le stationnement en gare,
l’entretien hivernal des pistes.
Le comité du 14 avril doit arbitrer entre deux scénarios : accélérer sur les axes structurants, ou
densifier les liaisons de quartier.
```

**La fiche de lecture** :

```text
Sujet          : point d’étape du plan vélo 2024-2027
Public         : direction générale, comité du 14 avril
Objectif       : faire décider
Décision       : arbitrer entre « axes structurants » et « liaisons de quartier »
Messages clés  : le réseau a doublé ; l’usage suit ; l’objectif 2027 demande 22 M€ ; il faut choisir
Chiffres       : 48 → 126 km (note, mars 2027) ; 1 900 → 4 200 passages/jour ; 6,4 % de part modale ;
                 22 M€ à engager ; objectifs 180 km (2027) et 9 % (2030)
Dates          : 2024, fin 2026, printemps 2027, 14 avril, 2030
Comparaisons   : deux scénarios à trancher
Manques        : le coût et le gain de chaque scénario, l’état d’avancement par commune
```

**Trois lignes du plan qui en découlent** :

| N° | Type | Pourquoi ce type |
| --- | --- | --- |
| 4 | `kpi` | Trois indicateurs suivis, chacun avec son évolution : linéaire, passages, part modale. |
| 5 | `graph` en `large`, type `courbe` | Une évolution dans le temps, c’est la pente qui prouve ; la note ne donne que 2024 et 2026, les années manquantes sont à demander (« À vérifier »). |
| 7 | `colonnes` avec `"accent": true` | Les deux scénarios du 14 avril, côte à côte, celui qu’on recommande mis en avant. |

La suite — le message de validation, puis le JSON — est montrée de bout en bout dans
`references/exemple-complet.md`.
