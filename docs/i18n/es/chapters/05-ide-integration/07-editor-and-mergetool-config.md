# 5.7 Configuración del editor y la herramienta de fusión

Git usa tres ajustes para entregar trabajo a un programa externo: `core.editor` para texto, `merge.tool` para la resolución de conflictos y `diff.tool` para ver los cambios.

## Definir el editor de commit

```bash
git config --global core.editor "code --wait"     # VS Code
git config --global core.editor "codium --wait"   # VSCodium
```

Para un IDE de JetBrains, usa su lanzador de línea de comandos, por ejemplo `git config --global core.editor "idea --wait"` una vez instalado el lanzador.

## Configurar una herramienta de fusión

```bash
git config --global merge.tool vscode
git config --global mergetool.vscode.cmd 'code --wait --merge $REMOTE $LOCAL $BASE $MERGED'
git config --global mergetool.keepBackup false
```

Cuando ocurra un conflicto, ejecuta:

```bash
git mergetool
```

Git abre la herramienta configurada para cada archivo en conflicto. Después de guardar y cerrar, marca el resultado con `git add` y continúa la fusión o el rebase.

## Configurar una herramienta de diff

```bash
git config --global diff.tool vscode
git config --global difftool.vscode.cmd 'code --wait --diff $LOCAL $REMOTE'
git difftool HEAD~1 HEAD
```

Visual Studio y los IDE de JetBrains también se registran como herramientas de fusión y de diff durante la instalación en la mayoría de las plataformas; consulta su documentación para el nombre exacto de `merge.tool`.

## Ejercicio

Configura `merge.tool`, crea un conflicto en un repositorio de práctica editando la misma línea en dos ramas, ejecuta `git mergetool`, resuélvelo en el editor y finaliza con `git commit`.
