# 5.5 Otros editores

Los mismos conceptos de Git aparecen en muchas otras herramientas. Esta es una orientación breve, no una guía completa de cada una.

- **Xcode** tiene un menú y un navegador **Source Control** para commit, push, pull, rama y resolución de conflictos en proyectos de macOS.
- **Eclipse** usa el complemento **EGit**, que añade una vista **Git Staging** y una vista **History**.
- **Sublime Merge** es un cliente Git independiente de los creadores de Sublime Text, con un grafo de commits rápido y preparación por hunk; Sublime Text se integra con él.
- **Vim y Neovim** suelen usar `vim-fugitive` para los comandos y `gitsigns` (Neovim) o `vim-gitgutter` para las marcas en el margen.
- **Emacs** se apoya en **Magit**, una interfaz guiada por teclado que refleja la mayoría de los comandos de Git.
- **GitHub Desktop** y **GitKraken** son clientes gráficos que combinan bien con cualquier editor.

Sea cual sea la herramienta, está llamando a Git. Si un panel y `git status` no coinciden, actualiza el panel o confía en la línea de comandos.

## Ejercicio

Elige una herramienta de esta lista que no uses habitualmente. Abre en ella un repositorio de práctica, haz un commit y verifica el resultado con `git log --oneline` en una terminal.
