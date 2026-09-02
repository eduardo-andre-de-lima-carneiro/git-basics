# 3.1 Le flux de travail quotidien

Utilisez une boucle courte et observable :

```bash
git status
git add path/to/file
git diff --staged
git commit -m "Describe the change"
git status
```

Examinez la différence mise en staging avant de créer le commit. Cette habitude empêche des fichiers sans rapport d'être inclus dans un commit.
