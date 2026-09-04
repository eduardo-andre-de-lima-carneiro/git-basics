# 3.6 Ejercicios prácticos

Completa estos ejercicios en un directorio temporal:

1. Inicializa un repositorio, crea un archivo y haz dos commits enfocados. Entre los commits, usa `git status` y `git diff --staged` para confirmar exactamente qué contendrá cada commit antes de ejecutar `git commit`.
2. Crea una rama, cambia la misma línea de forma distinta en ambas ramas y resuelve el conflicto de fusión deliberadamente, en lugar de aceptar automáticamente un lado.
3. Añade un remoto, obtén su historial y compara las ramas local y remota con `git log --oneline main..origin/main` antes de integrar nada.
4. Practica restaurar una edición no preparada con `git restore`, sacar un archivo de la preparación con `git restore --staged` y revertir un commit publicado con `git revert` — usando la [tabla de decisión de 3.5](05-undo.md) para elegir el comando correcto en cada caso.

Para cada ejercicio, registra el comando usado, el estado antes de él y el resultado mostrado por `git status`.

## Referencias

- Manual de Git — [git-status](https://git-scm.com/docs/git-status)
- Manual de Git — [git-log](https://git-scm.com/docs/git-log)
- Manual de Git — [git-restore](https://git-scm.com/docs/git-restore)
- Manual de Git — [git-revert](https://git-scm.com/docs/git-revert)
