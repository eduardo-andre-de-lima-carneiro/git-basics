# 5.6 Flujos asistidos por IA

Esta sección es opcional. Muchos editores ahora ofrecen asistentes de IA que pueden redactar mensajes de commit, resumir un diff, explicar un conflicto o sugerir la descripción de un pull request.

## Dónde aparece

- **Visual Studio Code** y **Visual Studio**: GitHub Copilot puede generar un mensaje de commit a partir de los cambios preparados y redactar el texto del pull request.
- **IDE de JetBrains**: el AI Assistant ofrece "Generate Commit Message" en la ventana **Commit**.
- Clientes independientes como GitKraken exponen ayudas similares para los mensajes de commit.

## Cómo usarlo de forma segura

- Trata el texto generado como un primer borrador. Lee el diff tú mismo y edita el mensaje para que diga *por qué*, no solo *qué*.
- Nunca dejes que un asistente prepare o confirme cambios que no has revisado.
- Da por hecho que el diff y el contenido de los archivos pueden enviarse a un servicio externo. No uses estas funciones en repositorios con secretos o código restringido sin la aprobación de tu organización.
- Mantén las convenciones de mensaje que tu equipo ya acordó; un asistente no las conoce salvo que se le indiquen.

## Ejercicio

Prepara un cambio pequeño en un repositorio de práctica y pide un mensaje de commit al asistente de tu editor. Reescríbelo con tus propias palabras para explicar el motivo del cambio y luego confirma el commit.
