
---

**División en subredes en el límite del octeto:**

La creación de subredes (_subnetting_) consiste básicamente en **tomar prestados bits** de la porción de host para convertirlos en bits de red. Al ampliar la máscara de subred, alteramos el balance entre la cantidad de subredes disponibles y el número de hosts por cada una.

**La Regla de Equilibrio:** **Más bits prestados:** Aumentas el número de subredes posibles, pero **disminuyes** la cantidad de hosts permitidos por subred.

**Menos bits prestados:** Reduces el número de subredes, pero **aumentas** la capacidad de hosts por segmento.

**Límites de Octeto (/8, /16, /24):** Subdividir redes en estos límites es la forma más sencilla y común de practicar el _subnetting_. Al trabajar con prefijos más extensos (moverse hacia la derecha en la máscara), la red se vuelve más granular, permitiendo crear más segmentos, pero sacrificando necesariamente el espacio disponible para dispositivos individuales en cada uno.

---

**Máscaras de subred en límites de octetos**

![](Máscaras%20de%20subred%20en%20límites%20de%20octetos.png)

----

### Subnetting Network 10.0.0.0/8 using a /16

![](01_CCNA/IMG/MODULO11IMG/Subnetting%20Network.png)


---

### Subnetting Network 10.0.0.0/8 using a /24 Prefix

![](Subnetting%20Network%201.png)

---

**Subred dentro de un límite de octeto:**

*Subnet a /24 Network.*

![](Subnet%20a%2024.png)

Por cada bit que se toma prestado en el cuarto octeto, la cantidad de subredes disponible se duplica, al tiempo que se reduce la cantidad de direcciones de host por subred.

**/25 fila** - Tomar prestado 1 bit del cuarto octeto crea 2 subredes que admiten 126 hosts cada una.

**/26 fila** - Tomar prestados 2 bits crea 4 subredes que admiten 62 hosts cada una.

**/27 fila** - Tomar prestados 3 bits crea 8 subredes que admiten 30 hosts cada una.

**/28 fila** - Tomar prestados 4 bits crea 16 subredes que admiten 14 hosts cada una.

**/29 fila** - Tomar prestados 5 bits crea 32 subredes que admiten 6 hosts cada una.

**/30 fila** - Tomar prestados 6 bits crea 64 subredes que admiten 2 hosts cada una.

----

