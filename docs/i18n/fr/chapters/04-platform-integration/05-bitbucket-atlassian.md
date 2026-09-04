# 4.5 Bitbucket et Atlassian

Bitbucket, d'Atlassian, fournit des dépôts Git avec des pull requests et Pipelines. Il peut relier le travail du dépôt aux tickets Jira et à d'autres services Atlassian.

## Connecter et publier

Créez un dépôt Bitbucket Cloud, puis exécutez localement :

```bash
git remote add origin https://bitbucket.org/WORKSPACE/REPOSITORY.git
git push -u origin main
```

Utilisez l'URL de clonage fournie par votre espace de travail Bitbucket. Bitbucket Data Center utilise des URL et des règles d'authentification propres à chaque organisation.

## Authentification

L'authentification HTTPS de Bitbucket Cloud a changé en 2026 : les [app passwords](https://support.atlassian.com/bitbucket-cloud/docs/app-passwords/) ont été retirés selon un calendrier progressif qui s'est achevé en juillet 2026 et ne fonctionnent plus du tout. La méthode actuelle pour les scripts, les outils de CI et la ligne de commande Git est un [API token](https://support.atlassian.com/bitbucket-cloud/docs/using-api-tokens/), créé depuis votre compte Atlassian et utilisé avec votre nom d'utilisateur Bitbucket comme identifiant Git. Si une page, un tutoriel ou un outil vous dit encore de créer un « app password », considérez cette instruction comme obsolète.

Une clé SSH ([Ed25519 recommandée](https://support.atlassian.com/bitbucket-cloud/docs/set-up-personal-ssh-keys-on-linux/)) n'est pas affectée par le retrait des app passwords et reste une bonne option pour un travail fréquent en ligne de commande.

Activez la [vérification en deux étapes](https://support.atlassian.com/bitbucket-cloud/docs/enable-two-step-verification/) sur le compte — via une application d'authentification ou une clé de sécurité — indépendamment de l'identifiant Git que vous utilisez au quotidien.

## Intégrations utiles

- Les pull requests permettent la révision, les approbations, les tâches et les vérifications de fusion.
- `bitbucket-pipelines.yml` définit les étapes de build et de déploiement de Bitbucket Pipelines.
- L'intégration Jira lie les branches, les commits et les pull requests aux éléments de travail.
- Les environnements de déploiement peuvent restreindre les variables et les mises en production.
- Les [permissions de branche](https://support.atlassian.com/bitbucket-cloud/docs/use-branch-permissions/) restreignent les personnes pouvant pousser ou fusionner sur une branche donnée ; la Marketplace et les webhooks connectent Bitbucket à d'autres outils d'ingénierie.

Utilisez des tokens d'accès au dépôt ou à l'espace de travail avec les permissions minimales nécessaires. Ne placez les clés de tickets Jira dans les noms de branches ou les messages de commit que si cette convention a été adoptée par l'équipe, et ne placez jamais de secrets dans ces champs.

## Pièges courants

- Suivre un ancien tutoriel qui demande de créer un « app password » — depuis mi-2026, ce flux n'existe plus ; créez plutôt un API token.
- Une intégration (outil de CI, gestionnaire de paquets, client Git) encore configurée avec un app password enregistré qui se casse silencieusement une fois le calendrier de retrait arrivé à la suppression complète, sans avertissement local préalable.
- Supposer qu'un API token se comporte exactement comme l'ancien app password : il authentifie Git et les appels d'API, mais il ne peut pas servir à se connecter à bitbucket.org lui-même.

## Exercice

Créez un API token Bitbucket, puis utilisez-le avec votre nom d'utilisateur Bitbucket pour authentifier un `git push` en HTTPS. Vérifiez dans les paramètres de sécurité de votre compte qu'aucun app password n'est encore listé comme actif.

## Références

- Atlassian Support — [App passwords](https://support.atlassian.com/bitbucket-cloud/docs/app-passwords/)
- Atlassian Support — [Utiliser les API tokens](https://support.atlassian.com/bitbucket-cloud/docs/using-api-tokens/)
- Atlassian Support — [Activer la vérification en deux étapes](https://support.atlassian.com/bitbucket-cloud/docs/enable-two-step-verification/)
- Atlassian Support — [Configurer des clés SSH personnelles](https://support.atlassian.com/bitbucket-cloud/docs/set-up-personal-ssh-keys-on-linux/)
- Atlassian Support — [Utiliser les permissions de branche](https://support.atlassian.com/bitbucket-cloud/docs/use-branch-permissions/)
