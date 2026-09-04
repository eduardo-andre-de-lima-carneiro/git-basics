# 4.6 Liste de contrôle pour une intégration sécurisée

Avant de considérer une intégration comme prête, vérifiez les points suivants :

- L'URL distante est correcte et ne contient aucun secret.
- L'authentification utilise des clés SSH, des tokens ou une identité d'application aux permissions limitées — jamais un mot de passe de compte ; chaque plateforme de ce chapitre a supprimé ou est en train de supprimer l'authentification par mot de passe pour Git en HTTPS.
- L'authentification à deux facteurs ou multifacteur est activée sur chaque compte humain disposant d'un accès push ou merge, pas seulement sur les comptes administrateurs.
- Les personal access tokens ont la portée la plus restreinte que la tâche exige, une expiration courte et un plan de rotation — un token qui « fonctionne éternellement sans y toucher » est un token que personne ne surveille.
- Les clés SSH utilisent un algorithme moderne (Ed25519 lorsque la plateforme l'accepte ; Azure Repos fait exception et exige RSA) et sont renouvelées ou supprimées lorsqu'une personne change de rôle ou quitte l'équipe.
- La branche par défaut est protégée contre les push directs accidentels.
- Les pull requests ou merge requests exigent une révision appropriée et la réussite des vérifications automatisées.
- La signature des commits (GPG, SSH, ou la méthode prise en charge par la plateforme) est activée là où l'équipe souhaite un badge vérifié comme preuve de la paternité, en sachant que toutes les plateformes ne l'appliquent pas de la même façon — GitHub et GitLab peuvent exiger des commits signés via une règle de branche, alors qu'Azure Repos n'a actuellement aucun équivalent dans ses règles de branche.
- Les secrets CI/CD sont stockés dans le gestionnaire de secrets de la plateforme, jamais dans un fichier de workflow ni dans un script.
- L'analyse des dépendances, des secrets et des vulnérabilités est activée lorsque cela est approprié.
- Le déploiement en production exige une approbation distincte ou un environnement protégé.
- Les webhooks valident leurs signatures et n'envoient que les données nécessaires.
- Les accès sont réexaminés lorsqu'une personne, un token, un runner ou un service change de rôle — et immédiatement lorsqu'il quitte l'équipe.

## Protections au niveau du compte

Chaque plateforme documente sa propre exigence et sa configuration actuelles :

- GitHub [exige la 2FA](https://docs.github.com/fr/authentication/securing-your-account-with-two-factor-authentication-2fa/about-two-factor-authentication) pour les comptes qui contribuent du code, et prend en charge la [signature des commits avec GPG, SSH ou S/MIME](https://docs.github.com/fr/authentication/managing-commit-signature-verification/about-commit-signature-verification).
- GitLab prend en charge la [2FA imposée au niveau du groupe ou de l'instance](https://docs.gitlab.com/user/profile/account/two_factor_authentication/) et les [commits signés via SSH, GPG ou X.509](https://docs.gitlab.com/user/project/repository/signed_commits/).
- Azure DevOps rattache l'authentification multifacteur au fournisseur d'identité de l'organisation : une [connexion Microsoft Entra ID hérite des règles MFA et d'accès conditionnel d'Entra](https://learn.microsoft.com/fr-fr/azure/devops/organizations/security/about-security-identity), et les comptes utilisant un compte Microsoft peuvent activer la 2FA directement.
- Bitbucket Cloud prend en charge la [vérification en deux étapes](https://support.atlassian.com/bitbucket-cloud/docs/enable-two-step-verification/) via une application d'authentification ou une clé de sécurité, indépendamment de l'identifiant Git (API token ou clé SSH) utilisé par le compte.

## Pièges courants

- Confondre « la 2FA est exigée pour l'organisation » avec « la 2FA est activée pour chaque membre » — un paramètre d'application et l'inscription individuelle sont deux vérifications distinctes, et l'une peut être en retard sur l'autre.
- Exiger des commits signés sur GitHub ou GitLab sans jamais montrer aux contributeurs comment configurer la signature SSH ou GPG en local, de sorte que l'exigence bloque des push légitimes au lieu de détecter un vrai problème.
- Auditer les tokens et les clés une seule fois, à la mise en place du projet, et plus jamais ensuite. La rotation est une tâche récurrente, pas un point de contrôle unique.

Une intégration est réussie lorsqu'elle rend la livraison plus traçable et reproductible sans faciliter l'utilisation abusive des identifiants ou les modifications de production.

## Références

- GitHub Docs — [À propos de l'authentification à deux facteurs](https://docs.github.com/fr/authentication/securing-your-account-with-two-factor-authentication-2fa/about-two-factor-authentication)
- GitHub Docs — [À propos de la vérification de signature des commits](https://docs.github.com/fr/authentication/managing-commit-signature-verification/about-commit-signature-verification)
- GitLab Docs — [Authentification à deux facteurs](https://docs.gitlab.com/user/profile/account/two_factor_authentication/)
- GitLab Docs — [Commits signés](https://docs.gitlab.com/user/project/repository/signed_commits/)
- Microsoft Learn — [À propos de l'authentification, de l'autorisation et des règles de sécurité](https://learn.microsoft.com/fr-fr/azure/devops/organizations/security/about-security-identity)
- Atlassian Support — [Activer la vérification en deux étapes](https://support.atlassian.com/bitbucket-cloud/docs/enable-two-step-verification/)
