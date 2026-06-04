
---

**Pasos básicos de la configuración de un router:**

---
1 - Configure el nombre del host.

![](../IMG/MODULO10IMG/Hostname.png)

---

2 - Proteja el modo EXEC con privilegios.

![](../IMG/MODULO10IMG/Enable%20secret.png)

---

3 - Proteger el modo EXEC de usuario.

![](../IMG/MODULO10IMG/Line%20console%200.png)

---

4 - Proteger el acceso remoto por Telnet y SSH.

![](../IMG/MODULO10IMG/Line%20VTY%200%204.png)

---

5 - Proteja todas las contraseñas del archivo de configuración.

![](../IMG/MODULO10IMG/Encriptar%20password.png)

---

6 - Proporcione una notificación legal.

![](../IMG/MODULO10IMG/Banner%20moth.png)

---

7 - Guarde la configuración.

![](../IMG/MODULO10IMG/Guardar%20config.png)

---

**Configuración básica de un router:**

En el siguiente ejemplo, el router R1 del diagrama de la topología se configurará en la configuración inicial.

![](../IMG/MODULO10IMG/Configuración%20básica%20de%20un%20router.png)

**Para configurar el nombre del dispositivo para R1, utilice los siguientes comandos.**

![](../IMG/MODULO10IMG/configurar%20el%20nombre%20del%20dispositivo.png)

---

Los siguientes comandos aseguran el modo EXEC privilegiado y el modo EXEC de usuario, habilitan el acceso remoto Telnet y SSH y cifran todas las contraseñas de texto sin formato (es decir, EXEC de usuario y línea VTY).

![](../IMG/MODULO10IMG/EXEC%20privilegiado%20y%20el%20modo%20EXEC%20de%20usuario.png)

---
La notificación legal advierte a los usuarios que solo deben acceder al dispositivo los usuarios permitidos. La notificación legal se configura de la siguiente manera.

![](../IMG/MODULO10IMG/Moth%20banner.png)

---

Si se configuraron los comandos anteriores y el router perdió energía accidentalmente, se perderían todos los comandos configurados. Por esta razón, es importante guardar la configuración cuando se implementen los cambios. Los sigueintes comandos guardan la configuración en ejecución en la NVRAM.

![](../IMG/MODULO10IMG/Copy%20run%20start.png)

---

