# 4.4 Azure Repos

Azure Repos héberge des dépôts Git dans des projets Azure DevOps et se connecte naturellement à Azure Boards, Pipelines, Test Plans et Artifacts.

## Connecter et publier

Créez ou sélectionnez un dépôt dans un projet Azure DevOps, puis exécutez localement :

```bash
git remote add origin https://dev.azure.com/ORGANIZATION/PROJECT/_git/REPOSITORY
git push -u origin main
```

L'URL exacte peut être copiée à partir de l'action Clone du dépôt.

## Authentification

Les recommandations de Microsoft placent désormais les personal access tokens en dernier recours, pas en premier choix : la [documentation Azure DevOps](https://learn.microsoft.com/fr-fr/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate) indique d'« éviter d'utiliser des PAT lorsqu'une méthode d'authentification plus sûre est disponible » et recommande la connexion Microsoft Entra ID (via Git Credential Manager) ou un service principal / une identité managée pour tout ce qui est automatisé. Si un [personal access token](https://learn.microsoft.com/fr-fr/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate) reste le bon choix — un script ponctuel, un outil incapable de se connecter via Entra — donnez-lui la portée la plus restreinte et l'expiration la plus courte que la tâche permet ; la cadence de rotation recommandée par Microsoft elle-même est de 90 jours pour un PAT personnel et de 30 jours pour un PAT privilégié.

[SSH](https://learn.microsoft.com/fr-fr/azure/devops/repos/git/use-ssh-keys-to-authenticate) est également pris en charge, avec une particularité propre à cette plateforme : Azure Repos n'accepte que les clés **RSA**, pas les clés Ed25519 que GitHub et GitLab recommandent désormais — réutiliser ici une clé Ed25519 existante de GitHub/GitLab échoue. Générez une clé RSA distincte pour Azure Repos : `ssh-keygen -t rsa -b 3072`.

## Intégrations utiles

- Les pull requests prennent en charge les réviseurs, les [règles de branche](https://learn.microsoft.com/fr-fr/azure/devops/repos/git/branch-policies?view=azure-devops), les éléments de travail liés et la validation des builds.
- Azure Pipelines peut compiler, tester, analyser et déployer à partir des événements du dépôt.
- Azure Boards lie les commits et les pull requests aux éléments de travail pour assurer la traçabilité.
- Les règles de branche peuvent exiger des réviseurs, des builds réussis et la résolution des commentaires — contrairement à GitHub ou GitLab, les règles de branche d'Azure Repos ne comportent pas d'option intégrée « exiger des commits signés ».
- Azure Artifacts fournit des flux pour les packages et les dépendances de build.

Accordez les permissions par l'intermédiaire de groupes lorsque c'est possible. Protégez les connexions de service et les groupes de variables, et séparez l'approbation des déploiements en production des droits de contribution au code.

## Pièges courants

- Générer une clé Ed25519 par habitude (parce que ça a fonctionné sur GitHub) et se heurter à un rejet déroutant d'Azure Repos, qui n'accepte que les clés RSA pour SSH.
- Laisser un personal access token à une longue expiration par défaut pour un pipeline CI au lieu de le faire tourner — un token non renouvelé qui traîne pendant des mois est facile à repérer par un administrateur dans le journal d'audit, mais seulement si quelqu'un regarde.
- Traiter un PAT comme un identifiant de service à long terme. Microsoft recommande explicitement de migrer les charges de travail automatisées vers un service principal ou une identité managée.

## Exercice

Créez un personal access token limité à **Code (Read & write)** pour un projet, avec une expiration de 7 jours. Utilisez-le pour authentifier un `git push` en HTTPS, puis vérifiez dans le journal d'audit de l'organisation l'événement `PatCreated` correspondant.

## Références

- Microsoft Learn — [Utiliser des personal access tokens pour l'authentification](https://learn.microsoft.com/fr-fr/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate)
- Microsoft Learn — [Utiliser l'authentification par clé SSH](https://learn.microsoft.com/fr-fr/azure/devops/repos/git/use-ssh-keys-to-authenticate)
- Microsoft Learn — [Définir et gérer les règles de branche](https://learn.microsoft.com/fr-fr/azure/devops/repos/git/branch-policies?view=azure-devops)
- Microsoft Learn — [À propos de l'authentification, de l'autorisation et des règles de sécurité](https://learn.microsoft.com/fr-fr/azure/devops/organizations/security/about-security-identity)
