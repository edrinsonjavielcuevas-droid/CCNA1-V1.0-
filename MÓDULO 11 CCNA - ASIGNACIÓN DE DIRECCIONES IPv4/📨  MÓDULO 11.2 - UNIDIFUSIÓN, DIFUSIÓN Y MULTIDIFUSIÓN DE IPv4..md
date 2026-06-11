
---

#### Transmisión de Unidifusión (Unicast)

Es la comunicación **uno a uno**. Un dispositivo envía un mensaje a un **único** dispositivo de destino.

**Reglas de las Direcciones IP:**

**Destino:** El paquete lleva la IP específica del receptor único.

**Origen (Regla Estricta):** La dirección IP de origen **siempre tiene que ser una dirección de unidifusión**. Un paquete de red solo puede originarse desde un único equipo a la vez, independientemente de si el mensaje se envía a uno, a varios o a todos los dispositivos.

---

#### Transmisión de Difusión (Broadcast)

Es la comunicación de **uno a todos**. Un dispositivo envía un mensaje que debe ser recibido por todos los demás dispositivos en su segmento de red.

**Estructura de la IP:** La dirección IPv4 de destino se forma llenando de unos (`1`) toda la porción de host.

Todo dispositivo que se encuentre dentro del mismo dominio de difusión está **obligado** a procesar el paquete.

**Tipos de Difusión:**

**Difusión Limitada:** Utiliza la dirección `255.255.255.255`. El mensaje se entrega exclusivamente a los hosts de la red local donde se originó.

**Difusión Dirigida:** Se envía a todos los hosts de una red _específica_ (por ejemplo, enviar a `172.16.4.255` para alcanzar a todos en la red `172.16.4.0/24`).

**Dos reglas de oro para recordar:**

**Comportamiento del Router:** Por defecto, los routers **nunca** reenvían paquetes de difusión (actúan como barreras para el broadcast).

**Pv4 vs IPv6:** IPv4 utiliza este tipo de transmisión constantemente, pero **IPv6 NO utiliza paquetes de difusión** en absoluto.

**Nota:** Debido a problemas de seguridad y abuso previo de usuarios malintencionados, las transmisiones dirigidas se desactivan de forma predeterminada a partir de Cisco IOS Release 12.0 con el comando de configuración global **no ip directed-broadcasts**.

---



