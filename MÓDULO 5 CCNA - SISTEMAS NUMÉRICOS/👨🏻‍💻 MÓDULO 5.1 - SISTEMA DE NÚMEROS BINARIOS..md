
----
### Direcciones Binarias e IPv4

Las direcciones IPv4 operan internamente de forma **binaria** con una serie de unos y ceros llamados bits porque es el sistema que utilizan los hosts, servidores y dispositivos de red para identificarse entre sí. Como gestionar cadenas de binarios es complejo para los humanos, los administradores de red las convierten al sistema **decimal** son los números del 0 al 9 para facilitar su configuración y lectura.

![](Direcciones%20Binarias%20e%20IPv4.png)

Una dirección IPv4 está compuesta por **32 bits** de longitud, los cuales se dividen en **cuatro secciones llamadas octetos**.

**Composición:** Cada octeto contiene exactamente **8 bits** lo que equivale a 1 byte y se separan visualmente mediante un punto.

 **Notación:** Para los dispositivos de red, la dirección es una cadena binaria (ej. `11000000.10101000.00001010.00001010`), pero los humanos la expresamos en **notación decimal con puntos** (ej. `192.168.10.10`) para que sea manejable.

![](Composición%20de%20la%20IPv4.png)

---

Para convertir de binario a decimal es fundamental entender la **notación posicional**: significa que un dígito representa un valor diferente según la **posición** que ocupa en la secuencia de números.

**Base 10 (Decimal):** Cada posición representa potencias de 10 (unidades, decenas, centenas...).

 **Base 2 (Binario):** Cada posición representa potencias de 2 ($2^0, 2^1, 2^2\dots$), duplicando su valor de derecha a izquierda en el octeto (1, 2, 4, 8, 16, 32, 64, 128).
 
![](notación%20posicional.png)

El funcionamiento de la tabla de **notación posicional** se basa en tomar la **base (radix)** del sistema y asignarle a cada columna un **exponente correlativo** de derecha a izquierda comenzando estrictamente desde cero; luego, se calcula el peso de cada columna elevando la base a dicho exponente (donde $n^0 = 1$) para obtener el **valor posicional** final. Para evaluar o convertir cualquier número, simplemente se alinea cada uno de sus dígitos con el valor calculado para su respectiva columna.

![](tabla%20de%20notación%20posicional.png)

Por otro lado de tabla de notación posicional  decimal opera de manera diferente.

![](notación%20posicional%20%20decimal.png)

En el sistema binario, la lógica posicional se aplica usando como **base (radix) el número 2**, donde cada columna recibe un exponente que aumenta de derecha a izquierda empezando en cero. Al elevar la base a dicho exponente se calcula el valor de cada posición (generando los pesos de unidades, doses, cuatros, ochos, etc.), lo que permite que un conjunto de bits activos se traduzca directamente a su equivalente decimal sumando los valores de las columnas ocupadas.

![](En%20el%20sistema%20binario.png)

---

### Tabla: Conversión completa IPv4 de binario a decimal

| Octeto | Representación Binaria (8 Bits) | Pesos Activos ($1$) | Operación (Suma) | Decimal |
| :---: | :---: | :---: | :---: | :---: |
| **1°** | `1 1 0 0 0 0 0 0` | $128, 64$ | $128 + 64$ | **192** |
| **2°** | `1 0 1 0 1 0 0 0` | $128, 32, 8$ | $128 + 32 + 8$ | **168** |
| **3°** | `0 0 0 0 1 0 1 1` | $8, 2, 1$ | $8 + 2 + 1$ | **11** |
| **4°** | `0 0 0 0 1 0 1 0` | $8, 2$ | $8 + 2$ | **10** |

---

**Conertir de decimal a binario**

![](128.png)

![](64.png)

![](32.png)

![](16.png)

![](8.png)

![](4.png)

![](2.png)

![](1.png)

---

**Perspectivas de una Dirección IPv4**

**1. Dirección Decimal Punteada (Dotted Decimal Address):** Es la representación en formato legible para humanos. Consiste en cuatro números decimales separados por puntos (ej. `192.168.10.10`). Es la forma en la que configuramos e identificamos los dispositivos en el día a día.

![](Dirección%20Decimal%20Punteada.png)

----

**2. Octetos (Octets):** Son las cuatro secciones independientes que forman la dirección. Cada octeto está compuesto exactamente por **8 bits** (1 byte). Los puntos sirven exclusivamente para separar visualmente estos bloques y facilitar la conversión matemática.

![](Octetos.png)

---

**3. Dirección de 32 bits (32-bit Address):** Es la dirección en formato binario puro (una cadena continua de 32 unos y ceros sin puntos, ej. `11000000101010000000101000001010`). Este es el único formato que los routers y las computadoras entienden y procesan a nivel de hardware.

![](Dirección%20de%2032%20bits.png)

----
