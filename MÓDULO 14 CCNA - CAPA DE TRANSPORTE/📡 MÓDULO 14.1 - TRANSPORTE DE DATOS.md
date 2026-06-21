
---

### Función de la capa de transporte:

La capa de transporte actúa como el enlace esencial entre las aplicaciones y la red subyacente, encargándose de gestionar las comunicaciones lógicas y las sesiones temporales entre programas que se ejecutan en diferentes hosts. Opera de forma abstracta, enfocándose exclusivamente en la entrega de datos sin involucrarse en detalles técnicos como la ruta, el tipo de medio o la congestión de la red, y cumple esta misión apoyándose en dos protocolos fundamentales: **TCP** (Protocolo de Control de Transmisión) y **UDP** (Protocolo de Datagramas de Usuario).

![](Función%20de%20la%20capa%20de%20transporte.png)

----
### Responsabilidades de la Capa de Transporte

| **Responsabilidad**                            | **¿Qué hace exactamente?**                                                                                                                                                               |
| ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Seguimiento de conversaciones individuales** | Mantiene un registro de cada flujo de comunicación por separado entre las aplicaciones de origen y destino (puedes tener muchas pestañas del navegador o apps abiertas al mismo tiempo). |
| **Segmentación de datos y rearmado**           | Divide los datos grandes de la aplicación en bloques más pequeños (segmentos) para que puedan viajar por la red, y los vuelve a unir en el orden correcto al llegar al destino.          |
| **Agregar información de encabezado**          | Añade un encabezado a cada segmento con datos de control cruciales (como los números de puerto) para asegurar la entrega y el rearmado.                                                  |
| **Identificación de las aplicaciones**         | Utiliza **números de puerto** para saber a qué aplicación específica debe entregar los datos (por ejemplo, puerto 80 para web, puerto 22 para SSH).                                      |
| **Multiplexión de conversaciones**             | Entrelaza los segmentos de diferentes aplicaciones para que todas puedan usar la red simultáneamente sin que sus datos se mezclen.                                                       |

----
#### Protocolos de capa de transporte.

Mientras que el protocolo IP se encarga exclusivamente del direccionamiento y enrutamiento de los paquetes, la **capa de transporte** es la responsable de definir cómo se entregan realmente esos mensajes entre los dispositivos. Dado que cada aplicación tiene diferentes necesidades de fiabilidad en su comunicación, esta capa ofrece dos protocolos principales, **TCP y UDP**, para administrar y adaptar adecuadamente el transporte de los datos según los requisitos específicos de cada conversación.

![](Protocolos%20de%20capa%20de%20transporte.png)

---

### Protocolo de Control de Transmisión (TCP)

A diferencia del protocolo IP (que solo se encarga de enrutar los paquetes sin importar si llegan o no), **TCP es un protocolo confiable y completo** que asume la responsabilidad absoluta de garantizar que todos los datos lleguen a su destino de forma correcta.

**Características principales:**

**Unidad de datos:** TCP toma los datos de la aplicación y los divide en bloques llamados **segmentos**.

**Orientado a la conexión:** Antes de enviar cualquier dato, TCP establece primero una conexión formal entre el remitente y el receptor para poder rastrear el estado de la conversación.

**Analogía:** Funciona como un servicio de paquetería con número de rastreo, donde el cliente puede verificar paso a paso que todas las partes de su envío lleguen y lo hagan en el orden correcto.


**Operaciones básicas de confiabilidad y control de flujo:** Para lograr esta entrega garantizada (lo cual requiere mayor poder de procesamiento en los equipos), TCP ejecuta las siguientes cinco acciones:

**Numerar y rastrear:** Asigna un identificador a cada segmento de datos transmitido entre las aplicaciones.

**Confirmar recepción:** El receptor envía un aviso (acuse de recibo) confirmando qué datos ya llegaron a salvo.

**Retransmitir:** Si el remitente no recibe la confirmación después de un tiempo determinado, vuelve a enviar esa información automáticamente.

**Secuenciar:** Si los segmentos toman rutas distintas y llegan desordenados, TCP los vuelve a armar en la secuencia original exacta.

**Controlar la velocidad:** Regula el ritmo de envío para que los datos viajen a una velocidad eficiente y aceptable, evitando saturar al equipo receptor.

![680](TCP.png)

---

### Protocolo de Datagramas de Usuario (UDP)

A diferencia de TCP, **UDP es un protocolo mucho más simple y rápido**, diseñado para entregar datos entre aplicaciones con la mínima sobrecarga posible. Para lograr esta velocidad, sacrifica deliberadamente todas las funciones de confiabilidad y control de flujo.

**Características principales:**

**Unidad de datos:** UDP divide la información de la aplicación en bloques conocidos estrictamente como **datagramas** (aunque en la práctica a veces también se les llame segmentos).

**Sin conexión y sin estado (_Stateless_):** No establece ninguna sesión o "saludo" previo con el receptor antes de comenzar a transmitir. Además, no lleva ningún registro ni seguimiento de los datos que entran o salen.

**Entrega de "mejor esfuerzo" (_Best-effort_):** UDP envía la información hacia el destino "esperando lo mejor". No exige acuses de recibo, lo que significa que el emisor jamás se entera si los datos llegaron correctamente, si llegaron en desorden o si se perdieron en el camino.

**Baja sobrecarga:** Al no tener que administrar acuses de recibo, retransmisiones ni secuencias, sus campos de encabezado son mucho más pequeños y los dispositivos pueden procesarlos a gran velocidad.


> **La analogía perfecta:** Usar UDP es como enviar una **carta regular y sin registrar por correo**. Simplemente la echas al buzón; no sabes si el destinatario está disponible, no tienes un número de rastreo, y la oficina de correos no se hace responsable de avisarte si la carta nunca llegó a su destino.

![](UDP.png)

---

La elección entre TCP y UDP recae en los desarrolladores y depende completamente de qué es más importante para la aplicación: **la precisión absoluta o la velocidad sin interrupciones**.

**¿Cómo elegir el protocolo correcto?**

| **Protocolo** | **Prioridad**                                                               | **Tolerancia**                                                            | **Casos de uso típicos**                                                            |
| ------------- | --------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| **UDP**       | **Velocidad y tiempo real.** Requiere poca sobrecarga en la red.            | Tolera la pérdida de datos (glitches), pero **NO tolera retrasos** (lag). | Voz sobre IP (VoIP), Video en vivo, DNS.                                            |
| **TCP**       | **Confiabilidad e integridad.** Requiere que la información llegue intacta. | Tolera retrasos (buffering), pero **NO tolera pérdida de datos**.         | Navegadores web (HTTP/HTTPS), Correo electrónico, Bases de datos, Video almacenado. |

---
### Desglose de Aplicaciones Específicas:

**Aplicaciones de Voz y Video en Vivo (UDP):** Si pierdes uno o dos paquetes de datos durante una llamada, quizás escuches una leve distorsión o veas un salto en la imagen, pero la conversación continúa. Si usaras TCP, la llamada se pausaría constantemente esperando retransmisiones, haciéndola incomprensible.

Excepción de Firewall: Las videoconferencias intentan usar UDP por defecto, pero si un firewall corporativo lo bloquea, la aplicación puede verse forzada a usar TCP como plan de respaldo.

**Servicio de Nombres de Dominio - DNS (UDP):** Usa UDP porque la transacción es mínima (una simple pregunta y respuesta). Si la PC no recibe respuesta rápido, simplemente vuelve a enviar la solicitud sin necesidad de establecer una conexión compleja previa.

**Video Almacenado / Películas a pedido (TCP):** Plataformas como Netflix usan TCP. Si tu ancho de banda cae, la aplicación prefiere pausar la película y mostrar el mensaje "Almacenando en búfer..." (_buffering_) para recuperar los segmentos perdidos y asegurar que veas el video con la calidad correcta, en lugar de saltarse escenas.

**Web, Correo y Datos Financieros (TCP):** Aquí la confiabilidad lo es todo. Si falta un solo paquete de datos al cargar tu estado de cuenta bancario, la información sería ilegible o corrupta. TCP garantiza que todo llegue en su formato original.

![](Apps%20especifícas%20para%20el%20tcp%20y%20udp.png)

----

