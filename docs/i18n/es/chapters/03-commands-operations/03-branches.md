# 3.3 Ramas y colaboración

Las ramas son nombres móviles que apuntan a commits. Crea el trabajo lejos de la base compartida:

```bash
git switch -c feature/example
git switch main
git merge feature/example
```

## Qué hacen realmente `switch -c` y `merge`

- [`git switch -c <nombre>`](https://git-scm.com/docs/git-switch) crea la nueva rama y cambia a ella en un solo paso transaccional — equivalente a `git branch <nombre>` seguido de `git switch <nombre>`, salvo que la rama nunca queda a medio crear si el cambio falla.
- [`git merge`](https://git-scm.com/docs/git-merge) se comporta de forma distinta según la forma del historial:
  - **Fast-forward:** si la punta de la rama actual es antecesora de la rama que se está fusionando — ningún commit local divergió — Git simplemente mueve el puntero de la rama hacia adelante. No se crea ningún commit de fusión.
  - **Commit de fusión:** si ambas ramas tienen commits que la otra no tiene, Git crea un nuevo commit con dos padres para combinarlas. Pasa `--no-ff` para forzar un commit de fusión incluso cuando sería posible un fast-forward, si quieres que la existencia de la rama quede visible en el historial.

## Un conflicto es una decisión, no un fallo

Antes de fusionar, examina el historial y resuelve los conflictos deliberadamente. Un conflicto significa que las mismas líneas cambiaron en ambos lados y Git no puede adivinar qué versión — o combinación — es correcta; es una solicitud de decisión humana, no un fallo de comando que ocultar aceptando un lado a ciegas.

## Errores comunes

- Las ramas de larga vida acumulan divergencia y producen conflictos más grandes y difíciles de resolver. Fusionar `main` periódicamente en la rama de funcionalidad (o hacerle rebase, para trabajo aún no publicado) mantiene pequeña la fusión final.
- `git merge --no-ff` frente a un fast-forward simple cambia de forma permanente el aspecto de tu historial — acuerda una convención con el equipo en lugar de mezclar ambos de forma inconsistente.

## Ejercicio

En un repositorio de práctica, crea una rama, haz un commit y fusiónala de vuelta en `main` sin ningún otro commit de por medio — confirma con `git log --oneline --graph` que no se creó ningún commit de fusión (un fast-forward). Luego crea una segunda rama, haz también un commit en `main` y fusiona de nuevo — confirma que esta vez sí aparece un commit de fusión.

## Referencias

- Manual de Git — [git-switch](https://git-scm.com/docs/git-switch)
- Manual de Git — [git-branch](https://git-scm.com/docs/git-branch)
- Manual de Git — [git-merge](https://git-scm.com/docs/git-merge)
- Pro Git (2.ª ed.) — [Branches in a Nutshell](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
