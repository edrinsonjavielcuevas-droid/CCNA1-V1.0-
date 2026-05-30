---

---

---

**Descripción general de ARP  (Address Resolution Protocol)** 

En redes que operan bajo el protocolo de comunicaciones IPv4, el **Protocolo de Resolución de Direcciones (ARP)** es el mecanismo fundamental utilizado para descubrir y asignar direcciones físicas (MAC) a partir de direcciones lógicas (IPv4) conocidas.

Cuando un dispositivo necesita enviar datos a través de una red Ethernet, debe construir una trama de Capa 2. Esta trama obligatoriamente debe contener dos direcciones físicas para poder ser transmitida por el medio:

**Dirección MAC de origen:** Es la dirección física de la Tarjeta de Interfaz de Red (NIC) del dispositivo que está enviando la información.

**Dirección MAC de destino:** Si el host de destino se encuentra en el **mismo segmento de red local**, será la dirección MAC de ese dispositivo final.

Si el host de destino se encuentra en una **red remota** (diferente subred), será la dirección MAC del gateway predeterminado (el router local).

La siguiente imagen muestra el problema de enviar una trama a otro host en el mismo segmento de red IPv4.

![](../IMG/MODULO9IMG/Descripción%20general%20de%20ARP.png)


---

**Funciones Básicas de ARP**

Para que la comunicación ocurra dentro de una misma red local (LAN), un dispositivo emisor necesita obligatoriamente dos datos del receptor: su dirección lógica (IPv4) y su dirección física (MAC). Mientras que la IP suele conocerse de antemano o resolverse a través de nombres de dominio (DNS), la dirección MAC debe ser descubierta directamente en el segmento de red.

Es aquí donde interviene el **Protocolo de resolución de direcciones (ARP)**, el cual cumple dos funciones operativas críticas:

**Resolución de direcciones:** Traduce (o "resuelve") una dirección IPv4 conocida a su correspondiente dirección MAC física en la red local.

**Mantenimiento de la tabla ARP:** Almacena y administra temporalmente estas asignaciones (el mapeo de IPv4 a MAC) en la memoria del dispositivo, creando un registro para optimizar futuras comunicaciones con el mismo host sin tener que volver a preguntar a toda la red.

---

**Operación de la Tabla ARP (Caché ARP)**

Antes de que un dispositivo pueda encapsular un paquete IP dentro de una trama Ethernet de Capa 2, necesita conocer la dirección MAC de destino. Para evitar saturar la red preguntando constantemente, el dispositivo consulta primero una base de datos temporal almacenada en su memoria RAM, conocida como **Tabla ARP** o **Caché ARP**.

El proceso de búsqueda lógica se divide en dos escenarios:

**Para destinos en la misma red local:** El dispositivo emisor busca directamente la dirección IPv4 del host de destino dentro de su tabla ARP.

**Para destinos en redes remotas:** El dispositivo emisor comprende que el paquete debe salir de la red local, por lo que busca en su tabla la dirección IPv4 de su **puerta de enlace predeterminada** (_default gateway_ o router local).


**Estructura y Resultados de la Búsqueda:** La tabla funciona como un "mapa" de asignaciones: cada fila enlaza una dirección IPv4 específica con su dirección MAC física correspondiente.

Al consultar esta tabla ocurren dos posibles resultados:

**Coincidencia exitosa:** Si la dirección IPv4 buscada está en la tabla, el dispositivo utiliza inmediatamente la dirección MAC asociada para armar la trama y enviarla.

 **Entrada no encontrada:** Si la tabla no contiene un registro para esa dirección IP, el dispositivo no puede armar la trama. Como consecuencia, pausa el envío y genera una **Solicitud ARP** (_ARP Request_) dirigida a toda la red para descubrir la MAC faltante.

---

**El Proceso de Solicitud de ARP (ARP Request)**

Cuando un dispositivo necesita comunicarse con una dirección IPv4 pero no encuentra la asignación física en su caché temporal, debe generar una **Solicitud ARP**.

Es fundamental entender que los mensajes ARP operan a nivel de enlace de datos: se encapsulan **directamente** dentro de una trama Ethernet, sin necesidad de un encabezado IPv4.

La trama de la solicitud ARP se construye con las siguientes características en su encabezado:

**Dirección MAC de destino (Broadcast):** Se utiliza una dirección de difusión (típicamente `FF:FF:FF:FF:FF:FF`), lo que obliga a todas las tarjetas de red (NIC) del segmento local a recibir, aceptar y procesar la trama.

**Dirección MAC de origen:** La dirección física real del dispositivo que origina la pregunta.

**Campo de Tipo (`0x806`):** Este valor hexadecimal específico le indica a la NIC receptora que la carga útil (_payload_) de esa trama pertenece a un mensaje ARP y debe enviarse al sistema operativo para su procesamiento.

---
**Comportamiento en la Red**

**Distribución:** Al ser un mensaje de _broadcast_, el switch local reenvía la solicitud por todos sus puertos activos (excepto por el puerto donde ingresó).

**Límite de difusión:** Un router **nunca** reenvía mensajes de _broadcast_ por sus otras interfaces; las solicitudes ARP se mantienen estrictamente confinadas a la red local.

**Resolución:** Todos los dispositivos de la red reciben e inspeccionan la solicitud. Sin embargo, **solo** el dispositivo que posee la dirección IPv4 exacta solicitada responderá. Los demás dispositivos ignoran y descartan el mensaje silenciosamente.

---

**La Respuesta ARP (ARP Reply)**

Solo el dispositivo que posee la dirección IPv4 solicitada enviará una respuesta. A diferencia de la solicitud (que es _broadcast_), la respuesta ARP es un mensaje **unicast**, es decir, va dirigido única y directamente al dispositivo que hizo la pregunta inicial.

Esta respuesta se encapsula en una trama Ethernet con el siguiente encabezado:

**Dirección MAC de destino:** La MAC del remitente de la solicitud original.

**Dirección MAC de origen:** La MAC del dispositivo que está respondiendo (el objetivo).

**Tipo (`0x806`):** Indica a la tarjeta de red (NIC) receptora que debe enviar los datos al proceso ARP del sistema operativo.

**Procesamiento y Mantenimiento de la Caché**

**Actualización:** Al recibir la respuesta, el solicitante original agrega el "mapa" (la asignación de IPv4 a MAC) a su tabla ARP. A partir de este momento, ya puede construir la trama Ethernet y enviar los paquetes de datos reales.

**Descarte:** Si nadie responde a la solicitud ARP, el paquete IP se descarta porque es imposible construir la trama de enlace de datos necesaria para enviarlo.

**Temporizadores (Timestamps):** Las entradas dinámicas en la tabla ARP tienen un tiempo de vida limitado. Si un dispositivo no se comunica con esa entrada antes de que caduque el tiempo, la asignación se elimina automáticamente.

**Entradas Estáticas:** Un administrador puede introducir mapeos de forma manual en la tabla ARP. Estas entradas no caducan con el tiempo y deben borrarse manualmente (aunque su uso es poco frecuente).

**El equivalente en IPv6:** IPv6 no utiliza el protocolo ARP. En su lugar, emplea el proceso **ICMPv6 Neighbor Discovery (ND)**, el cual utiliza mensajes de "solicitud de vecino" y "anuncio de vecino" para lograr el mismo objetivo.

---

**El Rol de ARP en Comunicaciones Remotas**

Cuando un host necesita enviar información, el primer paso que realiza es comparar la dirección IPv4 de destino con su propia dirección para determinar si ambos equipos se encuentran en la misma red lógica (Capa 3).

Si el dispositivo determina que el destino está en una **red remota** (una subred diferente), el flujo de comunicación se adapta de la siguiente manera:

**Redirección al Gateway:** El dispositivo emisor no puede enviar la trama directamente al destino final. En su lugar, debe enviarla a su **puerta de enlace predeterminada** (_default gateway_), que es la interfaz del router local. El host ya conoce la IP de este router gracias a su propia configuración de red (DHCP o manual).

**Consulta ARP para el Router:** Para poder construir la trama Ethernet de Capa 2 y sacarla por el cable, el host necesita una dirección física. Por lo tanto, busca en su tabla ARP la dirección MAC que corresponde **a la IP del gateway predeterminado**, NO a la IP del destino final.

**Resolución y Envío:** Si la asignación no existe en la caché, el host genera una solicitud ARP estándar preguntando: ¿Quién tiene la IP del router?. Una vez que el router responde con su MAC, el host encapsula el paquete y se lo envía, dejando que el router se encargue del resto del viaje.

---

**Eliminación de entradas de una tabla ARP**

Debemos de saber que para mantener la eficiencia y precisión de la red, las asignaciones dinámicas en la tabla ARP no son permanentes. Las entradas pueden eliminarse mediante dos métodos:

**Eliminación Automática (Temporizadores):** Los sistemas operativos utilizan temporizadores internos que borran automáticamente las entradas si no se han utilizado durante un período específico. Este tiempo de caducidad varía según el sistema operativo (por ejemplo, los sistemas Windows más recientes suelen conservar las entradas en caché entre 15 y 45 segundos).

**Eliminación Manual:** Es posible intervenir a través de la línea de comandos para borrar entradas individuales o vaciar por completo la tabla ARP.


**Impacto de la eliminación:** Una vez que una entrada es eliminada (por caducidad o manualmente), el dispositivo emisor "olvida" esa dirección física. Si necesita volver a enviar datos a esa misma dirección IPv4, deberá reiniciar obligatoriamente el proceso completo (emitir un _ARP Request_ y recibir el _ARP Reply_) para poder registrar nuevamente la asignación MAC en su tabla.

![](../IMG/MODULO9IMG/Eliminación%20de%20entradas%20de%20una%20tabla%20ARP.png)

----

**Tablas ARP de dispositivos de red:**

En los routers de cisco usamos el comando *==show ip arp==*  para mostrar la tabla ARP.

![](../IMG/MODULO9IMG/Tablas%20ARP%20de%20dispositivos%20de%20red.png)

En los dispositivos con Windows 10 usamos el comando *==arp -a==* para ver las tablas ARP.

![](../IMG/MODULO9IMG/ARP%20-A.png)

---

**Problemas de ARP - Difusión ARP y Suplantación ARP**

Las solicitudes ARP son mensajes de difusión (_broadcast_) que todos los equipos de la red local están obligados a procesar. Aunque en condiciones normales su impacto es mínimo, si muchos dispositivos se conectan a la red simultáneamente, pueden generar un pico de tráfico de difusión que ralentice la red temporalmente. Sin embargo, este efecto dura muy poco; en cuanto los equipos obtienen las respuestas y guardan las direcciones MAC en su caché temporal, dejan de enviar difusiones y el rendimiento de la red vuelve rápidamente a la normalidad.

![](../IMG/MODULO9IMG/Difusión%20ARP.png)

---

El protocolo ARP es vulnerable a ataques de **suplantación o envenenamiento ARP (ARP Spoofing/Poisoning)**. En este escenario, un actor malicioso envía respuestas ARP falsificadas para engañar a un dispositivo, haciéndole creer que la MAC del atacante corresponde a una IP legítima de la red (como la del _gateway_ o router). La víctima guarda esta asignación corrupta en su tabla ARP y, sin saberlo, termina redirigiendo todo su tráfico hacia el atacante. Para defender la infraestructura contra esta técnica, se configura en los switches empresariales una medida de mitigación llamada **Inspección Dinámica de ARP (DAI)**.

![](../IMG/MODULO9IMG/envenenamiento%20ARP.png)

---

