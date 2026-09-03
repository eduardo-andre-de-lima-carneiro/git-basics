# 5.3 Visual Studio

Visual Studio (l'IDE complet pour Windows, pas VS Code) intègre la prise en charge de Git via le menu **Git** et deux fenêtres ancrées.

## Flux principal

- **Git > Clone Repository** ou **Create Git Repository** démarre un dépôt, en proposant un modèle de `.gitignore` et de licence.
- La fenêtre **Git Changes** montre les changements non préparés et préparés, la zone de message de commit et les boutons **Commit** / **Commit and Push**.
- La fenêtre **Git Repository** montre le graphe des branches, les commits entrants et sortants, et permet fetch, pull, push, merge, rebase et la gestion des branches.
- Le sélecteur de branche de la barre d'état change et crée des branches.
- Les conflits de fusion s'ouvrent dans le **Merge Editor**, avec des cases pour prendre les changements entrants, courants ou les deux.

## Authentification

Visual Studio utilise **Git Credential Manager**, installé avec lui, pour stocker les jetons des plateformes dans le Windows Credential Store. Connectez-vous via **Git > Settings** ou le sélecteur de compte ; évitez de mettre des identifiants dans les URL de dépôts distants.

## Note sur Team Explorer

Les anciennes versions faisaient passer Git par **Team Explorer**. Les versions actuelles utilisent le menu Git dédié et les fenêtres décrites ci-dessus ; c'est cette expérience plus récente qu'il faut apprendre.

## Exercice

Dans un dépôt d'exercice ouvert dans Visual Studio, faites un changement, préparez-le dans **Git Changes**, validez le commit, puis ouvrez la fenêtre **Git Repository** pour vérifier que le nouveau commit apparaît dans le graphe.
