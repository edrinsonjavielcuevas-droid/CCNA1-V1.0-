
---

# 15.4.1 Servicio de nombres de dominios

El **DNS (Domain Name System)** es un protocolo esencial de la capa de aplicación diseñado para hacer Internet mucho más accesible para los humanos. Su función principal es actuar como una "agenda telefónica" para la red.

### ¿Por qué es necesario el DNS?

Aunque los dispositivos en una red se identifican mediante **direcciones IP numéricas** para enviar y recibir datos, estas son extremadamente difíciles de recordar para las personas. El DNS se creó para convertir estas complejas direcciones numéricas en **nombres de dominio** sencillos y reconocibles.

**Ejemplo**: Es mucho más fácil recordar `www.cisco.com` que su dirección IP real, como `198.133.219.25`.

**Flexibilidad**: Si una empresa cambia la dirección IP de su servidor, el DNS permite actualizar la asociación con el nombre de dominio sin que el usuario note ningún cambio, garantizando que el acceso siga siendo constante.

### Funcionamiento técnico

El protocolo DNS define un servicio automatizado que hace coincidir nombres de recursos con sus direcciones IP solicitadas.

**Formato de mensaje único**: Todas las comunicaciones DNS (consultas de clientes, respuestas de servidores, mensajes de error y transferencias de registros entre servidores) utilizan un único formato estándar llamado **"mensaje"**.

Este servicio automatiza la resolución de nombres, eliminando la necesidad de configurar manualmente las conexiones o memorizar series de números para cada sitio que desees visitar.

---

## Formato de mensaje DNS

El servidor DNS almacena diferentes tipos de registros de recursos que son utilizados para resolver nombres en la red. Estos registros siempre contienen tres datos fundamentales: **el nombre, la dirección y el tipo de registro**.

**Tipos de Registros DNS**

A continuación, se detallan los tipos de registros más comunes que maneja un servidor DNS:

| **Tipo de Registro** | **Descripción**                                                    |
| -------------------- | ------------------------------------------------------------------ |
| **A**                | Se refiere a una dirección IPv4 de terminal.                       |
| **NS**               | Identifica a un servidor de nombre autoritativo.                   |
| **AAAA**             | Representa una dirección IPv6 de terminal (se pronuncia "quad-A"). |
| **MX**               | Es un registro de intercambio de correo electrónico.               |

 **¿Cómo funciona el proceso de consulta DNS?**

El proceso de resolución de nombres sigue un orden lógico para optimizar la velocidad y los recursos de la red:

**Consulta inicial:** Cuando un cliente realiza una consulta, el proceso DNS del servidor observa primero sus propios registros locales para intentar resolver el nombre.

**Escalamiento:** Si el servidor no puede resolver la consulta con los registros que tiene almacenados, se encarga de contactar a otros servidores para lograrlo.

**Almacenamiento en caché (Servidor):** Una vez que se encuentra una coincidencia y esta se devuelve al servidor solicitante original, este almacena temporalmente la dirección numérica. Esto se hace por si el cliente vuelve a solicitar el mismo nombre en el futuro, acelerando el proceso.

----

**Nota sobre dispositivos Windows:** El servicio del cliente DNS en los equipos con Windows también almacena en su memoria los nombres que ya han sido resueltos previamente. Para visualizar este historial en tu propia computadora, puedes utilizar el comando **`ipconfig /displaydns`**, el cual muestra todas las entradas de DNS que están guardadas en la caché.

---

### Estructura del Mensaje DNS

El protocolo DNS utiliza un formato de mensaje único y estandarizado. Este mismo formato se utiliza para múltiples propósitos: solicitudes de clientes, respuestas del servidor, mensajes de error y para la transferencia de información de registro de recursos entre servidores.

El mensaje se divide en las siguientes secciones:

| **Sección de mensajes DNS** | **Descripción**                                                                             |
| --------------------------- | ------------------------------------------------------------------------------------------- |
| **Pregunta**                | Contiene la pregunta específica que se le hace al servidor de nombres.                      |
| **Respuesta**               | Contiene los registros de recursos que responden a la pregunta realizada.                   |
| **Autoridad**               | Incluye los registros de recursos que apuntan hacia una autoridad de dominio.               |
| **Adicional**               | Contiene registros de recursos que poseen información adicional relevante para la consulta. |

----

## Jerarquía DNS

El protocolo DNS funciona mediante un sistema de base de datos **jerárquico y distribuido** que permite la resolución de nombres a nivel mundial de manera eficiente.

##### Puntos clave de su funcionamiento:

**Zonas de administración:** La estructura completa de nombres de Internet se divide en zonas pequeñas y manejables.

**Bases de datos locales:** Cada servidor DNS solo es responsable de mantener el archivo y administrar las traducciones (de nombre a IP) de su porción específica dentro de la jerarquía.

**Reenvío de solicitudes:** Si un servidor recibe una consulta que no pertenece a su zona y no puede resolverla, simplemente reenvía la solicitud a otro servidor DNS que sí corresponda a esa zona.

**Escalabilidad:** Gracias a que la carga de trabajo se distribuye entre miles de servidores en todo el mundo, el sistema DNS es altamente escalable y no colapsa.

##### Dominios de Nivel Superior (TLD)

En esta jerarquía, los dominios de primer nivel (la última parte de una dirección web) indican el tipo de organización o el país de origen. Ejemplos comunes incluyen:

**.com** - Empresas o industrias comerciales.

**.org** - Organizaciones sin fines de lucro.

**.au** - Australia (código de país).

**.co** - Colombia (código de país).

---

## El comando `nslookup`

Los dispositivos utilizan servidores DNS (generalmente asignados por el ISP) para traducir nombres solicitados por el usuario a direcciones IP numéricas.

**¿Qué es `nslookup`?** Es una utilidad del sistema operativo que permite hacer consultas manuales a los servidores DNS para resolver un nombre de host.

**¿Para qué sirve?** Se utiliza principalmente para solucionar problemas de resolución de nombres y verificar el estado actual de los servidores DNS.

**Funcionamiento:** Al ejecutar el comando, te muestra primero cuál es tu servidor DNS predeterminado. Luego, te da un _prompt_ donde puedes escribir cualquier dominio para realizar pruebas exhaustivas de la resolución DNS.

![](nslookup.png)

---

## Protocolo de configuración dinámica de host (DHCP)

El **DHCP** es un servicio que automatiza la asignación de configuraciones de red, como direcciones IPv4, máscaras de subred y gateways. A este proceso se le conoce como **direccionamiento dinámico**, el cual es la alternativa moderna y eficiente al direccionamiento estático (donde un administrador debe introducir las IP a mano).

**Funcionamiento básico:** Cuando un host se conecta a la red, contacta al servidor DHCP. El servidor elige una IP disponible de su rango configurado (llamado "pool" o grupo) y se la otorga al dispositivo.

**Período de concesión (Lease):** Las direcciones IP se prestan por un tiempo limitado. Cuando este tiempo expira, o si el dispositivo se desconecta (enviando un mensaje `DHCPRELEASE`), la IP se devuelve al pool para que otro equipo la pueda reutilizar. Esto da muchísima flexibilidad cuando los usuarios se mueven con frecuencia.

**¿Dónde se aloja el servidor DHCP?**

**Redes domésticas:** Por lo general, tu router (el que te da el proveedor de internet) hace el trabajo de servidor DHCP.

**Redes grandes empresariales:** Se utilizan servidores locales dedicados (equipos potentes) para manejar el gran volumen de solicitudes.

**Dinámico vs. Estático en la práctica**

La mayoría de las redes utilizan una combinación inteligente de ambos métodos:

**DHCP (Dinámico):** Se usa para dispositivos de propósito general (laptops de usuarios, teléfonos móviles).

**Estático (Manual):** Se reserva estrictamente para equipos clave de la red que nunca deben cambiar de dirección para que siempre los podamos encontrar (servidores, impresoras de red, switches, gateways).

**La variante para IPv6 (DHCPv6)**

DHCPv6 ofrece servicios muy similares para redes modernas, pero con una **diferencia técnica importante**: DHCPv6 **no** entrega la dirección del gateway predeterminado. En IPv6, los dispositivos obtienen esa dirección específica escuchando los anuncios dinámicos que emite el propio router.

![](Protocolo%20de%20configuración%20dinámica%20de%20host%20(DHCP).png)

---

## Funcionamiento de DHCP (Proceso DORA)

Cuando un dispositivo se conecta a la red, sigue este intercambio de mensajes con el servidor:

| **Paso** | **Mensaje**      | **¿Quién lo envía?** | **Acción**                                                                        |
| -------- | ---------------- | -------------------- | --------------------------------------------------------------------------------- |
| 1        | **DHCPDISCOVER** | Cliente              | El cliente "grita" en la red buscando cualquier servidor DHCP disponible.         |
| 2        | **DHCPOFFER**    | Servidor             | El servidor responde ofreciendo una dirección IP, máscara, DNS y gateway.         |
| 3        | **DHCPREQUEST**  | Cliente              | El cliente elige una oferta y solicita formalmente esa configuración al servidor. |
| 4        | **DHCPACK**      | Servidor             | El servidor confirma ("Acknowledge") que la concesión ha finalizado con éxito.    |

---

**Detalles importantes a considerar:**

**¿Qué pasa si hay varios servidores?** El cliente puede recibir múltiples ofertas (`DHCPOFFER`), pero el mensaje `DHCPREQUEST` especifica qué servidor y qué oferta eligió.

**Reconocimiento negativo (`DHCPNAK`):** Si la dirección que el cliente solicita ya no está disponible, el servidor responde con un `DHCPNAK` (Negative Acknowledgment). En este caso, el proceso debe reiniciarse desde el primer paso (`DHCPDISCOVER`).

**Renovación:** Antes de que la concesión (el tiempo de préstamo de la IP) expire, el cliente debe enviar un nuevo `DHCPREQUEST` para renovar su dirección y seguir conectado.

**Garantía de unicidad:** El servidor DHCP es responsable de asegurar que ninguna dirección IP se asigne a dos dispositivos simultáneamente.

----
### Comparación con DHCPv6

Aunque el proceso es conceptualmente similar para IPv6, los nombres de los mensajes cambian:

| **Función**  | **Mensaje en IPv4** | **Mensaje en DHCPv6** |
| ------------ | ------------------- | --------------------- |
| Búsqueda     | DISCOVER            | SOLICIT               |
| Oferta       | OFFER               | ADVERTISE             |
| Solicitud    | REQUEST             | INFORMATION REQUEST   |
| Confirmación | ACK                 | REPLY                 |

---

![697](Funcionamiento%20de%20DHCP.png)

---

