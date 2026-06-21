
---
### Características de UDP

UDP se define por su simplicidad y eficiencia, operando bajo un modelo de "mejor esfuerzo" que prioriza la velocidad sobre la garantía de entrega. Al ser un protocolo liviano, evita la sobrecarga de gestión propia de TCP, lo que lo hace ideal para aplicaciones donde la rapidez es crítica y la pérdida ocasional de datos es tolerable.

| **Característica**            | **Implicación técnica**                                                                                                          |
| ----------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| **Orden de recepción**        | Los datos se reconstruyen exactamente en el orden en que llegan, sin realizar procesos de reordenamiento.                        |
| **Sin retransmisión**         | Si un datagrama se pierde en la red, no existe un mecanismo para solicitar su reenvío; se pierde permanentemente.                |
| **Sin conexión**              | No se establece una sesión previa entre emisor y receptor, ahorrando pasos y tiempo de procesamiento.                            |
| **Independiente de recursos** | El emisor no verifica la disponibilidad de memoria o CPU del receptor antes de transmitir, enviando los datos de forma continua. |
**Nota:** Debido a su naturaleza minimalista, UDP suele describirse mejor por lo que **no hace** en comparación con TCP. Si necesitas profundizar en sus especificaciones técnicas, puedes consultar los RFC (Request for Comments) correspondientes en Internet.

---

### Encabezado UDP

**Protocolo sin estado:** UDP no rastrea la sesión de comunicación. Si se necesita confiabilidad, debe ser gestionada por la propia aplicación.

**Ideal para tiempo real:** Es perfecto para voz y video en vivo porque prioriza la velocidad de flujo y tolera pequeñas pérdidas de datos que son casi imperceptibles.

**Funcionamiento:** Envía bloques de datos llamados datagramas o segmentos bajo un modelo de "mejor esfuerzo".

**Encabezado simple:** Es mucho más sencillo que el de TCP, ocupando solo 8 bytes (64 bits) distribuidos en cuatro campos.

![697](Encabezado%20UDP.png)

---

### Campos de encabezado UDP

La siguiente table muestra la descripción de los campos de encabezado UDP.

![](Campos%20de%20encabezado%20UDP.png)

---

### Aplicaciones de utilizan UDP

UDP es el protocolo ideal para tres categorías de aplicaciones específicas donde la velocidad es la máxima prioridad:

**Aplicaciones óptimas para UDP**

| **Categoría de Aplicación**                      | **Por qué usan UDP**                                                     | **Ejemplos**                      |
| ------------------------------------------------ | ------------------------------------------------------------------------ | --------------------------------- |
| **Video y multimedia en vivo**                   | Toleran pérdidas menores de datos pero no permiten retrasos (_lag_).     | VoIP, Streaming de video en vivo. |
| **Solicitudes de petición-respuesta**            | Transacciones rápidas y simples donde se espera una respuesta inmediata. | DNS, DHCP.                        |
| **Aplicaciones que autogestionan su fiabilidad** | Aplicaciones que manejan su propio control de errores y flujo.           | SNMP, TFTP.                       |

**Nota importante:** Aunque estos servicios usan UDP por defecto, pueden cambiar a **TCP** según el contexto. Por ejemplo, el **DNS** cambia a TCP si la respuesta excede los 512 bytes (muchos datos), y el **SNMP** puede configurarse para usar TCP si el administrador de red lo requiere por seguridad o fiabilidad.

![](Aplicaciones%20óptimas%20para%20UDP.png)

---

