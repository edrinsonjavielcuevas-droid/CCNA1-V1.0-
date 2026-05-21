
---

### Acceso a los Medios (Providing Access to Media)

A lo largo del viaje de un paquete desde el origen hasta su destino, este cruza diferentes entornos de red con características físicas totalmente distintas (por ejemplo, una LAN Ethernet con muchos hosts compitiendo por el cable vs. un enlace serial WAN que conecta directamente solo a dos routers sin competencia).

Debido a esto, la trama cambia en cada tramo del camino para adaptarse al medio físico.

---

#### Las 4 Funciones de Capa 2 en cada Salto (Hop)

En cada router intermedio del trayecto se repite estrictamente este proceso de hardware:

1. **Recibe:** Acepta la trama desde el medio de entrada (Capa 1).
    
2. **Desencapsula:** Abre la trama eliminando el encabezado y el tráiler de Capa 2 para dejar al descubierto el paquete de Capa 3 (IP).
    
3. **Reencapsula:** Toma ese mismo paquete IP intacto y lo introduce dentro de una **nueva trama** diseñada específicamente para el tipo de medio del siguiente enlace.
    
4. **Reenvía:** Envía la nueva trama hacia el canal físico correspondiente.

---

### Estándares de la Capa de Enlace de Datos

A diferencia de los protocolos de las capas superiores de la suite TCP/IP (que son de software y se definen mediante **RFCs** a través de la **IETF**), los protocolos de las capas bajas (Capa 1 y Capa 2) dependen directamente de tecnologías de hardware y compatibilidad física.

Por lo tanto, la Capa de Enlace de Datos es regulada por **organizaciones de ingeniería** que definen estándares y protocolos abiertos:

**IEEE** (Institute of Electrical and Electronics Engineers)

**ITU** (International Telecommunication Union)

**ISO** (International Organization for Standardization)

**ANSI** (American National Standards Institute)

![](Estándares%20de%20la%20Capa%20de%20Enlace%20de%20Datos.png)

---
