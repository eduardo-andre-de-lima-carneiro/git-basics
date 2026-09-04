# 3.1 Le flux de travail quotidien

Chaque changement passe par trois endroits avant d'être en sécurité : l'**arbre de travail** (working tree, les fichiers que vous éditez), la **zone de préparation** ou index (ce qui ira dans le prochain commit) et l'**historique du dépôt** (les commits déjà enregistrés). Utilisez une petite boucle observable pour vous déplacer délibérément entre ces trois endroits :

```bash
git status
git add path/to/file
git diff --staged
git commit -m "Describe the change"
git status
```

## Ce que chaque commande vérifie réellement

- [`git status`](https://git-scm.com/docs/git-status) rapporte trois groupes : les changements préparés pour le commit, les changements non préparés, et les fichiers non suivis. Savoir dans quel groupe se trouve un fichier vous dit exactement ce que le prochain `git add` ou `git commit` lui fera.
- `git diff` sans argument compare l'arbre de travail à l'index — il montre les modifications que vous *pourriez* préparer mais que vous n'avez pas encore préparées.
- `git diff --staged` (synonyme de `--cached`) compare l'index au `HEAD` — il montre exactement ce que contiendra le prochain commit, ce qui explique pourquoi le relire avant `git commit` permet de repérer des erreurs que `git diff` seul manquerait.
- [`git add`](https://git-scm.com/docs/git-add) copie le contenu du fichier dans l'index. C'est un instantané pris au moment où vous l'exécutez : éditez le fichier à nouveau ensuite, et il faudra relancer `git add` pour inclure ces nouvelles modifications.

## Préparer une partie d'un fichier

`git add path/to/file` prépare le fichier entier. Quand seule une partie de vos modifications appartient à ce commit, préparez des blocs (hunks) individuels :

```bash
git add -p path/to/file
```

Cela parcourt chaque bloc modifié et demande s'il faut le préparer, ce qui permet de répartir des modifications non liées dans le même fichier sur des commits distincts et ciblés.

## Pièges courants

- `git add .` prépare tout ce qui se trouve dans le répertoire courant, y compris des fichiers modifiés pour des raisons sans rapport (traces de débogage, configuration locale, fichiers résiduels de l'éditeur). Préférez nommer les chemins explicitement, ou utilisez `git add -p`, et gardez hors du dépôt les fichiers qui ne doivent jamais être préparés grâce à [`.gitignore`](https://git-scm.com/docs/gitignore).
- Committer sans vérifier `git diff --staged` est la façon la plus courante d'inclure des changements sans rapport dans un commit — la zone de préparation peut contenir, en silence, plus que ce dont vous vous souvenez avoir ajouté.

## Exercice

Dans un dépôt d'exercice, modifiez deux fichiers sans rapport. Préparez un seul bloc d'un seul fichier avec `git add -p`, confirmez avec `git status` et `git diff --staged` que la zone de préparation contient exactement ce bloc, committez-le, puis vérifiez que les autres modifications sont toujours intactes avec `git status`.

## Références

- Manuel de Git — [git-status](https://git-scm.com/docs/git-status)
- Manuel de Git — [git-diff](https://git-scm.com/docs/git-diff)
- Manuel de Git — [git-add](https://git-scm.com/docs/git-add)
- Manuel de Git — [gitignore](https://git-scm.com/docs/gitignore)
- Pro Git (2e éd.) — [Recording Changes to the Repository](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository)
