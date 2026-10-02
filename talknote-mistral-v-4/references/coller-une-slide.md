# Mode « coller une slide »

> Ouvre ce fichier dès que l’utilisateur veut ajouter, refaire ou corriger **une ou quelques slides** dans une
> présentation déjà ouverte dans TalkNote, ou dès qu’il colle le JSON d’une slide. Dans ce mode, tu ne livres
> pas une présentation : tu livres la ou les slides, à coller.

## 1. Reconnaître le mode

Ce mode s’applique si **l’une** de ces conditions est vraie :

- la demande vise une slide précise : « ajoute une slide sur… », « une slide de plus pour… », « refais la 7 »,
  « corrige cette slide », « change le graphique de la slide 4 » ;
- l’utilisateur colle un objet JSON qui commence par `{ "layout"` (une slide copiée dans TalkNote avec ⌘ C : elle
  n’a ni `id`, ni les champs laissés à leur valeur par défaut) ;
- l’utilisateur dit qu’il a déjà une présentation et veut la compléter.

Il ne s’applique **pas** si l’utilisateur veut une présentation entière, une refonte, une autre durée ou un
autre style pour toute la présentation : suis alors les cinq étapes de `SKILL.md`.

Si tu hésites entre les deux modes, pose une seule question : « Une slide à coller dans ta présentation ouverte, ou
une présentation entière ? »

## 2. Le déroulé, en quatre temps

1. **Lire la demande.** Note : le contenu de la slide, la place voulue (après quelle slide), le modèle et le thème de
   la présentation si l’utilisateur les donne.
2. **Poser au plus deux questions**, seulement si le contenu ou le type reste ambigu, chacune avec une réponse par
   défaut. Si la demande est claire, ne pose aucune question et écris la slide.
3. **Écrire la slide.**
   - Choisis le type avec la table « Choisir le type » de `SKILL.md`. Ouvre la fiche `references/types/<id>.md`
     de ce type et lis-la en entier. Pour un graphique, ouvre aussi `references/graphiques.md`.
   - Si l’utilisateur a collé une slide, **garde tous ses champs** et ne change que ce qu’il demande.
   - Ouvre `references/format-json.md` pour la syntaxe du texte et la liste de contrôle.
4. **Livrer** selon la section 3.

## 3. Le format de livraison, exact

Livre, dans cet ordre, sans rien d’autre :

1. **Un seul bloc de code `json`**, qui contient soit une slide, soit une liste de slides.
2. Deux lignes au plus : les chiffres à vérifier, les images à ajouter.
3. La consigne : « Dans TalkNote, ouvre ta présentation, sélectionne la slide après laquelle insérer, puis ⌘ V
   (hors d’un champ de texte). » Si c’est un remplacement, ajoute : « Supprime ensuite l’ancienne slide. »

Une slide :

```json
{ "layout": "kpi", "eyebrow": "Bilan 2026", "title": "Trois indicateurs progressent.", "content": "Satisfaction | 84 % | +3 pts | Enquête de juin\nDélai moyen | 2,4 j | −0,9 j | Toutes écoles\nSignalements | 412 | +18 % | Depuis janvier", "notes": "Source : rapport annuel 2026.\n[À vérifier] Le périmètre de l’enquête." }
```

Plusieurs slides :

```json
[
  { "layout": "section", "eyebrow": "Partie 03", "title": "Ce qui reste à faire", "content": "Trois chantiers pour 2027." },
  { "layout": "etapes", "title": "Trois étapes jusqu’à la rentrée.", "content": "Diagnostic | Relevés dans chaque école\n> Travaux | Été 2027\nBilan | Septembre 2027" }
]
```

## 4. Ce qui change par rapport à une présentation entière

| Élément | Dans ce mode |
| --- | --- |
| Enveloppe (`version`, `title`, `theme`, `modele`, `transition`, `footer`, `slides`) | **Ne pas l’écrire.** Le bloc contient la slide ou la liste, rien autour. |
| `id` | **Ne pas l’écrire.** TalkNote en crée un. |
| Champs d’une slide et syntaxe du texte | Identiques à `references/format-json.md`. |
| Thème et modèle | La slide prend ceux de la présentation ouverte. N’écris ni `theme` ni `modele`. |
| Première slide `titre` et dernière slide `fin` | **Non exigées** dans ce mode. Écris un `titre` ou une `fin` seulement si on te le demande. |
| Notes | Comme dans une présentation : `Source : …`, `[À vérifier]`, `Image à ajouter : …`. |
| Images | `image`, `photos`, `portraits`, `captures` restent vides. |
| Longueur | Une slide ou une liste courte. Au-delà de 5 slides, propose plutôt une présentation entière. |

Règle inchangée : **le bloc reste un JSON entier et valide**. Une slide n’est jamais coupée, ni résumée par « … »,
ni accompagnée d’un commentaire dans le bloc.

## 5. Modifier une slide existante

1. Pars de la slide que l’utilisateur a collée. S’il ne l’a pas collée, demande-la : « Colle le JSON de la slide
   (⌘ C sur la slide dans TalkNote). » Ne la reconstruis pas de mémoire.
2. Change **uniquement** ce qui est demandé ; laisse tous les autres champs identiques, mot pour mot.
3. Redonne la slide **entière** dans le bloc, pas seulement le champ modifié.
4. Si le type de la slide doit changer, réécris-la depuis la fiche du nouveau type et dis-le en une ligne.

## 6. Ajuster après la livraison

Termine par une ligne : « Autre chose sur cette slide, ou une autre slide à ajouter ? ». Ne pose pas la carte
de choix de `references/dialogue.md`. À chaque changement demandé, redonne la slide ou la liste **entière**.

## 7. Liste de contrôle

- [ ] Le bloc contient une slide `{ … }` ou une liste `[ … ]`, sans enveloppe et sans `id`.
- [ ] Chaque objet a un `layout` pris dans les 24 identifiants, sans accent.
- [ ] Les champs, dispositions et syntaxes sont ceux de la fiche du type.
- [ ] Retours à la ligne en `\n` (un seul antislash) ; aucun commentaire ; aucune virgule finale.
- [ ] `image`, `photos`, `portraits`, `captures` sont vides ; les images attendues sont dans les `notes`.
- [ ] Après le bloc : deux lignes au plus, puis la consigne ⌘ V.
