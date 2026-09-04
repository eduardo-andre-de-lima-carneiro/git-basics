# 5.4 IDE de JetBrains

IntelliJ IDEA, PyCharm, WebStorm, PhpStorm, Rider, GoLand y Android Studio comparten la misma [integración con Git](https://www.jetbrains.com/help/idea/using-git-integration.html) en el menú **Git** (o **VCS**).

## Flujo principal

- **Git > Clone** crea el repositorio local; **VCS > Enable Version Control Integration** inicia uno en un proyecto existente.
- La [ventana **Commit**](https://www.jetbrains.com/help/idea/commit-and-push-changes.html) enumera los cambios, los agrupa en changelists y prepara archivos o hunks. Debajo están el cuadro de mensaje y los botones **Commit** / **Commit and Push**.
- La pestaña **Log** de la ventana **Git** muestra el grafo completo de ramas, con filtros por rama, usuario y ruta.
- El widget de rama de la barra de estado cambia, crea y compara ramas.
- **Update Project** ejecuta fetch más merge o rebase, según tu configuración.
- Los conflictos abren un resolvedor de tres paneles con **Accept Left**, **Accept Right** y edición manual en el panel de resultado.

## Rebase interactivo

Haz clic derecho en un commit del **Log** y elige **Interactively Rebase from Here** para reordenar, combinar (squash), editar o descartar commits mediante un cuadro de diálogo, en lugar de un archivo de texto.

## Shelve frente a stash

**Shelve** es una función de JetBrains que aparta cambios dentro del IDE. **Stash** es el comando de Git. Ambos funcionan; prefiere stash si compañeros con otros editores necesitan ver el mismo estado guardado a través de Git.

## Ejercicio

En un repositorio de práctica, haz dos ediciones sin relación, sepáralas en dos changelists en la ventana **Commit** y confírmalas por separado. Verifica los dos commits en la pestaña **Log**.

## Referencias

- JetBrains — [Git integration in IntelliJ IDEA](https://www.jetbrains.com/help/idea/using-git-integration.html)
- JetBrains — [Commit and push changes](https://www.jetbrains.com/help/idea/commit-and-push-changes.html)
- JetBrains — [Edit Git project history (rebase interactivo)](https://www.jetbrains.com/help/idea/edit-project-history.html)
- JetBrains — [Resolve Git conflicts](https://www.jetbrains.com/help/idea/resolve-conflicts.html)
