# 1.4 Le modèle mental de Git

Pensez à trois espaces :

1. Arbre de travail : fichiers actuellement modifiés.
2. Zone de staging : instantané en cours de préparation.
3. Historique du dépôt : instantanés validés.

Le flux de base est `edit -> git add -> git commit`. `git status` affiche les différences entre ces espaces et devrait être votre commande de diagnostic la plus fréquente.

## Pourquoi le staging est une étape distincte

La zone de staging (aussi appelée l'index) permet de composer un commit à partir d'une partie seulement de vos changements — par exemple, mettre en staging un correctif terminé avec `git add`, tout en laissant une modification distincte, encore en cours, hors staging dans l'arbre de travail. Ce qui finit dans le commit est exactement ce qui était en staging au moment où vous avez exécuté `git commit`, pas l'état du fichier ensuite. Voir [Enregistrer des modifications dans le dépôt](https://git-scm.com/book/fr/v2/Les-bases-de-Git-Enregistrer-des-modifications-dans-le-d%c3%a9p%c3%b4t) dans le livre Pro Git.

## Pièges courants

- **Un commit n'est pas un diff.** Chaque commit pointe vers un instantané complet de l'arborescence du projet, pas vers une delta par rapport au commit précédent ; Git calcule les diffs à la demande en comparant deux instantanés. C'est pourquoi extraire un ancien commit est un remplacement direct de l'arborescence des fichiers, plutôt que de rejouer une chaîne de patches. Voir [Rudiments de Git](https://git-scm.com/book/fr/v2/D%C3%A9marrage-rapide-Rudiments-de-Git).
- **Staged et modified ne sont pas le même état.** Si vous modifiez à nouveau un fichier après `git add`, `git status` l'affichera à la fois comme staged et modified — la copie en staging reste figée au moment où vous avez exécuté `add`, et un second `git add` est nécessaire pour la mettre à jour.

## Mise en pratique

Modifiez un fichier, exécutez `git add`, puis modifiez à nouveau le même fichier sans le remettre en staging. Exécutez `git status`, puis `git diff` (arbre de travail vs. staging) et `git diff --staged` (staging vs. dernier commit), pour voir les trois espaces diverger.

## Références

Cette page s'appuie sur les sources officielles suivantes :

- Pro Git (2ᵉ éd.) — [Enregistrer des modifications dans le dépôt](https://git-scm.com/book/fr/v2/Les-bases-de-Git-Enregistrer-des-modifications-dans-le-d%c3%a9p%c3%b4t)
- Pro Git (2ᵉ éd.) — [Rudiments de Git](https://git-scm.com/book/fr/v2/D%C3%A9marrage-rapide-Rudiments-de-Git)
- Manuel de référence de Git — [git-status](https://git-scm.com/docs/git-status/fr)
- Manuel de référence de Git — [git-diff](https://git-scm.com/docs/git-diff/fr)
