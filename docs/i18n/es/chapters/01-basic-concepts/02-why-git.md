# 1.2 Por qué Git

Git es distribuido: cada clon contiene el historial del proyecto necesario para la mayoría de las operaciones locales. Esto hace que los commits, las comparaciones y la creación de ramas sean rápidos y estén disponibles sin conexión.

Git también proporciona puntos de control explícitos llamados commits. Un buen commit responde: ¿qué cambió y por qué?

## De dónde viene Git

Git fue creado en 2005 por Linus Torvalds y la comunidad del kernel de Linux, después de que la herramienta propietaria que el proyecto del kernel venía usando, BitKeeper, dejara de estar disponible de forma gratuita. Los objetivos de diseño eran velocidad, un diseño simple, un fuerte soporte para el desarrollo no lineal (ramas), ser totalmente distribuido y poder manejar con eficiencia proyectos grandes como el propio kernel de Linux. Consulta la [breve historia de Git](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Una-breve-historia-de-Git) en el libro Pro Git para la historia completa.

## Instantáneas, no diffs

A diferencia de los sistemas que almacenan una lista de cambios por archivo, Git almacena una instantánea de todo el proyecto en cada commit; un archivo que no ha cambiado simplemente se enlaza a la versión idéntica anterior en lugar de duplicarse. Cada objeto recibe una suma de verificación antes de almacenarse — históricamente con SHA-1, con SHA-256 disponible como opción más reciente a través de la [transición de función hash](https://git-scm.com/docs/hash-function-transition) de Git — de modo que la corrupción silenciosa o la manipulación sean detectables. Consulta [Fundamentos de Git](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Fundamentos-de-Git) en el libro Pro Git.

## Git vs. Subversion vs. Mercurial

| | Git | Subversion (SVN) | Mercurial |
|---|---|---|---|
| Modelo | [Distribuido](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Acerca-del-Control-de-Versiones) | [Centralizado](https://subversion.apache.org/) | [Distribuido](https://www.mercurial-scm.org/) |
| Costo de ramificar | Una rama es un puntero móvil a un commit — [casi instantáneo de crear](https://git-scm.com/book/es/v2/Ramificaciones-en-Git-%c2%bfQu%c3%a9-es-una-rama%3F) | Una [copia barata del lado del servidor](https://svnbook.red-bean.com/en/1.7/svn.branchmerge.using.html), pero crearla y usarla igual requiere el servidor central | Barato; las ramas y los bookmarks viven en el clon local |
| Capacidad sin conexión | Total — commit, diff, log y rama funcionan sin red | Limitada — la mayoría de las operaciones necesitan contactar al servidor | Total — "cada clon contiene todo el historial del proyecto" |
| Uso típico hoy | Elección por defecto para la mayoría de los proyectos nuevos; usado por el [96 % de los desarrolladores profesionales](https://git-scm.com/about) (encuesta de Stack Overflow de 2022) | Todavía presente en algunas empresas que quieren control de acceso centralizado sobre el historial | De nicho; sobre todo implementaciones heredadas, ampliamente superado por Git |

## Errores comunes

- **Un commit no es un diff.** Git registra la instantánea completa preparada en el área de staging en el momento del commit, no solo lo que cambió — eso es lo que hace que hacer checkout de un commit antiguo sea una operación directa sobre el árbol de archivos, en lugar de reaplicar una cadena de parches. Consulta [Guardando cambios en el Repositorio](https://git-scm.com/book/es/v2/Fundamentos-de-Git-Guardando-cambios-en-el-Repositorio).

## Idea clave

Git no es solo un sistema para hacer copias de seguridad de archivos. Es una herramienta para construir, inspeccionar y compartir una línea de tiempo de cambios intencionales.

## Referencias

Esta página se basa en las siguientes fuentes oficiales:

- Pro Git (2.ª ed.) — [Una breve historia de Git](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Una-breve-historia-de-Git)
- Pro Git (2.ª ed.) — [Fundamentos de Git](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Fundamentos-de-Git)
- Manual de referencia de Git — [Transición de función hash de Git](https://git-scm.com/docs/hash-function-transition)
- git-scm.com — [About Git](https://git-scm.com/about)
- Apache Subversion — [subversion.apache.org](https://subversion.apache.org/)
- Mercurial — [mercurial-scm.org](https://www.mercurial-scm.org/)
