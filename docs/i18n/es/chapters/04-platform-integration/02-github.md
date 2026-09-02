# 4.2 GitHub

GitHub combina repositorios Git alojados con pull requests, Issues, Actions, Projects, Packages y funciones de seguridad.

## Conectar y publicar

Crea un repositorio vacío en GitHub y ejecuta localmente:

```bash
git remote add origin https://github.com/OWNER/REPOSITORY.git
git push -u origin main
```

Sustituye `OWNER`, `REPOSITORY` y `main` por tus valores. No inicialices el repositorio de GitHub con un segundo README cuando tu repositorio local ya tenga uno, a menos que planees reconciliar los historiales.

## Integraciones útiles

- Las pull requests proporcionan revisión, debate, aprobaciones obligatorias y comprobaciones de estado.
- GitHub Actions puede probar, analizar, empaquetar y desplegar con cada push o pull request.
- La protección de ramas puede exigir revisiones, comprobaciones aprobadas y commits firmados.
- Los entornos pueden restringir los despliegues y proteger los secretos de producción.
- Los webhooks y la API conectan los eventos del repositorio con sistemas externos.

Utiliza tokens de acceso personal detallados con los privilegios mínimos o GitHub Apps. Guarda los secretos de automatización en los secretos del repositorio o del entorno, nunca en los archivos de workflow ni en el código fuente.
