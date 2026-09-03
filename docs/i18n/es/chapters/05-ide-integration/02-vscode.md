# 5.2 Visual Studio Code

Visual Studio Code incluye compatibilidad con Git activada cuando Git está instalado y en el `PATH`.

## Flujo principal

- La vista **Source Control** (Ctrl/Cmd+Shift+G) enumera los cambios. Pasa el cursor sobre un archivo y haz clic en **+** para prepararlo, o prepara un solo bloque desde el editor de diff.
- Escribe un mensaje en el cuadro de commit y pulsa Ctrl/Cmd+Enter para confirmar.
- El nombre de la rama en la barra de estado, abajo a la izquierda, abre el menú de cambio y creación de ramas.
- **Sync Changes** ejecuta `git pull` y luego `git push` para la rama actual.
- La vista **Timeline**, en la parte inferior del Explorador, muestra el historial de commits de un archivo.

## Usar VS Code como editor de Git

```bash
git config --global core.editor "code --wait"
```

La opción `--wait` hace que Git se detenga hasta que cierres la pestaña, lo que es necesario para los mensajes de commit y el rebase interactivo.

## Extensiones útiles

- **GitLens** añade blame línea por línea, un grafo de commits y navegación por el historial.
- **GitHub Pull Requests and Issues** permite crear, revisar y fusionar pull requests sin salir del editor.

Instala extensiones solo de publicadores en los que confíes y revisa los permisos que solicitan.

## Ejercicio

Define `core.editor` como `code --wait` y ejecuta `git commit` sin `-m` en un repositorio de práctica. Escribe el mensaje en la pestaña de VS Code, guarda y ciérrala; comprueba el commit con `git log --oneline`.
