# 4.2 GitHub

GitHub associe des dépôts Git hébergés à des pull requests, Issues, Actions, Projects, Packages et des fonctionnalités de sécurité.

## Connecter et publier

Créez un dépôt vide sur GitHub, puis exécutez localement :

```bash
git remote add origin https://github.com/OWNER/REPOSITORY.git
git push -u origin main
```

Remplacez `OWNER`, `REPOSITORY` et `main` par vos valeurs. N'initialisez pas le dépôt GitHub avec un deuxième README lorsque votre dépôt local en possède déjà un, sauf si vous prévoyez de réconcilier les historiques.

## Authentification

GitHub a [supprimé l'authentification par mot de passe pour les opérations Git en août 2021](https://docs.github.com/fr/authentication/keeping-your-account-and-data-secure/about-authentication-to-github) ; l'invite HTTPS attend désormais un token, pas le mot de passe de votre compte. Choisissez l'une des options suivantes :

- **Un [personal access token](https://docs.github.com/fr/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)** utilisé à la place du mot de passe. GitHub recommande les tokens *fine-grained*, plus récents — limités à des dépôts et des permissions spécifiques — plutôt que les tokens *classic*, qui accordent des portées larges à l'échelle du compte comme `repo`. Un token classic inutilisé est automatiquement révoqué au bout d'un an ; un token fine-grained doit recevoir une expiration dès sa création.
- **Une [clé SSH](https://docs.github.com/fr/authentication/connecting-to-github-with-ssh)** — GitHub recommande de générer une clé Ed25519 — ajoutée une seule fois à votre compte, après quoi `git push`/`git pull` ne demandent plus aucun identifiant.
- **GitHub CLI (`gh auth login`) ou Git Credential Manager**, que la documentation de GitHub suggère elle-même avant de générer un token à la main, car ces outils gèrent le stockage et le renouvellement du token pour vous.

GitHub [exige aussi l'authentification à deux facteurs (2FA)](https://docs.github.com/fr/authentication/securing-your-account-with-two-factor-authentication-2fa/about-two-factor-authentication) pour les comptes qui contribuent du code, via une application TOTP, une clé de sécurité physique ou GitHub Mobile.

## Intégrations utiles

- Les pull requests permettent la révision, la discussion, les approbations obligatoires et les vérifications d'état.
- GitHub Actions peut tester, analyser, empaqueter et déployer lors des push ou des pull requests.
- Les [règles de protection des branches](https://docs.github.com/fr/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches) peuvent exiger des révisions, des vérifications réussies et des commits signés.
- Les environnements peuvent restreindre les déploiements et protéger les secrets de production.
- Les webhooks et l'API connectent les événements du dépôt à des systèmes externes.

Utilisez des personal access tokens précis et dotés du principe du moindre privilège, ou des GitHub Apps. Stockez les secrets d'automatisation dans les secrets du dépôt ou de l'environnement, jamais dans les fichiers de workflow ni dans le code source.

## Pièges courants

- Un PAT classic collé dans un script avec la portée `repo` complète, alors que le script ne fait push que vers un seul dépôt — la fuite de ce token compromet tous les dépôts accessibles au compte. Utilisez plutôt un token fine-grained limité à ce seul dépôt.
- Définir l'expiration d'un PAT puis l'oublier : le jour où il expire, `git push` échoue avec une erreur d'authentification qui ressemble à un dépôt distant cassé plutôt qu'à un identifiant expiré.
- Générer une clé SSH sans phrase secrète sur une machine partagée. GitHub peut vérifier que la clé vient bien de vous, mais ne peut pas protéger un fichier de clé privée que n'importe qui ayant accès au disque peut lire.

## Exercice

Créez un personal access token fine-grained limité à un dépôt d'exercice, avec la permission **Contents: Read and write** et une expiration courte (7 jours). Utilisez-le une fois pour faire `git push` en HTTPS, puis révoquez-le prématurément et vérifiez que le push suivant échoue avec une erreur d'authentification.

## Références

- GitHub Docs — [À propos de l'authentification à GitHub](https://docs.github.com/fr/authentication/keeping-your-account-and-data-secure/about-authentication-to-github)
- GitHub Docs — [Gérer vos personal access tokens](https://docs.github.com/fr/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)
- GitHub Docs — [Se connecter à GitHub avec SSH](https://docs.github.com/fr/authentication/connecting-to-github-with-ssh)
- GitHub Docs — [À propos de l'authentification à deux facteurs](https://docs.github.com/fr/authentication/securing-your-account-with-two-factor-authentication-2fa/about-two-factor-authentication)
- GitHub Docs — [À propos des branches protégées](https://docs.github.com/fr/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)
