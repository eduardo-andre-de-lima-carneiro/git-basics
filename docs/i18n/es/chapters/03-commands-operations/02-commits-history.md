# 3.2 Commits e historial

Algunos comandos de inspección útiles:

```bash
git log --oneline --decorate --graph
git show <commit>
git diff <commit-a> <commit-b>
```

## Cómo leer la salida

- [`git log --oneline`](https://git-scm.com/docs/git-log) es un atajo de `--pretty=oneline --abbrev-commit`: una línea por commit, con un hash corto en lugar del hash completo de 40 caracteres.
- `--decorate` imprime los nombres de referencia — puntas de ramas y etiquetas — que apuntan a cada commit mostrado, para que veas dónde están actualmente `main`, `HEAD` o una etiqueta en el grafo.
- `--graph` dibuja un grafo en texto a la izquierda de la salida, mostrando cómo divergieron y se combinaron las ramas; es más útil combinado con `--oneline --decorate`.
- [`git show <commit>`](https://git-scm.com/docs/git-show) muestra el mensaje de log de un solo commit junto con su diff completo — la forma más rápida de inspeccionar un cambio sin listar el historial alrededor.
- `git diff <commit-a> <commit-b>` compara directamente dos commits arbitrarios, independientemente de la estructura de ramas entre ellos.

## Commits enfocados y mensajes

Prefiere commits enfocados que representen un solo cambio lógico — un commit que mezcla una corrección de error con una pasada de formato es más difícil de revisar, revertir o seguir después con `git log --follow`. El historial es más fácil de navegar cuando los mensajes de commit usan una descripción imperativa y específica ("Corrige la comprobación de nulo en el parser", no "correcciones").

Una convención muy usada para estructurar ese mensaje es [Conventional Commits](https://www.conventionalcommits.org/es/v1.0.0/): un prefijo `type(scope): description` (`fix:`, `feat:`, `docs:`, …) que hace el historial fácil de escanear con `git log --oneline` y permite que las herramientas generen changelogs automáticamente. Es opcional aquí, pero vale la pena adoptarlo si tu proyecto aún no tiene una convención de mensajes.

## Errores comunes

- Un hash abreviado de `--oneline` es inequívoco solo respecto a los objetos que existen actualmente en tu repositorio; no lo fijes en documentación que deba sobrevivir a la rama.
- Reescribir el mensaje o el contenido de un commit ya enviado a una rama compartida requiere un force-push y coordinación con quien ya lo haya obtenido — consulta [3.5 Deshacer cambios de forma segura](05-undo.md) antes de hacerlo.

## Ejercicio

En un repositorio de práctica, haz tres commits pequeños. Ejecuta `git log --oneline --decorate --graph --all` e identifica los nombres de referencia mostrados. Usa `git show` en el commit del medio para ver solo su diff, y luego `git diff` entre el primer y el último commit para ver el cambio acumulado.

## Referencias

- Manual de Git — [git-log](https://git-scm.com/docs/git-log)
- Manual de Git — [git-show](https://git-scm.com/docs/git-show)
- Manual de Git — [git-diff](https://git-scm.com/docs/git-diff)
- Pro Git (2.ª ed.) — [Viewing the Commit History](https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History)
- [Conventional Commits](https://www.conventionalcommits.org/es/v1.0.0/)
