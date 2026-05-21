
---

### La Capa de Enlace de Datos (Capa 2)

La **Capa de Enlace de Datos** actúa como el puente definitivo entre el software y el mundo físico, encargándose de la comunicación directa entre tarjetas de red (**NIC a NIC**). Básicamente, toma los paquetes de la Capa 3 (como IPv4 o IPv6) y los empaqueta en **tramas (frames)** para enviarlos a través del cable o el aire sin que las capas superiores tengan que preocuparse por el tipo de medio utilizado; además, controla el acceso a ese medio y se encarga de **detectar errores**, descartando de inmediato cualquier trama que se haya corrompido en el camino.

![](../IMG/Enlace%20de%20datos..png)

Un **nodo** es cualquier dispositivo de red (PC, switch, etc.). La **Capa 2** es clave porque aísla al protocolo IP (Capa 3) del tipo de cable o señal: toma el paquete IP, le añade las direcciones físicas (NIC origen y destino) para crear la trama y se la pasa a la Capa 1, evitando que IP tenga que cambiar cada vez que se invente un nuevo medio físico.

![](../IMG/nodo.png)

### Subcapas de la Capa de Enlace de Datos (IEEE 802)

Los estándares IEEE 802 dividen la **Capa 2 (Enlace de Datos)** en dos subcapas independientes para separar las funciones lógicas de software de las acciones físicas del hardware:

---

### 1. LLC (Logical Link Control - Control de Enlace Lógico)

Es la subcapa superior basada en **software** (IEEE 802.2) y actúa como interfaz entre el software de red y el hardware.

Su función principal es tomar el paquete de red (usualmente IPv4 o IPv6) y añadirle información de control para **identificar qué protocolo de Capa 3 se está utilizando**. Gracias a esto, múltiples protocolos de red pueden compartir la misma tarjeta de red (NIC) y el mismo medio físico.


---

### 2. MAC (Media Access Control - Control de Acceso al Medio)

Es la subcapa inferior basada en **hardware** (específica para cada tecnología: IEEE 802.3 para Ethernet, 802.11 para Wi-Fi, etc.). Controla directamente la NIC para enviar y recibir datos en el medio, y se encarga de dos tareas críticas:

**Encapsulación de datos:**

**Delimitación de tramas (_Frame delimiting_):** Añade bits especiales de sincronización para que los nodos sepan exactamente dónde empieza y termina una trama.

**Direccionamiento (_Addressing_):** Agrega las direcciones físicas (MAC de origen y destino) para transportar la trama en el medio compartido.

**Detección de errores (_Error detection_):** Incluye un tráiler al final de la trama para comprobar si los datos se corrompieron en el camino.

**Control de acceso al medio:** Administra cuándo y cómo los dispositivos transmiten datos en entornos compartidos (**Half-duplex**). 

Nota de examen: Las comunicaciones Full-duplex no requieren este control de acceso.

![](../IMG/Subcapas%20de%20la%20Capa%20de%20Enlace%20de%20Datos%20(IEEE%20802).png)

---
