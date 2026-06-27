
---

Para que una red sea funcional, debe soportar programas que facilitan la comunicación y el acceso a los recursos. Estos se dividen en dos categorías principales:

**Aplicaciones de Red:** Son programas de usuario final que interactúan directamente con la red. Estos implementan protocolos de capa de aplicación y se comunican directamente con las capas inferiores del modelo OSI. Ejemplos claros son los navegadores web (como Chrome o Edge) y los clientes de correo electrónico.

**Servicios de Capa de Aplicación:** Son programas que trabajan en segundo plano para preparar y gestionar la transferencia de datos sin que el usuario intervenga. Actúan como intermediarios para tareas como la transferencia de archivos o la administración de colas de impresión, asegurando que distintos formatos (texto, vídeo, gráficos) sean procesados y formateados correctamente por los protocolos subyacentes.

Sin estos protocolos y servicios, la red no tendría un estándar común para direccionar o dar formato a la información. En sistemas como Windows, puedes observar esta distinción utilizando el **Administrador de tareas**, donde se diferencian claramente las aplicaciones de usuario de los procesos y servicios de red que mantienen la conectividad activa.

![697](Aplicaciones%20de%20red.png)

---

### PROTOCOLOS DE COMUNES

### 1. Protocolos de Acceso Remoto

Los administradores de red requieren acceso a los dispositivos (routers, switches, servidores) sin necesidad de estar físicamente presentes. Para esto se utilizan principalmente dos protocolos:

| **Protocolo**          | **Características Clave**                                                                                                                                  | **Nivel de Seguridad**                                      |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------- |
| **Telnet**             | Método tradicional para establecer una sesión de acceso remoto a la línea de comandos.                                                                     | **Inseguro.** Los datos se transmiten en texto sin formato. |
| **SSH (Secure Shell)** | Permite al administrador acceder al dispositivo como si hubiera iniciado sesión localmente. Requiere que tanto el cliente como el dispositivo admitan SSH. | **Seguro.** Establece una conexión cifrada.                 |

---
### 2. Protocolos de Servidor Web

Rigen el intercambio de información entre los navegadores web y los servidores.

|**Protocolo**|**Función**|
|---|---|
|**HTTP**|Protocolo de Transferencia de Hipertexto. Define cómo se formatea y transmite el tráfico web estándar.|
|**HTTPS**|Protocolo de Transferencia de Hipertexto Seguro. Cumple la misma función que HTTP, pero añade una capa de cifrado para proteger la comunicación.|

---

**Nota para el examen:** Un mismo servidor físico o virtual puede proporcionar **varios servicios de red simultáneamente**. Una sola máquina puede funcionar a la vez como servidor web, servidor de correo electrónico, servidor FTP y servidor SSH.

---

### 3. Elementos que Define un Protocolo de Red

Los protocolos son el conjunto de herramientas fundamental para los profesionales de red. Todo protocolo define estrictamente los siguientes seis parámetros:

Los procesos que ocurren en cualquier extremo de una sesión de comunicación.

Los tipos de mensajes que se van a intercambiar.

La sintaxis (estructura y formato) de los mensajes.

El significado específico de los campos informativos dentro del mensaje.

La forma en que se envían los mensajes y cuál es la respuesta esperada.

La interacción con la siguiente capa inferior del modelo de protocolos.

---

### 4. Políticas de Seguridad Corporativa

Como regla estándar de la industria, las empresas deben implementar políticas que obliguen a utilizar las versiones seguras de los protocolos siempre que estén disponibles.

Las transiciones obligatorias son:

Telnet ➔ **SSH**

FTP ➔ **SFTP**

HTTP ➔ **HTTPS**

---

![](Protocolos%20comunes.png)

---

### Aplicaciones de Voz y Vídeo

El incremento del trabajo remoto y la comunicación corporativa exige que las redes modernas soporten telefonía IP y transmisión de medios (vídeo) de manera fluida y sin interrupciones.

**El Rol del Administrador de Red:** La principal responsabilidad es garantizar que la red cuente con el equipo físico adecuado y que las configuraciones aseguren la entrega de datos basándose en un sistema de prioridades (QoS), para que la voz y el vídeo no sufran retrasos.

**Factores de Diseño: Infraestructura** Para admitir correctamente las aplicaciones en tiempo real, se deben evaluar los siguientes puntos a nivel de infraestructura física:

**Capacidad Operativa:** La arquitectura de la red debe estar diseñada específicamente para admitir y procesar aplicaciones en tiempo real.

**Auditoría Física:** Todo el cableado y los dispositivos de red que ya existen en la empresa deben ser probados y validados para comprobar que soportan las nuevas cargas de trabajo.

**Actualización Tecnológica:** Si los equipos actuales son insuficientes o antiguos, es altamente probable que se necesite invertir en productos de red más recientes y de mayor capacidad.

----



