# 2.2 Configurer l'identité et les valeurs par défaut

Définissez le nom et l'adresse e-mail que Git enregistrera dans les nouveaux commits :

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
```

`user.name` et `user.email` sont enregistrés dans chaque commit que vous créez et ne peuvent pas être modifiés rétroactivement sans réécrire l'historique ; définissez-les donc avant votre premier commit. `init.defaultBranch` n'affecte que les dépôts créés ensuite avec `git init` ; il ne renomme pas les branches des dépôts que vous avez déjà.

Examinez la configuration effective, et de quel fichier provient chaque valeur, avec :

```bash
git config --list --show-origin
```

## Niveaux de portée de la configuration

Git lit la configuration dans plusieurs fichiers et les fusionne, une portée plus spécifique l'emportant sur une portée moins spécifique. De la précédence la plus faible à la plus forte :

| Portée | Option | S'applique à | Emplacement typique |
| --- | --- | --- | --- |
| Système | `--system` | Tous les utilisateurs de la machine | `/etc/gitconfig` (Linux/macOS) ; `C:\ProgramData\Git\config` (Windows) |
| Globale | `--global` | L'utilisateur courant, tous les dépôts | `~/.gitconfig` ou `$XDG_CONFIG_HOME/git/config` (Linux/macOS) ; `%USERPROFILE%\.gitconfig` (Windows) |
| Locale | `--local` (par défaut) | Le dépôt courant uniquement | `.git/config` dans le dépôt |
| Worktree | `--worktree` | Un worktree d'un dépôt à plusieurs worktrees | `.git/config.worktree` (utilisé seulement si `extensions.worktreeConfig` est activé) |

La portée locale prime sur la globale, qui prime sur le système ; le worktree, s'il est activé, prime sur les trois. Exécuter `git config` sans option de portée écrit dans `--local` ; ne le faites donc depuis un dépôt que si vous voulez définir une valeur pour ce dépôt seul. Voir la [référence `git-config`](https://git-scm.com/docs/git-config#FILES) pour les règles complètes de découverte des fichiers, y compris la résolution de `$XDG_CONFIG_HOME`.

## Configuration de l'éditeur

Git ouvre un éditeur externe pour les messages de commit, le rebase interactif et des tâches similaires, contrôlé par `core.editor`. Ce cours détaille la configuration de l'éditeur et de l'outil de fusion dans [Configuration de l'éditeur et de l'outil de fusion](../05-ide-integration/07-editor-and-mergetool-config.md) ; un exemple minimal :

```bash
git config --global core.editor "code --wait"
```

## Pièges courants

- **Oublier `user.email`.** Sans lui, Git refuse le commit ou utilise une adresse devinée à partir de votre nom d'utilisateur système et du nom de machine, ce qui produit des commits attribués à la mauvaise personne — un problème particulièrement gênant sur une machine partagée ou en CI. Vérifiez avec `git config --get user.email` avant votre premier commit dans un nouvel environnement.
- **Définir l'identité seulement globalement sur une machine partagée.** Si plusieurs personnes ou rôles utilisent le même compte (par exemple un exécuteur CI), définissez `user.name`/`user.email` avec `--local` par dépôt plutôt que de dépendre d'une seule identité globale.
- **Confondre la précédence des portées.** Une valeur définie avec `--local` l'emporte toujours sur la même clé définie avec `--global`, même si la valeur globale a été définie plus récemment. Utilisez `git config --list --show-origin` quand un réglage ne semble pas prendre effet.

## Exercice

Exécutez `git config --global user.name "Your Name"`, `git config --global user.email "you@example.com"` et `git config --global init.defaultBranch main`. Puis exécutez `git config --list --show-origin` et vérifiez que les trois valeurs apparaissent avec votre fichier de configuration global comme origine.

## Références

Voici les sources officielles utilisées pour cette page :

- Manuel de référence de Git — [git-config](https://git-scm.com/docs/git-config)
- Pro Git (2e édition) — [Paramétrage à la première utilisation de Git](https://git-scm.com/book/fr/v2/D%c3%a9marrage-rapide-Param%c3%a9trage-%c3%a0-la-premi%c3%a8re-utilisation-de-Git)
- Pro Git (2e édition) — [Configuration de Git](https://git-scm.com/book/fr/v2/Personnalisation-de-Git-Configuration-de-Git)
