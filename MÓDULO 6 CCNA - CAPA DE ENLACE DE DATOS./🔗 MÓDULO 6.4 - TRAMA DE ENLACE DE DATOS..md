
---

### La Trama (The Frame)

La Capa de Enlace de Datos prepara los paquetes de Capa 3 (IPv4 o IPv6) para su transporte local envolviéndolos con un **encabezado (Header)** y un **tráiler (Trailer)**, creando así una **trama**. Su función principal es garantizar la comunicación directa de tarjeta a tarjeta (**NIC a NIC**) dentro de la misma red.

Sin importar el protocolo físico que utilices, toda trama se divide estrictamente en tres partes básicas:

 **Header (Encabezado):** Contiene información de control al inicio, como las direcciones físicas de origen y destino.

**Data (Datos):** El paquete de Capa 3 intacto que se está transportando en el campo central.

**Trailer (Tráiler):** Información añadida al **final** de la trama. 

**OJO:** La Capa 2 es la única del modelo OSI que agrega un tráiler al final de su PDU.

![](../IMG/La%20Trama.png)

---

### Campos de la Trama (Frame Fields)

La encapsulación de la Capa 2 añade indicadores específicos al inicio y al final del paquete de datos. Los campos clave que componen una trama genérica son:

**Inicio de trama (Frame Start):** Utiliza bits especiales de sincronización para alertar a las interfaces receptoras de que una nueva trama está llegando.

**Direccionamiento (Addressing):** Contiene las direcciones físicas de hardware de la red local:

Dirección física de origen (Source MAC).
 
Dirección física de destino (Destination MAC).

**Tipo (Type):** Este es un campo utilizado exclusivamente por la subcapa LLC para identificar con precisión qué protocolo de Capa 3 (IPv4, IPv6, ARP, etc.) viene encapsulado dentro de la trama.

**Control (Control):** Especifica servicios especiales de control de flujo o priorización del tráfico (como Calidad de Servicio / QoS).

**Datos (Data):** Contiene la carga útil de la trama, que corresponde al paquete de la capa de red intacto (PDU de Capa 3).

**Detección de errores (Error Detection):** Campo del tráiler utilizado para verificar que la trama no haya sufrido alteraciones eléctricas o físicas durante su transporte.

----

### Direccionamiento de Capa 2 (Layer 2 Addressing)

A diferencia de las direcciones lógicas de la Capa 3 (IP), que sirven para enrutar datos de extremo a extremo a través de múltiples redes globales, las direcciones de la Capa 2 se utilizan únicamente para el transporte local.

En cierto modo la función exclusiva de esta mimsa es garantizar la entrega del mensaje de una interfaz de red (**NIC**) a otra interfaz de red dentro de la **misma red física o segmento**.

**Comportamiento en los Routers:** Cuando el paquete necesita salir de la red local hacia otra red remota, el router intermedio elimina la trama de Capa 2 por completo, procesa la dirección IP de Capa 3 y empaqueta el mismo paquete en una **nueva trama** con direcciones físicas locales totalmente distintas para el siguiente enlace.

---

### Tramas LAN y WAN (LAN and WAN Frames)

Debemos saber que los protocolos de Capa 2 varían según la infraestructura, la distancia geográfica y el tipo de medio físico utilizado:

 **Protocolos LAN (Redes de Área Local):** Utilizan principalmente tecnologías de acceso múltiple basadas en contención donde muchos hosts comparten el mismo medio. El estándar predominante es **Ethernet (IEEE 802.3)** para conexiones cableadas, y **WLAN (IEEE 802.11)** para el espectro inalámbrico.

**Protocolos WAN (Redes de Área Amplia):** Tradicionalmente estas interconectan puntos geográficos distantes mediante enlaces dedicados punto a punto, por lo que no requieren mecanismos complejos de control de acceso múltiple. Los protocolos comunes de ingeniería WAN incluyen:

**PPP** (Point-to-Point Protocol).

**HDLC** (High-Level Data Link Control).

**Frame Relay** (Legacy).

**ATM** (Asynchronous Transfer Mode - Legacy).

---

![](../IMG/Campos%20de%20la%20Trama.png)

---

| **Campo**                         | **Tamaño**      | **Tipo**   | **Función Técnica en Hardware**                                                                                     |
| --------------------------------- | --------------- | ---------- | ------------------------------------------------------------------------------------------------------------------- |
| **Preamble**                      | 7 Bytes         | Encabezado | Sincronización de relojes internos del receptor (bits alternos `10101010`).                                         |
| **SFD** _(Start Frame Delimiter)_ | 1 Byte          | Encabezado | Indica el fin del preámbulo (`10101011`) y el inicio de los datos de direccionamiento.                              |
| **Destination MAC**               | 6 Bytes         | Encabezado | Dirección física del destino. El switch la lee primero para saber por qué puerto conmutar.                          |
| **Source MAC**                    | 6 Bytes         | Encabezado | Dirección física del origen. El switch la usa para registrarla en su tabla MAC.                                     |
| **Type / Length**                 | 2 Bytes         | Encabezado | Identifica el protocolo de Capa 3 (**Ethernet II**) o la longitud exacta de los datos (**IEEE 802.3**).             |
| **Data and Pad**                  | 46 - 1500 Bytes | Datos      | El paquete IP encapsulado. Si mide menos de 46 bytes, se aplica un relleno (_Pad_) de bits vacíos.                  |
| **FCS** _(Frame Check Sequence)_  | 4 Bytes         | Tráiler    | Contiene el valor del algoritmo matemático **CRC**. Si el cálculo no coincide en el receptor, la trama se descarta. |

---

**Host to Router:**

![](../IMG/Host%20to%20Router.png)

**Router to Router:**

![](../IMG/Router%20to%20Router.png)

**Router to Host:**

![](../IMG/Router%20to%20Host.png)

---

#### Mecánica de Control y Campos Especiales de la Trama

 **Frame Start y Frame Stop Indicator Flags:** Son banderas de marcado (patrones específicos de bits) ubicadas en los extremos absolutos de la estructura. Sirven para delimitar los límites iniciales y finales de la trama, permitiendo a la NIC saber exactamente dónde termina el flujo eléctrico de una trama y dónde empieza la siguiente.

**Control de Flujo Dinámico (QoS):** El campo _Control_ no solo prioriza, sino que gestiona servicios de flujo específicos. Por ejemplo, las tramas de **Voz sobre IP (VoIP)** reciben marcas de control críticas debido a su extrema sensibilidad al retardo físico (_delay_) y a la fluctuación de fase (_jitter_).

#### Naturaleza de las Direcciones de Capa 2 vs. Capa 3

**Ausencia de Jerarquía:** A diferencia de las direcciones IP de Capa 3 (que son jerárquicas e indican la red y subred exacta donde se encuentra un host), las direcciones físicas de Capa 2 son **planas**. No indican la ubicación geográfica ni la red del dispositivo.

**Invariabilidad del Hardware:** La dirección física es grabada por el fabricante en la ROM de la NIC y es permanente. El dispositivo conservará exactamente la misma dirección de Capa 2 incluso si se traslada físicamente a otra red, otra ciudad o una subred IP completamente diferente.

**Posicionamiento en el Header:** Las direcciones físicas se sitúan estrictamente al principio del encabezado de la trama. Esto permite que la tarjeta de red (NIC) receptora intercepte y verifique el destino de forma casi instantánea, descartando el resto de la trama inmediatamente si la dirección MAC no coincide con la suya, ahorrando ciclos de procesamiento.

---

El protocolo de Capa 2 se elige según el alcance geográfico, costo y ancho de banda: las **LAN** (áreas cortas) aprovechan tecnologías baratas de gran ancho de banda para conectar muchos hosts (_Ethernet/Wi-Fi_), mientras que las **WAN** tradicionales (largas distancias) limitaban su ancho de banda por el alto costo del cableado, usando protocolos optimizados para líneas seriales (_PPP/HDLC_). Actualmente, esta división desaparece gracias a la transición hacia **Metro Ethernet**, que extiende las tramas Ethernet a nivel global.

---
