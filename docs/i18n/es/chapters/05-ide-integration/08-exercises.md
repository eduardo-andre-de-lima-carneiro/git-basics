# 5.8 Ejercicios prácticos

Realízalos en un repositorio temporal, usando tu editor para las acciones de Git y una terminal para verificar.

1. Prepara un solo hunk (no el archivo entero) desde la vista de diff del editor, confirma el commit y verifica con `git show`.
2. Crea una rama y cámbiate a ella desde la barra de estado, haz un commit y vuelve a la anterior.
3. Configura tu editor como `core.editor`, ejecuta `git commit` sin `-m` y escribe el mensaje en el editor.
4. Crea un conflicto de fusión en una línea, resuélvelo con la vista de fusión de tres paneles del editor y finaliza la fusión.
5. Configura `merge.tool` y repite el ejercicio 4 usando `git mergetool` en lugar del panel integrado.
6. Haz un commit firmado desde el editor y verifícalo con `git log --show-signature`.

Para cada ejercicio, anota la acción realizada en el editor y la salida del comando que confirmó el resultado.

## Referencias

- Manual de Git — [git-mergetool](https://git-scm.com/docs/git-mergetool)
- Manual de Git — [git-difftool](https://git-scm.com/docs/git-difftool)
- Pro Git (2.ª ed.) — [Signing Your Work](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work)
