# 3.5 Annuler des changements en toute sécurité

Git propose trois commandes « d'annulation » différentes, et elles agissent sur trois endroits différents. Choisir la bonne dépend de l'endroit où se trouve le changement indésirable et du fait que quelqu'un d'autre l'ait déjà vu ou non.

## Tableau de décision : restore vs. revert vs. reset

| Commande | Agit sur | Réécrit l'historique publié ? | Usage typique | Sécurité / récupération |
| --- | --- | --- | --- | --- |
| [`git restore <fichier>`](https://git-scm.com/docs/git-restore) | Arbre de travail (cible par défaut) | Non — ce n'est pas une opération d'historique | Abandonner des modifications indésirables et non committées d'un fichier | Le contenu abandonné disparaît ; Git ne conserve aucun reflog des modifications de l'arbre de travail, donc sauvegardez tout ce dont vous pourriez avoir besoin au préalable |
| `git restore --staged <fichier>` | Zone de préparation (index) uniquement | Non | Désindexer un fichier ajouté par erreur, en conservant ses modifications dans l'arbre de travail | Sûr — l'arbre de travail n'est pas touché, rien n'est perdu |
| [`git revert <commit>`](https://git-scm.com/docs/git-revert) | Historique, en ajoutant un nouveau commit | Non — il enregistre un nouveau commit qui annule le changement au lieu de modifier les commits existants | Annuler l'effet d'un commit déjà poussé ou partagé | Sûr sur des branches partagées ; peut nécessiter une résolution de conflit si des commits ultérieurs ont touché les mêmes lignes |
| [`git reset [--soft\|--mixed\|--hard] <commit>`](https://git-scm.com/docs/git-reset) | `HEAD` et l'index ; `--hard` écrase aussi l'arbre de travail | Oui — déplace le pointeur de branche, supprimant des commits de son historique | Annuler des commits locaux non publiés, ou tout désindexer d'un coup | Ne jamais l'utiliser sur des commits que quelqu'un d'autre possède déjà ; les commits supprimés restent en général récupérables un moment via [`git reflog`](https://git-scm.com/docs/git-reflog), mais `--hard` abandonne aussi les modifications non committées de l'arbre de travail, que le reflog ne peut pas restaurer |

Les trois modes de `reset` diffèrent par ce qu'ils annulent : `--soft` déplace seulement `HEAD` (index et arbre de travail intacts — utile pour regrouper des commits récents avant de recommitter), `--mixed` (par défaut) réinitialise aussi l'index pour que rien ne soit préparé, et `--hard` écrase en plus l'arbre de travail pour l'aligner sur le commit cible.

## Pourquoi cet ordre de préférence compte

Préférez `restore` et `revert` par défaut, car ni l'un ni l'autre ne peut altérer un historique dont d'autres personnes dépendent. N'utilisez `reset` que lorsque vous êtes certain que les commits concernés sont encore privés — la documentation officielle est explicite : ne faites pas de reset supprimant des commits déjà donnés à quelqu'un d'autre, car son historique local divergera silencieusement du vôtre.

## Pièges courants

- Confondre `git restore <fichier>` (arbre de travail) et `git restore --staged <fichier>` (index) est l'erreur la plus courante — l'option change la couche affectée, pas seulement l'ampleur de l'annulation.
- `git reset --hard` est la seule commande de ce tableau capable de détruire du travail non committé sans aucun moyen de récupération. Lancez `git status` juste avant.
- Lancez `git status` avant et après toute commande de récupération — c'est le moyen le plus simple de confirmer que vous avez modifié la couche voulue.

## Exercice

Dans un dépôt d'exercice : (1) modifiez un fichier sans le préparer, puis abandonnez la modification avec `git restore` ; (2) préparez un fichier, puis désindexez-le avec `git restore --staged` et confirmez que la modification est toujours présente ; (3) committez un changement, puis annulez son effet avec `git revert` et confirmez qu'il existe désormais deux commits ; (4) faites un commit de plus, annulez-le localement avec `git reset --mixed HEAD~1`, confirmez avec `git status` que le changement est maintenant désindexé, puis retrouvez le commit supprimé avec `git reflog`.

## Références

- Manuel de Git — [git-restore](https://git-scm.com/docs/git-restore)
- Manuel de Git — [git-revert](https://git-scm.com/docs/git-revert)
- Manuel de Git — [git-reset](https://git-scm.com/docs/git-reset)
- Manuel de Git — [git-reflog](https://git-scm.com/docs/git-reflog)
- Pro Git (2e éd.) — [Reset Demystified](https://git-scm.com/book/en/v2/Git-Tools-Reset-Demystified)
