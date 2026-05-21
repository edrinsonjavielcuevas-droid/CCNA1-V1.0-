
---

### Direcciones Hexadecimales e IPv6

Para dominar **IPv6**, es obligatorio entender el sistema **hexadecimal (Base 16)** y saber cómo convertirlo a decimal y binario, de la misma forma que se hace con IPv4 y el sistema binario.

**El Sistema Base 16:** Utiliza 16 caracteres únicos para representar valores.

Números del **0 al 9** (valores del 0 al 9).
 
Letras de la **A a la F** (valores del 10 al 15).
  
**Representación:** Cada dígito hexadecimal representa exactamente **4 bits** (un _nibble_ o medio octeto), yendo desde `0000` hasta `1111`.

![](../IMG/Direcciones%20Hexadecimales%20e%20IPv6.png)

---

Las direcciones IPv6 miden **128 bits** y se representan mediante **32 dígitos hexadecimales** (los cuales no distinguen mayúsculas y abarcan del 0 al 9 y de la A a la F, donde cada carácter condensa 4 bits binarios). Esta infraestructura se organiza en el formato preferido `x:x:x:x:x:x:x:x`, compuesto por **8 segmentos de 16 bits llamados hextetos** y separados por dos puntos, lo que optimiza la lectura y escritura de grandes volúmenes de datos en comparación con las cadenas binarias puras utilizadas por el hardware.

![](../IMG/128%20bits.png)

**Ejemplo de una topologia IPv6:**

![](../IMG/Ejemplo%20de%20una%20topologia%20IPv6.png)

---

### Conversión de Decimal a Hexadecimal

El método oficial de Cisco (y el más fácil para no volverse loco dividiendo entre 16) consiste en usar el sistema binario como puente en **3 pasos**:

1. **Convertir** el número decimal a su formato binario de 8 bits.
    
2. **Dividir** esa cadena binaria en dos grupos de 4 bits (_nibbles_), de derecha a izquierda.
    
3. **Traducir** cada grupo de 4 bits a su dígito hexadecimal correspondiente (0-9, A-F).

Ejemplo Práctico: Convertir el número **168**

| **Paso** | **Acción**              | **Resultado**    |
| -------- | ----------------------- | ---------------- |
| **1**    | Convertir 168 a binario | `10101000`       |
| **2**    | Dividir en grupos de 4  | `1010` \| `1000` |
| **3**    | Traducir a Hexadecimal  | **A** \| **8**   |

---

### Conversión de Hexadecimal a Decimal

El proceso inverso también utiliza el sistema binario como un puente sencillo para evitar cálculos complejos:

1. **Expandir:** Convierte cada dígito hexadecimal en su equivalente de **4 bits binarios** (un _nibble_).
    
2. **Agrupar:** Une los bloques de 4 bits para formar una cadena continua de **8 bits** (un octeto completo).
    
3. **Calcular:** Traduce ese octeto binario final a su valor decimal sumando las posiciones de los bits activos ($1$).

Flujo de Conversión: Hexadecimal a Decimal **(D2)**

| Paso  | Proceso                 | Datos / Resultado   |
| :---: | :---------------------- | :------------------ |
| **-** | **Dígito Hexadecimal**  | **D** (13) y **2**  |
| **1** | **Convertir a 4 bits**  | `1101` y `0010`     |
| **2** | **Unir en un Octeto**   | `11010010`          |
| **3** | **Suma de Pesos ($1$)** | $128 + 64 + 16 + 2$ |
| **=** | **Resultado Decimal**   | **210**             |

---
