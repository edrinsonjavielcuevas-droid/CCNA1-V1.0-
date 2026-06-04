---

---

---

En este punto, los routers tienen sus configuraciones básicas. El siguiente paso es configurar sus interfaces. Esto se debe a que los dispositivos finales no pueden acceder a los enrutadores hasta que se configuran las interfaces. Existen muchos tipos diferentes de interfaces para los routers Cisco. Por ejemplo, el router Cisco ISR 4321 está equipado con dos interfaces Gigabit Ethernet:

- **GigabitEthernet 0/0/0 (G0/0/0)**
- **GigabitEthernet 0/0/1 (G0/0/1)**

La tarea de configurar una interfaz de enrutador es muy similar a un SVI de administración en un conmutador. Específicamente, incluye la emisión de los siguientes comandos:

![](CONFIG%20INTERFACES.png)

**Nota:** Cuando se habilita una interfaz de enrutador, se deben mostrar mensajes de información confirmando el vínculo habilitado.

---

El comando `description` es una excelente práctica para documentar interfaces, permitiendo añadir hasta 240 caracteres de información útil, como contactos de proveedores o detalles de conexión. Por otro lado, el comando `no shutdown` es indispensable para habilitar administrativamente una interfaz (activándola físicamente); recuerda que, para que esta pase a estado "up", el cable debe estar conectado a otro dispositivo activo (como un switch o router) y, en el caso de enlaces directos entre routers, ambos extremos deben estar configurados y habilitados simultáneamente.

---

**Ejemplo de Configuración de interfaces de routers**

En este ejemplo, se habilitarán las interfaces directamente conectadas de R1 en el diagrama de topología.

![](Ejemplo%20de%20Configuración%20de%20interfaces%20de%20routers.png)


Para configurar las interfaces en R1, utilice los siguientes comandos.

|**Comando**|**Uso / Descripción**|**Contexto / Modo**|
|---|---|---|
|`enable`|Entra al modo EXEC privilegiado (permite usar comandos de configuración y visualización avanzada).|Modo EXEC del usuario (`R1>`)|
|`configure terminal`|Ingresa al modo de configuración global (para hacer cambios que afectan a todo el dispositivo).|Modo EXEC privilegiado (`R1#`)|
|`interface gigabitEthernet 0/0/0`|Selecciona una interfaz específica para configurarla (en este caso, la Gigabit 0/0/0).|Modo de configuración global (`R1(config)#`)|
|`description Link to LAN`|Añade una etiqueta de texto a la interfaz (muy útil para documentar a dónde va conectada).|Modo de configuración de interfaz (`R1(config-if)#`)|
|`ip address 192.168.10.1 255.255.255.0`|Asigna una dirección IPv4 y su máscara de subred a la interfaz.|Modo de configuración de interfaz (`R1(config-if)#`)|
|`ipv6 address 2001:db8:acad:10::1/64`|Asigna una dirección IPv6 y la longitud de su prefijo a la interfaz.|Modo de configuración de interfaz (`R1(config-if)#`)|
|`no shutdown`|Enciende (habilita administrativamente) la interfaz.|Modo de configuración de interfaz (`R1(config-if)#`)|
|`exit`|Sale del modo actual y regresa al nivel de configuración anterior (de interfaz a global).|Varios modos|

---
**Nota sobre los mensajes del sistema (Syslog):** Esos textos que dicen `%LINK-3-UPDOWN` y `%LINEPROTO-5-UPDOWN` no son comandos, sino notificaciones del router. Te están avisando que, después de ejecutar el `no shutdown`, la interfaz subió (estado físico "up") y el protocolo de línea también se activó (estado lógico "up").

---

**Nota:** Observe los mensajes informativos que nos informan de que G0/0/0 y G0/0/1 están activados.

---

**Verificación de configuración de interfaz**

Existen varios comandos que se pueden utilizar para verificar la configuración de interfaz. El más útil de estos es el comando **show ip interface brief** y **show ipv6 interface brief**, como se muestra en el ejemplo.

![](Verificación%20de%20configuración%20de%20interfaz.png)

---

**Configuración comandos de Verificación**

En la tabla se resumen los comandos **show** más populares utilizados para verificar la configuración de la interfaz.

![](Configuración%20comandos%20de%20Verificación.png)

---

**OJO CON LA SALIDA DE CADA COMANDO**

**1 - Show ip interface brief.**

![](Show%20ip%20interface%20brief.png)

**2 - Show ipv6 interface brief.**

![](Show%20ipv6%20interface%20brief.png)

**3 - Show ip router.**

![](Show%20ip%20router.png)

**4 - Show ipv6 route.**

![](Show%20ipv6%20route.png)

**5 - Show interfaces.**

![](Show%20interfaces.png)

**6 - Show ip interface.**

![](Show%20ip%20interface.png)

**7 - Show ipv6 interface.**

![](Show%20ipv6%20interface.png)

---

R1# configure terminal

R1(config)# interface gigabitethernet 0/0/0

R1(config-if)# description Link to LAN

R1(config-if)# ip address 192.168.10.1 255.255.255.0

R1(config-if)# ipv6 address 2001:db8:acad:10::1/64

R1(config-if)# no shutdown

R1(config-if)# exit

---

En resumen, accedimos al modo de configuración del router para inicializar la interfaz GigabitEthernet 0/0/0. Le añadimos una descripción para documentar que conecta a la LAN, configuramos su direccionamiento lógico de doble pila (asignándole tanto una dirección IPv4 como una IPv6) y, finalmente, la activamos físicamente con el comando `no shutdown`, dejándola completamente operativa y lista para enrutar tráfico en la red.

----

