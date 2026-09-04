# 4.4 Azure Repos

Azure Repos aloja repositorios Git dentro de proyectos de Azure DevOps y se conecta de forma natural con Azure Boards, Pipelines, Test Plans y Artifacts.

## Conectar y publicar

Crea o selecciona un repositorio en un proyecto de Azure DevOps y ejecuta localmente:

```bash
git remote add origin https://dev.azure.com/ORGANIZATION/PROJECT/_git/REPOSITORY
git push -u origin main
```

La URL exacta se puede copiar desde la acción Clone del repositorio.

## Autenticación

La propia guía de Microsoft coloca ahora los personal access tokens en último lugar, no en primero: la [documentación de Azure DevOps](https://learn.microsoft.com/es-es/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate) indica que hay que "evitar usar PAT cuando exista un método de autenticación más seguro disponible" y recomienda el inicio de sesión con Microsoft Entra ID (a través de Git Credential Manager) o un service principal / identidad administrada para cualquier tarea automatizada. Si un [personal access token](https://learn.microsoft.com/es-es/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate) sigue siendo la opción adecuada — un script puntual, una herramienta que no puede iniciar sesión con Entra — dale el alcance más reducido y la expiración más corta que permita la tarea; la cadencia de rotación recomendada por la propia Microsoft es de 90 días para un PAT personal y de 30 días para uno privilegiado.

[SSH](https://learn.microsoft.com/es-es/azure/devops/repos/git/use-ssh-keys-to-authenticate) también es compatible, con una particularidad propia de esta plataforma: Azure Repos solo acepta claves **RSA**, no las claves Ed25519 que GitHub y GitLab recomiendan ahora — reutilizar aquí una clave Ed25519 existente de GitHub/GitLab falla. Genera una clave RSA independiente para Azure Repos: `ssh-keygen -t rsa -b 3072`.

## Integraciones útiles

- Las pull requests admiten revisores, [políticas de rama](https://learn.microsoft.com/es-es/azure/devops/repos/git/branch-policies?view=azure-devops), elementos de trabajo vinculados y validación de compilaciones.
- Azure Pipelines puede compilar, probar, analizar y desplegar a partir de eventos del repositorio.
- Azure Boards vincula commits y pull requests con elementos de trabajo para facilitar la trazabilidad.
- Las políticas de rama pueden exigir revisores, compilaciones correctas y resolución de comentarios — a diferencia de GitHub o GitLab, las políticas de rama de Azure Repos no tienen una opción integrada de "exigir commits firmados".
- Azure Artifacts proporciona fuentes de paquetes y dependencias de compilación.

Concede permisos mediante grupos siempre que sea posible. Protege las conexiones de servicio y los grupos de variables, y separa la aprobación de los despliegues en producción de los permisos para contribuir al código.

## Errores comunes

- Generar una clave Ed25519 por costumbre (porque funcionó en GitHub) y toparse con un rechazo confuso de Azure Repos, que solo acepta claves RSA para SSH.
- Dejar un personal access token con una expiración larga predeterminada para un pipeline de CI en lugar de rotarlo — un token sin rotar que lleva meses activo es fácil de detectar para un administrador en el registro de auditoría, pero solo si alguien lo revisa.
- Tratar un PAT como una credencial de servicio a largo plazo. Microsoft recomienda explícitamente migrar las cargas de trabajo automatizadas a un service principal o una identidad administrada.

## Ejercicio

Crea un personal access token con alcance **Code (Read & write)** para un proyecto, con una expiración de 7 días. Úsalo para autenticar un `git push` por HTTPS y, después, comprueba en el registro de auditoría de la organización el evento `PatCreated` correspondiente.

## Referencias

- Microsoft Learn — [Usar personal access tokens para autenticarte](https://learn.microsoft.com/es-es/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate)
- Microsoft Learn — [Usar autenticación por clave SSH](https://learn.microsoft.com/es-es/azure/devops/repos/git/use-ssh-keys-to-authenticate)
- Microsoft Learn — [Definir y gestionar políticas de rama](https://learn.microsoft.com/es-es/azure/devops/repos/git/branch-policies?view=azure-devops)
- Microsoft Learn — [Acerca de la autenticación, la autorización y las políticas de seguridad](https://learn.microsoft.com/es-es/azure/devops/organizations/security/about-security-identity)
