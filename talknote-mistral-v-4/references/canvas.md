# Mode « Canvas d'écriture » : la page d'écriture partagée et modifiable

> La page d'écriture vit dans un **canvas** : un document partagé que l'utilisateur peut modifier à tout
> moment, y compris entre deux messages. Tu peux aussi l'éditer toi-même. Ce fichier complète
> `references/page-ecriture.md` : la syntaxe des repères (`[SECTION]`, `[SLIDE]`), les notes mot pour mot
> et le découpage y restent la règle. Ce fichier ajoute le protocole d'édition partagée.

## 1. Reconnaître le mode

Ce mode s'applique quand la page d'écriture est **un document partagé** que tu vois dans la conversation,
et non un texte collé une fois entre `--- PAGE D'ÉCRITURE ---` et `--- FIN ---`. Signaux :

- la page est visible comme document éditable, avec ou sans les repères `--- PAGE D'ÉCRITURE ---` ;
- l'utilisateur demande de modifier « la page », « le document », ou parle de ce qu'il vient de changer ;
- une demande de présentation est faite alors que le canvas contient déjà le texte.

Si tu hésites entre ce mode et une présentation entière classique (matière collée dans le message), pose
une seule question : « La page dans le canvas est-elle ta matière, ou veux-tu partir d'un autre texte ? »

## 2. Relire avant chaque action

1. **Relis le canvas en entier** avant chaque réponse, même si tu crois te souvenir de son état. L'état
   courant du canvas est la seule source de vérité ; ta mémoire de la version précédente ne l'est pas.
2. Ne repars jamais d'une copie antérieure du texte. Si tu dois écrire dans le canvas, tes modifications
   partent de l'état courant, relecture faite.
3. Ce que l'utilisateur a changé depuis ton dernier message est **son dernier mot** : il ne se commente
   pas, ne se corrige pas, ne s'annule pas.

## 3. Qui écrit quoi

| Acte | Toi | L'utilisateur |
| --- | --- | --- |
| Écrire le texte de son propos | Non. Tu ne réécris jamais ses phrases, même pour corriger. | Oui. |
| Poser ou déplacer les repères `[SECTION]`, `[SLIDE]`, `[/SLIDE]` | Oui, sur demande, en insérant des lignes sans toucher au texte autour. | Oui. |
| Découper le texte libre en slides (le plan) | Oui, validé comme en mode page d'écriture. | Oui, en le demandant. |
| Changer le titre, le thème, le modèle, le nombre de slides | Uniquement sur demande explicite. | Oui. |

- Tes éditions du canvas sont **des insertions de repères ou des ajouts de lignes**, jamais des
  réécritures du texte existant. Un repère se pose sur sa propre ligne.
- Si l'utilisateur te demande de réécrire son texte (« reformule ce paragraphe »), fais-le uniquement
  pour les passages désignés, et indique en une ligne sous le plan ce qui a changé.

## 4. Divergence : l'état courant gagne

1. Si l'état courant du canvas contredit ta dernière version (l'utilisateur a édité, supprimé, déplacé),
   **l'état courant l'emporte**. Applique le plan sur l'état courant, pas sur ta version.
2. Ne signale une divergence que si elle rend le plan caduc (un `[SLIDE]` supprimé, une section
   renommée, un nombre de slides dépassé). Dans ce cas, une ligne sous le plan : « Ta modification
   change le plan : … », puis un nouveau plan à valider.
3. Si la modification de l'utilisateur invalide une slide déjà livrée, redonne **uniquement** les slides
   touchées, au format du mode « slide à coller » (`references/coller-une-slide.md`, section 3) — jamais
   la présentation entière.

## 5. Le déroulé, en quatre temps

1. **Lire** le canvas en entier (section 2).
2. **Proposer le plan** en conversation, au format de `references/page-ecriture.md` (section 3) : tableau
   à cinq colonnes, nombre total, une seule question. Attends la réponse.
3. **Écrire le JSON** dans la conversation, au format de `references/page-ecriture.md` (sections 5 à 7).
   Le canvas garde le texte ; le JSON reste livré dans un bloc de code, il ne s'écrit pas dans le canvas.
4. **Ajuster** : à chaque modification demandée ou observée dans le canvas, relis (section 2), applique
   uniquement ce qui change, et redonne soit les slides touchées (section 4.3), soit le JSON entier si
   l'utilisateur le demande.

Si l'utilisateur dit « fais directement », saute le temps 2.

## 6. Ce qui ne change pas

- Syntaxe des repères, libellés de type, notes mot pour mot : `references/page-ecriture.md`.
- Champs, enveloppe, liste de contrôle : `references/format-json.md` et la fiche de chaque type.
- Aucun chiffre, nom, date ou citation inventé ; images vides ; pictogrammes de
  `references/pictogrammes.md` seulement.
- Le JSON livré reste un bloc unique, valide, sans commentaire ni champ inventé.

## 7. Liste de contrôle

- [ ] J'ai relu le canvas en entier au tour courant, pas à partir de ma mémoire.
- [ ] Aucune phrase de l'utilisateur n'a été réécrite, déplacée ou supprimée par moi sans demande.
- [ ] Mes éditions du canvas ne sont que des repères ou des lignes ajoutées, sur l'état courant.
- [ ] Toute divergence entre ma version précédente et le canvas a été tranchée pour le canvas.
- [ ] Les notes redonnent le texte du canvas mot pour mot, dans l'ordre, sans doublon ni manque.
- [ ] Livraison conforme : slides touchées seules, ou JSON entier sur demande.
