
---

**Espacio de direcciones IPv4 privado de subred frente al espacio público.**

**Intranet** - Esta es la parte interna de la red de una empresa, accesible sólo dentro de la organización. Los dispositivos de la intranet utilizan direcciones IPv4 privadas.

**DMZ** - Esto es parte de la red de la compañía que contiene recursos disponibles para Internet, como un servidor web. Los dispositivos de la DMZ utilizan direcciones IPv4 públicas.

**Espacio de direcciones IPv4 público y privado**

![](Espacio%20de%20direcciones%20IPv4%20público%20y%20privado.png)

**Subredes en la Intranet y DMZ**

La intranet utiliza direcciones IP privadas, como la red `10.0.0.0/8`. Al contar con 24 bits de host (más de 16 millones de direcciones), facilita enormemente la división en subredes utilizando los límites de octeto (como `/16` o `/24`).

**Ejemplo Práctico (de /8 a /16):** Si divides la red `10.0.0.0/8` usando una máscara `/16`, obtienes **256 subredes**, cada una con **65,534 hosts**.

Esta configuración es ideal para organizaciones que necesitan menos de 200 subredes, ya que cubre la demanda actual, permite un crecimiento futuro y deja direcciones de host más que suficientes en cada segmento.

---
### Subnetting Network 10.0.0.0/8 using a /16

![](Subnetting%20Network%202.png)

Otra opción que utiliza la dirección de red privada IPv4 10.0.0.0/8 es subred usando una máscara /24. Como se muestra en la tabla, esto da como resultado 65.536 subredes, con 254 hosts por subred. Si una organización necesita más de 256 subredes, se puede utilizar un /24 con 254 hosts por subred.

---
### Subnetting Network 10.0.0.0/8 using a /24

![](Subnetting%20Network%2010.png)


El 10.0.0.0/8 también se puede subred usando cualquier otro número de longitudes de prefijo, como /12, /18, /20, etc. Esto daría al administrador de red una amplia variedad de opciones. El uso de una dirección de red IPv4 privada 10.0.0.0/8 facilita la planificación e implementación de subredes.

---

**¿Qué pasa con la DMZ?**

Los dispositivos en la DMZ requieren **direcciones IPv4 públicas** para ser accesibles desde Internet, pero debido al agotamiento global de estas direcciones, el espacio disponible es actualmente muy limitado. Para maximizar su uso y minimizar el desperdicio de IPs que quedarían sin utilizar, los administradores segmentan sus redes públicas creando subredes con diferentes tamaños de máscara, una técnica de optimización fundamental que se conoce como **Máscara de Subred de Longitud Variable (VLSM)**.

----

**Minimizar las direcciones IPv4 de host no utilizadas y maximizar las subredes**

Para optimizar el direccionamiento IPv4 sin desperdiciar IPs, la planificación debe equilibrar dos factores críticos: la cantidad total de subredes que necesitas y el número de equipos requeridos en cada una. Dado que existe una relación inversa estricta al tomar más bits prestados ganas subredes pero pierdes capacidad de hosts, el diseño de toda la red debe guiarse siempre por el segmento que te exija la mayor cantidad de direcciones, asegurándote de dejar suficientes bits de host para cumplir con la fórmula matemática de direcciones utilizables ($2^n - 2$).

---

### Subnetting a /24 Network

![](Subnetting%20a%2024%20Network.png)

Los administradores de redes deben diseñar un esquema de direccionamiento de red que admita la cantidad máxima de hosts para cada red y la cantidad de subredes. El esquema de direccionamiento debe permitir el crecimiento tanto de la cantidad de direcciones de host por subred como de la cantidad total de subredes.

---

**Topología corporativa con cinco sitios**

![](Topología%20corporativa%20con%20cinco%20sitios.png)

La dirección de red 172.16.0.0/22 tiene 10 bits de host, como se muestra en la figura. Debido a que la subred más grande requiere 40 hosts, se debe tomar prestado un mínimo de 6 bits de host para proporcionar el direccionamiento de los 40 hosts. Esto se determina utilizando esta fórmula: 2^6 - 2 = 62 hosts.

---

**Esquema de subredes**

![](Esquema%20de%20subredes.png)

---

**Asignaciones de subred a cada sitio e ISP**

![](Asignaciones%20de%20subred%20a%20cada%20sitio%20e%20ISP.png)

---

