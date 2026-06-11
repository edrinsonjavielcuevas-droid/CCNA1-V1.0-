
---

### Planificación de Direcciones IPv4:

Antes de segmentar una red, es fundamental diseñar un esquema que contemple el crecimiento futuro y analice las necesidades exactas de subredes y hosts. Este diseño debe considerar dos entornos principales:

**DMZ (Direcciones Públicas):** Como estas IPs son muy limitadas, exigen una **conservación estricta**. Aquí se calculan cuidadosamente las subredes y se suele aplicar la técnica VLSM para no desperdiciar direcciones.

**Intranet (Direcciones Privadas):** Ofrece mucha **flexibilidad** gracias a los grandes bloques de IPs privadas. Aunque sobra espacio para la mayoría, las organizaciones gigantescas pueden llegar a agotarlo, siendo esto un motivo clave para migrar a IPv6.

**Estrategia de Asignación:** El esquema debe detallar el tamaño de cada subred y cómo se entregarán las direcciones (qué equipos usarán IP estática y cuáles DHCP). Esto evita conflictos, facilita la gestión y mejora el rendimiento y la seguridad.

### Asignación de Direcciones por Tipo de Dispositivo:

Para facilitar la administración, el monitoreo y la seguridad de la red, es una buena práctica establecer un patrón o esquema coherente sobre cómo se asignan las direcciones IP dependiendo de la función de cada equipo:

**Usuarios finales (Clientes):** Se les asignan direcciones de forma dinámica mediante **DHCP**. Al "alquilar" las IPs temporalmente, se reducen los errores manuales y se facilita la conexión de usuarios transitorios o inalámbricos.

**Servidores y periféricos:** Requieren una dirección IP **estática y predecible** (fija) para que siempre puedan ser localizados en la red por los usuarios que necesitan sus recursos.

**Servidores públicos (Accesibles desde Internet):** Necesitan direcciones **públicas** (frecuentemente gestionadas a través de NAT). Si son servidores privados a los que se accede desde fuera, utilizan IP privada combinada con una conexión **VPN**.

**Dispositivos intermediarios:** (Como los switches). Necesitan direcciones IP **estáticas predecibles** específicamente para que los administradores puedan conectarse a ellos y gestionar, monitorear y asegurar la red.

**Puerta de enlace (Gateway):** A la interfaz del router o firewall de cada red se le suele asignar de manera estandarizada la **dirección IP más baja o más alta** disponible en ese segmento.

---

