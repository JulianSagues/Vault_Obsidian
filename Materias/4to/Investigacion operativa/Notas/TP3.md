
---
[[TP3_2026.pdf]]

---
**Ejercicio 1:**

**Variables:**

R: Carne molida de res
C: Carne molida de cerdo

**Función Objetivo:**

Min Z  = 800 * R + 600 * C

**Restricciones:**

R * 0,20 + C * 0,32 <= 0.25
R + C = 1
R , C >= 0

---

**Ejercicio 2**

**Variables:**

S: Soldaditos de juguete
T: Trenes de juguete

**Función Objetivo:**

Max z = 3 * S + 2 * T

**Restricciones:**

 2 * S + T <= 100
 S + T  <= 80
 S <= 40
 S , T >= 0

---
**Ejercicio 3:**

**Variables:**

A: Alimento A
B: Alimento B
C: Alimento C
D: Alimento D
E: Alimento E
F: Alimento F

**Función Objetivo:**

Min Z = 2 * A + 3 * B + 3,36 * C + 6 * D + 8 * E + 8 * F

**Restricciones:**

A + B + C + D +E +F = 1 ????

A * 20 + B * 30 + C * 40 + D * 40 + E * 45 + F * 30 >= 70
A * 50 + B * 30 + C * 20 + D * 25 + E * 50 + F * 20 >=100
A * 4 + B * 9 + C * 11 + D * 10 + E * 9 + F * 10 >= 20
A , B , C , D , E , F >= 0

---
**Ejercicio 4**

**Variables:**

A: Producto I
B: Producto II
C: Producto III
D: Producto IV

**Función Objetivo:**

Max z = A * 6000 + B * 4000 + C * 6000 + D * 8000

**Restricciones:**

A * 3 + B * 2 + C * 2 + D * 4 <= 480
A * 1 + B * 1 + C * 2 + D * 3 <= 400
A * 2 + B * 1 + C * 2 + D * 1 <= 400
D <= 25
A >= 50
B + C + D >=100
A , B , C , D >=0

---
**Ejercicio 5**

**Variables:**

A: Producto A
B: Producto B
C: Producto C

**Función Objetivo:**

Max z = A * 700 + B * 2100 + C * 3500
 
 **Restricciones:**

A + 2 * B + C * 3 <= 40
A - 2 * B >= 0
B - C >= 0
A , B , C >= 0

---
**Ejercicio 6**

**Variables:**

F: Carne de filet
L:  Carne de lomo
C: Carne de cerdo

**Función Objetivo:**

Min z = 0,3 * F + 1,4 * L + 0,5 * C

**Restricciones:**

F = 200
L = 800
C = 150
F , C , L >= 0

---
**Ejercicio 7**

**Variables:**

NR: Barriles de petróleo nacional mezclado en la nafta regular
IR: Barriles de petróleo importado mezclado en la nafta regular
NE: Barriles de petróleo nacional mezclado en la nafta extra
IE: Barriles de petróleo importado mezclado en la nafta extra

**Función Objetivo:**

Max z = 4000 * NR - 3000 * IR + 6000 * NE - 1000 * IE

**Restricciones:**

NR + IR <= 100000
6 * NE - 5 * IE <= 0
2 * NR - 8 * IR <= 0
2 * NE - 8 * IE <= 0 
NR, IR, NE, IE >= 0

---
**Ejercicio 8** 

**Variables:**

T: Unidades de publicidad a contratar en televisión
R: Unidades de publicidad a contratar en radio
P: Unidades de publicidad a contratar en prensa

**Funcion Objetivo:**

Max z = 100000 * T + 18000 * R + 40000 * P

**Restricciones:**

20000 * T + 3000 * R + 6000 * P <= 18500
T <= 10
R <= 20
P <= 10
-0,5 * T + 0,5 * R - 0,5 * P <= 0
0,9 * T - 0,1 * R - 0,1 * P >= 0
T, R, P >= 0