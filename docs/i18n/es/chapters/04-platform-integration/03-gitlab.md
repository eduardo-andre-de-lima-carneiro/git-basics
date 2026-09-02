# 4.3 GitLab

GitLab proporciona repositorios Git con merge requests, Issues, pipelines de CI/CD, Package Registry y paneles de seguridad en una sola plataforma.

## Conectar y publicar

Crea un proyecto en GitLab y ejecuta localmente:

```bash
git remote add origin https://gitlab.com/GROUP/PROJECT.git
git push -u origin main
```

Usa los nombres reales de tu grupo, proyecto y rama predeterminada. Revisa el remoto con `git remote -v` antes de enviar cambios.

## Integraciones útiles

- Las merge requests combinan revisión, aprobaciones, debates y resultados de los pipelines.
- `.gitlab-ci.yml` define trabajos de CI/CD, etapas, artefactos y reglas de despliegue.
- Las ramas y los entornos protegidos controlan quién puede combinar o desplegar.
- Los tokens de despliegue, los tokens de acceso al proyecto y los runners permiten la automatización.
- Los webhooks y las integraciones notifican a los gestores de incidencias, herramientas de chat y sistemas de seguridad.

Utiliza variables de CI/CD enmascaradas y protegidas para las credenciales. Mantén los runners actualizados, restringe los runners privilegiados y concede a los tokens únicamente los ámbitos necesarios para su trabajo.
