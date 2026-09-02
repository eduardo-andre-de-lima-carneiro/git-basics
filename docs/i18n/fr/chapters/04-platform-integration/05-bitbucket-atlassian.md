# 4.5 Bitbucket et Atlassian

Bitbucket, d'Atlassian, fournit des dépôts Git avec des pull requests et Pipelines. Il peut relier le travail du dépôt aux tickets Jira et à d'autres services Atlassian.

## Connecter et publier

Créez un dépôt Bitbucket Cloud, puis exécutez localement :

```bash
git remote add origin https://bitbucket.org/WORKSPACE/REPOSITORY.git
git push -u origin main
```

Utilisez l'URL de clonage fournie par votre espace de travail Bitbucket. Bitbucket Data Center utilise des URL et des règles d'authentification propres à chaque organisation.

## Intégrations utiles

- Les pull requests permettent la révision, les approbations, les tâches et les vérifications de fusion.
- `bitbucket-pipelines.yml` définit les étapes de build et de déploiement de Bitbucket Pipelines.
- L'intégration Jira lie les branches, les commits et les pull requests aux éléments de travail.
- Les environnements de déploiement peuvent restreindre les variables et les mises en production.
- La Marketplace et les webhooks connectent Bitbucket à d'autres outils d'ingénierie.

Utilisez des tokens d'accès au dépôt ou à l'espace de travail avec les permissions minimales nécessaires. Ne placez les clés de tickets Jira dans les noms de branches ou les messages de commit que si cette convention a été adoptée par l'équipe, et ne placez jamais de secrets dans ces champs.
