# 2.1 Instalar Git

Se recomienda Git 2.23 o posterior para los ejemplos de `git switch` y `git restore` usados más adelante. Las versiones anteriores pueden requerir comandos equivalentes como `git checkout`. Instala Git con el gestor de paquetes o el instalador recomendado para tu sistema operativo, listados a continuación, o explora todas las opciones en la [página oficial de descargas](https://git-scm.com/downloads).

## Windows

Instala con [winget](https://learn.microsoft.com/es-es/windows/package-manager/winget/install), incluido de serie en Windows 10/11 modernos:

```bash
winget install --id Git.Git -e --source winget
```

También puedes descargar el instalador desde [git-scm.com/downloads/win](https://git-scm.com/downloads/win). Durante la instalación, mantén la opción predeterminada "Git from the command line and also from 3rd-party software" para que `git` se añada al `PATH`; de lo contrario, los comandos posteriores de este curso fallarán con "command not found" en una terminal recién abierta.

## macOS

Si usas [Homebrew](https://docs.brew.sh/Installation), instala con:

```bash
brew install git
```

macOS también ofrece Git a través de las Xcode Command Line Tools:

```bash
xcode-select --install
```

Las command line tools instalan un Git funcional, pero a menudo más antiguo que el de Homebrew. Si necesitas una versión reciente concreta, prefiere Homebrew y ejecuta `brew upgrade git` periódicamente.

## Linux

Usa el gestor de paquetes de tu distribución. En Debian y Ubuntu:

```bash
sudo apt install git
```

En Fedora y otras distribuciones basadas en `dnf`:

```bash
sudo dnf install git
```

Los repositorios de las distribuciones pueden quedar meses por detrás de la última versión de Git. Si necesitas una versión más reciente en Ubuntu, añade el [PPA git-core](https://git-scm.com/downloads/linux) antes de instalar; en Fedora, `dnf` suele seguir de cerca el proyecto original, por lo que rara vez es necesario.

## Verificar la instalación

```bash
git --version
```

La versión exacta puede variar. El comando debería mostrar una versión en lugar de un error. Si muestra "command not found" justo después de instalar en Windows, vuelve a abrir la terminal (o reinicia) para que el `PATH` actualizado tenga efecto.

## Después de instalar

Un Git recién instalado no tiene identidad ni nombre de rama predeterminado configurados. Antes de hacer tu primer commit, configúralos como se describe en [Configurar la identidad y los valores predeterminados](02-configure.md); un `user.email` sin configurar genera commits atribuidos a una dirección genérica en lugar de a ti.

## Errores comunes

- **Instalar desde una fuente no oficial.** Usa solo los gestores de paquetes y el instalador anteriores, o la [página oficial de descargas](https://git-scm.com/downloads); los "instaladores de Git" no oficiales que aparecen en búsquedas pueden estar desactualizados o ser inseguros.
- **Instalaciones múltiples de Git.** Instalar Git por más de un método (por ejemplo, Xcode tools y Homebrew) puede dejar un `git` más antiguo antes en el `PATH`. Ejecuta `which git` (macOS/Linux) o `where git` (Windows) para confirmar qué binario se ejecuta realmente.
- **Saltarse la verificación de versión.** Ejecuta siempre `git --version` justo después de instalar: es la forma más sencilla de confirmar que la instalación funcionó antes de investigar cualquier otro problema.

## Ejercicio

Instala Git para tu sistema operativo con el método anterior y ejecuta `git --version`, confirmando que reporta 2.23 o una versión posterior. Si reporta una versión anterior, actualiza con el mismo gestor de paquetes (`brew upgrade git`, `sudo apt update && sudo apt upgrade git` o `winget upgrade --id Git.Git`).

## Referencias

Estas son las fuentes oficiales consultadas para esta página:

- Git — [Downloads](https://git-scm.com/downloads)
- Pro Git (2.ª edición) — [Instalación de Git](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Instalaci%c3%b3n-de-Git)
- Homebrew — [Installation](https://docs.brew.sh/Installation)
- Microsoft Learn — [Instalar winget](https://learn.microsoft.com/es-es/windows/package-manager/winget/install)
