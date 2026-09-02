# 3.5 Annuler des changements en toute sécurité

Choisissez la commande en fonction de l'endroit où se trouve le changement indésirable :

- Arbre de travail : `git restore <file>`. Cette commande supprime définitivement les changements non validés de l'arbre de travail ; sauvegardez d'abord ce qui pourrait être nécessaire.
- Zone de staging : `git restore --staged <file>`.
- Historique publié : préférez `git revert <commit>`.
- Commit local non publié : n'envisagez `git reset` qu'après avoir vérifié les conséquences.

Exécutez `git status` avant et après les commandes de récupération.
