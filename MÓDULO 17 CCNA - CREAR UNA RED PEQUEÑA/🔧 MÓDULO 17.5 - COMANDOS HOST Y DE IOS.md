
---

### Configuración de IP en un host Windows

|**Parámetro**|**Función Principal**|
|---|---|
|**Dirección IP**|Identifica al dispositivo de forma única dentro de la red.|
|**Máscara de subred**|Determina qué parte de la IP corresponde a la red y cuál al host.|
|**Puerta de enlace (Router)**|Es la dirección del router; necesaria para salir a redes externas (Internet).|
|**Servidor DNS**|Traduce nombres de dominio (URLs) a direcciones IP numéricas.|

**Nota para el examen:** Si alguno de estos cuatro elementos está configurado incorrectamente o falta, el dispositivo no podrá comunicarse correctamente con otros hosts o con el exterior, incluso si el enlace físico funciona.

En Windows, la ruta para acceder a esta información de manera gráfica es: **Network and Sharing Center** > **Cambiar configuración del adaptador** > **Estado del adaptador** > **Detalles**.

Sin embargo, los administradores de red suelen ver la información de direcciones IP en un host de Windows ejecutando el comando**ipconfig** en la línea de comandos de un equipo con Windows, como se muestra en el ejemplo.

![](ipconfig.png)

Utilice el comando **ipconfig /all** para ver la dirección MAC junto con varios detalles relacionados con la asignación de direcciones de capa 3 del dispositivo, Como se muestra en el ejemplo.

![](ipconfigall.png)

Si un host está configurado como cliente DHCP, la configuración de la dirección IP se puede renovar utilizando los comandos **ipconfig /release** **ipconfig /renew** y, como se muestra en el resultado de ejemplo.

![](release.png)

El servicio del cliente DNS en PC con Windows también optimiza el rendimiento de la resolución de nombres DNS al almacenar en la memoria los nombres resueltos previamente. El comando **ipconfig /displaydns** muestra todas las entradas DNS en caché en un sistema de computación Windows., como se muestra en el ejemplo.

![](displaydns.png)

---

### Configuración de IP en un host Linux

La verificación de la configuración IP usando la GUI en una máquina Linux variará dependiendo de la distribución Linux (distribución) y la interfaz de escritorio. La figura muestra el **Connection Information** cuadro de diálogo en la distribución Ubuntu que ejecuta el escritorio Gnome.

![697](COnfig%20ip%20en%20host%20linux.png)

En la línea de comandos, los administradores de red utilizan el comando **ifconfig** para mostrar el estado de las interfaces activas actualmente y su configuración IP, como se muestra en la salida.

![](ifconfig.png)

El comando **ip address** se utiliza para mostrar direcciones y sus propiedades. También se puede usar para agregar o eliminar direcciones IP.

**Nota:** La salida mostrada puede variar dependiendo de la distribución Linux.

----

### Configuración de IP en un host macOS

En la GUI de un host Mac, abra **Network Preferences > Advanced** para obtener la información de direccionamiento IP, como se muestra en la figura.

![](IP%20en%20un%20IOS.png)

Sin embargo, el comando **ifconfig** también se puede utilizar para verificar la configuración IP de la interfaz, como se muestra en el ejemplo.

![](IFCONFIG%20EN%20MAC.png)

Otros comandos útiles de macOS para verificar la configuración IP del host incluyen **networksetup -listallnetworkservices** y el **networksetup -getinfo <**_network service_**>,** como se muestra en el siguiente resultado.

![](OTROS%20COMANDAS.png)

---

### El comando ARP

El comando **arp** se ejecuta desde el símbolo del sistema de Windows, Linux o Mac. El comando enumera todos los dispositivos que se encuentran actualmente en la caché ARP del host, lo cual incluye la dirección IPv4, la dirección física y el tipo de direccionamiento (estático/dinámico) para cada dispositivo

Por ejemplo, consulte la topología en la figura

![](Comando%20arp.png)

Se muestra la salida del comando **arp -a** en el host PC-A de Windows.

![](Salida%20arp.png)

El comando **ARP** (Address Resolution Protocol) es fundamental para mapear direcciones IP a direcciones MAC en una red local. Aquí tienes la gestión de la tabla ARP resumida:

| **Acción**           | **Comando**                          | **Descripción**                                                                                      |
| -------------------- | ------------------------------------ | ---------------------------------------------------------------------------------------------------- |
| **Ver tabla ARP**    | `arp -a`                             | Muestra la lista actual de vínculos IP a MAC almacenados en el caché local.                          |
| **Cargar tabla ARP** | `ping [IP_destino]`                  | Obliga al host a realizar una solicitud ARP para obtener la MAC del destino y guardarla en la tabla. |
| **Borrar caché ARP** | `netsh interface ip delete arpcache` | Elimina todas las entradas para forzar una actualización fresca de la información.                   |

---

### Comandos show comunes

Para verificar el estado y la configuración de dispositivos intermediarios en Cisco IOS, los comandos `show` son la herramienta fundamental. Aquí tienes un resumen de los más comunes que todo técnico de red debe dominar:

|**Comando**|**Útil para...**|
|---|---|
|**show running-config**|Verificar la configuración actual (lo que está en ejecución).|
|**show interfaces**|Revisar el estado físico de la interfaz y detectar mensajes de error.|
|**show ip interface**|Verificar la configuración de Capa 3 de una interfaz (IP, estado).|
|**show arp**|Ver la tabla de mapeo de direcciones IP a direcciones MAC locales.|
|**show ip route**|Examinar la tabla de enrutamiento de Capa 3.|
|**show protocols**|Confirmar qué protocolos de red están activos.|
|**show version**|Revisar hardware, memoria, interfaces y licencias instaladas.|

---

El **Cisco Discovery Protocol (CDP)** es un protocolo de capa de enlace de datos (Capa 2), exclusivo de dispositivos Cisco. Su gran ventaja es que permite que dispositivos vecinos se descubran automáticamente, incluso si no tienen conectividad de Capa 3 (IP).

### ¿Qué información obtienes con `show cdp neighbors`?

Este comando es esencial para el reconocimiento de topología. Por cada vecino conectado directamente, obtendrás:

|**Campo**|**Descripción**|
|---|---|
|**ID del dispositivo**|El nombre de host del vecino.|
|**Lista de direcciones**|Direcciones IP configuradas (si existen).|
|**ID de puerto**|La interfaz local y la interfaz remota (ej. G0/0/1 a F0/5).|
|**Lista de capacidades**|Si es un switch, un router, etc.|
|**Plataforma**|El modelo de hardware (ej. Cisco serie 1841).|

![](show%20cpd%20neighbors.png)

Observa que R3 solo ve a S3. Esto ocurre porque CDP es un protocolo de **vecinos directamente conectados**; no es capaz de ver dispositivos "detrás" de sus vecinos (como S4).

Si necesitas más información que la tabla básica, el comando `show cdp neighbors detail` es la herramienta de diagnóstico definitiva, ya que revela la dirección IP del vecino, lo cual es vital para detectar errores de configuración de Capa 3 cuando no hay conectividad entre routers.

### Seguridad: Mejores prácticas

Aunque CDP facilita la administración, también expone detalles de tu infraestructura a posibles atacantes. Para mitigar este riesgo:

| **Acción**                           | **Comando**     | **Nivel de aplicación**                        |
| ------------------------------------ | --------------- | ---------------------------------------------- |
| **Deshabilitar CDP globalmente**     | `no cdp run`    | Desactiva el protocolo en todo el dispositivo. |
| **Deshabilitar CDP en una interfaz** | `no cdp enable` | Desactiva CDP solo en un puerto específico.    |

---
 
 **Regla de oro de seguridad:** Siempre deshabilita CDP en los puertos orientados a los usuarios finales (puertos de acceso) y habilítalo únicamente en los puertos que conectan dispositivos de infraestructura Cisco. Esto mantiene la visibilidad de tu red interna intacta mientras cierras una puerta de información hacia el exterior.

---

### SHOW IP INTERFACE BRIEF

El comando `show ip interface brief` es, probablemente, el comando más utilizado por los técnicos de red para obtener un diagnóstico rápido y eficiente de la salud de un dispositivo Cisco. A diferencia de `show ip interface`, este ofrece una vista simplificada en formato de tabla.

### Interpretación de la salida

Este comando muestra cuatro columnas clave que debes saber analizar para cualquier examen de certificación o resolución de problemas:

**Interface:** Nombre físico o lógico de la interfaz.

**IP-Address:** Dirección IP asignada (o "unassigned" si no tiene).

**Status:** Indica si la capa física (Capa 1) está funcionando.

**up:** El cable está conectado y detecta señal.

**down:** No hay señal física.

**administratively down:** La interfaz ha sido apagada manualmente mediante el comando `shutdown`.

**Protocol:** Indica si la capa de enlace de datos (Capa 2) está funcionando correctamente.    

### Análisis de estado 

Para que una interfaz sea funcional, **ambas columnas deben estar en "up/up"**.

**up / up:** La interfaz funciona perfectamente.

**up / down:** Problema en Capa 2 (ejemplo: falta de coincidencia de encapsulación o falta de señal de keepalive).

**down / down:** Problema en Capa 1 (ejemplo: cable desconectado o fallo en el dispositivo remoto).

**administratively down / down:** El puerto ha sido desactivado intencionalmente por un administrador.

----


