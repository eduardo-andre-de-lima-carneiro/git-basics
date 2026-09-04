# 3.4 Dépôts distants et synchronisation

Synchronisez explicitement :

```bash
git fetch origin
git log --oneline main..origin/main
git push -u origin feature/example
```

## Fetch, pull et push ne sont pas la même opération

- [`git fetch`](https://git-scm.com/docs/git-fetch) télécharge les commits et met à jour vos références de suivi distant (`origin/main`, par exemple), mais ne touche jamais à votre arbre de travail ni à vos branches locales. Il est toujours sûr à exécuter.
- `git log --oneline main..origin/main` montre ensuite exactement quels commits existent sur `origin/main` mais pas encore sur votre `main` locale — une étape de relecture avant d'intégrer quoi que ce soit.
- [`git pull`](https://git-scm.com/docs/git-pull) exécute `git fetch` puis intègre le résultat dans votre branche courante. **Son mode d'intégration par défaut est `--ff-only`** : si votre branche locale a divergé du distant (les deux côtés ont des commits nouveaux), un simple `git pull` échoue au lieu de créer silencieusement un commit de fusion. Passez `--rebase` pour rejouer vos commits locaux par-dessus l'historique récupéré au lieu de fusionner, ou `--no-rebase` pour autoriser un commit de fusion.
- [`git push -u origin <branche>`](https://git-scm.com/docs/git-push) pousse la branche et enregistre la relation de suivi amont (`branch.<nom>.remote` / `branch.<nom>.merge`) en une seule étape. Ensuite, un simple `git push` et `git pull` sur cette branche savent quelle branche distante utiliser sans avoir à la nommer à nouveau.

## Pièges courants

- `git pull --rebase` réécrit les commits qu'il rejoue. C'est sûr pour des commits que vous seul possédez — c'est risqué dès que quelqu'un d'autre les a déjà récupérés, car son historique et le vôtre ne correspondront plus. Réservez `--rebase` aux branches que vous n'avez pas encore partagées, et préférez une fusion (ou `git pull --no-rebase`) une fois que d'autres dépendent de vos commits.
- Comme le comportement par défaut de `git pull` est désormais d'échouer plutôt que de fusionner en cas de divergence, ne présumez pas qu'un ancien tutoriel décrivant « pull fusionne toujours » correspond encore à votre version de Git — vérifiez `pull.rebase` et `pull.ff` dans `git config --list` si le comportement semble incohérent d'une machine à l'autre.
- Faites un fetch avant de pousser sur une branche partagée ; pousser sans avoir vérifié `main..origin/main` risque un push rejeté ou un conflit évitable.

## Exercice

Dans un dépôt d'exercice avec un distant configuré, lancez `git fetch origin`, puis `git log --oneline main..origin/main` pour voir ce qui a changé à distance avant de toucher à quoi que ce soit localement. Poussez une nouvelle branche avec `git push -u origin <branche>`, puis confirmez la relation de suivi avec `git branch -vv`.

## Références

- Manuel de Git — [git-fetch](https://git-scm.com/docs/git-fetch)
- Manuel de Git — [git-pull](https://git-scm.com/docs/git-pull)
- Manuel de Git — [git-push](https://git-scm.com/docs/git-push)
- Pro Git (2e éd.) — [Working with Remotes](https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes)
