
---

### COMUNICACIONES MÚLTIPLES SEPARADAS

Tanto TCP como UDP utilizan **números de puerto** para lograr la "multiplexión", que es la capacidad de gestionar múltiples conversaciones o aplicaciones independientes de forma simultánea a través de una única conexión de red.

**El rol de los puertos en la comunicación**

|**Tipo de Puerto**|**Función**|**¿Quién lo asigna?**|
|---|---|---|
|**Puerto de origen**|Identifica de forma exclusiva la aplicación o proceso específico dentro de tu host local.|Tu sistema operativo lo genera dinámicamente para cada nueva solicitud.|
|**Puerto de destino**|Identifica el servicio específico que se solicita al servidor remoto.|Es un número estándar (conocido) que el servidor está escuchando (ej. puerto 80 para web).|
![](COMUNICACIONES%20MÚLTIPLES%20SEPARADAS.png)

---
### Ejemplo Práctico: Navegación Web

Cuando abres una página en tu navegador, este genera un número de puerto de origen aleatorio. Esto es vital porque permite que tu PC pueda tener, por ejemplo, tres pestañas distintas abiertas; cada una tiene un número de puerto de origen diferente, por lo que cuando los datos regresan del servidor, tu PC sabe exactamente a qué pestaña debe entregar cada respuesta.

Al mismo tiempo, el puerto de destino es fijo (puerto 80), lo que le indica al servidor que lo que quieres es ver una página web. Esto permite que un mismo servidor ofrezca múltiples servicios (como Web en el puerto 80 y FTP en el 21) al mismo tiempo sin ninguna confusión.

---

### PARES DE SOCKETS

### Clasificación de los Números de Puerto

Los números de puerto están organizados en grupos específicos por la IANA (Internet Assigned Numbers Authority) para diferenciar sus funciones y usos:

| **Categoría de Puerto**          | **Rango de Números** | **Descripción**                                                                                                                                                |
| -------------------------------- | -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Puertos Conocidos**            | **0 a 1023**         | Reservados para servicios y aplicaciones estándar de Internet (como HTTP, FTP, SSH). Son los más utilizados y reconocibles.                                    |
| **Puertos Registrados**          | **1024 a 49151**     | Asignados a entidades para procesos o aplicaciones específicas (por ejemplo, aplicaciones de usuario o juegos). No son tan universales como los conocidos.     |
| **Puertos Dinámicos / Privados** | **49152 a 65535**    | También llamados puertos efímeros. Se asignan de forma automática y temporal por el sistema operativo cuando se inicia una conexión, y se liberan al terminar. |

**Puntos clave a recordar:**

**Asignación automática:** El puerto de origen siempre es un puerto dinámico elegido por el cliente al iniciar la petición.

**Consistencia:** El puerto de destino siempre es un puerto conocido o registrado, ya que el servidor necesita escuchar en un número fijo para que los clientes sepan cómo contactarlo.

**Multiplexión:** Esta división es lo que permite que tu computadora maneje múltiples conexiones simultáneas sin que la información de una aplicación interfiera con otra.

![](PARES%20DE%20SOCKETS.png)

Un **socket** es simplemente la unión de una **dirección IP** y un **número de puerto**. Su función es identificar de manera única una aplicación específica dentro de una computadora.

### El ejemplo explicado de forma sencilla:

Imagina que tu PC (IP `192.168.1.5`) quiere descargar un archivo (FTP) y ver una página web al mismo tiempo:

1. **Para FTP:** Crea un socket `192.168.1.5:1305` que se conecta al servidor (`192.168.1.7:21`).

2. **Para Web:** Crea otro socket distinto, `192.168.1.5:1099`, que se conecta al servidor (`192.168.1.7:80`).


**¿Por qué es importante?** Al combinar estos sockets en un **par** (`Socket Origen + Socket Destino`), la computadora sabe exactamente a qué aplicación debe entregar cada respuesta. Sin esto, la información del archivo FTP y la de la página web se mezclarían, causando un error. En resumen, los sockets actúan como un sistema de etiquetas que permite que varias conversaciones ocurran simultáneamente sin confundirse.

---
### Puertos conocidos

![](Puertos%20conocidos.png)

---

### EL COMANDO NETSTAT 

El comando **`netstat`** es una utilidad de red esencial para la seguridad, que permite listar todas las conexiones TCP activas en un host. Su salida muestra:

- **Proto:** Protocolo (ej. TCP).
    
- **Local Address:** IP y puerto de origen local.
    
- **Foreign Address:** IP o nombre de dominio y servicio remoto.
    
- **State:** Estado de la conexión (ej. `ESTABLISHED`).
    

Por defecto, intenta resolver nombres de dominio y puertos. Usando la opción **`-n`**, muestra los resultados en formato numérico (IPs y puertos), lo cual es ideal para un diagnóstico más preciso.

![](EL%20COMANDO%20NETSTAT.png)

Las variables (opciones) más útiles para el comando **netstat** son:

**`-n`**: Muestra las direcciones y números de puerto en formato numérico (evita la resolución de nombres DNS).

**`-a`**: Muestra todas las conexiones y puertos de escucha (incluyendo los que no están activos).

**`-o`**: Muestra el PID (ID de proceso) asociado a cada conexión, permitiendo identificar qué programa específico abrió el puerto.
    
**`-b`**: Muestra el archivo ejecutable involucrado en la creación de cada conexión (requiere permisos de administrador).

**`-r`**: Muestra la tabla de enrutamiento del host.

---

