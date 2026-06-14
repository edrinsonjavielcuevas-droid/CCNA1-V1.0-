
---

Para la configuración dinámica de direcciones GUA, los routers utilizan mensajes **ICMPv6** específicos:

### Conceptos básicos

**RS (Router Solicitation):** El dispositivo envía este mensaje para solicitar información a un router.

**RA (Router Advertisement):** El router responde periódicamente (cada 200 segundos) o al recibir un RS. Contiene el prefijo de red, la longitud de prefijo, la dirección de puerta de enlace (la LLA del router) y el DNS.

**Comando clave:** Para activar estas funciones en un router Cisco, debes ejecutar el comando global `ipv6 unicast-routing`, ya que está deshabilitado por defecto.

---
### Los 3 métodos de configuración mediante RA

El mensaje RA indica al dispositivo cómo completar su configuración mediante estas opciones:

|**Método**|**Nombre**|**Descripción**|
|---|---|---|
|**1**|**SLAAC**|El router entrega todo: prefijo, longitud y puerta de enlace.|
|**2**|**SLAAC + DHCPv6 sin estado**|El router entrega prefijo y puerta de enlace; el dispositivo obtiene DNS de un servidor DHCPv6.|
|**3**|**DHCPv6 con estado**|El router solo da la puerta de enlace; un servidor DHCPv6 asigna toda la demás información.|

**Mensajes de RS y RA de ICMPv6.**

![](../IMG/MODULO12IMG/Mensajes%20de%20RS%20y%20RA%20de%20ICMPv6.png)

---

SLAAC (Configuración automática de direcciones sin estado) es un método que permite a los dispositivos configurar su propia dirección GUA sin depender de un servidor DHCPv6.

### Funcionamiento de SLAAC

El dispositivo utiliza la información contenida en los mensajes **ICMPv6 RA** (Router Advertisement) enviados por el router local para completar su configuración. Como es un proceso "sin estado", no existe un servidor central que gestione o registre las direcciones asignadas; el cliente es totalmente autónomo.

### Composición de la dirección GUA en SLAAC:

La dirección se construye combinando dos elementos:

**Prefijo:** Obtenido directamente del mensaje RA enviado por el router.

**ID de interfaz:** Generado por el propio dispositivo utilizando:

**Proceso EUI-64:** Deriva el identificador a partir de la dirección MAC del dispositivo.

**Generación aleatoria:** El sistema operativo crea un número de 64 bits de forma aleatoria.

![](../IMG/MODULO12IMG/Funcionamiento%20de%20SLAAC.png)

----

El método **SLAAC con DHCPv6 sin estado** es una solución híbrida que aprovecha la rapidez de la autoconfiguración para la dirección IP y la centralización de servicios para la configuración adicional.

### Funcionamiento del método:

En esta modalidad, el router envía un mensaje RA que instruye al dispositivo a actuar de la siguiente manera:

**Autoconfiguración (SLAAC):** El dispositivo crea su propia dirección GUA (prefijo + ID de interfaz).

**Puerta de enlace:** Utiliza automáticamente la LLA del router (el origen del mensaje RA) como _default gateway_.

**Servicios adicionales:** Para obtener información complementaria, como **direcciones de servidores DNS y nombre de dominio**, el dispositivo contacta a un servidor **DHCPv6 sin estado** (_stateless_).


> **Nota importante:** El servidor DHCPv6 en este método es "sin estado" porque **no asigna ni registra direcciones GUA**; su función se limita exclusivamente a entregar parámetros de configuración adicionales, como el DNS.



![](../IMG/MODULO12IMG/Funcionamiento%20del%20método.png)

---

El **DHCPv6 con estado** (_stateful_) es la forma más cercana al DHCP tradicional de IPv4, donde un servidor central tiene el control total sobre la asignación de direcciones.

### Funcionamiento del método:

El router envía un mensaje RA que instruye al dispositivo a ignorar la autoconfiguración de la dirección GUA y solicitar toda la información a un servidor DHCPv6:

**Dirección GUA y más:** El dispositivo contacta a un servidor DHCPv6 _stateful_ para obtener su dirección IPv6, la longitud del prefijo, las direcciones DNS y el nombre de dominio.

**Puerta de enlace:** Es el único dato que el servidor DHCPv6 **no** entrega. El dispositivo obtiene su _default gateway_ obligatoriamente desde el mensaje RA del router (usando la LLA del router).

**Control central:** El servidor mantiene una lista o "estado" de qué dispositivo tiene qué dirección, permitiendo un control administrativo centralizado.

> **Dato crítico:** El mensaje RA del router es indispensable en todos los casos, ya que es el único mecanismo que proporciona la **dirección de puerta de enlace predeterminada**. Ni los servidores DHCPv6 _stateful_ ni los _stateless_ tienen la capacidad de configurar este parámetro en el cliente.

![](../IMG/MODULO12IMG/Funcionamiento%20del%20método%201.png)


---
**Proceso EUI-64 versus generodo aleatoriamente**

En los métodos SLAAC y SLAAC con DHCPv6 sin estado, el router proporciona el prefijo de red, pero el dispositivo cliente es responsable de crear su propio **ID de interfaz de 64 bits** para completar la dirección. Este ID se genera mediante uno de dos procesos: el **proceso EUI-64**, que deriva el identificador a partir de la dirección MAC física del dispositivo, o mediante la creación de un **número aleatorio de 64 bits**, cuya elección depende estrictamente de las especificaciones del sistema operativo utilizado por el cliente.

**Creación dinámica de un ID de interfaz**

![](../IMG/MODULO12IMG/Creación%20dinámica%20de%20un%20ID%20de%20interfaz.png)

---

**Proceso EUI-64**

| **Concepto Clave**            | **Detalle Importante para el Examen**                                                                                                                                                                                   |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **¿Qué hace el EUI-64?**      | Convierte una dirección MAC física de **48 bits** en un ID de interfaz IPv6 de **64 bits**.                                                                                                                             |
| **Estructura MAC (48 bits)**  | Se divide en dos partes de 24 bits:<br><br>  <br><br>1. **OUI:** Identificador del fabricante (asignado por IEEE).<br><br>  <br><br>2. **ID del dispositivo:** Valor único asignado al equipo.                          |
| **Paso 1: Dividir**           | La dirección MAC se parte exactamente por la mitad (entre el OUI y el ID del dispositivo).                                                                                                                              |
| **Paso 2: Insertar**          | Se inserta el valor hexadecimal `fffe` (16 bits) justo en el medio de las dos mitades. _Tip de examen: Si ves "fffe" en el medio de una dirección IPv6, casi seguro se generó por EUI-64._                              |
| **Paso 3: Invertir el Bit 7** | Se toma el primer octeto de la dirección, se pasa a binario, y **se invierte el 7º bit** (conocido como bit U/L o Universal/Local). Si es `0` cambia a `1`, y si es `1` cambia a `0`.                                   |
| **Ventaja principal**         | Facilita a los administradores de red rastrear una dirección IPv6 directamente hasta el hardware físico (la tarjeta de red) usando la dirección MAC.                                                                    |
| **Desventaja (Privacidad)**   | Al exponer la MAC, genera preocupaciones de privacidad porque los paquetes pueden rastrearse hasta un equipo físico real. Por esto, muchos sistemas operativos modernos prefieren **generar el ID de forma aleatoria**. |

![](../IMG/MODULO12IMG/Proceso%20EUI-64.png)

**ID de interfaz generada por EUI-64**

![](../IMG/MODULO12IMG/ID%20de%20interfaz%20generada%20por%20EUI-64.png)

---

### Generación Aleatoria de ID de Interfaz

Para proteger la privacidad de los usuarios en la red y evitar rastreos, la mayoría de los sistemas operativos abandonaron el método EUI-64 (que expone la dirección MAC física) en favor de generar la porción de host de forma aleatoria.

**Comportamiento por Sistema Operativo:**

**Sistemas Modernos:** Windows (desde Vista), macOS y las distros modernas de Linux utilizan identificadores aleatorios de 64 bits por defecto.

**Sistemas Antiguos:** Windows XP y anteriores dependían de EUI-64.

**Mecanismo de Seguridad Vital (DAD):** Dado que la dirección se inventa al azar, existe una minúscula probabilidad de chocar con otro equipo. Para evitarlo, IPv6 utiliza un proceso llamado **DAD (Detección de Direcciones Duplicadas)**. Es el equivalente al ARP gratuito en IPv4: el equipo envía un mensaje a la red preguntando "¿Alguien más está usando esta dirección?". Si hay silencio, se la asigna.

---

### Mi Propio Ejemplo Práctico

Supongamos que tu router envía un mensaje RA anunciando el prefijo de red **`2001:db8:cafe:99::/64`**. 

Tu PC genera internamente un ID de interfaz completamente aleatorio, por ejemplo: **`a1b2:c3d4:e5f6:7788`**.

Al abrir tu CMD y ejecutar `ipconfig`, la salida se vería así:

C:\> ipconfig

Configuración IP de Windows
Adaptador de Ethernet Conexión de área local:

Sufijo DNS específico para la conexión. . :
Dirección IPv6. . . . . . . . . . . . . . : 2001:db8:cafe:99:a1b2:c3d4:e5f6:7788
Dirección IPv6 local de vínculo . . . . . : fe80::a1b2:c3d4:e5f6:7788
Puerta de enlace predeterminada . . . . . : fe80::1

**NOTA:** Puedes saber instantáneamente que esta PC generó su dirección de forma aleatoria (y no por EUI-64) porque en el medio de su ID de interfaz (`a1b2:c3d4:e5f6:7788`) **no** aparece el valor `ff:fe`.

---



