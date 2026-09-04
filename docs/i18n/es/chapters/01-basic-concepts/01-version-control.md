# 1.1 Sistemas de control de versiones

El control de versiones registra los cambios de los archivos a lo largo del tiempo. Permite a un equipo comparar revisiones, identificar autores, restaurar estados anteriores y trabajar en cambios separados sin sobrescribirse.

## El problema que resuelve

Sin control de versiones, nombres como `project-final-final-2` se convierten en el historial. Git conserva el historial en un repositorio estructurado.

## Tres generaciones de control de versiones

Los sistemas de control de versiones se dividen en tres grandes categorías, descritas en la [visión general del control de versiones](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Acerca-del-Control-de-Versiones) del libro Pro Git:

- **VCS local** (p. ej., RCS) mantiene una base de datos de parches en una sola máquina. No hay colaboración posible, ni protección si esa máquina se pierde.
- **VCS centralizado** (p. ej., CVS, Subversion) almacena todo el historial en un servidor; los clientes hacen checkout de copias de trabajo. La colaboración funciona, pero el servidor es un punto único de fallo — si se cae, o su base de datos se corrompe sin copia de seguridad, el historial del proyecto puede perderse.
- **VCS distribuido** (p. ej., Git, Mercurial) da a cada clon el historial completo. Cualquier clon puede restaurar el proyecto si se pierde un servidor, y la mayoría de las operaciones del día a día no necesitan la red.

## Errores comunes

- **El control de versiones no es un servicio de copia de seguridad.** Una copia de seguridad copia archivos; el control de versiones también registra *por qué* cambió algo y permite comparar, identificar al autor (blame) y revertir cambios individuales.
- **Un repositorio no es lo mismo que una única copia con checkout.** Borrar tu copia de trabajo no borra el historial que ya está confirmado y almacenado de forma segura en otro lugar (localmente o en un remoto).

## Práctica

Crea un archivo de texto pequeño, cámbialo dos veces y anota qué necesitarías saber para recuperar la primera versión. Esa lista representa el valor que ofrece el control de versiones.

## Referencias

Esta página se basa en las siguientes fuentes oficiales:

- Pro Git (2.ª ed.) — [Acerca del Control de Versiones](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Acerca-del-Control-de-Versiones)
- Manual de referencia de Git — [git-scm.com/docs](https://git-scm.com/docs)
