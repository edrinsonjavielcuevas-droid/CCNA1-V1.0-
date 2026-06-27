
---

**Estrategias Fundamentales de Mitigación**

|**Estrategia**|**Descripción**|**Propósito Principal**|
|---|---|---|
|**Defensa en Profundidad**|Uso de múltiples capas superpuestas de controles de red y software.|Evitar un único punto de falla; si cae una barrera, hay otra detrás.|
|**Copias de Seguridad**|Respaldo regular, verificado y almacenado fuera de línea.|Garantizar la recuperación ante _ransomware_, sabotajes o fallas físicas.|
|**Gestión de Parches**|Actualización constante de sistemas operativos, firmware y aplicaciones.|Cerrar rápidamente las vulnerabilidades conocidas antes de que sean explotadas.|

---

**Control de Acceso: El Modelo AAA**

Este es el estándar de la industria para gestionar quién entra a la red y qué hace dentro de ella.

|**Componente**|**Función**|**Pregunta Clave**|**Ejemplos**|
|---|---|---|---|
|**Autenticación**|Verifica la identidad del usuario o dispositivo que intenta ingresar.|_¿Quién eres?_|Contraseñas, huellas dactilares, tokens de doble factor (2FA).|
|**Autorización**|Asigna los permisos y el nivel de acceso a los recursos de la red.|_¿Qué puedes hacer?_|Listas de control de acceso (ACL), asignación de roles.|
|**Contabilidad**|Registra minuciosamente la actividad, tiempos y comandos ejecutados.|_¿Qué hiciste?_|Registros de auditoría (_Logs_), servidores Syslog.|

----
**Tecnologías de Barrera: Firewalls y Terminales**
#### 1. Tipos de Firewalls (Seguridad Perimetral)

Actúan como guardias de tráfico entre tu red interna de confianza y el exterior (Internet).

|**Tipo de Firewall**|**Nivel de Operación**|**Características Clave**|
|---|---|---|
|**Filtrado de Paquetes**|Capas 3 y 4 (OSI)|Básico y estático. Decide bloquear o permitir basándose solo en IPs y Puertos.|
|**Inspección de Estado**|Capas 3 y 4 + Sesiones|Dinámico. Recuerda qué computadora interna inició la conexión para permitir su respuesta.|
|**Próxima Generación (NGFW)**|Hasta Capa 7 (Aplicación)|Avanzado. Analiza el contenido profundo del tráfico, incluye prevención de intrusiones (IPS).|

##### 2. Seguridad de Terminales (Seguridad Final)

Los firewalls protegen la frontera, pero los terminales protegen el destino final.

|**Concepto**|**Descripción**|
|---|---|
|**El Objetivo (Endpoint)**|Dispositivos finales como laptops, computadoras de escritorio, servidores o teléfonos móviles.|
|**Las Herramientas**|Software Antimalware, Firewalls locales (basados en host) y Sistemas de Prevención de Intrusiones de Host (HIPS).|

---
----

