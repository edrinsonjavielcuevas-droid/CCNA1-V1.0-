
---

La **capa de aplicación** es el nivel más cercano al usuario final en los modelos OSI y TCP/IP. Su función principal es actuar como la interfaz necesaria para que las aplicaciones puedan comunicarse a través de la red, permitiendo el intercambio de datos entre programas en diferentes hosts.

**Consolidación:** Mientras que el modelo OSI distingue entre las capas de _Aplicación_, _Presentación_ y _Sesión_, el modelo TCP/IP agrupa todas estas funciones dentro de su única capa de aplicación.

**Interoperabilidad:** Utiliza protocolos estandarizados para que aplicaciones de distintos fabricantes o sistemas puedan "hablar" entre sí.

### Ejemplos de protocolos comunes:

**HTTP:** Para la navegación web (transferencia de hipertexto).

**FTP:** Para el movimiento de archivos.

**DNS:** Traduce nombres de dominio a direcciones IP (la "agenda" de Internet).

**IMAP:** Para la gestión y acceso al correo electrónico.

**TFTP:** Una versión simplificada de FTP para transferencias básicas.

Estos protocolos no son estáticos; están en constante evolución para adaptarse a las nuevas necesidades de comunicación. 

![](../IMG/MODULO14IMG/CAPA%20DE%20APLICACIÓN.png)

---

**Capa de presentación y sección**

**1. Capa de Presentación**

Actúa como un **traductor y optimizador** de los datos para asegurar que el dispositivo de destino pueda entender la información enviada por el de origen. Sus tres funciones principales son:

**Formateo:** Convierte los datos a un lenguaje o formato común (ej. imágenes como GIF, JPEG, PNG; vídeo como MPEG, QuickTime).

**Compresión:** Reduce el tamaño de los datos para una transmisión más eficiente.

**Cifrado:** Protege la información mediante el cifrado para garantizar la seguridad durante el transporte.

**2. Capa de Sesión**

Actúa como un **gestor de diálogos** entre aplicaciones. Se encarga de:

**Iniciar y mantener:** Establece, gestiona y termina las sesiones de comunicación entre los dispositivos.

**Sincronización:** Mantiene activos los diálogos y permite reiniciar sesiones que se interrumpieron o quedaron inactivas por mucho tiempo.

En pocas palabras: la **presentación** prepara el _mensaje_ (cómo se ve, qué tamaño tiene y si está cifrado), mientras que la **sesión** coordina la _conversación_ (cuánto dura y qué hacer si se corta).

![](../IMG/MODULO14IMG/Capa%20de%20presentación%20y%20sección.png)

---

Los protocolos de aplicación en el modelo TCP/IP son el conjunto de reglas que definen **cómo se estructuran los datos y cómo se controlan las funciones de comunicación** en Internet.

Para que una comunicación sea exitosa, estos protocolos actúan como un lenguaje común:

**Estandarización:** Especifican tanto el formato de los datos (cómo se empaqueta la información) como la información de control (instrucciones sobre cómo gestionar el envío/recepción).

**Compatibilidad obligatoria:** El aspecto crítico es que tanto el dispositivo de origen como el de destino **deben implementar el mismo protocolo** de manera compatible. Si el host de origen habla HTTP y el de destino no lo entiende, la comunicación simplemente no ocurre.

Es esta compatibilidad la que permite que, por ejemplo, un navegador en tu dispositivo (usando HTTP/HTTPS) pueda comunicarse sin problemas con un servidor web al otro lado del mundo; ambos "acuerdan" seguir las mismas reglas definidas por el protocolo.

**Sistemas de nombres**

![](../IMG/MODULO14IMG/Sistemas%20de%20nombres.png)

**Configuración de host**

![](../IMG/MODULO14IMG/Configuración%20de%20host.png)

**Correo electrónico**

![](../IMG/MODULO14IMG/Correo%20electrónico.png)

**Tranferencia de archivos**

![](../IMG/MODULO14IMG/Tranferencia%20de%20archivos.png)

**La web**

![](../IMG/MODULO14IMG/La%20web.png)

---
