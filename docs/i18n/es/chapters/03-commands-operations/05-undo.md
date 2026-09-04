# 3.5 Deshacer cambios de forma segura

Git tiene tres comandos de "deshacer" distintos, y actúan sobre tres lugares distintos. Elegir el correcto depende de dónde vive el cambio no deseado y de si alguien más ya lo ha visto.

## Tabla de decisión: restore vs. revert vs. reset

| Comando | Actúa sobre | ¿Reescribe historial publicado? | Uso típico | Seguridad / recuperación |
| --- | --- | --- | --- | --- |
| [`git restore <archivo>`](https://git-scm.com/docs/git-restore) | Árbol de trabajo (destino por defecto) | No — no es una operación de historial | Descartar ediciones no deseadas y sin commitear de un archivo | El contenido descartado desaparece; Git no mantiene reflog de las ediciones del árbol de trabajo, así que respalda antes lo que puedas necesitar |
| `git restore --staged <archivo>` | Solo el área de preparación (índice) | No | Sacar de la preparación un archivo añadido por error, conservando sus ediciones en el árbol de trabajo | Seguro — el árbol de trabajo no se toca, no se pierde nada |
| [`git revert <commit>`](https://git-scm.com/docs/git-revert) | Historial, añadiendo un nuevo commit | No — registra un nuevo commit que revierte el cambio en lugar de alterar los commits existentes | Deshacer el efecto de un commit que ya se ha enviado o compartido | Seguro en ramas compartidas; puede requerir resolución de conflictos si commits posteriores tocaron las mismas líneas |
| [`git reset [--soft\|--mixed\|--hard] <commit>`](https://git-scm.com/docs/git-reset) | `HEAD` y el índice; `--hard` también sobrescribe el árbol de trabajo | Sí — mueve el puntero de la rama, descartando commits de su historial | Deshacer commits locales aún no publicados, o quitar todo de la preparación de una vez | Nunca lo uses sobre commits que alguien más ya tiene; los commits descartados suelen seguir siendo recuperables durante un tiempo mediante [`git reflog`](https://git-scm.com/docs/git-reflog), pero `--hard` también descarta ediciones sin commitear del árbol de trabajo, que el reflog no puede recuperar |

Los tres modos de `reset` difieren en hasta dónde deshacen: `--soft` mueve solo `HEAD` (índice y árbol de trabajo intactos — útil para agrupar commits recientes antes de volver a commitear), `--mixed` (el predeterminado) también reinicia el índice, de modo que nada queda preparado, y `--hard` además sobrescribe el árbol de trabajo para igualarlo con el commit objetivo.

## Por qué importa este orden de preferencia

Prefiere `restore` y `revert` por defecto, porque ninguno de los dos puede alterar historial del que dependan otras personas. Recurre a `reset` solo cuando estés seguro de que los commits en cuestión siguen siendo privados — la documentación oficial es explícita: no hagas reset descartando commits que ya le diste a otra persona, porque su historial local divergirá silenciosamente del tuyo.

## Errores comunes

- Confundir `git restore <archivo>` (árbol de trabajo) con `git restore --staged <archivo>` (índice) es el error más común — la opción cambia qué capa se ve afectada, no solo cuánto se deshace.
- `git reset --hard` es el único comando de esta tabla que puede destruir trabajo sin commitear sin ninguna vía de recuperación. Ejecuta `git status` justo antes.
- Ejecuta `git status` antes y después de cualquier comando de recuperación — es la forma más barata de confirmar que cambiaste la capa que pretendías.

## Ejercicio

En un repositorio de práctica: (1) edita un archivo sin prepararlo, luego descarta la edición con `git restore`; (2) prepara un archivo, luego sácalo de la preparación con `git restore --staged` y confirma que la edición sigue presente; (3) haz commit de un cambio, luego deshaz su efecto con `git revert` y confirma que ahora existen dos commits; (4) haz un commit más, deshazlo localmente con `git reset --mixed HEAD~1`, confirma con `git status` que el cambio ahora está fuera de la preparación, y luego encuentra de nuevo el commit descartado con `git reflog`.

## Referencias

- Manual de Git — [git-restore](https://git-scm.com/docs/git-restore)
- Manual de Git — [git-revert](https://git-scm.com/docs/git-revert)
- Manual de Git — [git-reset](https://git-scm.com/docs/git-reset)
- Manual de Git — [git-reflog](https://git-scm.com/docs/git-reflog)
- Pro Git (2.ª ed.) — [Reset Demystified](https://git-scm.com/book/en/v2/Git-Tools-Reset-Demystified)
