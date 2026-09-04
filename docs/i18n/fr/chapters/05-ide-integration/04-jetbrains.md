# 5.4 IDE JetBrains

IntelliJ IDEA, PyCharm, WebStorm, PhpStorm, Rider, GoLand et Android Studio partagent la même [intégration Git](https://www.jetbrains.com/help/idea/using-git-integration.html) sous le menu **Git** (ou **VCS**).

## Flux principal

- **Git > Clone** crée le dépôt local ; **VCS > Enable Version Control Integration** en démarre un dans un projet existant.
- La [fenêtre **Commit**](https://www.jetbrains.com/help/idea/commit-and-push-changes.html) liste les changements, les regroupe en changelists et prépare des fichiers ou des hunks. Une zone de message et les boutons **Commit** / **Commit and Push** se trouvent en dessous.
- L'onglet **Log** de la fenêtre **Git** montre le graphe complet des branches, avec un filtrage par branche, utilisateur et chemin.
- Le widget de branche de la barre d'état change, crée et compare des branches.
- **Update Project** exécute fetch plus merge ou rebase, selon votre réglage.
- Les conflits ouvrent un résolveur à trois panneaux avec **Accept Left**, **Accept Right** et l'édition manuelle dans le panneau de résultat.

## Rebase interactif

Faites un clic droit sur un commit dans le **Log** et choisissez **Interactively Rebase from Here** pour réordonner, fusionner (squash), modifier ou supprimer des commits via une boîte de dialogue, plutôt qu'un fichier texte.

## Shelve et stash

**Shelve** est une fonction JetBrains qui met des changements de côté dans l'IDE. **Stash** est la commande Git. Les deux fonctionnent ; préférez stash si des collègues sur d'autres éditeurs doivent voir le même état enregistré via Git.

## Exercice

Dans un dépôt d'exercice, faites deux modifications sans rapport, séparez-les en deux changelists dans la fenêtre **Commit** et validez-les séparément. Vérifiez les deux commits dans l'onglet **Log**.

## Références

- JetBrains — [Git integration in IntelliJ IDEA](https://www.jetbrains.com/help/idea/using-git-integration.html)
- JetBrains — [Commit and push changes](https://www.jetbrains.com/help/idea/commit-and-push-changes.html)
- JetBrains — [Edit Git project history (rebase interactif)](https://www.jetbrains.com/help/idea/edit-project-history.html)
- JetBrains — [Resolve Git conflicts](https://www.jetbrains.com/help/idea/resolve-conflicts.html)
