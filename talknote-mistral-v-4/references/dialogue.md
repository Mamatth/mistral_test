# Faire valider avant le JSON

> Ouvre ce fichier quand ta réflexion est prête et qu’il reste à la faire valider : poser les trois ou
> quatre questions que la matière ne tranche pas, faire valider le plan en un seul message, puis enchaîner
> les ajustements après le JSON.

La matière a déjà répondu à l’essentiel : ne redemande jamais ce qu’elle dit. Le dialogue tient en **un
aller-retour**. Tu montres ce que tu as lu et le plan que tu proposes, tu poses dans le **même message**
les seules questions qui restent, l’utilisateur répond en un mot ou d’un clic, tu écris le JSON.

```text
Toi  : « Ce que j’ai lu » + le plan en tableau + 3 ou 4 questions + « Valider ce plan ? »
Lui  : « 1A 2B ok »        (un clic, ou trois caractères)
Toi  : le JSON entier, puis trois lignes : hypothèses, chiffres à vérifier, images à ajouter
Lui  : « change la 7, plus court »
Toi  : le JSON entier à nouveau
```

Ce que contient le message de réflexion — « Ce que j’ai lu », le plan en tableau, ce qui est marqué
« (proposition) » — est décrit dans `references/analyse.md`. Ce fichier-ci ne traite que des questions,
des réponses et de la suite.

## 1. Ce qu’on demande, ce qu’on ne demande pas

Choisis **trois questions de fond au plus**, celles qui changeraient vraiment la présentation ; la
validation du plan (section 4) est la quatrième et dernière. Les options se déduisent du sujet : jamais de
choix passe-partout.

| Question | La poser quand | Options à construire |
| --- | --- | --- |
| Public | La matière ne dit pas devant qui on parle | Les publics plausibles pour ce sujet : direction, équipes, élus, partenaires, clients, grand public |
| Objectif et décision | L’intention reste floue, ou une décision est attendue sans qu’on sache laquelle | Informer, convaincre, faire décider, former ; ou les arbitrages possibles, tirés de la matière |
| Durée ou format | Rien n’indique le temps de parole | Deux ou trois formats chiffrés : « 5 min, 7 slides » ; « 15 min, 13 slides » ; « document envoyé, textes plus complets » |
| Style | Aucun thème ni modèle n’est imposé | Deux ou trois styles adaptés au sujet et au public — voir `references/styles.md` |
| Images | Le sujet s’y prête et rien n’est fourni | « J’ai des photos » ; « Sans photo » ; « Des cadres vides à remplir plus tard » |
| Parties à couvrir | La matière est large et plusieurs découpages tiennent | Deux ou trois découpages possibles, en trois ou quatre parties chacun |

Une question posée doit avoir un effet visible sur le plan. Dis cet effet dans la description de chaque
option (« 7 slides, le constat et l’arbitrage »), pas dans un commentaire à côté.

**On ne demande jamais :**

- le **nombre de slides** à part : il découle de la durée ;
- ce que la matière dit déjà, même à moitié : on le retient et on le marque « À vérifier » ;
- un **thème en plus d’un modèle complet** : le modèle apporte ses couleurs (`references/styles.md`) ;
- une question qui n’a qu’une réponse raisonnable : prends-la, et signale-la « (proposition) » ;
- les contenus slide par slide : le plan les montre déjà, une seule validation suffit.

Un seul tour de questions avant le JSON, celui qui accompagne le plan. Une réponse « B · Ajuster » ne le
rouvre pas : tu appliques le changement, tu réécris les lignes du plan qui bougent et tu écris le JSON.

## 2. Avec l’outil de questions (Mistral Vibe)

Si tu disposes de `ask_user_question` — ou de tout outil de questions à options — **pose tes questions avec
lui**, jamais en texte libre.

- Une à quatre questions par appel, deux à quatre options chacune.
- Une option « Autre » (réponse libre) est ajoutée automatiquement : ne l’écris pas.
- L’en-tête : un ou deux mots (« Public », « Durée », « Style », « Le plan »).
- Chaque option : un libellé de cinq mots au plus, et une description d’une ligne qui dit **ce que le
  choix change** dans la présentation.
- L’option que tu recommandes vient en premier, avec « (recommandé) » à la fin du libellé.
- Ce qu’il faut lire pour choisir — ce que tu as lu, le plan, les chiffres à vérifier — s’écrit **dans ton
  message, juste avant l’appel** : l’outil ne montre que les questions.
- La dernière question est toujours la validation du plan (section 4).
- Si l’outil échoue ou n’existe pas, bascule sur la carte de choix (section 3) sans le commenter.

Un appel, en clair (les noms exacts des champs dépendent de ton outil ; garde les trois éléments :
l’intitulé, l’en-tête, les options décrites) :

```text
ask_user_question
  1. intitulé : « Combien de temps aurez-vous devant le comité du 14 avril ? »
     en-tête  : « Durée »
     options  :
       - « 15 minutes (recommandé) » — 13 slides, une partie par message clé
       - « 5 minutes d’ouverture »   — 7 slides : le constat, puis l’arbitrage
       - « Document envoyé »         — mêmes slides, textes et notes plus complets
  2. intitulé : « Quel style pour cette séance ? »
     en-tête  : « Style »
     options  :
       - « Minuit (recommandé) » — fond sombre, chiffres très lisibles en salle
       - « Papier »              — clair et sobre, meilleur à l’impression
  3. intitulé : « Ce plan vous va-t-il ? »
     en-tête  : « Le plan »
     options  :
       - « Valider (recommandé) » — j’écris le JSON tout de suite
       - « Ajuster »              — dites les numéros à retirer, fusionner, ajouter, déplacer
       - « Plus court »           — 8 slides, les messages clés seulement
       - « Plus détaillé »        — 18 slides, une slide par argument
```

## 3. Sans outil (Le Chat, ou toute conversation en texte)

Les mêmes questions deviennent une **carte de choix**, à la fin du message qui porte le plan, exactement
dans ce format :

```text
**1 · Durée** — Combien de temps devant le comité du 14 avril ?
- **A** · 15 minutes *(recommandé)* — 13 slides, une partie par message clé
- **B** · 5 minutes d’ouverture — 7 slides : le constat, puis l’arbitrage
- **C** · Document envoyé avant la séance — mêmes slides, textes et notes plus complets
- **Autre** : écrivez-le

**2 · Style** — Quelle allure pour cette séance ?
- **A** · Minuit *(recommandé)* — fond sombre, chiffres très lisibles en salle
- **B** · Papier — clair et sobre, meilleur à l’impression
- **Autre** : écrivez-le

**3 · Images** — Avez-vous des photos du réseau cyclable ?
- **A** · Sans photo *(recommandé)* — des graphiques et des chiffres
- **B** · J’ai des photos — je prévois trois slides qui les attendent
- **Autre** : écrivez-le

**4 · Le plan ci-dessus** — On part là-dessus ?
- **A** · Valider *(recommandé)* — j’écris le JSON
- **B** · Ajuster — les numéros à retirer, fusionner, ajouter, déplacer
- **C** · Plus court — 8 slides, les messages clés seulement
- **D** · Plus détaillé — 18 slides, une slide par argument

**Réponse express** : `1A 2B 3A 4A`, ou `ok` pour garder mes recommandations. Vous pouvez aussi écrire
librement : `1 : 10 minutes`, `4B : retirer la 9, fusionner 5 et 6`.
```

Règles de la carte :

- questions numérotées, options en **A**, **B**, **C**, **D** au plus, recommandation en **A** ;
- une ligne « Autre : écrivez-le » par question, et la ligne **Réponse express** à la fin, avec un exemple
  tiré de la carte elle-même ;
- rien après la carte : elle ferme le message.

## 4. La validation du plan, toujours en dernière question

Une seule validation, et c’est celle du plan entier :

| Réponse | Ce que tu fais |
| --- | --- |
| **A · Valider** | Tu écris le JSON. Aucune autre question. |
| **B · Ajuster** | Tu appliques les changements demandés, tu réécris **les seules lignes du plan qui bougent** (deux ou trois lignes de tableau), puis tu enchaînes sur le JSON sans reposer de question. |
| **C · Plus court** | Tu retires les slides de détail, tu fusionnes les parties voisines, tu gardes `titre`, les messages clés et la `fin` ; tu annonces le nouveau nombre de slides en une ligne, puis le JSON. |
| **D · Plus détaillé** | Tu ajoutes les slides que la matière permet vraiment : une donnée par slide, une annexe hors sommaire ; jamais du remplissage. |

Si l’ajustement change la nature de la présentation (un autre public, un autre objectif), refais le plan
complet et repose seulement cette question-là.

## 5. Lire les réponses

- **Réponse partielle** (`2B` seulement) : tes recommandations valent pour le reste.
- **Texte libre** ou « Autre » : c’est une information, pas une option — lis-la et adapte le plan.
- **`ok`, « oui », « ça me va »** : tout est validé, tu écris le JSON.
- **Réponse contradictoire** (5 minutes et 20 slides) : tu tranches en faveur de la contrainte la plus
  dure, tu le dis en une ligne.
- Avant d’écrire le JSON, **récapitule en une ligne** ce qui est retenu :
  « Retenu : comité du 14 avril · 15 minutes · 13 slides · thème Papier · sans photo. »
- Une question tranchée ne se repose jamais, même autrement formulée.

## 6. Après le JSON : les ajustements

Sous le bloc JSON, trois lignes au plus (hypothèses, chiffres à vérifier, images à ajouter), la phrase
d’import — voir `references/format-json.md` — puis une dernière carte, ou un dernier appel à l’outil :

```text
- **A** · C’est parfait
- **B** · Modifier des slides — les numéros et ce qui change
- **C** · Une version plus courte
- **D** · Essayer un autre style
```

À chaque modification d’une présentation entière, tu redonnes **le JSON complet**, jamais un extrait :
TalkNote importe une présentation entière. Pour une seule slide à coller dans une présentation ouverte, le
mode de `references/coller-une-slide.md` remplace cette règle. La nouvelle version s’ajoute à la bibliothèque ; l’ancienne peut
aller à la corbeille.

## 7. Quand on ne demande rien

Tu sautes la validation et tu écris le JSON tout de suite si :

- l’utilisateur dit « fais directement », « pas de questions », « j’ai besoin du JSON maintenant » ;
- il a déjà répondu à tout dans sa demande ;
- aucun échange n’est possible (une seule réponse attendue, pas d’interface de questions).

Dans ce cas, tu prends les hypothèses les plus raisonnables — public le plus probable, 12 slides environ,
un style adapté au sujet — et tu les **listes sous le bloc**, trois lignes au plus :

```text
Hypothèses : comité de direction, 15 minutes, 13 slides, thème Minuit.
À vérifier : les 22 M€ et la part modale de 6,4 % (notes de la slide 4).
Images : trois slides attendent une photo (5, 9, 12) — dites-le-moi et je les adapte.
```

Puis une seule phrase : « Dites-moi ce qui change, je vous redonne le JSON entier. »

## 8. Ce qui ne se fait pas

- Poser une question dont la matière donne la réponse, ou dont la réponse ne change rien.
- Séparer le plan et les questions en deux messages : ils voyagent ensemble.
- Enchaîner plus de deux tours de choix : un pour faire valider le plan, une carte après le JSON.
- Demander à l’utilisateur d’écrire lui-même un contenu, un chiffre ou un titre : tu proposes, il corrige.
- Livrer le JSON en même temps qu’une question ouverte : on valide d’abord, on écrit ensuite.
- Faire attendre pour rien : si tout est clair, valide en une question et écris.
