# 2.2 Configurer l'identité et les valeurs par défaut

Définissez le nom et l'adresse e-mail que Git enregistrera dans les nouveaux commits :

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
```

Examinez la configuration effective avec `git config --list --show-origin`.
