# 4.1 Fondamentaux de l'intégration

Les plateformes hébergées ajoutent des services de collaboration et de livraison autour d'un dépôt Git. Les commandes locales restent familières; la plateforme fournit l'identité, les permissions, la révision, l'automatisation et la visibilité sur le projet.

## Le flux commun

1. Créez ou sélectionnez un dépôt distant.
2. Connectez le dépôt local avec `git remote add origin <repository-url>`.
3. Envoyez une branche avec `git push -u origin <branch-name>`.
4. Ouvrez une pull request ou une merge request pour la révision.
5. Laissez les vérifications obligatoires s'exécuter avant la fusion.
6. Supprimez la branche de courte durée une fois la modification intégrée.

## Choisir HTTPS ou SSH

HTTPS est simple pour commencer et utilise normalement un personal access token à la place du mot de passe du compte. SSH utilise une paire de clés et convient bien au travail fréquent en ligne de commande. Ne placez jamais de tokens, de clés privées ou d'identifiants dans un dépôt.

## Éléments à configurer

Au minimum, mettez-vous d'accord sur la branche par défaut, les règles de protection des branches, les exigences de révision, les vérifications d'état, la liaison avec les tickets et les personnes qui peuvent envoyer ou fusionner des modifications. Ces règles font partie du processus de livraison de l'équipe, et ne sont pas de simples éléments décoratifs de la plateforme.
