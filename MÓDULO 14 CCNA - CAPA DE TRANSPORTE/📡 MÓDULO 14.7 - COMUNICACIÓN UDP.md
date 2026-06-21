
---

UDP destaca por su eficiencia y velocidad gracias a dos factores clave:

**Ausencia de conexión:** Al no requerir un establecimiento previo de sesión, elimina los retrasos iniciales, siendo ideal para servicios en tiempo real como VoIP.

**Baja sobrecarga:** Su encabezado de datagrama es extremadamente pequeño y no genera tráfico adicional de gestión o administración de red (como confirmaciones o ajustes de flujo), lo que maximiza la capacidad de transmisión útil.

En esencia, UDP sacrifica la confiabilidad y el control de TCP para lograr una transferencia de datos directa, ligera y casi instantánea.

![](../IMG/MODULO14IMG/COMUNICACIÓN%20UDP.png)

---

A diferencia de TCP, UDP prioriza la velocidad sobre el orden y la integridad:

**Sin seguimiento:** UDP no utiliza números de secuencia para rastrear el orden de los datagramas.

**Procesamiento inmediato:** Los datagramas se entregan a la aplicación tal cual llegan, aunque estén desordenados.

**Responsabilidad de la aplicación:** Si el orden es fundamental para la aplicación (como en un streaming de video), es la propia aplicación la que debe incluir mecanismos para reordenar o gestionar la secuencia de los datos recibidos.

**UDP: sin conexión y poco confiable**

![](../IMG/MODULO14IMG/UDP%20sin%20conexión%20y%20poco%20confiable.png)


---

En los servidores basados en UDP, el funcionamiento es similar al de TCP en cuanto a la asignación de puertos, aunque con menor sobrecarga:

**Asignación:** Las aplicaciones y servicios UDP utilizan puertos conocidos o registrados para escuchar solicitudes entrantes.

**Procesamiento:** Cuando llega un datagrama UDP, el sistema operativo identifica el puerto de destino y entrega los datos directamente a la aplicación correspondiente que esté ejecutándose en ese puerto.

**Simplicidad:** Al no haber conexión ni procesos complejos de administración (como en TCP), el servidor simplemente recibe y procesa el datagrama de inmediato.


> **Nota:** Un ejemplo común es el servidor **RADIUS** (Servicio de usuario de acceso telefónico de autenticación remota), que utiliza UDP para gestionar la autenticación, autorización y contabilidad de usuarios en la red de forma eficiente.

**Servidor UDP a la escucha de solicitudes**

![](../IMG/MODULO14IMG/Servidor%20UDP%20a%20la%20escucha%20de%20solicitudes.png)

---

Al igual que en TCP, la comunicación UDP inicia cuando un cliente solicita datos a un servidor. El cliente selecciona dinámicamente un puerto de origen aleatorio, mientras que el puerto de destino suele ser el puerto conocido o registrado del servicio del servidor. Una vez establecidos, este mismo par de puertos se utiliza en el encabezado de todos los datagramas durante la transacción. Cuando el servidor necesita devolver los datos al cliente, simplemente invierte estos números de puerto (origen y destino) en el encabezado de su respuesta.

| **Elemento de la transacción UDP**      | **Descripción**                                                                                                                                                                           |
| --------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Clientes que envían solicitudes UDP** | El proceso inicia cuando una aplicación cliente necesita un servicio rápido (como consultar un DNS) y genera un datagrama para enviarlo al servidor.                                      |
| **Puertos de destino de solicitud UDP** | Es el puerto "conocido" o registrado en el servidor (ej. puerto 53 para DNS). El cliente dirige su mensaje a este puerto porque sabe que el servicio correspondiente está escuchando ahí. |
| **Puertos de origen de solicitud UDP**  | Es un número de puerto generado dinámicamente (al azar) por el sistema operativo del cliente. Sirve como "dirección de remitente" para esta conversación específica.                      |
| **Destino de respuesta UDP**            | Cuando el servidor envía su respuesta, el puerto de destino ahora es el puerto dinámico que el cliente generó en el paso anterior.                                                        |
| **Puertos de origen de respuesta UDP**  | Al responder, el servidor utiliza su puerto conocido original como origen, indicándole al cliente de qué servicio proviene la información.                                                |

---

![](../IMG/MODULO14IMG/Clientes%20que%20envían%20solicitudes%20UDP.png)

---

![](../IMG/MODULO14IMG/Puertos%20de%20destino%20de%20solicitud%20UDP.png)

---

![](../IMG/MODULO14IMG/Puertos%20de%20origen%20de%20solicitud%20UDP.png)

---

![](../IMG/MODULO14IMG/Puertos%20de%20origen%20de%20respuesta%20UDP.png)

---

![](../IMG/MODULO14IMG/Destino%20de%20respuesta%20UDP.png)

---

