
---

El protocolo **ICMP** (Internet Control Message Protocol) es la herramienta fundamental de diagnóstico en redes TCP/IP. Aunque el protocolo IP es inherentemente de "mejor esfuerzo" y no garantiza entrega, ICMP se encarga de proporcionar retroalimentación sobre el procesamiento de paquetes.

**Propósito:** Notificar errores y enviar mensajes informativos. No hace que IP sea confiable, solo informa sobre el estado de la comunicación.

**Seguridad:** Debido a que pueden revelar información de la red, es común que los administradores bloqueen los mensajes ICMP en dispositivos perimetrales (firewalls).

**Versiones:** Existe **ICMPv4** (para redes IPv4) e **ICMPv6** (para redes IPv6), siendo este último más avanzado y funcional.

---

**Accesibilidad al host:**

La accesibilidad de un host en una red IP se puede verificar mediante el uso de mensajes de eco ICMP. En este proceso, el host local envía una solicitud de eco ICMP a un dispositivo de destino, el cual responde con una respuesta de eco si se encuentra disponible. Este intercambio de mensajes de eco ICMP constituye la base técnica de la utilidad conocida como **ping**.

![](Accesibilidad%20al%20host.png)

---

**Destino o servicio inaccesible:**

Cuando un host o gateway no puede entregar un paquete, genera un mensaje ICMP de "destino inalcanzable" para notificar al emisor, incluyendo un código específico que explica la razón del fallo.

**Códigos de Destino Inalcanzable**

| **Código** | **ICMPv4 (Motivo)**    | **ICMPv6 (Motivo)**                            |
| ---------- | ---------------------- | ---------------------------------------------- |
| **0**      | Red inalcanzable       | No hay ruta para el destino                    |
| **1**      | Host inalcanzable      | Prohibido administrativamente (ej. Firewall)   |
| **2**      | Protocolo inalcanzable | Más allá del alcance de la dirección de origen |
| **3**      | Puerto inalcanzable    | No se puede alcanzar la dirección              |
| **4**      | —                      | Puerto inalcanzable                            |

**Nota:** ICMPv6 tiene códigos similares pero ligeramente diferentes para los mensajes de destino inalcanzable.

---

**Tiempo excedido**

Cuando un router recibe un paquete y su contador de tiempo llega a cero, este descarta el paquete y envía un mensaje de "tiempo superado" al host de origen para notificarle que el paquete no pudo ser reenviado. En redes IPv4, este contador se denomina **Time to Live (TTL)**, mientras que en redes IPv6 se utiliza el campo **Límite de salto (Hop Limit)** para determinar si el paquete ha caducado.

> **Nota:** La herramienta `traceroute` utiliza estos mensajes de tiempo excedido para mapear el camino de un paquete.

---

**Mensajes ICMPv6**

ICMPv6 introduce mejoras funcionales sobre ICMPv4, encapsulándose directamente en paquetes IPv6 para gestionar la comunicación crítica entre dispositivos mediante el protocolo de **Detección de Vecinos (NDP)**. Este protocolo permite que routers y hosts intercambien información para la asignación dinámica de direcciones, resolución de resolución de nombres y detección de posibles conflictos, sustituyendo procesos que en IPv4 dependían de protocolos como ARP.

**Mensajes del Protocolo de Detección de Vecinos (NDP)**

| **Tipo de Mensaje**          | **Función Principal**                                                                              | **Comunicación**          |
| ---------------------------- | -------------------------------------------------------------------------------------------------- | ------------------------- |
| **Solicitud de Router (RS)** | El host solicita información de direccionamiento al router.                                        | Host a Router             |
| **Anuncio de Router (RA)**   | El router responde periódicamente (cada 200s) o ante un RS con el prefijo, DNS y puerta de enlace. | Router a Host             |
| **Solicitud de Vecino (NS)** | Un dispositivo verifica la accesibilidad o busca la dirección MAC de otro vecino en el enlace.     | Dispositivo a Dispositivo |
| **Anuncio de Vecino (NA)**   | Respuesta a un mensaje NS para confirmar la disponibilidad o indicar la dirección MAC propia.      | Dispositivo a Dispositivo |

**Nota:** Adicionalmente, el NDP de ICMPv6 incluye un mensaje de redireccionamiento, el cual cumple una función similar a la del protocolo en ICMPv4.

----

