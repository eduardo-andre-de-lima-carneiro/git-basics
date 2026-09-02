# 4.6 Lista de comprobación para una integración segura

Antes de considerar que una integración está lista, comprueba lo siguiente:

- La URL remota es correcta y no contiene ningún secreto.
- La autenticación utiliza claves SSH, tokens o una identidad de aplicación con un alcance limitado.
- La rama predeterminada está protegida contra pushes directos accidentales.
- Las solicitudes de extracción o combinación requieren la revisión adecuada y comprobaciones automatizadas aprobadas.
- Los secretos de CI/CD se almacenan en el gestor de secretos de la plataforma.
- El análisis de dependencias, secretos y vulnerabilidades está habilitado cuando corresponde.
- El despliegue en producción requiere una aprobación independiente o un entorno protegido.
- Los webhooks validan sus firmas y envían únicamente los datos que necesitan.
- El acceso se revisa cuando una persona, token, runner o servicio cambia de función.

Una integración tiene éxito cuando hace que la entrega sea más trazable y repetible sin facilitar el uso indebido de credenciales o cambios en producción.
