# 3.5 Deshacer cambios de forma segura

Elige el comando según el lugar donde exista el cambio no deseado:

- Árbol de trabajo: `git restore <file>`. Este comando descarta permanentemente los cambios no confirmados del árbol de trabajo; guarda primero cualquier cosa que puedas necesitar.
- Área de preparación: `git restore --staged <file>`.
- Historial publicado: prefiere `git revert <commit>`.
- Commit local no publicado: considera `git reset` solo después de comprobar las consecuencias.

Ejecuta `git status` antes y después de los comandos de recuperación.
