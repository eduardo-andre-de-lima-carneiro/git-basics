# 4.1 Fundamentos de la integración

Las plataformas alojadas añaden servicios de colaboración y entrega alrededor de un repositorio Git. Los comandos locales siguen siendo conocidos; la plataforma proporciona identidad, permisos, revisión, automatización y visibilidad del proyecto.

## El flujo común

1. Crea o selecciona un repositorio remoto.
2. Conecta el repositorio local con [`git remote add origin <repository-url>`](https://git-scm.com/docs/git-remote).
3. Envía una rama con `git push -u origin <branch-name>`.
4. Abre una solicitud de extracción o una solicitud de combinación para su revisión.
5. Deja que se ejecuten las comprobaciones obligatorias antes de combinar.
6. Elimina la rama de corta duración después de integrar el cambio.

## Elige HTTPS o SSH

HTTPS es una opción sencilla para empezar. Hoy en día, toda plataforma relevante autentica las operaciones Git por HTTPS con un token o un inicio de sesión federado en lugar de una contraseña de cuenta — GitHub eliminó la autenticación por contraseña para Git en agosto de 2021, y las demás plataformas de este capítulo han seguido el mismo patrón, cada una con su mecanismo actual (consulta las páginas de cada plataforma más adelante). SSH utiliza un par de claves, evita volver a introducir credenciales en cada operación y también puede firmar commits. Nunca coloques tokens, claves privadas ni credenciales en un repositorio, y no des por hecho que una página leída hace tiempo sigue describiendo el comportamiento predeterminado actual — estas plataformas cambian sus métodos de autenticación predeterminados con más frecuencia de lo que cambian la mayoría de los comandos de Git.

## Comparación entre plataformas

La tabla refleja la documentación propia de cada plataforma, verificada en vivo en lugar de recordada de memoria. Los límites numéricos (asientos, almacenamiento, minutos de CI) cambian con frecuencia y se han dejado fuera a propósito — consulta la página de precios actual de cada plataforma para eso.

| Plataforma | Modelo de alojamiento | Autenticación predeterminada para Git por HTTPS | Nombre de la unidad de revisión | Repositorios privados en el plan gratuito |
| --- | --- | --- | --- | --- |
| [GitHub](https://docs.github.com/es) | SaaS (GitHub.com) o autoalojado (GitHub Enterprise Server) | Personal access token, clave SSH o un asistente de credenciales como GitHub CLI / Git Credential Manager — las contraseñas de cuenta se rechazan | Pull request | Sí |
| [GitLab](https://docs.gitlab.com/) | SaaS (GitLab.com) o autoalojado (GitLab Self-Managed) | Personal access token (obligatorio en cuanto se habilita 2FA o SSO) o clave SSH | Merge request | Sí |
| [Azure Repos](https://learn.microsoft.com/es-es/azure/devops/repos/) | SaaS (Azure DevOps Services) o autoalojado (Azure DevOps Server) | Inicio de sesión con Microsoft Entra ID a través de Git Credential Manager, preferido frente a un personal access token con alcance limitado | Pull request | Sí |
| [Bitbucket](https://support.atlassian.com/bitbucket-cloud/) | SaaS (Bitbucket Cloud) o autoalojado (Bitbucket Data Center) | API token o clave SSH — los app passwords se retiraron por completo en 2026 | Pull request | Sí |

## Qué configurar

Como mínimo, acuerden la rama predeterminada, las reglas de protección de ramas, los requisitos de revisión, las comprobaciones de estado, la vinculación de incidencias y quién puede enviar cambios o combinar ramas. Estas políticas forman parte del proceso de entrega del equipo, no son solo decoración de la plataforma.

## Errores comunes

- Reutilizar un único token de larga duración y con un alcance amplio en todas las herramientas. Si se filtra, todas las integraciones que lo usaban quedan comprometidas a la vez — da a cada token un alcance limitado a un solo propósito.
- Olvidar que un token tiene fecha de expiración. Un push que funcionó ayer puede fallar hoy con un error de autenticación en cuanto el token expira — trátalo como algo rutinario, no como un fallo, y rota el token.
- Suponer que HTTPS todavía pide una contraseña de cuenta. Ninguna de las cuatro plataformas de este capítulo lo hace; el aviso pide un token o un inicio de sesión gestionado por una CLI.

## Referencias

- Manual de referencia de Git — [git-remote](https://git-scm.com/docs/git-remote)
- GitHub Docs — [Acerca de la autenticación en GitHub](https://docs.github.com/es/authentication/keeping-your-account-and-data-secure/about-authentication-to-github)
- GitLab Docs — [Personal access tokens](https://docs.gitlab.com/user/profile/personal_access_tokens/)
- Microsoft Learn — [Usar personal access tokens para autenticarte](https://learn.microsoft.com/es-es/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate)
- Atlassian Support — [App passwords (Bitbucket Cloud)](https://support.atlassian.com/bitbucket-cloud/docs/app-passwords/)
