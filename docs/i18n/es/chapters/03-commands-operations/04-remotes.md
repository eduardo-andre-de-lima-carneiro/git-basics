# 3.4 Remotos y sincronización

Sincroniza de forma explícita:

```bash
git fetch origin
git log --oneline main..origin/main
git push -u origin feature/example
```

## Fetch, pull y push no son la misma operación

- [`git fetch`](https://git-scm.com/docs/git-fetch) descarga commits y actualiza tus referencias de seguimiento remoto (`origin/main`, por ejemplo), pero nunca toca tu árbol de trabajo ni tus ramas locales. Siempre es seguro ejecutarlo.
- `git log --oneline main..origin/main` muestra entonces exactamente qué commits existen en `origin/main` pero aún no en tu `main` local — un paso de revisión antes de integrar nada.
- [`git pull`](https://git-scm.com/docs/git-pull) ejecuta `git fetch` y luego integra el resultado en tu rama actual. **Su modo de integración por defecto es `--ff-only`**: si tu rama local ha divergido de la remota (ambos lados tienen commits nuevos), un `git pull` simple falla en lugar de crear silenciosamente un commit de fusión. Pasa `--rebase` para reaplicar tus commits locales sobre el historial obtenido en lugar de fusionar, o `--no-rebase` para permitir un commit de fusión.
- [`git push -u origin <rama>`](https://git-scm.com/docs/git-push) envía la rama y registra la relación de seguimiento upstream (`branch.<nombre>.remote` / `branch.<nombre>.merge`) en un solo paso. Después de eso, un `git push` y `git pull` simples en esta rama saben qué rama remota usar sin necesidad de nombrarla de nuevo.

## Errores comunes

- `git pull --rebase` reescribe los commits que reaplica. Eso es seguro para commits que solo tú tienes — deja de serlo en cuanto alguien más ya los ha obtenido, porque su historial y el tuyo dejarán de coincidir. Reserva `--rebase` para ramas que aún no has compartido, y prefiere una fusión (o `git pull --no-rebase`) cuando otras personas ya dependen de tus commits.
- Como el comportamiento por defecto de `git pull` ahora es fallar en vez de fusionar cuando hay divergencia, no des por hecho que la descripción de un tutorial antiguo ("pull siempre fusiona") sigue coincidiendo con tu versión de Git — revisa `pull.rebase` y `pull.ff` en `git config --list` si el comportamiento parece inconsistente entre máquinas.
- Haz fetch antes de hacer push al trabajar en una rama compartida; enviar sin antes comprobar `main..origin/main` arriesga un push rechazado o un conflicto evitable.

## Ejercicio

En un repositorio de práctica con un remoto configurado, ejecuta `git fetch origin` y luego `git log --oneline main..origin/main` para ver qué cambió de forma remota antes de tocar nada localmente. Envía una rama nueva con `git push -u origin <rama>` y luego confirma la relación de seguimiento con `git branch -vv`.

## Referencias

- Manual de Git — [git-fetch](https://git-scm.com/docs/git-fetch)
- Manual de Git — [git-pull](https://git-scm.com/docs/git-pull)
- Manual de Git — [git-push](https://git-scm.com/docs/git-push)
- Pro Git (2.ª ed.) — [Working with Remotes](https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes)
