
---

**La decisión de reenvío de host**

**Itself (El mismo):** Se refiere al dispositivo que está iniciando la solicitud o enviando el paquete. Es el "nodo origen" desde la perspectiva de la interfaz que intenta comunicarse.

**Local Host (Host Local):** Es el dispositivo emisor (o tu propio equipo) que reside en el mismo segmento de red local (enlace local) que el destino. La comunicación ocurre sin necesidad de pasar por un router.

**Remote Host (Host Remoto):** Es el dispositivo de destino que se encuentra en una red diferente a la del emisor. Para alcanzarlo, el paquete debe ser enviado primero a un router (gateway) para que este realice el enrutamiento hacia la red de destino.

---
![](../IMG/MODULO8IMG/La%20decisión%20de%20reenvío%20de%20host.png)

**Tipos de Rutas en la Tabla de Enrutamiento (IPv6)**

Un host IPv6 clasifica el tráfico según el destino para determinar el siguiente paso en la comunicación:

**Ruta de Enlace Local (Local Link Route):** Se utiliza cuando el destino se encuentra en el mismo segmento de red física que el emisor. El paquete se entrega directamente utilizando la dirección _Link-Local_ y la dirección física (MAC) del vecino descubierta mediante los mensajes de _Neighbor Discovery_.

**Ruta a Host Local (Local Host Route):** Es la ruta específica hacia el propio host (habitualmente referida a la dirección de _loopback_ `::1`). Este tráfico es procesado internamente por el propio stack de red del dispositivo.

**Ruta Remota (Remote Route):** Se aplica cuando el destino reside en una red diferente. El host identifica que la dirección IP de destino está fuera de su prefijo local y envía el paquete a la dirección _Link-Local_ de su router predeterminado (_default gateway_), quien es el responsable de encaminar el paquete hacia el destino final fuera del enlace local.

---

**Puerta de enlace predeterminada (Gateway)**

La puerta de enlace predeterminada (_default gateway_) es el dispositivo de red, típicamente un router o un switch de Capa 3, encargado de habilitar la comunicación con otras redes. Funciona como el punto de salida exclusivo para los paquetes cuyo destino se encuentra fuera del segmento de red local.

**Características principales del dispositivo:**

**Direccionamiento local:** Posee una dirección IP configurada dentro del mismo rango o subred que los demás hosts de la red local.

**Interconexión:** Tiene la capacidad técnica de recibir datos originados en la red local y reenviarlos hacia el exterior.

**Enrutamiento:** Ejecuta los procesos necesarios para dirigir de manera óptima el tráfico hacia redes remotas.

**Requisito de conectividad:** La puerta de enlace predeterminada es un componente crítico. Si la dirección del _gateway_ no está configurada en los hosts, si no hay un dispositivo presente, o si este se encuentra inactivo, el tráfico de red quedará estrictamente confinado al segmento local y será imposible alcanzar destinos externos (como Internet u otras sucursales).

---

**Un host enruta a la puerta de enlace predeterminada:**

La tabla de enrutamiento de un dispositivo final debe incluir la dirección de la puerta de enlace predeterminada para poder alcanzar redes remotas. El método para asignar esta dirección varía según la versión del protocolo IP:

**En redes IPv4:** El host adquiere la dirección de la puerta de enlace de forma dinámica a través del protocolo DHCP, o bien, se configura de manera manual.

**En redes IPv6:** El dispositivo obtiene esta información de forma automática a través de los anuncios emitidos por el router local, o también puede ser configurada manualmente.

En la siguiente imagen la PC1 y PC2 están configuradas con la dirección IPv4 de 192.168.10.1 como puerta de enlace predeterminada.

![](../IMG/MODULO8IMG/Un%20host%20enruta%20a%20la%20puerta%20de%20enlace%20predeterminada.png)

Una ruta predeterminada es la ruta o camino que la PC utiliza cuando intenta conectarse a la red remota.

---

**Tablas de enrutamiento de host**

En un host de Windows, el comando   **route print** ó **netstat**  se puede usar para mostrar la tabla de enrutamiento del host.

La siguiente imagen muestra una topología de ejemplo y la salida generada por el comando **netstat -r**.

![](../IMG/MODULO8IMG/netstat%20-r.png)

---

**Tabla de enrutamiento IPv4 para la PC1**

![](../IMG/MODULO8IMG/Tabla%20de%20enrutamiento%20IPv4%20para%20la%20PC1.png)

**OJO:** Esta salida solo muestra la tabla de rutas IPv4.

---

Al ingresar el comando `netstat -r` o el comando equivalente `route print`, se muestran tres secciones relacionadas con las conexiones de red TCP/IP actuales:

**Lista de interfaces:** enumera la dirección de control de acceso a medios (MAC) y el número de interfaz asignado de cada interfaz con capacidad de red en el host, incluidos los adaptadores Ethernet, Wi-Fi y Bluetooth.

**Tabla de rutas IPv4:** enumera todas las rutas IPv4 conocidas, incluidas las conexiones directas, la red local y las rutas locales predeterminadas.

**Tabla de rutas IPv6:** enumera todas las rutas IPv6 conocidas, incluidas las conexiones directas, la red local y las rutas locales predeterminadas.

---

