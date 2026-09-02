# 1.4 Le modèle mental de Git

Pensez à trois espaces :

1. Arbre de travail : fichiers actuellement modifiés.
2. Zone de staging : instantané en cours de préparation.
3. Historique du dépôt : instantanés validés.

Le flux de base est `edit -> git add -> git commit`. `git status` affiche les différences entre ces espaces et devrait être votre commande de diagnostic la plus fréquente.
