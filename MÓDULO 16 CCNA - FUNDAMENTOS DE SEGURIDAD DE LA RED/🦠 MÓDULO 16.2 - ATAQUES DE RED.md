
---

### Tipos de Malware

| **Tipo de Malware**  | **Descripción y Comportamiento**                                                                                                                                                                             | **Método de Propagación**                                                                                                  | **Intervención del Usuario**                                                                             |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| **Virus**            | Se adjunta a un archivo ejecutable y pasa a formar parte de otro programa. Puede sobrescribir o destruir el programa anfitrión, o causar denegación de servicio (DoS).                                       | Se transfiere de una computadora a otra mediante la red, discos, intercambio de archivos o adjuntos de correo electrónico. | **Sí.** El usuario debe ejecutar o abrir el archivo infectado para que el virus se active y se propague. |
| **Gusano**           | Software independiente que no necesita unirse a un programa anfitrión. Entra a través de vulnerabilidades del sistema y aprovecha sus características para viajar por la red.                                | Se autorreplica en copias funcionales y viaja a través de la red sin ayuda.                                                | **No.** No requiere ayuda humana ni de un programa anfitrión para propagarse.                            |
| **Caballo de Troya** | Pieza de software dañino que parece legítimo. Suele crear puertas traseras para que usuarios maliciosos accedan al sistema. No se reproduce infectando otros archivos ni se autorreplica de la misma manera. | Se extiende a través de la interacción del usuario, como abrir un correo electrónico o descargar archivos de Internet.     | **Sí.** Los usuarios suelen ser engañados para cargarlo y ejecutarlo en sus sistemas.                    |

---

### Clasificación de Ataques de Red y Reconocimiento

Además del malware, los ataques directos a la infraestructura de red se dividen en tres categorías fundamentales:

**Ataques de reconocimiento:** Consisten en el descubrimiento y mapeo de sistemas, servicios y vulnerabilidades. Es la fase inicial de recopilación de inteligencia.

**Ataques de acceso:** Implican la manipulación no autorizada de datos y la obtención de acceso ilegítimo al sistema o a escalada de privilegios de usuario.

**Denegación de servicio (DoS):** Tienen como objetivo desactivar, interrumpir o corromper el funcionamiento de redes, sistemas o servicios, agotando sus recursos.


**Anatomía de un Ataque de Reconocimiento** Para llevar a cabo el mapeo inicial, los actores de amenazas (y también los analistas defensivos) utilizan herramientas y comandos estándar de Internet:

**`whois` y `nslookup`:** Se utilizan para consultar registros públicos y determinar fácilmente el espacio de direcciones IP y dominios asignados a la organización objetivo.

**Barridos de ping (`fping`, `gping`):** Una vez obtenido el rango de direcciones IP, se automatiza el envío sistemático de solicitudes _ping_ a toda la subred. Esto permite al atacante identificar rápidamente qué IP públicas están "vivas" y expuestas (funciona exactamente igual que marcar todos los números de una guía telefónica para ver en cuáles contestan).

---

### Ataques de Acceso

Los ataques de acceso se centran en explotar vulnerabilidades conocidas en servicios comunes (como servicios de autenticación, FTP y Web) para ingresar de forma no autorizada a cuentas, bases de datos y otra información confidencial.

El objetivo final de estos ataques es eludir los controles de seguridad para que una persona obtenga acceso a información que no tiene derecho a ver.

La teoría clasifica estos ataques en **cuatro tipos principales**:

**Ataques de contraseña:** Intentos de descubrir, adivinar o robar las credenciales de inicio de sesión de un usuario legítimo (usualmente mediante fuerza bruta, diccionarios o ingeniería social).

![697](../IMG/MODULO16IMG/Ataques%20de%20contresena.png)

**Explotación de confianza:** Aprovechar los privilegios de un dispositivo o cuenta ya comprometida para acceder a otros sistemas dentro de la red que confían en ese origen.

![](../IMG/MODULO16IMG/Explotacion%20de%20canfianza.png)



**Redirección de puertos:** Utilizar un host comprometido como "puente" o intermediario para evadir un firewall y dirigir tráfico malicioso a un objetivo interno.

![](../IMG/MODULO16IMG/Reconocimiento%20de%20puertos.png)


**Man-in-the-middle (MitM):** El atacante se posiciona secretamente entre dos partes legítimas que se comunican, interceptando, leyendo y posiblemente alterando los datos en tránsito.

![](../IMG/MODULO16IMG/Man%20in%20the%20middle.png)

---

### Ataques de Denegación de Servicio (DoS y DDoS)

Los ataques de denegación de servicio son de los más comunes, perjudiciales y complejos de mitigar en el entorno de operaciones de seguridad. Su premisa básica no es robar información, sino **agotar los recursos del sistema** (ancho de banda, CPU, memoria, conexiones) para que los usuarios legítimos no puedan acceder al servicio.

**Ataque DoS (Denial of Service):** Se origina desde **una única fuente** (un solo host atacante). El atacante satura el servidor objetivo enviando una avalancha de tráfico malicioso o peticiones malformadas. Al ser un solo origen, a veces puede mitigarse bloqueando la IP atacante en el firewall, aunque sigue siendo un reto si el volumen de tráfico es lo suficientemente grande como para saturar el enlace de Internet.

**Ataque DDoS (Distributed Denial of Service):** El ataque se origina desde **múltiples fuentes simultáneas**. El atacante suele utilizar una _Botnet_ (una red de cientos o miles de dispositivos previamente infectados con malware, conocidos como "zombis"). El atacante (a través de un servidor de Comando y Control) ordena a todos los zombis que envíen tráfico al objetivo al mismo tiempo. Es exponencialmente más devastador y difícil de detener, ya que no puedes simplemente bloquear una única IP.

![](../IMG/MODULO16IMG/Ataques%20DoS%20ó%20Ataque%20DDoS.png)

