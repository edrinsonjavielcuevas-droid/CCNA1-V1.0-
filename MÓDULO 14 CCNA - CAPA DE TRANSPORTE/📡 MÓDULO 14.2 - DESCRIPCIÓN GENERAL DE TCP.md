
---

#### Características fundamentales de TCP

|**Característica**|**Descripción**|
|---|---|
|**Establecimiento de sesión**|TCP es un protocolo orientado a la conexión. Negocia y establece una sesión formal entre origen y destino antes de enviar cualquier dato, permitiendo administrar el tráfico de forma precisa.|
|**Entrega confiable**|Garantiza que todos los datos enviados lleguen intactos al destino, retransmitiendo cualquier segmento que se pierda o se corrompa en el camino.|
|**Entrega en orden**|Debido a que los segmentos pueden tomar rutas distintas y llegar desordenados, TCP los enumera y secuencia para reensamblarlos correctamente al llegar.|
|**Control de flujo**|Si TCP detecta que los recursos del receptor (memoria/procesamiento) están saturados, solicita al emisor que reduzca la velocidad de transmisión, evitando desbordamientos y retransmisiones innecesarias.|

**Nota:** Estas funciones de confiabilidad y ordenamiento requieren un procesamiento mayor por parte de los dispositivos en comparación con protocolos simples como UDP. Si necesitas profundizar en los detalles técnicos, la especificación original de TCP se encuentra en el **RFC 793**.

---

### Encabezado TCP

TCP es un protocolo "con estado" porque gestiona meticulosamente cada sesión de comunicación desde su inicio hasta su finalización, manteniendo un registro constante de los datos enviados y recibidos para garantizar su integridad. Para lograr esto, cada segmento TCP añade una sobrecarga técnica de **20 bytes (160 bits)** de información de control en su encabezado, la cual es indispensable para realizar el seguimiento, la secuenciación y la confirmación de la entrega de datos.

![](Encabezado%20TCP.png)

---

### Campos del encabezado TCP 

La siguiente tabla identifica y describe los 10 campos de un encabezado TCP.

![](Campos%20del%20encabezado%20TCP.png)

---

### Aplicaciones que utilizan TCP

TCP es el ejemplo perfecto de la división de tareas en la arquitectura TCP/IP. Al delegar todas las funciones complejas de transporte (segmentación, control de flujo, reordenamiento y garantía de fiabilidad) a la capa de transporte, **TCP libera a las aplicaciones de gestionar estos procesos técnicos**. Esto permite que programas como los navegadores web, clientes de correo o bases de datos simplemente entreguen sus datos a la capa de transporte y confíen en que llegarán íntegros a su destino.

![](Aplicaciones%20que%20utilizan%20TCP.png)

----

