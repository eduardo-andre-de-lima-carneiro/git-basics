# 5.2 Visual Studio Code

Visual Studio Code fournit la [prise en charge du contrôle de version Git](https://code.visualstudio.com/docs/sourcecontrol/overview), activée dès que Git est installé et présent dans le `PATH`.

## Flux principal

- La vue **Source Control** (Ctrl/Cmd+Maj+G) liste les changements. Survolez un fichier et cliquez sur **+** pour le préparer, ou préparez un seul bloc depuis l'éditeur de diff.
- Saisissez un message dans la zone de commit et appuyez sur Ctrl/Cmd+Entrée pour valider.
- Le nom de la branche dans la barre d'état, en bas à gauche, ouvre le menu de changement et de création de branches.
- **Sync Changes** exécute `git pull` puis `git push` pour la branche courante.
- La vue **Timeline**, en bas de l'Explorateur, montre l'historique des commits d'un fichier.

## Utiliser VS Code comme éditeur de Git

```bash
git config --global core.editor "code --wait"
```

L'option `--wait` fait attendre Git jusqu'à la fermeture de l'onglet, ce qui est requis pour les messages de commit et le rebase interactif.

## Extensions utiles

- [**GitLens**](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) ajoute le blame ligne par ligne, un graphe des commits et la navigation dans l'historique.
- [**GitHub Pull Requests and Issues**](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github) permet de créer, relire et fusionner des pull requests sans quitter l'éditeur.

N'installez des extensions que d'éditeurs de confiance et vérifiez les permissions qu'elles demandent.

## Exercice

Définissez `core.editor` sur `code --wait`, puis exécutez `git commit` sans `-m` dans un dépôt d'exercice. Rédigez le message dans l'onglet VS Code, enregistrez et fermez-le ; vérifiez le commit avec `git log --oneline`.

## Références

- Visual Studio Code — [Using Git source control in VS Code](https://code.visualstudio.com/docs/sourcecontrol/overview)
- Visual Studio Marketplace — [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
- Visual Studio Marketplace — [GitHub Pull Requests and Issues](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github)
- Manuel de Git — [git-config](https://git-scm.com/docs/git-config)
