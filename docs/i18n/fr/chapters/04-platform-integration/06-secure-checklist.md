# 4.6 Liste de contrôle pour une intégration sécurisée

Avant de considérer une intégration comme prête, vérifiez les points suivants :

- L'URL distante est correcte et ne contient aucun secret.
- L'authentification utilise des clés SSH, des tokens ou une identité d'application aux permissions limitées.
- La branche par défaut est protégée contre les push directs accidentels.
- Les pull requests ou merge requests exigent une révision appropriée et la réussite des vérifications automatisées.
- Les secrets CI/CD sont stockés dans le gestionnaire de secrets de la plateforme.
- L'analyse des dépendances, des secrets et des vulnérabilités est activée lorsque cela est approprié.
- Le déploiement en production exige une approbation distincte ou un environnement protégé.
- Les webhooks valident leurs signatures et n'envoient que les données nécessaires.
- Les accès sont réexaminés lorsqu'une personne, un token, un runner ou un service change de rôle.

Une intégration est réussie lorsqu'elle rend la livraison plus traçable et reproductible sans faciliter l'utilisation abusive des identifiants ou les modifications de production.
