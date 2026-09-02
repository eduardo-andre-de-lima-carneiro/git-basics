# 3.3 Ramas y colaboración

Las ramas son nombres móviles que apuntan a commits. Crea el trabajo separado de la base compartida:

```bash
git switch -c feature/example
git switch main
git merge feature/example
```

Antes de hacer el merge, inspecciona el historial y resuelve los conflictos de forma deliberada. Un conflicto es una solicitud de decisión humana, no un fallo de comando que haya que ocultar.
