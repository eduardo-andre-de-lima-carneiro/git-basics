# 2.2 Configurar la identidad y los valores predeterminados

Define el nombre y el correo electrónico que Git registra en los commits nuevos:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
```

`user.name` y `user.email` quedan grabados en cada commit que haces y no se pueden cambiar retroactivamente sin reescribir el historial, así que configúralos antes de tu primer commit. `init.defaultBranch` solo afecta a los repositorios creados después con `git init`; no renombra las ramas de los repositorios que ya tienes.

Revisa la configuración efectiva, y de qué archivo proviene cada valor, con:

```bash
git config --list --show-origin
```

## Niveles de alcance de la configuración

Git lee la configuración de varios archivos y los combina, y un alcance más específico prevalece sobre uno menos específico. De menor a mayor precedencia:

| Alcance | Opción | Se aplica a | Ubicación típica |
| --- | --- | --- | --- |
| Sistema | `--system` | Todos los usuarios de la máquina | `/etc/gitconfig` (Linux/macOS); `C:\ProgramData\Git\config` (Windows) |
| Global | `--global` | El usuario actual, todos los repositorios | `~/.gitconfig` o `$XDG_CONFIG_HOME/git/config` (Linux/macOS); `%USERPROFILE%\.gitconfig` (Windows) |
| Local | `--local` (predeterminado) | Solo el repositorio actual | `.git/config` dentro del repositorio |
| Worktree | `--worktree` | Un worktree de un repositorio con varios worktrees | `.git/config.worktree` (solo se usa si `extensions.worktreeConfig` está habilitado) |

Local prevalece sobre global, que prevalece sobre sistema; worktree, cuando está habilitado, prevalece sobre los tres. Ejecutar `git config` sin una opción de alcance escribe en `--local`, así que ejecútalo desde dentro de un repositorio solo cuando quieras fijar un valor para ese repositorio en concreto. Consulta la [referencia de `git-config`](https://git-scm.com/docs/git-config#FILES) para conocer las reglas completas de descubrimiento de archivos, incluida la forma en que se resuelve `$XDG_CONFIG_HOME`.

## Configuración del editor

Git abre un editor externo para los mensajes de commit, el rebase interactivo y tareas similares, controlado por `core.editor`. Este curso detalla la configuración del editor y la herramienta de fusión en [Configuración del editor y la herramienta de fusión](../05-ide-integration/07-editor-and-mergetool-config.md); un ejemplo mínimo:

```bash
git config --global core.editor "code --wait"
```

## Errores comunes

- **Olvidar `user.email`.** Sin él, Git se niega a hacer el commit o usa una dirección adivinada a partir de tu usuario del sistema y el nombre de la máquina, lo que genera commits atribuidos a la persona equivocada, un problema especialmente delicado en máquinas compartidas o de CI. Confírmalo con `git config --get user.email` antes de tu primer commit en un entorno nuevo.
- **Definir la identidad solo de forma global en una máquina compartida.** Si varias personas o roles usan la misma cuenta (por ejemplo, un runner de CI), define `user.name`/`user.email` con `--local` por repositorio en lugar de depender de una única identidad global.
- **Confundir la precedencia de los alcances.** Un valor definido con `--local` siempre prevalece sobre la misma clave definida con `--global`, aunque el valor global se haya definido más recientemente. Usa `git config --list --show-origin` cuando un ajuste no parezca surtir efecto.

## Ejercicio

Ejecuta `git config --global user.name "Your Name"`, `git config --global user.email "you@example.com"` y `git config --global init.defaultBranch main`. Luego ejecuta `git config --list --show-origin` y confirma que los tres valores aparecen con tu archivo de configuración global como origen.

## Referencias

Estas son las fuentes oficiales consultadas para esta página:

- Manual de referencia de Git — [git-config](https://git-scm.com/docs/git-config)
- Pro Git (2.ª edición) — [Configurando Git por primera vez](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Configurando-Git-por-primera-vez)
- Pro Git (2.ª edición) — [Configuración de Git](https://git-scm.com/book/es/v2/Personalizaci%c3%b3n-de-Git-Configuraci%c3%b3n-de-Git)
