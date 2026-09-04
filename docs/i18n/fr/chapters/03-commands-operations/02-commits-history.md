# 3.2 Commits et historique

Voici quelques commandes d'inspection utiles :

```bash
git log --oneline --decorate --graph
git show <commit>
git diff <commit-a> <commit-b>
```

## Lire la sortie

- [`git log --oneline`](https://git-scm.com/docs/git-log) est un raccourci pour `--pretty=oneline --abbrev-commit` : une ligne par commit, avec un hash court plutôt que le hash complet de 40 caractères.
- `--decorate` affiche les noms de référence — pointes de branches et tags — qui pointent vers chaque commit affiché, pour voir où se trouvent actuellement `main`, `HEAD` ou un tag dans le graphe.
- `--graph` dessine un graphe en texte à gauche de la sortie, montrant comment les branches ont divergé puis fusionné ; c'est surtout utile combiné à `--oneline --decorate`.
- [`git show <commit>`](https://git-scm.com/docs/git-show) affiche le message de log d'un seul commit accompagné de son diff complet — le moyen le plus rapide d'inspecter un changement sans lister l'historique autour.
- `git diff <commit-a> <commit-b>` compare directement deux commits arbitraires, indépendamment de la structure de branches qui les sépare.

## Commits ciblés et messages

Préférez des commits ciblés représentant un seul changement logique — un commit qui mélange une correction de bug et une passe de formatage est plus difficile à relire, annuler, ou suivre plus tard avec `git log --follow`. L'historique est plus facile à parcourir quand les messages de commit utilisent une description impérative et précise (« Corrige la vérification de nullité dans le parseur », pas « corrections »).

Une convention largement utilisée pour structurer ce message est [Conventional Commits](https://www.conventionalcommits.org/fr/v1.0.0/) : un préfixe `type(scope): description` (`fix:`, `feat:`, `docs:`, …) qui rend l'historique facile à parcourir avec `git log --oneline` et permet à des outils de générer automatiquement des changelogs. C'est facultatif ici, mais cela vaut la peine si votre projet n'a pas encore de convention de message.

## Pièges courants

- Un hash abrégé issu de `--oneline` n'est sans ambiguïté que par rapport aux objets présents actuellement dans votre dépôt ; ne le figez pas dans une documentation censée survivre à la branche.
- Réécrire le message ou le contenu d'un commit déjà poussé sur une branche partagée nécessite un force-push et une coordination avec quiconque a déjà récupéré ce commit — voir [3.5 Annuler des changements en toute sécurité](05-undo.md) avant de le faire.

## Exercice

Dans un dépôt d'exercice, faites trois petits commits. Lancez `git log --oneline --decorate --graph --all` et identifiez les noms de référence affichés. Utilisez `git show` sur le commit du milieu pour ne voir que son diff, puis `git diff` entre le premier et le dernier commit pour voir le changement cumulé.

## Références

- Manuel de Git — [git-log](https://git-scm.com/docs/git-log)
- Manuel de Git — [git-show](https://git-scm.com/docs/git-show)
- Manuel de Git — [git-diff](https://git-scm.com/docs/git-diff)
- Pro Git (2e éd.) — [Viewing the Commit History](https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History)
- [Conventional Commits](https://www.conventionalcommits.org/fr/v1.0.0/)
