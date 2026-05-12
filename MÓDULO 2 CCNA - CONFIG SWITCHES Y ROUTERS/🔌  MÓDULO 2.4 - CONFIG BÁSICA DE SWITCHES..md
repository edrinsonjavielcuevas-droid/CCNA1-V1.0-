
---
Asignar un nombre de host único (**hostname**) es el primer paso crítico en la configuración, ya que permite identificar cada dispositivo de forma remota y evitar confusiones en la red. El nombre debe seguir una convención lógica que indique la ubicación o propósito del equipo (por ejemplo, su piso o función). Para configurarlo, se entra al modo de configuración global con `configure terminal` y se ejecuta el comando `hostname` seguido del nombre deseado; para borrarlo y volver al nombre de fábrica, se usa `no hostname`.

![](../IMG/NOMBRE%20DE%20HOST.png)
### Pautas de Nomenclatura para Hosts

|**Regla**|**Descripción**|
|---|---|
|**Inicio**|Debe comenzar obligatoriamente con una letra.|
|**Espacios**|No debe contener espacios en blanco.|
|**Final**|Debe terminar con una letra o un dígito.|
|**Caracteres**|Utilizar únicamente letras, dígitos y guiones (`-`).|
|**Longitud**|Debe tener menos de 64 caracteres de largo.|

Para mantener la red segura, es obligatorio proteger todos los accesos (usuario, privilegiado y remoto) con contraseñas robustas que mezclen letras, números y símbolos. Una buena clave debe tener más de **ocho caracteres** y evitar palabras comunes o las típicas de laboratorio como "cisco". En el mundo real, estas siempre deben estar **encriptadas** para impedir que intrusos tomen el control administrativo de tus equipos.

**CONFIGURACIÓN DE CONTRASEÑA**

![](../IMG/CONTRASEÑA%20DE%20MODO%20USUARIO.png)

![](../IMG/MODO%20USUARIO%20%20CONTRASEÑA.png)

![](../IMG/LIne%20virtual.png)

**Encriptación de contraseña.**

![](../IMG/Encriptación%20de%20contraseña.png)

![](../IMG/Show%20running-config.png)

![](../IMG/banner%20motd.png)

**Comparación de Archivos de Configuración**

| **Archivo**        | **Ubicación** | **Tipo de Memoria** | **Descripción**                                                                                                  |
| ------------------ | ------------- | ------------------- | ---------------------------------------------------------------------------------------------------------------- |
| **running-config** | RAM           | Volátil             | Contiene la configuración que se está ejecutando **actualmente**. Si el equipo se apaga, los cambios se pierden. |
| **startup-config** | NVRAM         | No volátil          | Es la configuración guardada que el dispositivo carga automáticamente al **iniciar o reiniciar**.                |
