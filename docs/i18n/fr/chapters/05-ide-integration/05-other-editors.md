# 5.5 Autres éditeurs

Les mêmes notions Git se retrouvent dans de nombreux autres outils. Ceci est une brève orientation, pas un guide complet pour chacun.

- [**Xcode**](https://developer.apple.com/documentation/xcode/source-control-management) possède un menu et un navigateur **Source Control** pour commit, push, pull, branche et résolution de conflits sur les projets macOS.
- **Eclipse** utilise le greffon [**EGit**](https://wiki.eclipse.org/EGit/User_Guide), qui ajoute une vue **Git Staging** et une vue **History**.
- [**Sublime Merge**](https://www.sublimemerge.com/docs/) est un client Git autonome des créateurs de Sublime Text, avec un graphe de commits rapide et la préparation par hunk ; Sublime Text s'y intègre.
- **Vim et Neovim** utilisent couramment [`vim-fugitive`](https://github.com/tpope/vim-fugitive) pour les commandes et [`gitsigns.nvim`](https://github.com/lewis6991/gitsigns.nvim) (Neovim) ou `vim-gitgutter` pour les marques de marge.
- **Emacs** s'appuie sur [**Magit**](https://magit.vc/), une interface pilotée au clavier qui reprend la plupart des commandes Git.
- [**GitHub Desktop**](https://docs.github.com/fr/desktop) et **GitKraken** sont des clients graphiques qui s'associent bien à n'importe quel éditeur.

Quel que soit l'outil, il appelle Git. Si un panneau et `git status` divergent, rafraîchissez le panneau ou faites confiance à la ligne de commande.

## Exercice

Choisissez dans cette liste un outil que vous n'utilisez pas d'habitude. Ouvrez-y un dépôt d'exercice, faites un commit et vérifiez le résultat avec `git log --oneline` dans un terminal.

## Références

- Apple Developer — [Source control management in Xcode](https://developer.apple.com/documentation/xcode/source-control-management)
- Eclipse — [EGit User Guide](https://wiki.eclipse.org/EGit/User_Guide)
- [Documentation de Sublime Merge](https://www.sublimemerge.com/docs/)
- GitHub — [tpope/vim-fugitive](https://github.com/tpope/vim-fugitive)
- GitHub — [lewis6991/gitsigns.nvim](https://github.com/lewis6991/gitsigns.nvim)
- [Magit — a Git porcelain inside Emacs](https://magit.vc/)
- GitHub Docs — [GitHub Desktop](https://docs.github.com/fr/desktop)
