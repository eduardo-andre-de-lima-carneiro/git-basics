# 3.1 El flujo de trabajo diario

Cada cambio pasa por tres lugares antes de estar seguro: el **árbol de trabajo** (working tree, los archivos que editas), el **área de preparación** o índice (lo que entrará en el próximo commit) y el **historial del repositorio** (los commits ya registrados). Usa un ciclo pequeño y observable para moverte deliberadamente entre ellos:

```bash
git status
git add path/to/file
git diff --staged
git commit -m "Describe the change"
git status
```

## Qué comprueba realmente cada comando

- [`git status`](https://git-scm.com/docs/git-status) informa de tres grupos: cambios preparados para el commit, cambios no preparados y archivos no rastreados. Saber en qué grupo está un archivo te dice exactamente qué le hará el siguiente `git add` o `git commit`.
- `git diff` sin argumentos compara el árbol de trabajo con el índice — muestra ediciones que *podrías* preparar pero que aún no has preparado.
- `git diff --staged` (sinónimo de `--cached`) compara el índice con `HEAD` — muestra exactamente lo que contendrá el próximo commit, por eso revisarlo antes de `git commit` detecta errores que `git diff` por sí solo no mostraría.
- [`git add`](https://git-scm.com/docs/git-add) copia el contenido del archivo al índice. Es una instantánea tomada en el momento en que lo ejecutas: si editas el archivo de nuevo después, tendrás que volver a ejecutar `git add` para incluir esas nuevas ediciones.

## Preparar solo parte de un archivo

`git add path/to/file` prepara el archivo completo. Cuando solo parte de tus ediciones pertenece a este commit, prepara bloques (hunks) individuales:

```bash
git add -p path/to/file
```

Esto recorre cada bloque modificado y pregunta si hay que prepararlo, lo que permite dividir ediciones no relacionadas dentro del mismo archivo en commits separados y enfocados.

## Errores comunes

- `git add .` prepara todo lo que hay bajo el directorio actual, incluidos archivos que tocaste por motivos no relacionados (impresiones de depuración, configuración local, archivos residuales del editor). Prefiere nombrar las rutas explícitamente, o usa `git add -p`, y mantén fuera de la preparación los archivos que nunca deben incluirse usando [`.gitignore`](https://git-scm.com/docs/gitignore).
- Hacer commit sin revisar `git diff --staged` es la forma más común de que cambios no relacionados terminen en un commit — el área de preparación puede contener, en silencio, más de lo que recuerdas haber añadido.

## Ejercicio

En un repositorio de práctica, edita dos archivos no relacionados. Prepara solo un bloque de un archivo con `git add -p`, confirma con `git status` y `git diff --staged` que el área de preparación contiene exactamente ese bloque, haz el commit y luego verifica que las otras ediciones siguen intactas con `git status`.

## Referencias

- Manual de Git — [git-status](https://git-scm.com/docs/git-status)
- Manual de Git — [git-diff](https://git-scm.com/docs/git-diff)
- Manual de Git — [git-add](https://git-scm.com/docs/git-add)
- Manual de Git — [gitignore](https://git-scm.com/docs/gitignore)
- Pro Git (2.ª ed.) — [Recording Changes to the Repository](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository)
