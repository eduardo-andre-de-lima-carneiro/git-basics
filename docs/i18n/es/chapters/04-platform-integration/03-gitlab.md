# 4.3 GitLab

GitLab proporciona repositorios Git con merge requests, Issues, pipelines de CI/CD, Package Registry y paneles de seguridad en una sola plataforma.

## Conectar y publicar

Crea un proyecto en GitLab y ejecuta localmente:

```bash
git remote add origin https://gitlab.com/GROUP/PROJECT.git
git push -u origin main
```

Usa los nombres reales de tu grupo, proyecto y rama predeterminada. Revisa el remoto con `git remote -v` antes de enviar cambios.

## Autenticación

Para HTTPS, GitLab acepta [cualquier cadena no vacía como nombre de usuario y un personal access token como contraseña](https://docs.gitlab.com/user/profile/personal_access_tokens/). Un token es *obligatorio*, no opcional, en cuanto se habilita la autenticación de dos factores o el SSO en la cuenta. Los tokens nuevos deben llevar una fecha de expiración; GitLab aplica un valor predeterminado de 365 días si no defines uno, y los administradores del plan Ultimate pueden imponer un máximo más corto.

Para el trabajo frecuente en la línea de comandos, una [clave SSH](https://docs.gitlab.com/user/ssh/) evita volver a introducir un token en cada push. GitLab recomienda el tipo de clave Ed25519 en lugar de RSA: `ssh-keygen -t ed25519 -C "<comment>"`. Las claves recién añadidas se comprueban contra una lista de claves conocidas como comprometidas antes de que GitLab las acepte.

GitLab también admite la [autenticación de dos factores](https://docs.gitlab.com/user/profile/account/two_factor_authentication/) — passkeys, apps OTP, llaves de seguridad WebAuthn o códigos por correo electrónico —, que un grupo o una instancia autoalojada puede exigir a todos sus miembros.

## Integraciones útiles

- Las merge requests combinan revisión, aprobaciones, debates y resultados de los pipelines.
- `.gitlab-ci.yml` define trabajos de CI/CD, etapas, artefactos y reglas de despliegue.
- Las [ramas protegidas](https://docs.gitlab.com/user/project/repository/branches/protected/) y los entornos controlan quién puede combinar o desplegar.
- Los tokens de despliegue, los tokens de acceso al proyecto y los runners permiten la automatización.
- Los webhooks y las integraciones notifican a los gestores de incidencias, herramientas de chat y sistemas de seguridad.

Utiliza variables de CI/CD enmascaradas y protegidas para las credenciales. Mantén los runners actualizados, restringe los runners privilegiados y concede a los tokens únicamente los ámbitos necesarios para su trabajo.

## Errores comunes

- Olvidar que GitLab aplica silenciosamente una expiración de 365 días a un personal access token creado sin una — un token que parece tener "sin expiración" dejará de funcionar igualmente al cabo de un año.
- Registrar una llave de seguridad WebAuthn en un nombre de host de GitLab (por ejemplo, una instancia autoalojada) y esperar que también funcione en `gitlab.com` — los registros WebAuthn están vinculados al nombre de host, así que cada uno necesita su propio registro.
- Hacer commits sin configurar nunca la firma de commits y luego sorprenderse de que el distintivo "verificado" de una rama protegida nunca aparezca; GitLab comprueba la firma contra una clave ya añadida a la cuenta.

## Ejercicio

Genera una clave SSH Ed25519, añade la clave pública a tu cuenta de GitLab y luego clona un proyecto por SSH y confirma que `git push` ya no pide un token.

## Referencias

- GitLab Docs — [Personal access tokens](https://docs.gitlab.com/user/profile/personal_access_tokens/)
- GitLab Docs — [Claves SSH](https://docs.gitlab.com/user/ssh/)
- GitLab Docs — [Autenticación de dos factores](https://docs.gitlab.com/user/profile/account/two_factor_authentication/)
- GitLab Docs — [Ramas protegidas](https://docs.gitlab.com/user/project/repository/branches/protected/)
- GitLab Docs — [Commits firmados](https://docs.gitlab.com/user/project/repository/signed_commits/)
