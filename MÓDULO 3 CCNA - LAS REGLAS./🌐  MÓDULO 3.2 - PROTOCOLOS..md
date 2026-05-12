# Descripción general del protocolo de red.

# Tipos de Protocolos y sus Funciones

Para que los dispositivos finales se comuniquen en red, deben cumplir un conjunto de reglas comunes llamadas **protocolos**. Estos se implementan tanto en hardware como en software y cada uno tiene su propia función, formato y reglas específicas.

## 📋 Tabla Resumen de Protocolos

| Tipo de Protocolo  | ¿Para qué sirve?            | Descripción Técnica                                                                                | Ejemplos Clave           |
| :----------------- | :-------------------------- | :------------------------------------------------------------------------------------------------- | :----------------------- |
| **Comunicaciones** | Es el **"idioma"** básico.  | Permite que dos o más dispositivos se comuniquen de forma compatible a través de la red.           | IP, TCP, HTTP, Ethernet. |
| **Seguridad**      | Es el **"guardaespaldas"**. | Protege los datos mediante cifrado, integridad y verificación de identidad (autenticación).        | SSH, SSL, TLS.           |
| **Enrutamiento**   | Es el **"GPS"**.            | Permite que los routers compartan información sobre las rutas y elijan el mejor camino al destino. | OSPF, BGP.               |
| **Detección**      | Es el **"buscador"**.       | Detecta automáticamente dispositivos o servicios (como nombres de dominio o IPs) en la red.        | DHCP, DNS.               |

---

## 🧠 Conceptos que debes "Digerir"

* **Implementación:** Los protocolos no son solo ideas; están "vivos" en el hardware (tarjetas de red) y el software (sistema operativo) de tus equipos.
* **Interoperabilidad:** No importa si usas Windows, Linux o Mac; si el protocolo es el mismo (ej. HTTP), las máquinas se entenderán.
* **Handshake (Apretón de manos):** Muchos protocolos requieren un acuerdo previo antes de soltar los datos para asegurar que el receptor está listo.

----


# Funciones de los Protocolos de Red

![](IPDATOS.jpg)

Los protocolos no solo son reglas, son los responsables de que el mensaje llegue sano y salvo desde tu PC hasta el servidor. 

## Tabla de Funciones Esenciales

| Función                    | ¿Qué hace?                                                                                                      | Protocolos que la usan    |
| :------------------------- | :-------------------------------------------------------------------------------------------------------------- | :------------------------ |
| **Direccionamiento**       | Identifica quién envía y quién recibe (como el remitente y destinatario de una carta).                          | Ethernet, IPv4, IPv6      |
| **Confiabilidad**          | Garantiza que si un mensaje se pierde o se daña en el camino, se vuelva a enviar.                               | TCP                       |
| **Control de flujo**       | Se encarga de que los datos viajen a una velocidad que ambos dispositivos puedan manejar (que nadie se sature). | TCP                       |
| **Secuenciación**          | Le pone un número a cada trozo de datos para que al llegar se puedan armar en el orden correcto.                | TCP                       |
| **Detección de errores**   | Revisa si los datos se corrompieron durante el viaje.                                                           | Ethernet, IPv4, IPv6, TCP |
| **Interfaz de aplicación** | Es el puente que permite que las aplicaciones (como Chrome) hablen con la red.                                  | HTTP, HTTPS               |

---

## Notas para recordar

* **TCP** es como el "supervisor" detallista: se encarga de que todo llegue en orden, sin errores y a la velocidad correcta.

* **IP** es como el "sistema de correos": se enfoca en poner las direcciones y detectar si hubo algún daño básico.

----

# Interacción de Protocolos


![](INTERNETT.jpg)

Para que una comunicación en red sea exitosa, los protocolos deben trabajar en conjunto. Cada uno tiene su propio formato y cumple una función distinta dentro del equipo.

### 💻 Ejemplo: Solicitud de una página web

Cuando envías una solicitud a un servidor web, se activa una "pila" de protocolos que interactúan de la siguiente manera:

- **HTTP (Protocolo de transferencia de hipertexto)**: Es el protocolo de la capa de aplicación que rige cómo interactúan el cliente y el servidor web. Define el formato de las solicitudes y las respuestas.
    
- **TCP (Protocolo de control de transmisión)**: Se encarga de administrar las conversaciones individuales. Su trabajo es garantizar que la información llegue de forma fiable (sin pérdidas) y controlar el flujo de datos entre los dispositivos.
    
- **IP (Protocolo de Internet)**: Es el responsable de entregar los mensajes desde el remitente original hasta el receptor final. Los enrutadores (routers) utilizan este protocolo para decidir por qué camino enviar el mensaje a través de las redes.
    
- **Ethernet**: Este protocolo se encarga de la entrega física del mensaje de una tarjeta de red (NIC) a otra dentro de la misma red local (LAN).

---

### 💡 Analogía para entender la interacción:

Imagina que estás enviando un paquete por correo:

1. **HTTP**: Es el contenido del paquete y la nota que explica qué hay dentro.
    
2. **TCP**: Es el servicio de seguimiento y el seguro que garantiza que el paquete llegue completo y en orden.
    
3. **IP**: Es la dirección de destino escrita en la etiqueta exterior que permite que el paquete viaje entre diferentes ciudades.
    
4. **Ethernet**: Es el vehículo físico (camión o avión) que mueve el paquete por el tramo local de la carretera.

----
