
---

**Introducción a la Detección de Vecinos (ND) en IPv6**

En las redes que operan con IPv6, el tradicional protocolo ARP (utilizado en IPv4) desaparece. En su lugar, el sistema emplea el **Protocolo de Detección de Vecinos (ND - _Neighbor Discovery_)**.

La función principal de ND es exactamente la misma que cumplía ARP: **descubrir y asociar (mapear) las direcciones lógicas IPv6 con sus respectivas direcciones físicas MAC** dentro de un segmento de red local. Esta resolución es un paso obligatorio para que los dispositivos puedan armar (encapsular) las tramas de Ethernet de Capa 2 y enviar los datos físicamente hacia el destino correcto.

---

**Mensajes de Descubrimiento de Vecinos (ND) en IPv6**

==El protocolo de Descubrimiento de Vecinos (ND o NDP) en IPv6 es mucho más robusto que el antiguo ARP de IPv4. ND no solo se encarga de la resolución de direcciones MAC, sino que también asume las tareas de descubrimiento de routers y redirección de tráfico.==

Para realizar estas funciones, ND opera mediante el protocolo **ICMPv6** utilizando cinco tipos de mensajes fundamentales:

**1. Mensajes para la resolución de direcciones (Dispositivo a Dispositivo)** Estos dos mensajes sustituyen el proceso exacto que hacía ARP en IPv4:

**NS (Neighbor Solicitation - Solicitud de vecino):** Un dispositivo pregunta a la red local por la dirección MAC asociada a una dirección IPv6 específica (el equivalente al _ARP Request_).

**NA (Neighbor Advertisement - Anuncio de vecino):** El dispositivo dueño de la IPv6 solicitada responde entregando su dirección física MAC (el equivalente al _ARP Reply_).


**2. Mensajes para la detección de Routers (Host a Router)**

**RS (Router Solicitation - Solicitud de router):** Cuando un host se conecta a la red, envía este mensaje para descubrir si hay routers disponibles que puedan proporcionarle su configuración de red.

**RA (Router Advertisement - Anuncio de router):** Los routers envían estos mensajes (como respuesta a un RS o de forma periódica) para anunciar su presencia y proporcionar a los hosts los parámetros de red (como el prefijo y el gateway predeterminado).


**3. Mensajes de optimización de rutas**

**Mensaje de Redirección:** Un router lo utiliza para informar a un host local que existe una ruta mucho mejor (un siguiente salto más directo) para alcanzar un destino específico en la red.

![](../IMG/MODULO9IMG/Solicitud%20de%20vecino.png)


![](../IMG/MODULO9IMG/01_CCNA/IMG/MODULO9IMG/HOST%20A%20ROUTER.png)

**OJO:** IPv6 ND se define en IEFT RFC 4861.

---

**Resolución de Direcciones en IPv6**

Al igual que en IPv4 dependemos de ARP, en IPv6 utilizamos el protocolo **ND (Descubrimiento de Vecinos)** para averiguar la dirección física (MAC) de un dispositivo del cual ya conocemos su dirección IPv6 lógica.

Este proceso de resolución reemplaza las antiguas difusiones ARP y se realiza de manera más eficiente mediante el intercambio de dos mensajes **ICMPv6** específicos:

**Solicitud de Vecino (NS - _Neighbor Solicitation_):** Es el equivalente exacto al _ARP Request_. Por ejemplo, si tu PC necesita comunicarse con la IP `2001:db8:acad::11`, emite este mensaje NS a la red local preguntando: _"¿A qué MAC le pertenece esta dirección IPv6?"_.

**Anuncio de Vecino (NA - _Neighbor Advertisement_):** Es el equivalente al _ARP Reply_. El dispositivo destino que posee esa dirección IPv6 recibe la solicitud y responde entregando su dirección MAC, permitiendo que tu PC pueda armar la trama de datos y establecer la comunicación.

![](../IMG/MODULO9IMG/Resolución%20de%20Direcciones%20en%20IPv6.png)

**SLAAC** (Stateless Address Autoconfiguration) es el ==mecanismo de IPv6 que permite a un dispositivo autoasignarse una dirección IP global y el _gateway_ predeterminado sin necesidad de un servidor DHCPv6==. Funciona de manera autónoma utilizando mensajes del protocolo ICMPv6.

---

### COMANDOS CLAVES:

**1. Gestión de ARP (IPv4)**

Permite ver y manipular la caché que asocia las direcciones IP con las direcciones MAC.

**Ver la tabla ARP:**

`arp -a` (Windows / Linux)

`show ip arp` (Cisco IOS)

**Borrar la caché ARP (Forzar una nueva solicitud ARP):**

`arp -d ` (Windows - requiere permisos de administrador)

`ip -s -s neigh flush all` (Linux)

`clear arp-cache` (Cisco IOS)

---

**2. Neighbor Discovery / ND (El equivalente a ARP en IPv6)**

Permite ver los vecinos descubiertos en redes IPv6.

**Ver la tabla de vecinos IPv6:**

`netsh interface ipv6 show neighbors` (Windows)

`ip -6 neigh show` (Linux)

`show ipv6 neighbors` (Cisco IOS)

`clear ipv6 neighbors` (Cisco IOS - para borrar la caché)

---

**3. Verificación de Direcciones (IP, MAC y Gateway)**

Para comprobar tu IP lógica, tu dirección física (MAC) de Capa 2 y tu puerta de enlace predeterminada.

**Ver configuración detallada (incluye IP y MAC):**

`ipconfig /all` (Windows)

`ip a` o `ifconfig` (Linux)

`show interfaces` (Cisco IOS - muestra la MAC grabada y la actual)

**Ver resumen de interfaces IP:**

`ip -br a` (Linux)

`show ip interface brief` (Cisco IOS)

---

**4. Tablas de Enrutamiento**

Para verificar a dónde enviará el equipo los paquetes destinados a redes remotas y confirmar el _Default Gateway_.

**Ver la tabla de rutas del host/router:**

`route print` o `netstat -rn` (Windows)

`ip route` o `route -n` (Linux)

`show ip route` (Cisco IOS - para IPv4)

`show ipv6 route` (Cisco IOS - para IPv6)

---

**5. Diagnóstico y Pruebas (TTL, Hop Limit y Bucle)**

Comandos para probar la pila TCP/IP local y el comportamiento de los saltos entre routers.

**Prueba de bucle invertido (_Loopback_):**

`ping 127.0.0.1` (Prueba la pila IPv4 local en cualquier SO)

`ping ::1` (Prueba la pila IPv6 local en cualquier SO)

**Rastrear la ruta (Ver cómo disminuye el TTL / Hop Limit en cada router):**

`tracert <dirección_IP>` (Windows)

`traceroute <dirección_IP>` (Linux / Cisco IOS)

---

