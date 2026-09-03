# Conceptos básicos de Git

> Aprende Git entendiendo qué es, practicando lo que hace y ganando confianza paso a paso.

Conceptos básicos de Git es un curso práctico y guiado para quienes están empezando a usar Git, vienen de Subversion o buscan un modelo mental más claro del control de versiones cotidiano.

[Comenzar el curso](menu.md) | [Elegir idioma](#idiomas) | [Contribuir](../../../CONTRIBUTING.md)

## Por qué existe este curso

La documentación de Git puede ser técnicamente correcta y, aun así, resultar difícil de abordar. Este proyecto convierte las ideas esenciales en un recorrido guiado: explicaciones breves, comandos reales, resultados visibles y ejercicios que se pueden practicar en un repositorio temporal.

El objetivo no es memorizar una lista de comandos. Es entender el estado del proyecto, hacer cambios intencionales y recuperarse con calma cuando algo sale mal.

## Qué aprenderás

- Cómo el control de versiones protege y explica la historia de un proyecto.
- Cómo encajan el árbol de trabajo, el área de preparación, los commits, las ramas y los remotos de Git.
- Cómo instalar y configurar Git para proyectos personales o de equipo.
- Cómo revisar los cambios antes de confirmarlos.
- Cómo crear ramas, sincronizarse con remotos y colaborar de forma segura.
- Cómo elegir el comando de recuperación adecuado para un cambio no deseado.

## Mapa del curso

| Capítulo                                                                           | Enfoque                                               | Practicarás                                                                            |
| ---------------------------------------------------------------------------------- | ----------------------------------------------------- | -------------------------------------------------------------------------------------- |
| [1. Conceptos básicos](chapters/01-basic-concepts/README.md)                       | Las ideas detrás del control de versiones y Git       | Pensar en instantáneas, historial y estados del proyecto                               |
| [2. Instalación y configuración](chapters/02-installation-configuration/README.md) | Preparar Git para usarlo                              | Comprobar la instalación, la identidad, los valores predeterminados y los repositorios |
| [3. Comandos y operaciones](chapters/03-commands-operations/README.md)             | Crear un flujo de trabajo diario confiable            | Commits, ramas, remotos, fusiones, ejercicios y recuperación                           |
| [4. Integración con plataformas](chapters/04-platform-integration/README.md)       | Conectar Git con plataformas de colaboración alojadas | Pull requests, merge requests, permisos, automatización y entregas seguras             |
| [5. Integración con IDE y editores](chapters/05-ide-integration/README.md)         | Usar Git desde editores de código e IDE               | Preparación, diffs, ramas, resolución de conflictos y configuración de herramientas    |

## Una primera práctica rápida

Cuando Git esté instalado, crea un repositorio temporal para practicar:

```bash
mkdir git-practice
cd git-practice
git init
printf "My first Git file\n" > notes.txt
git add notes.txt
git commit -m "Add first practice file"
git log --oneline
```

Acabas de crear un repositorio, preparar un cambio, registrar un commit y revisar su historial. El capítulo 1 explica qué ocurrió en cada etapa.

## Cómo usar la documentación

1. Empieza por el [menú de documentación](menu.md).
2. Lee el capítulo 1 antes de concentrarte en memorizar comandos.
3. Completa los pasos de configuración del capítulo 2.
4. Trabaja el capítulo 3 en un repositorio temporal.
5. Explora el capítulo 4 para conocer la plataforma que usa tu equipo.
6. Lee el capítulo 5 para tu editor de código o IDE.
7. Consulta el [glosario](glossary.md) cuando no conozcas un término.

Cada lección es un archivo Markdown independiente, enlazado mediante rutas relativas para poder leerlo directamente en GitHub.

## Idiomas

El curso está disponible en cuatro idiomas:

- [English](../../../README.md)
- [Français](../fr/README.md)
- [Português (Brasil)](../pt-br/README.md)
- [Español](README.md)

## Valores del proyecto

- **Práctico:** los ejemplos deben conducir a algo que el estudiante pueda observar.
- **Accesible:** explica la idea antes de presentar el comando.
- **Seguro:** usa repositorios temporales y deja claras las operaciones destructivas.
- **Abierto:** conserva la documentación gratuita, reutilizable y fácil de mejorar.

## Contribuir

¿Encontraste una explicación confusa, un ejercicio que falta o un enlace roto? Lee la [guía de contribución](../../../CONTRIBUTING.md) y ayuda a mejorar la primera experiencia con Git de la próxima persona que aprenda.

## Origen

Este curso surgió de una experiencia en DevSecOps apoyando a equipos que migraban de Subversion a Git. La documentación oficial y los sitios de referencia eran útiles, pero algunas personas necesitaban un camino más guiado y práctico para iniciarse. Conceptos básicos de Git se creó para ofrecer ese camino y facilitar que el aprendizaje se comparta.

El proyecto es intencionalmente colaborativo. Se agradecen los comentarios, las correcciones, los ejemplos y las traducciones.
