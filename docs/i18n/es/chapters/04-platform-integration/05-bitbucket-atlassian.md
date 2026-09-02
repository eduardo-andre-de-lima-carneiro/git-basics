# 4.5 Bitbucket y Atlassian

Bitbucket, de Atlassian, proporciona repositorios Git con pull requests y Pipelines. Puede conectar el trabajo del repositorio con incidencias de Jira y otros servicios de Atlassian.

## Conectar y publicar

Crea un repositorio de Bitbucket Cloud y ejecuta localmente:

```bash
git remote add origin https://bitbucket.org/WORKSPACE/REPOSITORY.git
git push -u origin main
```

Utiliza la URL de clonación que proporciona tu espacio de trabajo de Bitbucket. Bitbucket Data Center utiliza URL y políticas de autenticación específicas de cada organización.

## Integraciones útiles

- Las pull requests proporcionan revisión, aprobaciones, tareas y comprobaciones de combinación.
- `bitbucket-pipelines.yml` define los pasos de compilación y despliegue de Bitbucket Pipelines.
- La integración con Jira vincula ramas, commits y pull requests con elementos de trabajo.
- Los entornos de despliegue pueden restringir variables y versiones de producción.
- Marketplace y los webhooks conectan Bitbucket con otras herramientas de ingeniería.

Utiliza tokens de acceso del repositorio o del espacio de trabajo con los permisos mínimos necesarios. Conserva las claves de incidencias de Jira en los nombres de ramas o mensajes de commit solo cuando el equipo haya adoptado esa convención, y nunca coloques secretos en esos campos.
