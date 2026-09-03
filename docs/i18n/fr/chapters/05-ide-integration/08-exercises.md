# 5.8 Exercices pratiques

Réalisez-les dans un dépôt temporaire, en utilisant votre éditeur pour les actions Git et un terminal pour vérifier.

1. Préparez un seul hunk (pas le fichier entier) depuis la vue de diff de l'éditeur, validez-le et vérifiez avec `git show`.
2. Créez une branche et basculez dessus depuis la barre d'état, faites un commit, puis revenez en arrière.
3. Configurez votre éditeur comme `core.editor`, puis exécutez `git commit` sans `-m` et rédigez le message dans l'éditeur.
4. Créez un conflit de fusion sur une ligne, résolvez-le avec la vue de fusion à trois panneaux de l'éditeur et terminez la fusion.
5. Configurez `merge.tool` et refaites l'exercice 4 en utilisant `git mergetool` au lieu du panneau intégré.
6. Faites un commit signé depuis l'éditeur et vérifiez-le avec `git log --show-signature`.

Pour chaque exercice, notez l'action réalisée dans l'éditeur et la sortie de commande qui a confirmé le résultat.
