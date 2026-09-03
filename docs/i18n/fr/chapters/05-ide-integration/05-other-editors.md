# 5.5 Autres éditeurs

Les mêmes notions Git se retrouvent dans de nombreux autres outils. Ceci est une brève orientation, pas un guide complet pour chacun.

- **Xcode** possède un menu et un navigateur **Source Control** pour commit, push, pull, branche et résolution de conflits sur les projets macOS.
- **Eclipse** utilise le greffon **EGit**, qui ajoute une vue **Git Staging** et une vue **History**.
- **Sublime Merge** est un client Git autonome des créateurs de Sublime Text, avec un graphe de commits rapide et la préparation par hunk ; Sublime Text s'y intègre.
- **Vim et Neovim** utilisent couramment `vim-fugitive` pour les commandes et `gitsigns` (Neovim) ou `vim-gitgutter` pour les marques de marge.
- **Emacs** s'appuie sur **Magit**, une interface pilotée au clavier qui reprend la plupart des commandes Git.
- **GitHub Desktop** et **GitKraken** sont des clients graphiques qui s'associent bien à n'importe quel éditeur.

Quel que soit l'outil, il appelle Git. Si un panneau et `git status` divergent, rafraîchissez le panneau ou faites confiance à la ligne de commande.

## Exercice

Choisissez dans cette liste un outil que vous n'utilisez pas d'habitude. Ouvrez-y un dépôt d'exercice, faites un commit et vérifiez le résultat avec `git log --oneline` dans un terminal.
