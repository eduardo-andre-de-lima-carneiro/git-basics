# 1.4 El modelo mental de Git

Piensa en tres lugares:

1. Árbol de trabajo: los archivos que se están editando.
2. Área de preparación: la próxima instantánea que se está preparando.
3. Historial del repositorio: las instantáneas confirmadas.

El flujo básico es `edit -> git add -> git commit`. `git status` muestra las diferencias entre estos lugares y debería ser tu comando de diagnóstico más frecuente.

## Por qué la preparación es un paso separado

El área de preparación (también llamada índice) te permite construir un commit a partir de solo una parte de tus cambios — por ejemplo, preparar una corrección ya terminada con `git add`, mientras dejas una edición distinta, todavía en curso, sin preparar en el árbol de trabajo. Lo que termina en el commit es exactamente lo que estaba preparado en el momento en que ejecutaste `git commit`, no lo que el archivo parezca después. Consulta [Guardando cambios en el Repositorio](https://git-scm.com/book/es/v2/Fundamentos-de-Git-Guardando-cambios-en-el-Repositorio) en el libro Pro Git.

## Errores comunes

- **Un commit no es un diff.** Cada commit apunta a una instantánea completa del árbol del proyecto, no a una delta respecto al commit anterior; Git calcula los diffs bajo demanda comparando dos instantáneas. Por eso hacer checkout de un commit antiguo es un reemplazo directo del árbol de archivos, y no la reaplicación de una cadena de parches. Consulta [Fundamentos de Git](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Fundamentos-de-Git).
- **Staged y modified no son el mismo estado.** Si editas un archivo de nuevo después de `git add`, `git status` lo mostrará como staged y modified a la vez — la copia preparada queda congelada en el momento en que ejecutaste `add`, y hace falta un nuevo `git add` para actualizarla.

## Práctica

Cambia un archivo, ejecuta `git add`, luego cambia el mismo archivo de nuevo sin volver a prepararlo. Ejecuta `git status`, luego `git diff` (árbol de trabajo vs. preparado) y `git diff --staged` (preparado vs. último commit), para ver cómo divergen los tres lugares.

## Referencias

Esta página se basa en las siguientes fuentes oficiales:

- Pro Git (2.ª ed.) — [Guardando cambios en el Repositorio](https://git-scm.com/book/es/v2/Fundamentos-de-Git-Guardando-cambios-en-el-Repositorio)
- Pro Git (2.ª ed.) — [Fundamentos de Git](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Fundamentos-de-Git)
- Manual de referencia de Git — [git-status](https://git-scm.com/docs/git-status/es)
- Manual de referencia de Git — [git-diff](https://git-scm.com/docs/git-diff/es)
