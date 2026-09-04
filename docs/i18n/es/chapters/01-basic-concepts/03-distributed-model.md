# 1.3 El modelo distribuido de Git

Un repositorio individual normalmente tiene un árbol de trabajo, un historial local y repositorios remotos opcionales. Un remoto es un punto de colaboración, no la definición de Git en sí. Consulta la [visión general del control de versiones](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Acerca-del-Control-de-Versiones) del libro Pro Git para ver en qué se diferencia esto de un VCS centralizado.

## Operaciones comunes

Las operaciones habituales tienen propósitos distintos:

- [`clone`](https://git-scm.com/docs/git-clone/es) copia un repositorio, incluyendo todo su historial.
- [`fetch`](https://git-scm.com/docs/git-fetch/es) descarga el historial remoto sin cambiar el trabajo local — solo actualiza las ramas de seguimiento remoto (p. ej., `origin/main`).
- [`pull`](https://git-scm.com/docs/git-pull/es) ejecuta `fetch` y luego integra el resultado en la rama actual (merge o rebase, según la configuración).
- [`push`](https://git-scm.com/docs/git-push/es) publica los commits locales en un remoto.

## Errores comunes

- **"Distribuido" no significa "sin servidor central en la práctica".** El propio Git no exige un repositorio central — cualquier clon puede actuar como remoto de cualquier otro —, pero la mayoría de los equipos igual designan un remoto (a menudo alojado en GitHub, GitLab o similar) como la fuente de verdad compartida, por convención, y no porque Git lo exija técnicamente.
- **`fetch` es seguro, `pull` puede sorprenderte.** Como `pull` también hace merge o rebase, ejecuta primero [`git fetch`](https://git-scm.com/docs/git-fetch/es) si quieres inspeccionar los cambios entrantes antes de que toquen tu rama de trabajo.
- **El nombre de un remoto es solo una etiqueta.** [`git remote`](https://git-scm.com/docs/git-remote/es) muestra los nombres cortos (como `origin`) asociados a URLs reales; el nombre no tiene ningún significado especial para Git más allá de esa asociación.

## Ejercicio

Ejecuta `git remote -v` en un clon existente para ver las URLs detrás de los nombres de sus remotos. Luego ejecuta `git fetch` y compara `git log main` con `git log origin/main` — la diferencia es exactamente lo que `pull` traería.

## Referencias

Esta página se basa en las siguientes fuentes oficiales:

- Pro Git (2.ª ed.) — [Acerca del Control de Versiones](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Acerca-del-Control-de-Versiones)
- Manual de referencia de Git — [git-clone](https://git-scm.com/docs/git-clone/es)
- Manual de referencia de Git — [git-fetch](https://git-scm.com/docs/git-fetch/es)
- Manual de referencia de Git — [git-pull](https://git-scm.com/docs/git-pull/es)
- Manual de referencia de Git — [git-push](https://git-scm.com/docs/git-push/es)
- Manual de referencia de Git — [git-remote](https://git-scm.com/docs/git-remote/es)
