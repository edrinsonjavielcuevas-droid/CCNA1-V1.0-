
---

### Las 3 Grandes Limitaciones de IPv4

**Agotamiento de direcciones:** IPv4 tiene un límite teórico de unos 4,000 millones de direcciones únicas. Con la explosión de dispositivos inteligentes, conexiones constantes y el crecimiento tecnológico global, simplemente ya no hay suficientes direcciones públicas para todos.

**Falta de conectividad de extremo a extremo:** Para estirar la vida de IPv4, usamos **NAT**, que permite que muchos dispositivos compartan una sola dirección pública. El problema es que esto oculta la dirección real de los dispositivos internos, rompiendo la conectividad total y directa que requieren muchas tecnologías modernas.

**Complejidad excesiva:** NAT fue pensado solo como un "parche" temporal para transicionar a IPv6. Sin embargo, al seguir usándolo, hemos complicado las redes innecesariamente, añadiendo latencia y haciendo que diagnosticar errores sea mucho más difícil de lo que debería ser.

---

**Encabezado IPv6**

A diferencia de su predecesor, el protocolo IPv6 integra un diseño de encabezado optimizado para reducir la sobrecarga de procesamiento en los dispositivos intermedios (routers):

 **Encabezado de longitud fija:** El encabezado base tiene un tamaño constante de 40 bytes, lo que facilita y agiliza su lectura por parte del hardware.

**Simplificación de campos:** Se han eliminado campos redundantes y de control de fragmentación presentes en IPv4, centralizando las funciones necesarias para un enrutamiento más eficiente.

**Gestión de extensiones:** Cualquier funcionalidad adicional requerida se maneja mediante encabezados de extensión, manteniendo el encabezado base ligero y predecible.

Esta estructura permite que los equipos de red procesen los paquetes a mayor velocidad, cumpliendo con las exigencias de rendimiento de las infraestructuras actuales.

---

**Comparación del especio de direcciones IPv4 e IPv6:**

![](../IMG/MODULO8IMG/Comparación%20del%20especio%20de%20direcciones%20IPv4%20e%20IPv6.png)

---

**Encabezado de paquetes IPv6:**

![](../IMG/MODULO8IMG/Encabezado%20de%20paquetes%20IPv6.png)

---

| **Característica**              | **IPv4**                                              | **IPv6**                                                                      |
| ------------------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------- |
| **Longitud del encabezado**     | Variable (20 a 60 bytes).                             | Fija (40 bytes).                                                              |
| **Control de fragmentación**    | Incluye campos de control y desplazamiento.           | No posee campos de fragmentación (se gestiona mediante _Path MTU Discovery_). |
| **Checksum**                    | Obligatorio (se recalcula en cada salto).             | Eliminado (se delega a capas superiores para optimizar velocidad).            |
| **Opciones**                    | Integradas en el encabezado (aumentan la sobrecarga). | Desplazadas a encabezados de extensión.                                       |
| **Eficiencia de procesamiento** | Menor (debido a la complejidad del encabezado).       | Mayor (diseño optimizado para el hardware de red).                            |

**Nota técnica:** La simplificación del encabezado en IPv6 es un factor determinante para mejorar el rendimiento en los dispositivos de capa 3, reduciendo la latencia de procesamiento al eliminar campos que requerían cálculo constante por parte de los routers.

---

