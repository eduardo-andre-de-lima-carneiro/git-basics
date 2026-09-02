# 3.1 El flujo de trabajo diario

Usa un ciclo pequeño y observable:

```bash
git status
git add path/to/file
git diff --staged
git commit -m "Describe the change"
git status
```

Revisa la diferencia preparada antes de hacer el commit. Este hábito evita que archivos no relacionados entren en un commit.
