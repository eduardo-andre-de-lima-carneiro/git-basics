# 4.5 Bitbucket y Atlassian

Bitbucket, de Atlassian, proporciona repositorios Git con pull requests y Pipelines. Puede conectar el trabajo del repositorio con incidencias de Jira y otros servicios de Atlassian.

## Conectar y publicar

Crea un repositorio de Bitbucket Cloud y ejecuta localmente:

```bash
git remote add origin https://bitbucket.org/WORKSPACE/REPOSITORY.git
git push -u origin main
```

Utiliza la URL de clonación que proporciona tu espacio de trabajo de Bitbucket. Bitbucket Data Center utiliza URL y políticas de autenticación específicas de cada organización.

## Autenticación

La autenticación por HTTPS de Bitbucket Cloud cambió en 2026: los [app passwords](https://support.atlassian.com/bitbucket-cloud/docs/app-passwords/) se retiraron siguiendo un calendario por fases que terminó en julio de 2026 y ya no funcionan en absoluto. El método actual para scripts, herramientas de CI y la línea de comandos de Git es un [API token](https://support.atlassian.com/bitbucket-cloud/docs/using-api-tokens/), creado desde tu cuenta de Atlassian y utilizado junto con tu nombre de usuario de Bitbucket como credencial de Git. Si una página, un tutorial o una herramienta todavía te dice que crees un "app password", trata esa instrucción como obsoleta.

Una clave SSH ([se recomienda Ed25519](https://support.atlassian.com/bitbucket-cloud/docs/set-up-personal-ssh-keys-on-linux/)) no se ve afectada por la retirada de los app passwords y sigue siendo una buena opción para el trabajo frecuente en la línea de comandos.

Habilita la [verificación en dos pasos](https://support.atlassian.com/bitbucket-cloud/docs/enable-two-step-verification/) en la cuenta — mediante una app de autenticación o una llave de seguridad — con independencia de qué credencial de Git uses en el día a día.

## Integraciones útiles

- Las pull requests proporcionan revisión, aprobaciones, tareas y comprobaciones de combinación.
- `bitbucket-pipelines.yml` define los pasos de compilación y despliegue de Bitbucket Pipelines.
- La integración con Jira vincula ramas, commits y pull requests con elementos de trabajo.
- Los entornos de despliegue pueden restringir variables y versiones de producción.
- Los [permisos de rama](https://support.atlassian.com/bitbucket-cloud/docs/use-branch-permissions/) restringen quién puede hacer push o combinar en una rama determinada; el Marketplace y los webhooks conectan Bitbucket con otras herramientas de ingeniería.

Utiliza tokens de acceso del repositorio o del espacio de trabajo con los permisos mínimos necesarios. Conserva las claves de incidencias de Jira en los nombres de ramas o mensajes de commit solo cuando el equipo haya adoptado esa convención, y nunca coloques secretos en esos campos.

## Errores comunes

- Seguir un tutorial antiguo que indica crear un "app password" — desde mediados de 2026 ese flujo ya no existe; crea en su lugar un API token.
- Una integración (herramienta de CI, gestor de paquetes, cliente Git) que sigue configurada con un app password guardado y deja de funcionar en silencio cuando el calendario de retirada llega a la eliminación total, sin aviso local previo.
- Suponer que un API token se comporta exactamente como el antiguo app password: autentica Git y las llamadas a la API, pero no se puede usar para iniciar sesión en bitbucket.org.

## Ejercicio

Crea un API token de Bitbucket y, después, úsalo junto con tu nombre de usuario de Bitbucket para autenticar un `git push` por HTTPS. Comprueba en la configuración de seguridad de tu cuenta que ningún app password sigue listado como activo.

## Referencias

- Atlassian Support — [App passwords](https://support.atlassian.com/bitbucket-cloud/docs/app-passwords/)
- Atlassian Support — [Uso de API tokens](https://support.atlassian.com/bitbucket-cloud/docs/using-api-tokens/)
- Atlassian Support — [Habilitar la verificación en dos pasos](https://support.atlassian.com/bitbucket-cloud/docs/enable-two-step-verification/)
- Atlassian Support — [Configurar claves SSH personales](https://support.atlassian.com/bitbucket-cloud/docs/set-up-personal-ssh-keys-on-linux/)
- Atlassian Support — [Usar los permisos de rama](https://support.atlassian.com/bitbucket-cloud/docs/use-branch-permissions/)
