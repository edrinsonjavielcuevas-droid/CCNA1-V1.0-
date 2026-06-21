
---

## Protocolo de transferencia de archivos (FTP)

El **FTP (File Transfer Protocol)** es un protocolo de capa de aplicación diseñado específicamente para mover archivos de manera eficiente entre un cliente y un servidor en una red.

### ¿Cómo funciona la conexión?

A diferencia de otros protocolos que utilizan un solo canal, FTP utiliza **dos conexiones independientes** para realizar su trabajo:

| **Tipo de Conexión**    | **Puerto TCP** | **Función**                                                     |
| ----------------------- | -------------- | --------------------------------------------------------------- |
| **Conexión de Control** | **Puerto 21**  | Envía comandos de cliente y recibe las respuestas del servidor. |
| **Conexión de Datos**   | **Puerto 20**  | Se encarga de la transferencia real de los archivos.            |
### Detalles importantes:

**Conexión dinámica:** La conexión de control (puerto 21) permanece abierta durante toda la sesión, mientras que la conexión de datos (puerto 20) se abre y se cierra cada vez que se transfiere un archivo.

**Bidireccionalidad:** El cliente tiene la capacidad tanto de **descargar** (extraer) archivos desde el servidor, como de **subir** (insertar) sus propios archivos hacia el servidor.

![](Detalles%20importantes.png)

----

## Bloque de mensajes del servidor (SMB)

El **Bloque de mensajes del servidor (SMB)** es un protocolo de intercambio de archivos cliente/servidor que define cómo se accede y se estructura el uso de recursos compartidos en una red, tales como archivos, directorios, impresoras y puertos serie.

### Funciones Principales

SMB es un protocolo de **solicitud - respuesta** que se encarga de:

**Gestión de sesiones:** Iniciar, autenticar y finalizar las conexiones.

**Acceso a recursos:** Controlar quién puede acceder a qué archivos e impresoras.

**Interoperabilidad:** Autorizar aplicaciones para el envío y recepción de mensajes entre dispositivos.

### Características y Evolución

A diferencia de FTP, que establece conexiones temporales, **SMB crea una conexión a largo plazo**. Una vez establecida, el usuario puede acceder a los archivos del servidor como si estuvieran almacenados localmente en su propia computadora.

**Integración:** Es el pilar de las redes de Microsoft. A partir de Windows 2000, Microsoft integró la nomenclatura **DNS** con SMB, permitiendo que los protocolos TCP/IP gestionen de forma nativa el uso compartido de recursos.

**Universalidad:** Aunque es nativo de Microsoft, otros sistemas operativos también lo admiten para asegurar la compatibilidad:

**SAMBA:** Es la implementación que permite a los sistemas **LINUX y UNIX** intercambiar recursos con redes de Microsoft.

**Apple:** Los sistemas Macintosh también admiten el acceso a recursos compartidos mediante este protocolo.

![](SMB.png)

![](Características%20y%20Evolución.png)

----

