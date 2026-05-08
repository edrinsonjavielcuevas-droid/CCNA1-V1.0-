---

---
----

![[ICONOS DE REPRESENTACIÓN DE RED..png]]

| **Término**              | **Definición Simple**                                                 | **¿Dónde se encuentra?**    |
| ------------------------ | --------------------------------------------------------------------- | --------------------------- |
| **NIC** (Tarjeta de Red) | El hardware interno que permite que tu equipo se conecte a la red.    | Laptops, PCs, Servidores.   |
| **Puerto Físico**        | El conector o "entrada" física donde se enchufa el cable.             | Switches, Routers, Paredes. |
| **Interfaz**             | Puertos especializados que conectan redes individuales (capa lógica). | Routers y Firewalls.        |

---

### Diagramas de topologías de red.

| **Característica** | **Topología Física 🏠**                            | **Topología Lógica 💻**                                 |
| ------------------ | -------------------------------------------------- | ------------------------------------------------------- |
| **Enfoque**        | Ubicación **geográfica** y hardware.               | Flujo de **datos** y direccionamiento.                  |
| **Qué muestra**    | Estantes (racks), habitaciones, pisos y cables.    | Nombres de dispositivos, puertos e **IPs**.             |
| **Uso principal**  | Instalación, mantenimiento y reparación de cables. | Configuración de red, seguridad y resolución de fallas. |

**Topología física.**

![[Topologías de red físicas..png]]

**Topología lógica**

![[Pasted image 20260508111054.png]]

---

###  Tamaño y Escala de las Redes

 **SOHO (Small Office/Home Office):** Redes domésticas o de oficinas pequeñas que conectan unos pocos equipos a internet y entre sí.

**Redes Medianas a Grandes:** Utilizadas en corporaciones o universidades; cuentan con muchos lugares conectados, cientos de usuarios y servidores dedicados.

 **Redes Mundiales (Internet):** Es la red de redes que conecta cientos de millones de computadoras en todo el planeta.

#### Nota: 
*La principal diferencia entre estas es la **cantidad de usuarios**, el **número de dispositivos** y el **área geográfica** que cubren.*

### LAN VS WAN.

**LAN:** Son redes de aréa pequeña.

**WAN**: Son redes de aréa amplia y suelen conectar distintas redes LAN.


![[LAN VS WAN.png]]

**EL INTERNET:** No es más que una colección global de redes interconectadas entre sí
( Internetworks o internet para abreviar).

![[EL INTERNET..png]]

### Niveles de Acceso a la Red

**Intranet:** Es **privada**. Solo accesible para miembros de la organización (empleados). Se usa para compartir datos internos de forma segura.

 **Extranet:** Es **híbrida**. Permite acceso seguro a personas externas pero autorizadas (proveedores, clientes, socios o colaboradores externos).

 **Internet:** Es **pública**. Acceso global para todo el mundo.

![[Niveles de Acceso a la Red..png]]

| **Tipo de Usuario** | **Tecnologías Comunes**                                | **Características Clave**                                                                                              |
| ------------------- | ------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| **Hogar / SOHO**    | **Cable, DSL, Celular, Satelital**                     | Conexiones a través de un ISP para usuarios domésticos y trabajadores remotos.                                         |
| **Empresarial**     | **Líneas Arrendadas, Metro Ethernet, DSL Empresarial** | Requieren mayor velocidad, ancho de banda dedicado y soporte para servicios críticos (Telefonía IP, Centros de Datos). |

---

**Conexiones a internet domésticas y de oficinas pequeñas.**

![[Conexiones a internet domésticas y de oficinas pequeñas..png]]

Las conexiones domésticas varían según la tecnología: el **Cable** usa la misma infraestructura de la televisión para dar alta velocidad, mientras que el **DSL** utiliza la línea telefónica, siendo común el **ADSL**, donde descargas más rápido de lo que subes. El acceso **Celular** depende de la cobertura móvil y la capacidad de tu teléfono, el **Satelital** es la opción para zonas rurales sin cables pero requiere vista despejada al cielo, y el **Dial-up** es el método más antiguo y lento que funciona con cualquier línea telefónica básica.

---

**Conexiones a internet empresariales.**

![[Pasted image 20260508115243.png]]

Para las empresas, la conectividad se enfoca en la potencia y la exclusividad: las **Líneas Arrendadas** son circuitos privados reservados solo para la compañía, mientras que **Metro Ethernet** extiende la tecnología de alta velocidad de una oficina (LAN) a través de toda la ciudad (WAN). El **DSL empresarial** destaca por ser simétrico (SDSL), lo que significa que ofrece la misma velocidad para subir que para descargar archivos, y el servicio **Satelital** se mantiene como el respaldo de emergencia cuando no hay cables disponibles en la zona.

---

**Redes Tradicionales:** Son aquellas donde cada router o switch se configura de forma individual y manual. No hay un "cerebro" central; cada equipo toma sus propias decisiones de tráfico basándose en su propia configuración. Es un modelo robusto, pero lento de gestionar cuando la red crece mucho, ya que requiere entrar dispositivo por dispositivo para hacer cambios.

![[Redes tradicionales..png]]

**Redes Convergentes:** Es cuando diferentes tipos de datos (voz, video y archivos) viajan por la **misma infraestructura** de red. Antes, cada servicio necesitaba su propio cableado y reglas; ahora, todos comparten el mismo camino, lo que ahorra costos y facilita el mantenimiento.

![[Redes convergentes..png]]