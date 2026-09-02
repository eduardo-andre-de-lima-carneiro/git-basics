# 3.3 Branches et collaboration

Les branches sont des noms mobiles qui pointent vers des commits. Développez votre travail à l'écart de la base partagée :

```bash
git switch -c feature/example
git switch main
git merge feature/example
```

Avant la fusion, examinez l'historique et résolvez les conflits avec attention. Un conflit demande une décision humaine; ce n'est pas une erreur de commande à dissimuler.
