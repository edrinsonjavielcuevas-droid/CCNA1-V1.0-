
----

### Cisco AutoSecure 

Nunca confíes en la seguridad de fábrica. Los equipos nuevos vienen con configuraciones débiles y sistemas operativos desactualizados por el tiempo que pasan en los almacenes.

**La herramienta:** El comando `Router# auto secure` aplica ajustes de seguridad recomendados en equipos Cisco de forma automática, pero no garantiza seguridad absoluta.

**4 Pasos obligatorios antes de usar cualquier dispositivo:**

1. Cambiar usuarios y contraseñas predeterminados inmediatamente.

2. Restringir los accesos solo al personal estrictamente autorizado.

3. Apagar o desinstalar cualquier servicio o aplicación que no se vaya a usar.

4. Actualizar todo el software y aplicar parches de seguridad antes de conectarlo a la red.

---

### Pautas para Contraseñas Seguras

La primera línea de defensa para proteger cualquier dispositivo o cuenta es la gestión de credenciales. Las políticas estándar exigen cumplir con las siguientes reglas:

**Longitud:** Mínimo 8 caracteres, pero idealmente **10 o más**. A mayor longitud, mayor resistencia contra ataques de fuerza bruta.

**Complejidad:** Debe incluir una mezcla de letras (mayúsculas y minúsculas), números, símbolos especiales y, si el sistema lo permite, espacios.

**Imprevisibilidad:** Evitar por completo palabras de diccionario, secuencias (1234, abcd), información personal (fechas de nacimiento, nombres de mascotas, familiares, números de identificación) o el mismo nombre de usuario.

**Ofuscación:** Una buena táctica es utilizar palabras base pero aplicando errores ortográficos intencionales o sustituyendo letras por números y símbolos que se le parezcan.

**Rotación:** Cambiarlas con frecuencia. Si una clave es vulnerada en silencio, cambiarla limita la ventana de tiempo que tiene el atacante para usarla.

**Resguardo físico:** Nunca anotar las contraseñas en _post-its_ pegados al monitor, debajo del teclado o en libretas sobre el escritorio.

---
### Ejemplos Prácticos

**Contraseñas Débiles (Vulnerables a ataques de diccionario o deducción)**

|**Contraseña**|**Motivo de la debilidad**|
|---|---|
|`santiago2006`|Combina un nombre común con un año (información predecible).|
|`123456789`|Secuencia numérica básica; se rompe instantáneamente.|
|`contraseña`|Palabra exacta de diccionario.|
|`Admin123!`|Cumple con la complejidad, pero es un patrón globalmente usado y predecible.|

Contraseñas Fuertes (Aplicando ofuscación, longitud y complejidad)

|**Contraseña**|**Método utilizado**|
|---|---|
|`5egur1dad_T0tal!`|Sustitución intencional de letras por números (S=5, i=1, o=0) + símbolos.|
|`P3rr0B!anco#24`|Combina palabras inconexas con ofuscación, mayúsculas y caracteres especiales.|
|`5mYth_L0g1c*`|Uso del ejemplo del texto (Smith -> Smyth -> 5mYth) añadiendo longitud y símbolos.|

---

### Seguridad Adicional de Contraseñas (Cisco IOS)

Crear una contraseña compleja es solo el primer paso; el segundo es protegerla dentro del propio sistema operativo. Para los routers y switches Cisco, existen cuatro configuraciones esenciales que debes aplicar para evitar que las credenciales sean expuestas o vulneradas mediante ataques de fuerza bruta.

| **Acción**   | **Comando**                                   | **Efecto**                                    |
| ------------ | --------------------------------------------- | --------------------------------------------- |
| **Cifrado**  | `service password-encryption`                 | Oculta contraseñas en `running-config`.       |
| **Longitud** | `security passwords min-length [x]`           | Rechaza claves menores a `x` caracteres.      |
| **Bloqueo**  | `login block-for [s] attempts [n] within [s]` | Bloquea el acceso tras `n` intentos fallidos. |
| **Timeout**  | `exec-timeout [min] [seg]`                    | Cierra sesiones inactivas automáticamente.    |

![](../IMG/MODULO16IMG/Seguridad%20adicional.png)

---

### Habilitación de SSH

**Regla clave:** Telnet es inseguro porque envía todo en texto plano. Se debe usar **SSH** para cifrar el tráfico remoto.

**Los 6 pasos para configurar SSH en Cisco:**

| **Paso**             | **Comando**                                   | **Propósito**                                                           |
| -------------------- | --------------------------------------------- | ----------------------------------------------------------------------- |
| **1. Hostname**      | `hostname [nombre]`                           | Asignar un nombre único al dispositivo (no puede ser el default).       |
| **2. Dominio**       | `ip domain-name [dominio.com]`                | Configurar el nombre de dominio de la red.                              |
| **3. Llaves RSA**    | `crypto key generate rsa`                     | Generar las claves para encriptar (Se recomienda mínimo **1024 bits**). |
| **4. Usuario local** | `username [user] secret [pass]`               | Crear una cuenta en la base de datos del equipo.                        |
| **5. Autenticar**    | `line vty 0 4`<br><br>  <br><br>`login local` | Entrar a las líneas virtuales y exigir el usuario local para acceder.   |
| **6. Forzar SSH**    | `transport input ssh`                         | Bloquear Telnet y permitir **solo** conexiones SSH entrantes.           |

![](../IMG/MODULO16IMG/Habilitar%20SSH.png)

---
### Inhabilitación de Servicios no Utilizados 

**Regla clave:** Si un servicio no es estrictamente necesario en tu red, debe apagarse. Esto preserva recursos del equipo (CPU y RAM) y, lo más importante, **reduce la superficie de ataque** cerrando puertas que los ciberdelincuentes podrían explotar.

**1. Auditar: Comandos para verificar puertos abiertos** Dependiendo de la versión del sistema operativo del dispositivo, debes auditar qué servicios están "escuchando" (_LISTEN_):

| **Versión del Sistema**     | **Comando de Verificación**          |
| --------------------------- | ------------------------------------ |
| **Cisco IOS-XE** (Modernos) | `show ip ports all`                  |
| **Cisco IOS** (Anteriores)  | `show control-plane host open-ports` |

**2. Mitigar: Comandos para deshabilitar servicios inseguros** Si al auditar notas que hay servicios no cifrados (como HTTP o Telnet) corriendo, debes apagarlos inmediatamente:

| **Acción**                     | **Comando**           | **Nivel de Configuración**             |
| ------------------------------ | --------------------- | -------------------------------------- |
| **Apagar servidor web HTTP**   | `no ip http server`   | Modo Global (`Router(config)#`)        |
| **Apagar Telnet (Forzar SSH)** | `transport input ssh` | Modo de Línea (`Router(config-line)#`) |

----
----

