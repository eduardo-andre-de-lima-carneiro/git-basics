# 4.4 Azure Repos

Azure Repos héberge des dépôts Git dans des projets Azure DevOps et se connecte naturellement à Azure Boards, Pipelines, Test Plans et Artifacts.

## Connecter et publier

Créez ou sélectionnez un dépôt dans un projet Azure DevOps, puis exécutez localement :

```bash
git remote add origin https://dev.azure.com/ORGANIZATION/PROJECT/_git/REPOSITORY
git push -u origin main
```

L'URL exacte peut être copiée à partir de l'action Clone du dépôt. Utilisez l'authentification Microsoft Entra, SSH ou un personal access token correctement limité, conformément aux règles de votre organisation.

## Intégrations utiles

- Les pull requests prennent en charge les réviseurs, les règles de branche, les éléments de travail liés et la validation des builds.
- Azure Pipelines peut compiler, tester, analyser et déployer à partir des événements du dépôt.
- Azure Boards lie les commits et les pull requests aux éléments de travail pour assurer la traçabilité.
- Les règles de branche peuvent exiger des réviseurs, des builds réussis et la résolution des commentaires.
- Azure Artifacts fournit des flux pour les packages et les dépendances de build.

Accordez les permissions par l'intermédiaire de groupes lorsque c'est possible. Protégez les connexions de service et les groupes de variables, et séparez l'approbation des déploiements en production des droits de contribution au code.
