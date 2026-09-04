# 4.2 GitHub

GitHub combina repositorios Git alojados con pull requests, Issues, Actions, Projects, Packages y funciones de seguridad.

## Conectar y publicar

Crea un repositorio vacío en GitHub y ejecuta localmente:

```bash
git remote add origin https://github.com/OWNER/REPOSITORY.git
git push -u origin main
```

Sustituye `OWNER`, `REPOSITORY` y `main` por tus valores. No inicialices el repositorio de GitHub con un segundo README cuando tu repositorio local ya tenga uno, a menos que planees reconciliar los historiales.

## Autenticación

GitHub [eliminó la autenticación por contraseña para las operaciones Git en agosto de 2021](https://docs.github.com/es/authentication/keeping-your-account-and-data-secure/about-authentication-to-github); el aviso de HTTPS ahora espera un token, no la contraseña de tu cuenta. Elige una de estas opciones:

- **Un [personal access token](https://docs.github.com/es/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)** usado en lugar de la contraseña. GitHub recomienda los tokens *fine-grained* más recientes — con alcance limitado a repositorios y permisos específicos — frente a los tokens *classic*, que otorgan alcances amplios a nivel de cuenta como `repo`. Un token classic sin uso se revoca automáticamente al cabo de un año; un token fine-grained debe recibir una expiración al crearlo.
- **Una [clave SSH](https://docs.github.com/es/authentication/connecting-to-github-with-ssh)** — GitHub recomienda generar una clave Ed25519 — añadida a tu cuenta una sola vez, tras lo cual `git push`/`git pull` ya no piden más credenciales.
- **GitHub CLI (`gh auth login`) o Git Credential Manager**, que la propia documentación de GitHub sugiere antes que generar un token a mano, ya que estas herramientas gestionan el almacenamiento y la renovación del token por ti.

GitHub también [exige la autenticación de dos factores (2FA)](https://docs.github.com/es/authentication/securing-your-account-with-two-factor-authentication-2fa/about-two-factor-authentication) para las cuentas que contribuyen código, mediante una app TOTP, una llave de seguridad física o GitHub Mobile.

## Integraciones útiles

- Las pull requests proporcionan revisión, debate, aprobaciones obligatorias y comprobaciones de estado.
- GitHub Actions puede probar, analizar, empaquetar y desplegar con cada push o pull request.
- Las [reglas de protección de ramas](https://docs.github.com/es/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches) pueden exigir revisiones, comprobaciones aprobadas y commits firmados.
- Los entornos pueden restringir los despliegues y proteger los secretos de producción.
- Los webhooks y la API conectan los eventos del repositorio con sistemas externos.

Utiliza tokens de acceso personal detallados con los privilegios mínimos o GitHub Apps. Guarda los secretos de automatización en los secretos del repositorio o del entorno, nunca en los archivos de workflow ni en el código fuente.

## Errores comunes

- Un PAT classic pegado en un script con el alcance `repo` completo, cuando el script solo hace push a un único repositorio — la filtración de ese token compromete todos los repositorios a los que la cuenta tiene acceso. Usa en su lugar un token fine-grained limitado a ese único repositorio.
- Establecer la expiración de un PAT y olvidarla: el día en que caduca, `git push` falla con un error de autenticación que parece un remoto roto en lugar de una credencial vencida.
- Generar una clave SSH sin frase de contraseña en una máquina compartida. GitHub puede verificar que la clave es tuya, pero no puede proteger un archivo de clave privada que cualquiera con acceso al disco puede leer.

## Ejercicio

Crea un personal access token fine-grained con alcance a un repositorio de práctica, con el permiso **Contents: Read and write** y una expiración corta (7 días). Úsalo una vez para hacer `git push` por HTTPS, luego revócalo antes de tiempo y confirma que el siguiente push falla con un error de autenticación.

## Referencias

- GitHub Docs — [Acerca de la autenticación en GitHub](https://docs.github.com/es/authentication/keeping-your-account-and-data-secure/about-authentication-to-github)
- GitHub Docs — [Gestionar tus personal access tokens](https://docs.github.com/es/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)
- GitHub Docs — [Conectar con GitHub mediante SSH](https://docs.github.com/es/authentication/connecting-to-github-with-ssh)
- GitHub Docs — [Acerca de la autenticación de dos factores](https://docs.github.com/es/authentication/securing-your-account-with-two-factor-authentication-2fa/about-two-factor-authentication)
- GitHub Docs — [Acerca de las ramas protegidas](https://docs.github.com/es/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)
