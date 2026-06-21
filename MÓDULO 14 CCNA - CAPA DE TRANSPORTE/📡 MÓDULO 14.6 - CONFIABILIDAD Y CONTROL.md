
---

La fiabilidad de TCP se basa en su capacidad para garantizar que los datos lleguen completos y en el orden correcto, incluso si los segmentos se pierden o llegan desordenados en la red.

### Mecanismos de Confiabilidad de TCP

**Números de Secuencia:** A cada segmento se le asigna un número que indica la posición del primer byte de datos de ese segmento en el flujo total. Esto permite al receptor identificar, ordenar y reensamblar los datos tal como fueron enviados originalmente.

**ISN (Initial Sequence Number):** Al iniciar la sesión, se define un número de secuencia inicial aleatorio (por seguridad, para evitar ataques). A medida que se transmiten datos, este número se incrementa según la cantidad de bytes enviados.

**Seguimiento y Reensamblado:** Gracias a este seguimiento byte a byte, el receptor puede detectar fácilmente si falta un segmento (pérdida) y solicitar su retransmisión, o corregir el orden si los paquetes llegaron desordenados.

> **Nota:** Mientras que UDP entrega datos según llegan sin importar el orden, TCP utiliza esta numeración estricta para asegurar la integridad de la información, lo cual es vital para aplicaciones donde la corrupción de datos es inaceptable (como bases de datos o transferencias de archivos).

---

**Los segmentos TCP se reordenan en el destino:**

![](Los%20segmentos%20TCP%20se%20reordenan%20en%20el%20destino.png)


El proceso TCP receptor almacena los datos en un búfer, ordenándolos secuencialmente antes de entregarlos a la capa de aplicación.

Si llegan segmentos desordenados, el sistema los retiene y espera a que lleguen los bytes faltantes para procesar todo el conjunto en el orden correcto.

---

TCP gestiona la pérdida de datos mediante un mecanismo de **retransmisión**. Si un segmento no es reconocido (ACK) por el receptor, el emisor asume que se perdió y lo reenvía.

**Conceptos importantes:**

**SEQ (Sequence Number):** Identifica el primer byte de datos de un segmento para que el receptor sepa dónde encaja.

**ACK (Acknowledgment Number):** Es un "acuse de recibo de expectativa", donde el receptor confirma qué byte espera recibir a continuación.

**El problema de la ineficiencia original:**

Anteriormente, si se enviaban los segmentos del 1 al 10 y se perdían el 3 y el 4, el receptor solo podía pedir el número 3. El emisor, al no saber qué otros paquetes llegaron (del 5 al 10), tenía que **reenviar todo desde el 3 hasta el 10**. Esto provocaba duplicados innecesarios, desperdicio de ancho de banda y congestión en la red.

![](retransmisión.png)

El **SACK (Acuse de recibo selectivo)** optimiza la retransmisión de datos:

**Problema antiguo:** Si se perdían paquetes, el emisor reenviaba todo el bloque, duplicando datos innecesarios.

**Solución SACK:** El receptor informa al emisor qué paquetes llegaron exactamente (aunque haya huecos). Así, el emisor **solo reenvía lo que realmente falta**, evitando desperdiciar ancho de banda y reduciendo la congestión.

![](SACK.png)

**Acuses de recibo:** Por norma general, TCP envía un ACK por cada dos paquetes recibidos, aunque este comportamiento puede variar según condiciones de red externas.

**Temporizadores de retransmisión:** TCP utiliza temporizadores para medir el tiempo de espera; si no llega un ACK antes de que el temporizador expire, el protocolo asume que el segmento se perdió y procede automáticamente a reenviarlo.

----

El **control de flujo** en TCP asegura que el emisor no sature al receptor con más datos de los que puede procesar, manteniendo así la estabilidad y confiabilidad de la conexión.

### Tamaño de la Ventana

Para lograr esto, TCP utiliza un campo de **16 bits** en su encabezado llamado **"tamaño de la ventana"**.

**¿Cómo funciona?**: El receptor le indica al emisor, mediante este campo en cada acuse de recibo (ACK), cuántos bytes está dispuesto a recibir en ese momento (su capacidad actual de búfer).

**Ajuste dinámico**: Si el receptor está ocupado o su memoria se llena, reduce el tamaño de la ventana en sus mensajes ACK, obligando al emisor a reducir la velocidad de transmisión. Si el receptor tiene capacidad libre, aumenta la ventana para que la transferencia sea más rápida.

En esencia, el tamaño de la ventana es el "acelerador" de la comunicación: el receptor controla el ritmo para evitar desbordamientos y asegurar que todos los datos sean procesados correctamente.

---

**Ejemplo de tamaño de ventana**

![](Ejemplo%20de%20tamaño%20de%20ventana.png)

El **control de congestión** en TCP es el mecanismo que evita que la red se sature. A diferencia del control de flujo (que protege al receptor), este protege a toda la red:

**Evita el colapso:** Detecta cuando hay demasiados datos circulando a través de los nodos de la red.

**Ajuste dinámico:** Si la red se congestiona, TCP reduce automáticamente la velocidad de envío para aliviar la carga.

**Regreso a la normalidad:** Una vez que la congestión disminuye, TCP incrementa gradualmente la velocidad de transmisión para aprovechar el ancho de banda disponible sin causar nuevos problemas.

---
### Tamaño Máximo de Segmento (MSS)

Es la cantidad máxima de datos reales que un dispositivo puede recibir en un solo segmento TCP.

**Cálculo:** Se determina restando los encabezados (IP y TCP) de la **MTU** (Unidad Máxima de Transmisión) de la red.

**Estándar:** En una red Ethernet estándar (MTU de 1500 bytes), si restamos 20 bytes del encabezado IP y 20 bytes del encabezado TCP, obtenemos un **MSS de 1460 bytes**.

**En resumen:** Mientras que el **tamaño de la ventana** controla _cuántos_ bytes se pueden enviar antes de una pausa, el **MSS** controla _qué tan grande_ puede ser cada paquete individual para que no sea fragmentado por la red. Ambos se negocian al inicio de la conexión durante el enlace de tres vías.

![](Tamaño%20Máximo%20de%20Segmento.png)

![](MSS.png)

---

**Control de congestión TCP:**

Cuando una red se congestiona, los routers empiezan a descartar paquetes, lo que provoca retrasos y pérdidas de datos. Si el emisor retransmite agresivamente sin control, puede empeorar la situación creando un "efecto de retroalimentación" que colapse aún más la red.

Para prevenir esto, TCP aplica el **control de congestión**:

**Detección:** El emisor nota que sus segmentos no llegan o tardan demasiado en ser reconocidos (_ACK_).

**Acción:** El emisor reduce proactivamente el número de bytes que envía antes de recibir un reconocimiento.

**Distinción importante:** Esta reducción de tráfico la decide el **emisor** basándose en la congestión de la red, lo cual es distinto al "tamaño de la ventana" (que es el límite fijado por el destino según su propia capacidad de procesamiento).

En resumen: el emisor "baja la velocidad" cuando detecta que la red no puede manejar el tráfico actual para evitar un colapso.

![](Control%20de%20congestión%20TCP.png)

---

