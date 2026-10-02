# Un exemple de bout en bout

> À ouvrir pour voir la méthode entière sur un cas : de la matière reçue au JSON livré. Le cas prolonge
> celui d’`references/analyse.md`.

Quatre temps : la matière, la fiche de lecture, le message qui fait valider le plan, puis le JSON.

## 1. La matière reçue

L’utilisateur joint une note interne et écrit : « Fais-moi une présentation pour le comité du 14 avril. »

```text
Note à la direction générale — Plan vélo 2024-2027, point d’étape, mars 2027

Le réseau cyclable de l’agglomération est passé de 48 km en 2024 à 126 km fin 2026. L’objectif de 180 km
en 2027 suppose d’engager 22 M€ dès le printemps.

Les neuf compteurs permanents relèvent 4 200 passages par jour en 2026, contre 1 900 en 2024.
La part modale du vélo atteint 6,4 % (enquête ménages 2026), pour un objectif de 9 % en 2030.

Les travaux se sont enchaînés sans année blanche : schéma directeur voté en 2024, deux liaisons
structurantes en 2025 (38 km), montée en charge en 2026 (40 km et neuf compteurs).

Trois obstacles reviennent dans la concertation : les coupures aux carrefours, le stationnement en gare,
l’entretien hivernal des pistes.

Le comité du 14 avril doit arbitrer entre deux scénarios : accélérer sur les axes structurants, ou
densifier les liaisons de quartier.
```

## 2. La fiche de lecture

```text
Sujet          : point d’étape du plan vélo 2024-2027
Public         : direction générale, comité du 14 avril
Objectif       : faire décider
Décision       : arbitrer entre « axes structurants » et « liaisons de quartier »
Messages clés  : le réseau a doublé ; l’usage suit ; l’objectif 2027 demande 22 M€ ; il faut choisir
Chiffres       : 48 → 126 km ; 1 900 → 4 200 passages/jour ; 6,4 % de part modale ; 22 M€ ;
                 objectifs 180 km (2027) et 9 % (2030)
Dates          : 2024, 2025, 2026, printemps 2027, 14 avril, 2030
Étapes         : schéma directeur, liaisons structurantes, montée en charge, achèvement
Comparaisons   : deux scénarios à trancher
Citations      : aucune citation exacte dans la note
Images         : aucune fournie
Manques        : le coût et le gain de chaque scénario, le linéaire de 2025, le chiffrage du
                 stationnement en gare, le plan de financement des 22 M€
```

Ce que la matière tranche : le public, l’objectif, la décision attendue, la date. Ce qu’elle ne tranche
pas : la durée de la présentation, le style, et surtout les quatre chiffrages manquants. Ces manques ne
bloquent pas : ils deviennent une slide.

## 3. Le message qui fait valider le plan

C’est le seul message avant le JSON. Il dit ce qui a été lu, ce qui est proposé, et pose les trois
questions que la note ne tranche pas.

```text
Ce que j’ai lu
— Le réseau est passé de 48 à 126 km entre 2024 et fin 2026 ; l’objectif de 180 km en 2027 suppose
  22 M€ engagés au printemps.
— L’usage suit : 4 200 passages par jour contre 1 900 en 2024, une part modale de 6,4 %.
— Trois obstacles reviennent dans la concertation, et le comité du 14 avril doit trancher entre deux
  scénarios.
— Quatre éléments manquent pour comparer les scénarios : je les mets en slide plutôt que de les inventer.

Ce que je propose — 13 slides, environ 20 minutes
```

| N° | Type | Disposition | Titre | Contenu prévu | Pourquoi ce type |
| --- | --- | --- | --- | --- | --- |
| 1 | `titre` | — | Le réseau cyclable a doublé. Reste à choisir la suite. | Comité du 14 avril | Ouvre en annonçant le constat et la décision. |
| 2 | `sommaire` | — | Trois temps. | Le réseau · Ce qui freine · La décision | Trois parties, une ligne chacune. |
| 3 | `section` | — | Où en est le réseau. | 48 → 126 km en trois ans | Ouvre la première partie. |
| 4 | `kpi` | — | Les trois indicateurs sont orientés à la hausse. | Linéaire, passages, part modale, avec leur évolution | Trois indicateurs suivis, chacun avec sa variation. |
| 5 | `graph` | `large` | La courbe tient le rythme. | Courbe du linéaire, 2024 à 2027 | Une évolution dans le temps : c’est la pente qui prouve. |
| 6 | `jalons` | `escalier` | Ce qui a été livré depuis le lancement. | 2024, 2025, 2026, 2027 | Des dates structurantes, et une progression. |
| 7 | `section` | — | Ce qui freine. | Trois obstacles | Ouvre la deuxième partie. |
| 8 | `faits` | — | Trois obstacles, remontés partout. | Carrefours, gare, entretien hivernal | Trois constats, une idée par carte. |
| 9 | `citation` | — | « Après le carrefour, je redeviens une voiture qui gêne. » | Verbatim de concertation *(proposition)* | Donne une voix au constat. À remplacer par un verbatim exact. |
| 10 | `section` | temps fort | La décision du 14 avril. | Deux scénarios | Le point dur de la séance, sur fond de couleur. |
| 11 | `colonnes` | — | Accélérer sur les axes, ou densifier les quartiers. | Scénario A / Scénario B, B mis en avant | Deux options à confronter. |
| 12 | `tableau` | `plein` | Ce qu’il reste à chiffrer. | Quatre éléments, responsable, échéance, statut | Des lignes homogènes, avec des statuts. |
| 13 | `fin` | — | Décision attendue avant le 30 avril. | Contact et coordonnées | Clôt sur la décision, pas sur un remerciement. |

```text
Ce qui reste à trancher
1 · Durée : 20 minutes (13 slides), ou une version courte de 8 slides ?
2 · Recommandation : je marque le scénario B comme recommandé (il sert l’objectif 2030). Vous préférez
    rester neutre ?
3 · Style : thème « forêt » (vert profond, sujet territorial), ou « papier » (crème et encre,
    plus institutionnel) ?

Répondez « ok » pour garder ces propositions, ou corrigez le point qui ne va pas.
```

## 4. Le JSON livré

Après validation, un seul bloc, l’objet entier :

```json
{
  "version": 2,
  "title": "Plan vélo 2024-2027 · Point d’étape",
  "theme": "foret",
  "modele": "",
  "transition": "glisse",
  "footer": true,
  "slides": [
    {
      "layout": "titre",
      "eyebrow": "Comité de direction · 14 avril 2027",
      "title": "Le réseau cyclable a doublé. Reste à choisir la suite.",
      "content": "Point d’étape du plan vélo 2024-2027, et arbitrage entre deux scénarios d’investissement.",
      "author": "14 avril 2027 · Direction des mobilités",
      "notes": "Rappeler en ouverture que la séance doit aboutir à un choix entre deux scénarios. Vingt minutes de présentation, puis l’arbitrage."
    },
    {
      "layout": "sommaire",
      "eyebrow": "Sommaire",
      "title": "Trois temps.",
      "content": "Où en est le réseau | Trois ans de travaux, et l’usage qui suit\nCe qui freine | Les trois obstacles remontés par la concertation\nLa décision du 14 avril | Deux scénarios, une recommandation",
      "notes": "Annoncer que la décision est en fin de séance : la première partie est un constat, pas un débat."
    },
    {
      "layout": "section",
      "eyebrow": "Partie 01",
      "title": "Où en est le réseau.",
      "content": "De 48 à 126 kilomètres en trois ans, et un usage qui a plus que doublé.",
      "notes": "Source : note d’étape du plan vélo, mars 2027."
    },
    {
      "layout": "kpi",
      "title": "Les trois indicateurs du plan sont orientés à la hausse.",
      "content": "Linéaire aménagé | 126 km | +78 km depuis 2024 | Objectif 2027 : 180 km\nPassages quotidiens | 4 200 | +121 % | Moyenne des neuf compteurs permanents\nPart modale du vélo | 6,4 % | +2,1 pts | Objectif 2030 : 9 %",
      "notes": "Source : note d’étape, mars 2027 ; part modale issue de l’enquête ménages 2026. La part modale est l’indicateur qui compte pour 2030 : elle progresse, mais moins vite que le linéaire."
    },
    {
      "layout": "graph",
      "title": "La courbe du linéaire tient le rythme, l’objectif 2027 reste atteignable.",
      "content": "Trois années de travaux continus, sans année blanche.\n- Le rythme moyen est de 26 km par an\n- Les 54 km qui restent supposent d’engager 22 M€ au printemps",
      "content2": "type : courbe\ntitre : Linéaire cyclable aménagé\nsous-titre : Kilomètres, cumulés\naxe : 2024, 2025, 2026, 2027\nunité : km\noptions : aire\nLinéaire : 48, 86, 126, 180",
      "disposition": "large",
      "notes": "[À vérifier] La note ne donne que 2024 (48 km) et fin 2026 (126 km). La valeur 2025 et la projection 2027 sont des estimations linéaires, à confirmer par le service technique avant diffusion."
    },
    {
      "layout": "jalons",
      "title": "Ce qui a été livré depuis le lancement.",
      "content": "x 2024 | Lancement | Schéma directeur voté, 48 km existants\nx 2025 | Premiers axes | Deux liaisons structurantes, 38 km\nx 2026 | Montée en charge | 40 km et neuf compteurs permanents\n2027 | Achèvement | 54 km à engager, 180 km visés",
      "disposition": "escalier",
      "notes": "Insister sur la régularité : aucune année blanche depuis 2024, ce qui rend l’objectif crédible."
    },
    {
      "layout": "section",
      "eyebrow": "Partie 02",
      "title": "Ce qui freine.",
      "content": "Trois obstacles reviennent dans toutes les réunions de concertation.",
      "notes": "Source : synthèse de la concertation, décembre 2026."
    },
    {
      "layout": "faits",
      "title": "Trois obstacles, remontés partout.",
      "content": "Sécurité | Les coupures aux carrefours | Les pistes s’interrompent aux intersections les plus circulées | Prioritaire\nStationnement | Le stationnement en gare | Places saturées dès 8 h, pas d’abri sécurisé | À chiffrer\nEntretien | L’entretien hivernal | Verglas et feuilles non traités sur les pistes séparées | À arbitrer",
      "notes": "Source : synthèse de la concertation, décembre 2026. Les trois sujets sont cités dans les six réunions de quartier."
    },
    {
      "layout": "citation",
      "title": "J’ai une piste jusqu’au carrefour. Après, ==je redeviens une voiture qui gêne==.",
      "author": "Un participant aux réunions de quartier",
      "anim": "flou",
      "notes": "[À vérifier] Formulation proposée, fidèle au sens des remontées de la concertation mais non citée telle quelle dans la synthèse. À remplacer par un verbatim exact, ou à retirer."
    },
    {
      "layout": "section",
      "eyebrow": "Partie 03",
      "title": "La décision du 14 avril.",
      "content": "Deux scénarios, le même budget, deux effets très différents.",
      "fond": "rouge",
      "notes": "C’est le point dur de la séance : annoncer qu’une décision est attendue avant la fin."
    },
    {
      "layout": "colonnes",
      "title": "Accélérer sur les axes, ou densifier les quartiers.",
      "content": "> Scénario A\n# Axes structurants\n- Quatre liaisons de bout en bout\n- Priorité aux carrefours coupés\n- Effet visible sur les compteurs dès 2028\nPorte l’objectif 2027 des 180 km",
      "content2": ">> Scénario B\n# Liaisons de quartier\n- Un maillage fin autour des écoles et des gares\n- Stationnement sécurisé sur six pôles\n- Touche d’abord les trajets courts\nPorte l’objectif 2030 de part modale",
      "accent": true,
      "notes": "[À vérifier] Le coût et le gain de chaque scénario ne figurent pas dans la note d’étape : ils sont à demander au service technique avant le comité. Recommandation proposée : le scénario B, qui sert l’objectif 2030, l’objectif 2027 pouvant être tenu à un an près."
    },
    {
      "layout": "tableau",
      "title": "Ce qu’il reste à chiffrer avant de trancher.",
      "content": "Quatre éléments manquent pour comparer les scénarios à armes égales.",
      "content2": "Élément | Responsable | Échéance | Statut\nCoût au kilomètre par scénario | Service technique | 7 avril | En cours\nGain de part modale attendu | Agence d’urbanisme | 7 avril | En cours\nCoût du stationnement en gare | Pôle gares | 10 avril | À faire\nPlan de financement 22 M€ | Direction des finances | 12 avril | À faire",
      "disposition": "plein",
      "notes": "Ces quatre éléments conditionnent la comparaison. Si l’un manque le 14 avril, proposer de reporter l’arbitrage au comité de mai plutôt que de décider à l’aveugle."
    },
    {
      "layout": "fin",
      "title": "Décision attendue : ==retenir un scénario== avant le 30 avril.",
      "content": "Les quatre chiffrages manquants seront transmis avant le 12 avril.\nContact | Direction des mobilités\nCourriel | mobilites@exemple.fr\nTéléphone | 02 40 00 00 00",
      "author": "Direction des mobilités",
      "transition": "zoom",
      "notes": "Conclure sur la date : sans décision avant le 30 avril, les marchés ne peuvent pas être lancés pour la saison de travaux."
    }
  ]
}
```

## 5. Ce qui accompagne le JSON

Trois lignes au plus sous le bloc :

```text
Hypothèses : scénario B présenté comme recommandé ; 13 slides pour 20 minutes ; thème « forêt ».
À vérifier : le linéaire 2025 et la projection 2027 (estimations), le verbatim de la slide 9.
Images : aucune n’est nécessaire ; une photo de piste cyclable irait en slide 3 si vous en avez une.

Copiez le bloc, puis dans TalkNote : ⌘ V sur l’accueil (ou « Coller un JSON… »).
```

## Ce que cet exemple montre

- **Les manques deviennent une slide** (la 12) au lieu d’être comblés par des chiffres inventés.
- **Ce qui est estimé est signalé** : les `notes` des slides 5 et 9 commencent par `[À vérifier]`, et
  l’estimation est expliquée.
- **Les sources sont dans les `notes`**, pas sur la slide.
- **La dernière slide porte la décision**, avec sa date et ses coordonnées, parce que l’objectif était de
  faire décider.
- **Onze types différents** pour treize slides : chaque contenu a pris la forme qui le montre.
