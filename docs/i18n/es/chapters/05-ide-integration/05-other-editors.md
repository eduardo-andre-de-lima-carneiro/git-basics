# 5.5 Otros editores

Los mismos conceptos de Git aparecen en muchas otras herramientas. Esta es una orientación breve, no una guía completa de cada una.

- [**Xcode**](https://developer.apple.com/documentation/xcode/source-control-management) tiene un menú y un navegador **Source Control** para commit, push, pull, rama y resolución de conflictos en proyectos de macOS.
- **Eclipse** usa el complemento [**EGit**](https://wiki.eclipse.org/EGit/User_Guide), que añade una vista **Git Staging** y una vista **History**.
- [**Sublime Merge**](https://www.sublimemerge.com/docs/) es un cliente Git independiente de los creadores de Sublime Text, con un grafo de commits rápido y preparación por hunk; Sublime Text se integra con él.
- **Vim y Neovim** suelen usar [`vim-fugitive`](https://github.com/tpope/vim-fugitive) para los comandos y [`gitsigns.nvim`](https://github.com/lewis6991/gitsigns.nvim) (Neovim) o `vim-gitgutter` para las marcas en el margen.
- **Emacs** se apoya en [**Magit**](https://magit.vc/), una interfaz guiada por teclado que refleja la mayoría de los comandos de Git.
- [**GitHub Desktop**](https://docs.github.com/es/desktop) y **GitKraken** son clientes gráficos que combinan bien con cualquier editor.

Sea cual sea la herramienta, está llamando a Git. Si un panel y `git status` no coinciden, actualiza el panel o confía en la línea de comandos.

## Ejercicio

Elige una herramienta de esta lista que no uses habitualmente. Abre en ella un repositorio de práctica, haz un commit y verifica el resultado con `git log --oneline` en una terminal.

## Referencias

- Apple Developer — [Source control management in Xcode](https://developer.apple.com/documentation/xcode/source-control-management)
- Eclipse — [EGit User Guide](https://wiki.eclipse.org/EGit/User_Guide)
- [Documentación de Sublime Merge](https://www.sublimemerge.com/docs/)
- GitHub — [tpope/vim-fugitive](https://github.com/tpope/vim-fugitive)
- GitHub — [lewis6991/gitsigns.nvim](https://github.com/lewis6991/gitsigns.nvim)
- [Magit — a Git porcelain inside Emacs](https://magit.vc/)
- GitHub Docs — [GitHub Desktop](https://docs.github.com/es/desktop)
