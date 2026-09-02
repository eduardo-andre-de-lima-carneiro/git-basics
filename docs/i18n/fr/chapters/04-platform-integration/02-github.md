# 4.2 GitHub

GitHub associe des dépôts Git hébergés à des pull requests, Issues, Actions, Projects, Packages et des fonctionnalités de sécurité.

## Connecter et publier

Créez un dépôt vide sur GitHub, puis exécutez localement :

```bash
git remote add origin https://github.com/OWNER/REPOSITORY.git
git push -u origin main
```

Remplacez `OWNER`, `REPOSITORY` et `main` par vos valeurs. N'initialisez pas le dépôt GitHub avec un deuxième README lorsque votre dépôt local en possède déjà un, sauf si vous prévoyez de réconcilier les historiques.

## Intégrations utiles

- Les pull requests permettent la révision, la discussion, les approbations obligatoires et les vérifications d'état.
- GitHub Actions peut tester, analyser, empaqueter et déployer lors des push ou des pull requests.
- La protection des branches peut exiger des révisions, des vérifications réussies et des commits signés.
- Les environnements peuvent restreindre les déploiements et protéger les secrets de production.
- Les webhooks et l'API connectent les événements du dépôt à des systèmes externes.

Utilisez des personal access tokens précis et dotés du principe du moindre privilège, ou des GitHub Apps. Stockez les secrets d'automatisation dans les secrets du dépôt ou de l'environnement, jamais dans les fichiers de workflow ni dans le code source.
