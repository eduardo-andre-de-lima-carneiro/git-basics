# 3.6 Exercices pratiques

Réalisez ces exercices dans un répertoire temporaire :

1. Initialisez un dépôt, créez un fichier et faites deux commits ciblés. Entre les commits, utilisez `git status` et `git diff --staged` pour confirmer exactement ce que chaque commit va contenir avant de lancer `git commit`.
2. Créez une branche, modifiez la même ligne différemment sur les deux branches, et résolvez le conflit de fusion délibérément plutôt que d'accepter automatiquement un des deux côtés.
3. Ajoutez un distant, récupérez son historique, et comparez les branches locale et distante avec `git log --oneline main..origin/main` avant d'intégrer quoi que ce soit.
4. Entraînez-vous à restaurer une modification non préparée avec `git restore`, à désindexer un fichier avec `git restore --staged`, et à annuler un commit publié avec `git revert` — en utilisant le [tableau de décision de la section 3.5](05-undo.md) pour choisir la bonne commande dans chaque cas.

Pour chaque exercice, notez la commande utilisée, l'état avant celle-ci, et le résultat affiché par `git status`.

## Références

- Manuel de Git — [git-status](https://git-scm.com/docs/git-status)
- Manuel de Git — [git-log](https://git-scm.com/docs/git-log)
- Manuel de Git — [git-restore](https://git-scm.com/docs/git-restore)
- Manuel de Git — [git-revert](https://git-scm.com/docs/git-revert)
