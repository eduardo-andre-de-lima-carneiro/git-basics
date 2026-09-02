# 4.3 GitLab

GitLab fournit dans une même plateforme des dépôts Git avec des merge requests, Issues, des pipelines CI/CD, un Package Registry et des tableaux de bord de sécurité.

## Connecter et publier

Créez un projet sur GitLab, puis exécutez localement :

```bash
git remote add origin https://gitlab.com/GROUP/PROJECT.git
git push -u origin main
```

Utilisez les noms réels de votre groupe, de votre projet et de votre branche par défaut. Vérifiez le dépôt distant avec `git remote -v` avant d'envoyer des modifications.

## Intégrations utiles

- Les merge requests regroupent la révision, les approbations, les discussions et les résultats des pipelines.
- `.gitlab-ci.yml` définit les tâches CI/CD, les étapes, les artefacts et les règles de déploiement.
- Les branches et les environnements protégés contrôlent les personnes qui peuvent fusionner ou déployer.
- Les deploy tokens, project access tokens et runners prennent en charge l'automatisation.
- Les webhooks et les intégrations avertissent les gestionnaires de tickets, les outils de discussion et les systèmes de sécurité.

Utilisez des variables CI/CD masquées et protégées pour les identifiants. Maintenez les runners à jour, limitez les runners privilégiés et n'accordez aux tokens que les scopes nécessaires à leur tâche.
