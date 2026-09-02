# 1.3 Le modèle distribué de Git

Un dépôt individuel possède généralement un arbre de travail, un historique local et, éventuellement, des dépôts distants. Un dépôt distant est un point de collaboration, et non la définition de Git lui-même.

Les opérations courantes ont des objectifs distincts :

- `clone` copie un dépôt.
- `fetch` télécharge l'historique distant sans modifier le travail local.
- `pull` récupère et intègre les changements distants.
- `push` publie les commits locaux.
