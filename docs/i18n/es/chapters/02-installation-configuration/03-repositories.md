# 2.3 Repositorios locales y remotos

## `git init` frente a `git clone`

Empieza un proyecto nuevo en local con [`git init`](https://git-scm.com/docs/git-init):

```bash
git init
```

Esto crea un subdirectorio `.git` en la carpeta actual y la convierte en un repositorio Git sin commits y sin remoto configurado. Copia un proyecto existente, historial incluido, con [`git clone`](https://git-scm.com/docs/git-clone):

```bash
git clone <repository-url>
```

`git clone` crea un directorio nuevo, copia todo el historial, hace checkout de la rama predeterminada y configura automáticamente un remoto llamado `origin` que apunta al origen. Usa `git init` cuando un proyecto todavía no existe como repositorio Git; usa `git clone` cuando ya existe, ya sea en una plataforma de alojamiento o en una ruta local.

## Qué contiene realmente `.git/`

Ambos comandos te dejan con un directorio `.git/` que contiene los datos reales del repositorio; los archivos de trabajo que ves son solo una instantánea obtenida a partir de él. Incluye:

- `objects/` — el almacén direccionado por contenido de commits, trees y blobs (el historial en sí).
- `refs/heads/` y `refs/tags/` — punteros a las puntas de las ramas y a las etiquetas.
- `HEAD` — qué rama (o commit) está actualmente en checkout.
- `config` — la configuración local del repositorio (alcance `--local`, ver [2.2](02-configure.md)).
- Tras un clone, `refs/remotes/origin/` además de `remote.origin.url` y `remote.origin.fetch` en `config`, que registran de dónde se clonó el repositorio.

Eliminar `.git/` elimina todo el historial del repositorio; los archivos de trabajo que queden dejan de estar rastreados por Git.

## URL de remoto: HTTPS frente a SSH

Una URL de remoto adopta una de estas dos formas comunes:

```bash
# HTTPS
https://github.com/OWNER/REPOSITORY.git

# SSH
git@github.com:OWNER/REPOSITORY.git
```

HTTPS funciona desde cualquier red sin configuración local adicional y autentica con un token de acceso personal en lugar de la contraseña de tu cuenta; es el punto de partida más sencillo. SSH autentica con un par de claves registrado en la plataforma y resulta más cómodo para hacer push con frecuencia una vez configurado, ya que no pide un token cada vez. Ambas formas funcionan tanto con `git clone` como con `git remote add`. La configuración específica de cada plataforma para tokens y claves SSH se trata en el [Capítulo 4: Integración con plataformas](../04-platform-integration/01-integration-fundamentals.md#choose-https-or-ssh); usa la forma que ya coincida con cómo te autenticas en la plataforma.

## Inspeccionar y gestionar remotos

```bash
git remote -v
```

Enumera cada remoto configurado y su URL de fetch y push. Un repositorio recién clonado muestra `origin`; añade otro con `git remote add <name> <url>`, o cambia uno existente con `git remote set-url <name> <url>` (por ejemplo, para pasar `origin` de HTTPS a SSH sin volver a clonar).

## Errores comunes

- **Ejecutar `git clone` en un directorio que ya existe.** Git se niega a clonar en un directorio no vacío, así que `git clone <url>` dentro de una carpeta de proyecto existente falla; clona en un directorio nuevo o pasa un nombre de directorio de destino como segundo argumento.
- **Ejecutar `git init` dentro de un repositorio ya clonado.** Esto reinicializa `.git/` en el mismo sitio, algo normalmente inofensivo (el historial y la configuración existentes se conservan), pero rara vez es lo que se pretendía; comprueba `git status` o busca un `.git/` existente si no estás seguro de si una carpeta ya es un repositorio.
- **Suponer que un clone siempre usa `origin`.** `origin` es solo el nombre convencional que Git asigna automáticamente; un repositorio puede tener cero, uno o varios remotos con cualquier nombre.

## Ejercicio

Crea un directorio vacío, ejecuta `git init` dentro y luego `git remote -v`, confirmando que no muestra nada (todavía no hay remoto configurado). En otro directorio, clona cualquier repositorio público por HTTPS y ejecuta `git remote -v` de nuevo, confirmando que ahora aparece `origin` con una URL de fetch y otra de push.

## Referencias

Estas son las fuentes oficiales consultadas para esta página:

- Manual de referencia de Git — [git-init](https://git-scm.com/docs/git-init)
- Manual de referencia de Git — [git-clone](https://git-scm.com/docs/git-clone)
- Pro Git (2.ª edición) — [Obteniendo un repositorio Git](https://git-scm.com/book/es/v2/Fundamentos-de-Git-Obteniendo-un-repositorio-Git)
