
---
La estructura básica de un comando en Cisco IOS se compone de un **indicador** o prompt, seguido del **comando** principal, un espacio y, finalmente, una **palabra clave** (un parámetro específico ya definido por el sistema) o un **argumento** (un valor variable o dirección definida por el usuario). Para que el intérprete de la CLI procese la instrucción, es fundamental ingresar la sintaxis correcta en el modo de comando adecuado y presionar la tecla **Enter**, permitiendo así una administración precisa del dispositivo.

![](Estructura%20de%20comandos.png)

Para entender cómo escribir comandos en Cisco IOS, se utilizan convenciones visuales que indican qué partes son fijas y cuáles debes definir tú. La clave está en distinguir entre lo que el sistema exige literalmente y los datos variables que tú proporcionas, como direcciones IP o descripciones.

**Convenciones de Sintaxis en Cisco IOS**

| **Convención**         | **Descripción**                                                              |
| ---------------------- | ---------------------------------------------------------------------------- |
| **Negrita**            | Indica comandos y palabras clave que se escriben tal cual aparecen.          |
| _Cursiva_              | Indica los argumentos para los cuales el usuario debe proporcionar un valor. |
| **`[ x ]`**            | Los corchetes indican un elemento **opcional** (palabra clave o argumento).  |
| **`{ x }`**            | Las llaves indican un elemento **obligatorio**.                              |
| **`[ x { y \| z } ]`** | Indica que se requiere elegir una opción dentro de un elemento opcional.     |

**Ejemplo práctico:** En el comando `ping` _`ip-address`_:

- **ping**: Es la palabra clave fija (va en negrita).
- 
- _ip-address_: Es el argumento que tú defines (ej: `192.168.10.5`).

#### TECLAS DE ACCESO RAPIDO.

![](teclas%20rapidas.png)

![](teclas%20rap.png)

![](rapidas%20teclas.png)
