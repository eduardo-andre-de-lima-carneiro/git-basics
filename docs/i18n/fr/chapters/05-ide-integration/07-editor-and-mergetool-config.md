# 5.7 Configuration de l'éditeur et de l'outil de fusion

Git utilise trois réglages pour confier du travail à un programme externe : [`core.editor`](https://git-scm.com/docs/git-config) pour le texte, [`merge.tool`](https://git-scm.com/docs/git-mergetool) pour la résolution des conflits et [`diff.tool`](https://git-scm.com/docs/git-difftool) pour visualiser les changements.

## Définir l'éditeur de commit

```bash
git config --global core.editor "code --wait"     # VS Code
git config --global core.editor "codium --wait"   # VSCodium
```

Pour un IDE JetBrains, utilisez son lanceur en ligne de commande, par exemple `git config --global core.editor "idea --wait"` une fois le lanceur installé.

## Configurer un outil de fusion

```bash
git config --global merge.tool vscode
git config --global mergetool.vscode.cmd 'code --wait --merge $REMOTE $LOCAL $BASE $MERGED'
git config --global mergetool.keepBackup false
```

Quand un conflit survient, exécutez :

```bash
git mergetool
```

Git ouvre l'outil configuré pour chaque fichier en conflit. Après avoir enregistré et fermé, marquez le résultat avec `git add` et poursuivez la fusion ou le rebase.

## Configurer un outil de diff

```bash
git config --global diff.tool vscode
git config --global difftool.vscode.cmd 'code --wait --diff $LOCAL $REMOTE'
git difftool HEAD~1 HEAD
```

Visual Studio et les IDE JetBrains s'enregistrent aussi comme outils de fusion et de diff lors de l'installation sur la plupart des plateformes ; consultez leur documentation pour le nom exact de `merge.tool`.

## Exercice

Configurez `merge.tool`, créez un conflit dans un dépôt d'exercice en modifiant la même ligne sur deux branches, exécutez `git mergetool`, résolvez-le dans l'éditeur et terminez avec `git commit`.

## Références

- Manuel de Git — [git-config](https://git-scm.com/docs/git-config) (`core.editor`, `merge.tool`, `diff.tool`)
- Manuel de Git — [git-mergetool](https://git-scm.com/docs/git-mergetool)
- Manuel de Git — [git-difftool](https://git-scm.com/docs/git-difftool)
- Pro Git (2e éd.) — [Git Configuration: External Merge and Diff Tools](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration)
