# 4.6 Lista de comprobación para una integración segura

Antes de considerar que una integración está lista, comprueba lo siguiente:

- La URL remota es correcta y no contiene ningún secreto.
- La autenticación utiliza claves SSH, tokens o una identidad de aplicación con un alcance limitado — nunca una contraseña de cuenta; todas las plataformas de este capítulo han eliminado o están eliminando la autenticación por contraseña para Git por HTTPS.
- La autenticación de dos factores o multifactor está habilitada en toda cuenta humana con acceso de push o merge, no solo en las cuentas de administrador.
- Los personal access tokens tienen el alcance más reducido que exige la tarea, una expiración corta y un plan de rotación — un token que "simplemente funciona para siempre" es un token que nadie está vigilando.
- Las claves SSH usan un algoritmo moderno (Ed25519 cuando la plataforma lo acepta; Azure Repos es la excepción y exige RSA) y se rotan o eliminan cuando una persona cambia de función o deja el equipo.
- La rama predeterminada está protegida contra pushes directos accidentales.
- Las solicitudes de extracción o combinación requieren la revisión adecuada y comprobaciones automatizadas aprobadas.
- La firma de commits (GPG, SSH o el método admitido por la plataforma) está habilitada donde el equipo quiere un distintivo verificado como prueba de autoría, entendiendo que no todas las plataformas lo aplican de la misma forma — GitHub y GitLab pueden exigir commits firmados como una política de rama, mientras que Azure Repos actualmente no tiene un equivalente en sus políticas de rama.
- Los secretos de CI/CD se almacenan en el gestor de secretos de la plataforma, nunca en un archivo de workflow ni en un script.
- El análisis de dependencias, secretos y vulnerabilidades está habilitado cuando corresponde.
- El despliegue en producción requiere una aprobación independiente o un entorno protegido.
- Los webhooks validan sus firmas y envían únicamente los datos que necesitan.
- El acceso se revisa cuando una persona, token, runner o servicio cambia de función — e inmediatamente cuando alguien se marcha.

## Protecciones a nivel de cuenta

Cada plataforma documenta su propio requisito y configuración actuales:

- GitHub [exige 2FA](https://docs.github.com/es/authentication/securing-your-account-with-two-factor-authentication-2fa/about-two-factor-authentication) para las cuentas que contribuyen código, y admite la [firma de commits con GPG, SSH o S/MIME](https://docs.github.com/es/authentication/managing-commit-signature-verification/about-commit-signature-verification).
- GitLab admite la [2FA exigida a nivel de grupo o de instancia](https://docs.gitlab.com/user/profile/account/two_factor_authentication/) y los [commits firmados mediante SSH, GPG o X.509](https://docs.gitlab.com/user/project/repository/signed_commits/).
- Azure DevOps vincula la autenticación multifactor al proveedor de identidad de la organización: un [inicio de sesión con Microsoft Entra ID hereda las políticas de MFA y de acceso condicional de Entra](https://learn.microsoft.com/es-es/azure/devops/organizations/security/about-security-identity), y las cuentas con una cuenta Microsoft pueden habilitar 2FA directamente.
- Bitbucket Cloud admite la [verificación en dos pasos](https://support.atlassian.com/bitbucket-cloud/docs/enable-two-step-verification/) mediante una app de autenticación o una llave de seguridad, con independencia de qué credencial de Git (API token o clave SSH) use la cuenta.

## Errores comunes

- Confundir "la 2FA es obligatoria para la organización" con "la 2FA está habilitada para todos los miembros" — un ajuste de aplicación y la inscripción individual son dos comprobaciones distintas, y una puede ir por detrás de la otra.
- Exigir commits firmados en GitHub o GitLab sin mostrar nunca a los colaboradores cómo configurar la firma SSH o GPG en local, de modo que el requisito bloquea pushes legítimos en lugar de detectar un problema real.
- Auditar tokens y claves una sola vez, al configurar el proyecto, y nunca más. La rotación es una tarea recurrente, no un punto único de la lista de comprobación.

Una integración tiene éxito cuando hace que la entrega sea más trazable y repetible sin facilitar el uso indebido de credenciales o cambios en producción.

## Referencias

- GitHub Docs — [Acerca de la autenticación de dos factores](https://docs.github.com/es/authentication/securing-your-account-with-two-factor-authentication-2fa/about-two-factor-authentication)
- GitHub Docs — [Acerca de la verificación de firma de commits](https://docs.github.com/es/authentication/managing-commit-signature-verification/about-commit-signature-verification)
- GitLab Docs — [Autenticación de dos factores](https://docs.gitlab.com/user/profile/account/two_factor_authentication/)
- GitLab Docs — [Commits firmados](https://docs.gitlab.com/user/project/repository/signed_commits/)
- Microsoft Learn — [Acerca de la autenticación, la autorización y las políticas de seguridad](https://learn.microsoft.com/es-es/azure/devops/organizations/security/about-security-identity)
- Atlassian Support — [Habilitar la verificación en dos pasos](https://support.atlassian.com/bitbucket-cloud/docs/enable-two-step-verification/)
