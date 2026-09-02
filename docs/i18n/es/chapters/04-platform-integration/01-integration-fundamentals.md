# 4.1 Fundamentos de la integración

Las plataformas alojadas añaden servicios de colaboración y entrega alrededor de un repositorio Git. Los comandos locales siguen siendo conocidos; la plataforma proporciona identidad, permisos, revisión, automatización y visibilidad del proyecto.

## El flujo común

1. Crea o selecciona un repositorio remoto.
2. Conecta el repositorio local con `git remote add origin <repository-url>`.
3. Envía una rama con `git push -u origin <branch-name>`.
4. Abre una solicitud de extracción o una solicitud de combinación para su revisión.
5. Deja que se ejecuten las comprobaciones obligatorias antes de combinar.
6. Elimina la rama de corta duración después de integrar el cambio.

## Elige HTTPS o SSH

HTTPS es una opción sencilla para empezar y normalmente utiliza un token de acceso personal en lugar de la contraseña de la cuenta. SSH utiliza un par de claves y resulta práctico para trabajar frecuentemente desde la línea de comandos. Nunca coloques tokens, claves privadas ni credenciales en un repositorio.

## Qué configurar

Como mínimo, acuerden la rama predeterminada, las reglas de protección de ramas, los requisitos de revisión, las comprobaciones de estado, la vinculación de incidencias y quién puede enviar cambios o combinar ramas. Estas políticas forman parte del proceso de entrega del equipo, no son solo decoración de la plataforma.
