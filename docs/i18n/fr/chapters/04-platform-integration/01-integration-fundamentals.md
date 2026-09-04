# 4.1 Fondamentaux de l'intégration

Les plateformes hébergées ajoutent des services de collaboration et de livraison autour d'un dépôt Git. Les commandes locales restent familières; la plateforme fournit l'identité, les permissions, la révision, l'automatisation et la visibilité sur le projet.

## Le flux commun

1. Créez ou sélectionnez un dépôt distant.
2. Connectez le dépôt local avec [`git remote add origin <repository-url>`](https://git-scm.com/docs/git-remote).
3. Envoyez une branche avec `git push -u origin <branch-name>`.
4. Ouvrez une pull request ou une merge request pour la révision.
5. Laissez les vérifications obligatoires s'exécuter avant la fusion.
6. Supprimez la branche de courte durée une fois la modification intégrée.

## Choisir HTTPS ou SSH

HTTPS est simple pour commencer. Chaque grande plateforme authentifie désormais les opérations Git en HTTPS avec un jeton ou une connexion fédérée plutôt qu'avec un mot de passe de compte — GitHub a supprimé l'authentification par mot de passe pour Git en août 2021, et les autres plateformes de ce chapitre ont suivi le même schéma, chacune avec son mécanisme actuel (voir les pages de plateforme qui suivent). SSH utilise une paire de clés, évite de ressaisir des identifiants à chaque opération, et peut aussi signer des commits. Ne placez jamais de tokens, de clés privées ou d'identifiants dans un dépôt, et ne présumez pas qu'une page lue il y a un moment décrit encore le comportement par défaut d'aujourd'hui — ces plateformes changent leurs méthodes d'authentification par défaut plus souvent que la plupart des commandes Git ne changent.

## Comparaison des plateformes

Le tableau reflète la documentation propre à chaque plateforme, vérifiée en direct plutôt que rappelée de mémoire. Les limites chiffrées (sièges, stockage, minutes de CI) changent souvent et ont été volontairement omises — consultez la page tarifaire actuelle de chaque plateforme pour cela.

| Plateforme | Modèle d'hébergement | Authentification par défaut pour Git en HTTPS | Nom de l'unité de révision | Dépôts privés sur le plan gratuit |
| --- | --- | --- | --- | --- |
| [GitHub](https://docs.github.com/fr) | SaaS (GitHub.com) ou auto-hébergé (GitHub Enterprise Server) | Personal access token, clé SSH, ou un assistant d'identifiants comme GitHub CLI / Git Credential Manager — les mots de passe de compte sont rejetés | Pull request | Oui |
| [GitLab](https://docs.gitlab.com/) | SaaS (GitLab.com) ou auto-hébergé (GitLab Self-Managed) | Personal access token (obligatoire dès que la 2FA ou le SSO est activé) ou clé SSH | Merge request | Oui |
| [Azure Repos](https://learn.microsoft.com/fr-fr/azure/devops/repos/) | SaaS (Azure DevOps Services) ou auto-hébergé (Azure DevOps Server) | Connexion Microsoft Entra ID via Git Credential Manager, préférée à un personal access token limité en portée | Pull request | Oui |
| [Bitbucket](https://support.atlassian.com/bitbucket-cloud/) | SaaS (Bitbucket Cloud) ou auto-hébergé (Bitbucket Data Center) | API token ou clé SSH — les app passwords ont été totalement retirés en 2026 | Pull request | Oui |

## Éléments à configurer

Au minimum, mettez-vous d'accord sur la branche par défaut, les règles de protection des branches, les exigences de révision, les vérifications d'état, la liaison avec les tickets et les personnes qui peuvent envoyer ou fusionner des modifications. Ces règles font partie du processus de livraison de l'équipe, et ne sont pas de simples éléments décoratifs de la plateforme.

## Pièges courants

- Réutiliser un seul token à longue durée de vie et à portée large sur tous les outils. S'il fuit, toutes les intégrations qui l'utilisaient sont compromises d'un coup — donnez à chaque token une portée limitée à un seul usage.
- Oublier qu'un token a une date d'expiration. Un push qui fonctionnait hier peut échouer aujourd'hui avec une erreur d'authentification dès que le token expire — traitez cela comme un événement courant, pas comme un bug, et faites tourner le token.
- Supposer que HTTPS demande encore un mot de passe de compte. Aucune des quatre plateformes de ce chapitre ne le fait; l'invite demande un token ou une connexion gérée par une CLI.

## Références

- Manuel de référence de Git — [git-remote](https://git-scm.com/docs/git-remote)
- GitHub Docs — [À propos de l'authentification à GitHub](https://docs.github.com/fr/authentication/keeping-your-account-and-data-secure/about-authentication-to-github)
- GitLab Docs — [Personal access tokens](https://docs.gitlab.com/user/profile/personal_access_tokens/)
- Microsoft Learn — [Utiliser des personal access tokens pour l'authentification](https://learn.microsoft.com/fr-fr/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate)
- Atlassian Support — [App passwords (Bitbucket Cloud)](https://support.atlassian.com/bitbucket-cloud/docs/app-passwords/)
