


#  Protocolos y Modelos de Red

##  ¿Qué son los Protocolos?

Son las **reglas del juego**. Es el lenguaje común que utilizan dos dispositivos para poder entenderse. Sin ellos, el intercambio de información sería imposible.

*   **En una frase:** Es el **CÓMO** se comunican (el idioma y las normas).
*   **Ejemplo:** El protocolo **IP** es como el sistema de etiquetas en el correo; sin una dirección clara, el paquete no sabe a dónde ir.

---

## ¿Qué son los Modelos de Red?

Son la **estructura o el mapa**. Como enviar datos es un proceso muy complejo, los modelos lo dividen en "capas" o niveles para que sea más fácil de organizar y solucionar problemas.

*   **En una frase:** Es el **DÓNDE** ocurre cada proceso (la jerarquía).
*   **Los dos estándares:**


	1.  **Modelo OSI:** El mapa teórico de 7 capas (ideal para aprender y diagnosticar).
    2.  **Modelo TCP/IP:** El mapa práctico de 4 capas (el que realmente hace funcionar Internet).

---

## ⚖️ Diferencia Clave

| Concepto      | Función          | Analogía                                          |
| :------------ | :--------------- | :------------------------------------------------ |
| **Protocolo** | Regla específica | El idioma que hablan las personas.                |
| **Modelo**    | Marco general    | La organización de una oficina por departamentos. |

--- 

NOTA: Los dispositivos son ciegos, ellos solo pueden ver su propia informacion de por sí y para poder comunicarse con los demas usan los protocolos de red.

![](Como%20vemos%20la%20red..jpg)

![](Protocolos.jpg)

![](PROTOCOLS.jpg)

*La red es como un conjunto de protocolos que le permite a los dispositivos conectarse y comunicarse entre sí*

#  FUNDAMENTOS DE LA COMUNICACIÓN:

Conectar dos PCs con un cable no es suficiente para que hablen. Para que exista comunicación real, se necesitan estos **3 elementos esenciales**:

### 1. El Origen (Emisor) 

*   **¿Qué es?:** Es la persona o el dispositivo que genera el mensaje y decide enviarlo.
*   **Ejemplo:** Tú escribiendo un mensaje o tu PC enviando una petición a un servidor.

### 2. El Destino (Receptor) 

*   **¿Qué es?:** Es quien recibe el mensaje y, lo más importante, lo **interpreta**.
*   **Ejemplo:** Tu amigo leyendo el mensaje o el servidor procesando tu petición.

### 3. El Canal (Medio) 

*   **¿Qué es?:** Es el "camino" físico o inalámbrico por donde viaja la información desde el origen al destino.
*   **Ejemplo:** Un cable de red (Ethernet), fibra óptica o el aire (Wi-Fi).

---
> [!IMPORTANT]
> **Dato clave:** Aunque tengas estos tres, la comunicación solo funciona si ambos saben el **"cómo"** comunicarse (los protocolos).

--------------------------------------------

#  Protocolos de Comunicación

Los **protocolos** son las reglas que rigen cualquier envío de mensajes, ya sea cara a cara o a través de una red. Sin reglas acordadas, la comunicación no puede ocurrir.

## 💡 Conceptos Clave

* **Reglas específicas:** Los protocolos dependen del método de comunicación (no es lo mismo hablar por teléfono que enviar una carta).

* **Acuerdo previo:** Antes de hablar, las partes deben acordar el idioma y el formato del mensaje para que sea comprensible.

* **Estructura:** Si la estructura del mensaje es deficiente (como una mala gramática), el receptor puede malinterpretar la información.

---

##  El Proceso de Comunicación (Flujo)

Tanto en humanos como en computadoras, el proceso sigue estos elementos comunes:

1. **Origen de los mensajes:** La persona o dispositivo que necesita enviar información.

2. **Transmisor:** Convierte el mensaje en señales para el medio.

3. **Canal (Medios):** El camino físico o inalámbrico por donde viaja el mensaje.

4. **Receptor:** Recibe las señales y las interpreta para el destino.

5. **Destino del mensaje:** El dispositivo o persona final que recibe e interpreta el mensaje.

---
> [!NOTE]
> En el mundo digital existen muchísimas reglas o protocolos diferentes que rigen todos los métodos de comunicación actuales.

----

#  Requisitos de Protocolo de Red

Para que la comunicación sea efectiva, los protocolos no solo identifican quién envía y quién recibe; también definen **cómo** se transportan los mensajes.

### Los 5 Requisitos Fundamentales

Cualquier protocolo de red debe cumplir con estos puntos para funcionar correctamente:

1. **Codificación de los mensajes:** Convertir los datos en señales que puedan viajar por el medio (cable, aire, etc.).
2. **Formato y encapsulamiento:** Poner la información en un "sobre" estructurado para que sea reconocible.
3. **Tamaño del mensaje:** Dividir la información en trozos manejables (paquetes).
4. **Sincronización:** Controlar el tiempo, la velocidad y el flujo de los datos para que no se pierdan.
5. **Opciones de entrega:** Decidir si el mensaje va para uno solo (**Unicast**), para un grupo (**Multicast**) o para todos (**Broadcast**).

---
> [!TIP]
> Piensa en estos requisitos como el control de calidad que asegura que tus datos lleguen intactos y a tiempo.

# Lógica de los Requisitos de Protocolo

Para que los datos viajen con éxito, deben pasar por estos procesos. 

###  Codificación de los mensajes 

* **Lógica:** Es la **traducción**.
* **En sencillo:** Es convertir tus ideas o datos en señales (eléctricas, de luz o radio) que el cable o el aire puedan transportar.

### Formato y encapsulamiento 

* **Lógica:** Es el **empaquetado**.
* **En sencillo:** Imagina meter una carta en un sobre con remitente y destinatario. El protocolo pone los datos en un "sobre digital" para que la red sepa qué es y a dónde va.

### Tamaño del mensaje 

* **Lógica:** Es la **fragmentación**.
* **En sencillo:** Si el mensaje es muy grande, se corta en trozos pequeños. Es más fácil enviar 10 paquetes pequeños que un bloque gigante que pueda atascar la red.

### Sincronización del mensaje 

* **Lógica:** Es el **ritmo**.
* **En sencillo:** Controla la velocidad de la charla. Si uno envía demasiado rápido y el otro procesa lento, los datos se pierden. Aquí se acuerda a qué velocidad hablar.

### Opciones de entrega 

* **Lógica:** Es el **destino final**.
* **En sencillo:** Define si el mensaje es para una sola persona (Unicast o Unidifunción), para un grupo selecto (Multicast o Multidifunción) o un grito que todos deben escuchar (Broadcast o transmisión).

---

![](BITSSS.jpg)

Eso era el formato y el encapsulamiento del mensaje. 

##### NOTA: 
La dirección IP es responsable de enviar un mensaje desde el origen del mensaje hasta el destino a través de una o más redes.

## Una nota sobre el icono del nodo:

En las topologías de red, los dispositivos se representan como **nodos** (círculos). Dependiendo del objetivo del mensaje, existen tres formas de entrega:

### 1. Unidifusión (Unicast)

* **Definición:** Comunicación de uno a uno.
* **Lógica:** El mensaje tiene un único origen y un único destino específico.
* **Uso común:** Envío de un correo electrónico o un mensaje privado.

### 2. Multidifusión (Multicast)

* **Definición:** Comunicación de uno a varios.
* **Lógica:** El mensaje se envía a un grupo específico de nodos que han solicitado recibir la información.
* **Uso común:** Streaming de video para un grupo de suscriptores o actualizaciones de protocolos de enrutamiento.

### 3. Difusión (Broadcast)

* **Definición:** Comunicación de uno a todos.
* **Lógica:** El mensaje se envía a todos los nodos de la red sin excepción.
* **Uso común:** Peticiones ARP para encontrar una dirección MAC en la red local.

---
 ![](FUSIONES.png)