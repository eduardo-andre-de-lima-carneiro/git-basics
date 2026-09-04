# 5.1 Fondamentaux de l'intégration aux IDE

L'intégration Git d'un éditeur est une vue sur le même dépôt que celui utilisé en ligne de commande. Elle exécute `git status`, `git diff` et `git log` à votre place et transforme les actions courantes en boutons, marques de marge et panneaux.

## Ce que l'intégration apporte

- Un panneau de contrôle de version qui liste les fichiers modifiés, préparés et non suivis.
- Des marques de marge qui montrent les lignes ajoutées, modifiées et supprimées.
- Un diff visuel d'un fichier ou d'un seul bloc de lignes (un « hunk »).
- Une zone de commit pour le message, la préparation se faisant en cliquant sur des fichiers ou des hunks.
- Un indicateur de branche dans la barre d'état pour changer et créer des branches.
- Une vue à trois panneaux pour résoudre les conflits de fusion.

## Quand utiliser encore le terminal

Passez à la ligne de commande lorsque vous avez besoin d'un contrôle précis ou d'une opération peu courante : détails d'un rebase interactif, `git reflog`, `git bisect`, filtres `git log` personnalisés ou scripts. L'éditeur et le terminal agissent sur le même répertoire `.git`, vous pouvez donc passer de l'un à l'autre librement.

## Mise en place commune

- Configurez l'identité une seule fois avec [`git config`](https://git-scm.com/docs/git-config) `--global user.name` et `user.email` (voir [2.2 Configurer l'identité et les valeurs par défaut](../02-installation-configuration/02-configure.md)).
- Laissez un [credential helper](https://git-scm.com/docs/gitcredentials) ou le trousseau du système stocker les jetons pour que l'éditeur ne les demande pas à chaque push.
- Décidez si les dossiers propres à l'éditeur, comme `.vscode/` ou `.idea/`, doivent figurer dans le dépôt ; sinon, ajoutez-les au [`.gitignore`](https://git-scm.com/docs/gitignore).
- Gardez la [signature des commits](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work) (SSH ou GPG) configurée dans Git lui-même pour que les commits faits depuis l'éditeur soient également signés.

## Exercice

Ouvrez un dépôt d'exercice existant dans votre éditeur. Modifiez une ligne dans un fichier, puis vérifiez que le panneau de contrôle de version de l'éditeur et `git status` dans un terminal signalent le même changement.

## Références

- Manuel de Git — [git-config](https://git-scm.com/docs/git-config)
- Manuel de Git — [gitcredentials](https://git-scm.com/docs/gitcredentials)
- Manuel de Git — [gitignore](https://git-scm.com/docs/gitignore)
- Pro Git (2e éd.) — [Signing Your Work](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work)
