# 4.3 GitLab

GitLab fournit dans une même plateforme des dépôts Git avec des merge requests, Issues, des pipelines CI/CD, un Package Registry et des tableaux de bord de sécurité.

## Connecter et publier

Créez un projet sur GitLab, puis exécutez localement :

```bash
git remote add origin https://gitlab.com/GROUP/PROJECT.git
git push -u origin main
```

Utilisez les noms réels de votre groupe, de votre projet et de votre branche par défaut. Vérifiez le dépôt distant avec `git remote -v` avant d'envoyer des modifications.

## Authentification

Pour HTTPS, GitLab accepte [n'importe quelle chaîne non vide comme nom d'utilisateur et un personal access token comme mot de passe](https://docs.gitlab.com/user/profile/personal_access_tokens/). Un token est *obligatoire*, et non facultatif, dès que l'authentification à deux facteurs ou le SSO est activé sur le compte. Les nouveaux tokens doivent porter une date d'expiration ; GitLab applique une valeur par défaut de 365 jours si vous n'en définissez pas une, et les administrateurs de l'offre Ultimate peuvent imposer un maximum plus court.

Pour un travail fréquent en ligne de commande, une [clé SSH](https://docs.gitlab.com/user/ssh/) évite de ressaisir un token à chaque push. GitLab recommande le type de clé Ed25519 plutôt que RSA : `ssh-keygen -t ed25519 -C "<comment>"`. Les clés nouvellement ajoutées sont vérifiées par rapport à une liste de clés connues comme compromises avant que GitLab ne les accepte.

GitLab prend aussi en charge l'[authentification à deux facteurs](https://docs.gitlab.com/user/profile/account/two_factor_authentication/) — passkeys, applications OTP, clés de sécurité WebAuthn ou codes par e-mail — qu'un groupe ou une instance auto-hébergée peut exiger pour chaque membre.

## Intégrations utiles

- Les merge requests regroupent la révision, les approbations, les discussions et les résultats des pipelines.
- `.gitlab-ci.yml` définit les tâches CI/CD, les étapes, les artefacts et les règles de déploiement.
- Les [branches protégées](https://docs.gitlab.com/user/project/repository/branches/protected/) et les environnements contrôlent les personnes qui peuvent fusionner ou déployer.
- Les deploy tokens, project access tokens et runners prennent en charge l'automatisation.
- Les webhooks et les intégrations avertissent les gestionnaires de tickets, les outils de discussion et les systèmes de sécurité.

Utilisez des variables CI/CD masquées et protégées pour les identifiants. Maintenez les runners à jour, limitez les runners privilégiés et n'accordez aux tokens que les scopes nécessaires à leur tâche.

## Pièges courants

- Oublier que GitLab applique silencieusement une expiration de 365 jours à un personal access token créé sans en avoir défini une — un token qui semble "sans expiration" cessera quand même de fonctionner un an plus tard.
- Enregistrer une clé de sécurité WebAuthn sur un nom d'hôte GitLab (par exemple une instance auto-hébergée) et s'attendre à ce qu'elle fonctionne aussi sur `gitlab.com` — les enregistrements WebAuthn sont liés au nom d'hôte, chacun nécessite donc son propre enregistrement.
- Faire des commits sans jamais configurer la signature des commits, puis être surpris que le badge "vérifié" d'une branche protégée n'apparaisse jamais ; GitLab vérifie la signature par rapport à une clé déjà ajoutée au compte.

## Exercice

Générez une clé SSH Ed25519, ajoutez la clé publique à votre compte GitLab, puis clonez un projet en SSH et vérifiez que `git push` ne demande plus de token.

## Références

- GitLab Docs — [Personal access tokens](https://docs.gitlab.com/user/profile/personal_access_tokens/)
- GitLab Docs — [Clés SSH](https://docs.gitlab.com/user/ssh/)
- GitLab Docs — [Authentification à deux facteurs](https://docs.gitlab.com/user/profile/account/two_factor_authentication/)
- GitLab Docs — [Branches protégées](https://docs.gitlab.com/user/project/repository/branches/protected/)
- GitLab Docs — [Commits signés](https://docs.gitlab.com/user/project/repository/signed_commits/)
