# 5.6 Flujos asistidos por IA

Esta sección es opcional. Muchos editores ahora ofrecen asistentes de IA que pueden redactar mensajes de commit, resumir un diff, explicar un conflicto o sugerir la descripción de un pull request.

## Dónde aparece

- **Visual Studio Code** y **Visual Studio**: [GitHub Copilot puede generar un mensaje de commit](https://docs.github.com/es/copilot/responsible-use/copilot-commit-message-generation) a partir de los cambios preparados y redactar el texto del pull request. VS Code también expone esto desde la [vista Source Control](https://code.visualstudio.com/docs/sourcecontrol/overview).
- **IDE de JetBrains**: el [AI Assistant](https://www.jetbrains.com/help/idea/ai-assistant.html) ofrece "Generate Commit Message" en la ventana **Commit**.
- Clientes independientes como GitKraken exponen ayudas similares para los mensajes de commit.

## Cómo usarlo de forma segura

- Trata el texto generado como un primer borrador. Lee el diff tú mismo y edita el mensaje para que diga *por qué*, no solo *qué*.
- Nunca dejes que un asistente prepare o confirme cambios que no has revisado.
- Da por hecho que el diff y el contenido de los archivos pueden enviarse a un servicio externo. No uses estas funciones en repositorios con secretos o código restringido sin la aprobación de tu organización.
- Mantén las convenciones de mensaje que tu equipo ya acordó; un asistente no las conoce salvo que se le indiquen.

## Ejercicio

Prepara un cambio pequeño en un repositorio de práctica y pide un mensaje de commit al asistente de tu editor. Reescríbelo con tus propias palabras para explicar el motivo del cambio y luego confirma el commit.

## Referencias

- GitHub Docs — [Generación de mensajes de commit (uso responsable de Copilot)](https://docs.github.com/es/copilot/responsible-use/copilot-commit-message-generation)
- Visual Studio Code — [Using Git source control in VS Code](https://code.visualstudio.com/docs/sourcecontrol/overview)
- JetBrains — [AI Assistant](https://www.jetbrains.com/help/idea/ai-assistant.html)
