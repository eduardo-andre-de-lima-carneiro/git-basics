# 3.3 Branches et collaboration

Les branches sont des noms mobiles pointant vers des commits. Créez votre travail à l'écart de la base partagée :

```bash
git switch -c feature/example
git switch main
git merge feature/example
```

## Ce que font vraiment `switch -c` et `merge`

- [`git switch -c <nom>`](https://git-scm.com/docs/git-switch) crée la nouvelle branche et bascule dessus en une seule étape transactionnelle — l'équivalent de `git branch <nom>` suivi de `git switch <nom>`, sauf que la branche n'est jamais laissée à moitié créée si le changement échoue.
- [`git merge`](https://git-scm.com/docs/git-merge) se comporte différemment selon la forme de l'historique :
  - **Fast-forward :** si la pointe de la branche courante est un ancêtre de la branche fusionnée — aucun commit local n'a divergé — Git déplace simplement le pointeur de branche vers l'avant. Aucun commit de fusion n'est créé.
  - **Commit de fusion :** si les deux branches ont chacune des commits que l'autre n'a pas, Git crée un nouveau commit à deux parents pour les combiner. Passez `--no-ff` pour forcer un commit de fusion même quand un fast-forward serait possible, si vous voulez garder l'existence de la branche visible dans l'historique.

## Un conflit est une décision, pas un échec

Avant de fusionner, examinez l'historique et résolvez les conflits délibérément. Un conflit signifie que les mêmes lignes ont changé des deux côtés et que Git ne peut pas deviner quelle version — ou quelle combinaison — est correcte ; c'est une demande de décision humaine, pas un échec de commande à masquer en acceptant aveuglément un côté.

## Pièges courants

- Les branches à longue durée de vie accumulent de la divergence et produisent des conflits plus gros et plus difficiles à résoudre. Fusionner `main` périodiquement dans la branche de fonctionnalité (ou la rebaser, pour du travail non encore publié) garde la fusion finale petite.
- `git merge --no-ff` par rapport à un simple fast-forward change durablement l'apparence de votre historique — mettez-vous d'accord sur une convention avec l'équipe plutôt que de mélanger les deux de façon incohérente.

## Exercice

Dans un dépôt d'exercice, créez une branche, faites un commit, et fusionnez-la dans `main` sans aucun autre commit entre les deux — confirmez avec `git log --oneline --graph` qu'aucun commit de fusion n'a été créé (un fast-forward). Créez ensuite une seconde branche, faites aussi un commit sur `main`, et fusionnez à nouveau — confirmez que cette fois un commit de fusion apparaît.

## Références

- Manuel de Git — [git-switch](https://git-scm.com/docs/git-switch)
- Manuel de Git — [git-branch](https://git-scm.com/docs/git-branch)
- Manuel de Git — [git-merge](https://git-scm.com/docs/git-merge)
- Pro Git (2e éd.) — [Branches in a Nutshell](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
