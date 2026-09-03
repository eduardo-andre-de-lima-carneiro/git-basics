# 5.3 Visual Studio

Visual Studio (el IDE completo de Windows, no VS Code) tiene compatibilidad con Git integrada a través del menú **Git** y dos ventanas acopladas.

## Flujo principal

- **Git > Clone Repository** o **Create Git Repository** inicia un repositorio y ofrece una plantilla de `.gitignore` y de licencia.
- La ventana **Git Changes** muestra los cambios sin preparar y preparados, el cuadro de mensaje de commit y los botones **Commit** / **Commit and Push**.
- La ventana **Git Repository** muestra el grafo de ramas, los commits entrantes y salientes, y permite fetch, pull, push, merge, rebase y la gestión de ramas.
- El selector de rama de la barra de estado cambia y crea ramas.
- Los conflictos de fusión se abren en el **Merge Editor**, con casillas para tomar los cambios entrantes, los actuales o ambos.

## Autenticación

Visual Studio usa **Git Credential Manager**, instalado junto con él, para guardar los tokens de las plataformas en el Windows Credential Store. Inicia sesión en **Git > Settings** o en el selector de cuenta; evita poner credenciales en las URL de los remotos.

## Nota sobre Team Explorer

Las versiones antiguas encaminaban Git por **Team Explorer**. Las versiones actuales usan el menú Git dedicado y las ventanas descritas arriba; esa es la experiencia más reciente que conviene aprender.

## Ejercicio

En un repositorio de práctica abierto en Visual Studio, haz un cambio, prepáralo en **Git Changes**, confirma el commit y abre la ventana **Git Repository** para verificar que el nuevo commit aparece en el grafo.
