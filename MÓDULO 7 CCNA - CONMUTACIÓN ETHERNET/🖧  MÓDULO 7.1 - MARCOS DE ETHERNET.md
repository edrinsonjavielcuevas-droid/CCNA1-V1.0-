
---

### Encapsulación de Ethernet

Ethernet es en pocas palabras la tecnología LAN cableada predominante en la actualidad en conjunto con WLAN/Wi-Fi en el ámbito inalámbrico. Esta utiliza medios físicos como par trenzado, fibra óptica y cables coaxiales.

**Alcance del modelo OSI:** Opera simultáneamente en la **Capa 1 (Física)** y la **Capa 2 (Enlace de datos)**. Sus protocolos y tecnologías están estrictamente definidos bajo los estándares **IEEE 802.2** y **IEEE 802.3**.

**Capacidad de Ancho de Banda:** Admite velocidades de datos que escalan desde los 10 Mbps históricos hasta los 100 Gbps modernos (pasando por 100 Mbps, 1 Gbps, 10 Gbps y 40 Gbps).

![](Ethernet%20Switching.png)

---

### Subcapas de Enlace de Datos (Data Link Sublayers)

Los protocolos LAN/MAN de la familia IEEE 802 dividen la Capa 2 (Enlace de datos) en dos subcapas independientes para separar las funciones de software de las de hardware:

**Subcapa LLC (Logical Link Control - IEEE 802.2):** Es la sección orientada al software. ==Sirve de puente de comunicación entre el software de red de las capas superiores y el hardware de las capas inferiores.== Coloca información en la trama para identificar qué protocolo de Capa 3 se está utilizando (IPv4, IPv6, etc.), permitiendo que múltiples protocolos de red compartan la misma interfaz física y medio.

**Subcapa MAC (Media Access Control - IEEE 802.3, 802.11, 802.15):** Es la sección implementada directamente en el hardware de la NIC. Es responsable de la encapsulación de datos (armar la trama) y del control de acceso al medio. Proporciona el direccionamiento físico (direcciones MAC) y se integra directamente con las diversas tecnologías de la Capa Física (cobre, fibra o aire).

![](Data%20Link%20Sublayers.png)

**Subcapa MAC:** Es responsible de la encapsulación de la data y del acceso al medio directamente.

La subcapa MAC (**IEEE 802.3**) controla el hardware mediante dos tareas clave:

**Encapsulación de datos:** Estructura la trama, añade las direcciones físicas (MAC origen/destino) para la entrega local NIC a NIC, y agrega el tráiler **FCS** para la detección de errores.

**Control de acceso al medio:** Regula la salida de datos según la infraestructura física (cobre o fibra). En redes legadas compartidas (**half-duplex** con hubs), activa **CSMA/CD** y su algoritmo de respaldo (_back-off_) para gestionar colisiones; en redes modernas con switches (**full-duplex**), CSMA/CD se desactiva por completo al contar con canales bidireccionales dedicados y libres de colisiones.

![](Subcapa%20MAC.png)


---

### Tamaños de la Trama Ethernet

En Ethernet, el tamaño de una trama tiene límites estrictos de hardware que van desde los **64 bytes hasta los 1518 bytes** (contando desde la dirección MAC de destino hasta el campo FCS; el preámbulo no se incluye en esta suma). Si una trama se sale de estos márgenes, el switch o la tarjeta de red la descartan de inmediato.

---


**Runt Frame / Fragmento de colisión (Menos de 64 bytes):** Si una trama mide menos del mínimo obligatorio, el hardware asume que se rompió debido a un choque eléctrico (colisión) o interferencia en el cable. Se borra automáticamente.

**Jumbo Frame / Baby Giant (Más de 1500 bytes de datos):** Son tramas gigantes que superan el máximo estándar. Aunque los dispositivos normales las descartan por considerarlas inválidas, los switches y NICs modernos de Fast Ethernet y Gigabit Ethernet las permiten para mover volúmenes masivos de datos de forma más eficiente.

**Nota técnica:** Una trama estándar puede verse un poco más grande de 1518 bytes si incluye tecnologías adicionales como el etiquetado de VLANs (VLAN tagging).

---

![](CAMPOS%20DE%20TRAMA%20ETHERNET.png)

**Detalle de Campos: Trama Ethernet:**

| **Campo**                           | **Tamaño**                                   | **Función Clave (Qué hace en el hardware)**                                                               | **Detalles de Examen **                                                                                                                                                                   |
| ----------------------------------- | -------------------------------------------- | --------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Preámbulo y SFD**                 | **8 Bytes** total<br><br>  <br><br>_(7 + 1)_ | **Sincronización:** Avisa a las interfaces receptoras que se preparen para recibir una nueva trama.       | El SFD marca el límite exacto donde termina la preparación y empiezan los datos reales.                                                                                                   |
| **MAC de Destino**                  | **6 Bytes**                                  | **Direccionamiento:** Indica a quién va dirigido el mensaje. La NIC compara este campo con su propia MAC. | Puede ser una dirección de tipo **Unicast**, **Multicast** o **Broadcast**.                                                                                                               |
| **MAC de Origen**                   | **6 Bytes**                                  | **Identificación:** Identifica la NIC o interfaz física que generó la trama originalmente.                | El switch lee este campo para armar su tabla de direcciones MAC.                                                                                                                          |
| **Tipo / Longitud**                 | **2 Bytes**                                  | **Demultiplexación:** Identifica qué protocolo de Capa 3 está encapsulado dentro de los datos.            | Valores comunes (en Hexadecimal):<br><br>  <br><br>• `0x0800` $\rightarrow$ **IPv4**<br><br>  <br><br>• `0x86DD` $\rightarrow$ **IPv6**<br><br>  <br><br>• `0x0806` $\rightarrow$ **ARP** |
| **Campo de Datos**                  | **46 - 1500 Bytes**                          | **Carga útil (Payload):** Contiene el paquete real de la capa superior (PDU de Capa 3).                   | Si el paquete mide menos de 46 bytes, se rellenan automáticamente con bits vacíos (**Pad**) para alcanzar el mínimo de 64 bytes totales de la trama.                                      |
| **FCS** (Secuencia de Verificación) | **4 Bytes**                                  | **Detección de errores:** Valida que la trama no se haya dañado por interferencias eléctricas.            | Utiliza el algoritmo matemático **CRC**. Si el cálculo del emisor y el receptor no coincide, la trama **se descarta** de inmediato.                                                       |

---

