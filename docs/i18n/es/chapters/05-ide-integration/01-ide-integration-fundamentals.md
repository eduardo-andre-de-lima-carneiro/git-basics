# 5.1 Fundamentos de la integración con IDE

La integración de Git de un editor es una vista sobre el mismo repositorio que usa la línea de comandos. Ejecuta `git status`, `git diff` y `git log` por ti y convierte las acciones comunes en botones, marcas en el margen y paneles.

## Qué añade la integración

- Un panel de control de versiones que enumera los archivos modificados, preparados y sin seguimiento.
- Marcas en el margen que muestran las líneas añadidas, cambiadas y eliminadas.
- Un diff visual de un archivo o de un solo bloque de líneas (un "hunk").
- Un cuadro de commit para el mensaje, con la preparación hecha al hacer clic en archivos o hunks.
- Un indicador de rama en la barra de estado para cambiar y crear ramas.
- Una vista de tres paneles para resolver conflictos de fusión.

## Cuándo seguir usando la terminal

Recurre a la línea de comandos cuando necesites control exacto o una operación poco común: detalles de un rebase interactivo, `git reflog`, `git bisect`, filtros personalizados de `git log` o scripting. El editor y la terminal actúan sobre el mismo directorio `.git`, así que puedes alternar entre ambos con libertad.

## Configuración compartida

- Configura la identidad una vez con `git config --global user.name` y `user.email` (ver [2.2 Configurar la identidad y los valores predeterminados](../02-installation-configuration/02-configure.md)).
- Deja que un credential helper o el llavero del sistema guarde los tokens para que el editor no los pida en cada push.
- Decide si las carpetas propias del editor, como `.vscode/` o `.idea/`, deben estar en el repositorio; si no, agrégalas al `.gitignore`.
- Mantén la firma (SSH o GPG) configurada en el propio Git para que los commits hechos desde el editor también se firmen.

## Ejercicio

Abre un repositorio de práctica existente en tu editor. Cambia una línea de un archivo y comprueba que el panel de control de versiones del editor y `git status` en una terminal informan del mismo cambio.
