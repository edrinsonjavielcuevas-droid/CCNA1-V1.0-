
---

### Creación de Subredes a partir de un /16

**El Escenario:** Cuando una infraestructura requiere una gran cantidad de subredes, es obligatorio partir de una red IPv4 que ofrezca muchos bits de host disponibles para tomar prestados.

**Estructura del /16:** Una dirección como **172.16.0.0/16** (máscara **255.255.0.0**) está dividida exactamente a la mitad:

16 bits fijos para la porción de red.

**16 bits completos** disponibles en la porción de host.

**Ventaja:** Disponer de estos 16 bits de host te da un margen enorme para tomar bits prestados y crear múltiples escenarios de segmentación (subredes de tamaño fijo con la misma cantidad de hosts en cada una).

---

**Tabla de División en Subredes para un Prefijo /16**

| **Longitud de Prefijo** | **Máscara de Subred** | **Bits Prestados** | **Subredes Creadas (2n)** | **Hosts Utilizables (2h−2)** |
| ----------------------- | --------------------- | ------------------ | ------------------------- | ---------------------------- |
| **/16**                 | 255.255.0.0           | 0                  | 1                         | 65,534                       |
| **/17**                 | 255.255.128.0         | 1                  | 2                         | 32,766                       |
| **/18**                 | 255.255.192.0         | 2                  | 4                         | 16,382                       |
| **/19**                 | 255.255.224.0         | 3                  | 8                         | 8,190                        |
| **/20**                 | 255.255.240.0         | 4                  | 16                        | 4,094                        |
| **/21**                 | 255.255.248.0         | 5                  | 32                        | 2,046                        |
| **/22**                 | 255.255.252.0         | 6                  | 64                        | 1,022                        |
| **/23**                 | 255.255.254.0         | 7                  | 128                       | 510                          |
| **/24**                 | 255.255.255.0         | 8                  | 256                       | 254                          |
| **/25**                 | 255.255.255.128       | 9                  | 512                       | 126                          |
| **/26**                 | 255.255.255.192       | 10                 | 1,024                     | 62                           |
| **/27**                 | 255.255.255.224       | 11                 | 2,048                     | 30                           |
| **/28**                 | 255.255.255.240       | 12                 | 4,096                     | 14                           |
| **/29**                 | 255.255.255.248       | 13                 | 8,192                     | 6                            |
| **/30**                 | 255.255.255.252       | 14                 | 16,384                    | 2                            |

---

### Cree 100 subredes con un prefijo /16

![](01_CCNA/IMG/MODULO11IMG/Cantidad%20de%20subredes%20creadas.png)

Para satisfacer el requisito de 100 subredes, se necesitarían prestar 7 bits (es decir, 27 = 128 subredes) (para un total de 128 subredes), como se muestra en la figura.

**Red 172.16.0.0/23**

Recuerde que la máscara de subred debe modificarse para que se muestren los bits que se tomaron prestados. En este ejemplo, cuando se toman prestados 7 bits, la máscara se extiende 7 bits en el tercer octeto. En formato decimal, la máscara se representa como 255.255.254.0, o como el prefijo /23, debido a que, en formato binario, el tercer octeto es 11111110 y el cuarto octeto es 00000000.

En la figura, se muestran las subredes resultantes desde 172.16.0.0 /23 hasta 172.16.254.0 /23.

![697](subredes%20resultantes.png)

**Intervalo de direcciones para la subred 172.16.0.0/23**

![](ntervalo%20de%20direcciones%20para%20la%20subred.png)

---

### Cree 1000 subredes con un prefijo Slash 8

**Cantidad de subredes creadas**

![](Cantidad%20de%20subredes%20creadas%201.png)

**Subredes /18 resultantes**

![](Subredes%2018%20resultantes.png)

Prestar 10 bits para crear las subredes, deja 14 bits host para cada subred. Restar dos hosts por subred (uno para la dirección de red y otro para la dirección de difusión) equivale a 2^14 - 2 = 16382 hosts por subred. Esto indica que cada una de las 1000subredes puede admitir hasta 16382 hosts.

**Intervalo de direcciones para la subred 10.0.0.0/18**

![](Intervalo%20de%20direcciones%20para%20la%20subred.png)

----
