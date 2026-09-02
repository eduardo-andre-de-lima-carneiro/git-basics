# 4.4 Azure Repos

Azure Repos aloja repositorios Git dentro de proyectos de Azure DevOps y se conecta de forma natural con Azure Boards, Pipelines, Test Plans y Artifacts.

## Conectar y publicar

Crea o selecciona un repositorio en un proyecto de Azure DevOps y ejecuta localmente:

```bash
git remote add origin https://dev.azure.com/ORGANIZATION/PROJECT/_git/REPOSITORY
git push -u origin main
```

La URL exacta se puede copiar desde la acción Clone del repositorio. Utiliza la autenticación de Microsoft Entra, SSH o un token de acceso personal con el alcance adecuado, según la política de tu organización.

## Integraciones útiles

- Las pull requests admiten revisores, políticas de ramas, elementos de trabajo vinculados y validación de compilaciones.
- Azure Pipelines puede compilar, probar, analizar y desplegar a partir de eventos del repositorio.
- Azure Boards vincula commits y pull requests con elementos de trabajo para facilitar la trazabilidad.
- Las políticas de ramas pueden exigir revisores, compilaciones correctas y resolución de comentarios.
- Azure Artifacts proporciona fuentes de paquetes y dependencias de compilación.

Concede permisos mediante grupos siempre que sea posible. Protege las conexiones de servicio y los grupos de variables, y separa la aprobación de los despliegues en producción de los permisos para contribuir al código.
