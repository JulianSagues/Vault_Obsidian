### Parte 1 (Modelo Base, FCC y FCO):
# Deducción Detallada de Realizaciones en Variables de Estado (FCC, FCO, FCD)

---

## 0. Modelo Base de Trabajo

$$G(s) = \frac{Y(s)}{U(s)} = \frac{2s + 5}{s^2 + 5s + 6}$$

* **Polinomio del numerador:** $N(s) = 2s + 5 \implies b_1 = 2, \quad b_0 = 5$
* **Polinomio del denominador:** $D(s) = s^2 + 5s + 6 \implies a_1 = 5, \quad a_0 = 6$
* **Polos del sistema:**
  $$s^2 + 5s + 6 = 0 \implies p_1 = -2, \quad p_2 = -3$$

---

## 1. Forma Canónica Controlable (FCC)

### Justificación
La FCC descompone el sistema en dos bloques en serie: primero la dinámica pura de los polos generando una variable auxiliar $V(s)$, y luego el numerador que procesa las derivadas de $V(s)$.

### Paso 1: Planteo de la variable intermedia V(s)
$$Y(s) = (2s + 5) \cdot \left[ \frac{1}{s^2 + 5s + 6} U(s) \right]$$

Definimos:
$$V(s) \triangleq \frac{1}{s^2 + 5s + 6} U(s)$$

Ecuaciones resultantes:
* Dinámica interna: $(s^2 + 5s + 6)V(s) = U(s)$
* Salida: $Y(s) = (2s + 5)V(s) = 2sV(s) + 5V(s)$

### Paso 2: Pasaje al dominio del tiempo
$$(s^2 + 5s + 6)V(s) = U(s) \implies s^2 V(s) + 5s V(s) + 6V(s) = U(s)$$
$$\ddot{v}(t) + 5\dot{v}(t) + 6v(t) = u(t)$$
$$\ddot{v}(t) = -6v(t) - 5\dot{v}(t) + u(t)$$

### Paso 3: Definición de variables de estado (en cadena)
* $x_1(t) \triangleq v(t)$
* $x_2(t) \triangleq \dot{v}(t)$

### Paso 4: Derivadas de los estados
* $\dot{x}_1(t) = \dot{v}(t) = x_2(t)$
* $\dot{x}_2(t) = \ddot{v}(t) = -6x_1(t) - 5x_2(t) + u(t)$

### Paso 5: Ecuación de salida en el tiempo
$$y(t) = 5v(t) + 2\dot{v}(t) = 5x_1(t) + 2x_2(t)$$

### Paso 6: Matrices finales (FCC)
$$\begin{bmatrix} \dot{x}_1 \\ \dot{x}_2 \end{bmatrix} = \begin{bmatrix} 0 & 1 \\ -6 & -5 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} + \begin{bmatrix} 0 \\ 1 \end{bmatrix} u$$
$$y = \begin{bmatrix} 5 & 2 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix}$$

---

## 2. Forma Canónica Observable (FCO)

### Justificación
La FCO utiliza el método de desanidado de integradores: se divide por potencias de $s$ para que los estados se generen a la salida de integradores sucesivos $1/s$.

### Paso 1: Multiplicar cruzado
$$(s^2 + 5s + 6)Y(s) = (2s + 5)U(s)$$
$$s^2 Y(s) + 5s Y(s) + 6Y(s) = 2s U(s) + 5U(s)$$

### Paso 2: Despejar la máxima potencia y agrupar
$$s^2 Y(s) = s[2U(s) - 5Y(s)] + [5U(s) - 6Y(s)]$$

Dividiendo todo por $s^2$:
$$Y(s) = \frac{1}{s} \left( [2U(s) - 5Y(s)] + \frac{1}{s}[5U(s) - 6Y(s)] \right)$$

### Paso 3: Definición de estados (de adentro hacia afuera)
* $X_1(s) \triangleq \frac{1}{s}[5U(s) - 6Y(s)]$
* $X_2(s) \triangleq \frac{1}{s}[X_1(s) - 5Y(s) + 2U(s)]$
* Salida directa: $Y(s) = X_2(s) \implies y(t) = x_2(t)$

### Paso 4: Despeje temporal de derivadas
* Para $X_1$:
  $$s X_1(s) = -6Y(s) + 5U(s) \implies \dot{x}_1(t) = -6x_2(t) + 5u(t)$$
* Para $X_2$:
  $$s X_2(s) = X_1(s) - 5Y(s) + 2U(s) \implies \dot{x}_2(t) = x_1(t) - 5x_2(t) + 2u(t)$$

### Paso 5: Matrices finales (FCO)
$$\begin{bmatrix} \dot{x}_1 \\ \dot{x}_2 \end{bmatrix} = \begin{bmatrix} 0 & -6 \\ 1 & -5 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} + \begin{bmatrix} 5 \\ 2 \end{bmatrix} u$$
$$y = \begin{bmatrix} 0 & 1 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix}$$
### Parte 2 (FCD y Tabla Comparativa):
## 3. Forma Canónica Diagonal (FCD)

### Justificación
La FCD representa el sistema como subsistemas de primer orden desacoplados en paralelo. Requiere polos distintos y se basa en la descomposición en fracciones simples.

### Paso 1: Factorizar el denominador
$$\frac{Y(s)}{U(s)} = \frac{2s + 5}{(s + 2)(s + 3)}$$

### Paso 2: Descomposición en fracciones simples
$$\frac{2s + 5}{(s + 2)(s + 3)} = \frac{c_1}{s + 2} + \frac{c_2}{s + 3}$$

Cálculo de residuos:
* $c_1 = \lim_{s \to -2} \left[ \frac{2s + 5}{s + 3} \right] = \frac{2(-2) + 5}{-2 + 3} = 1$
* $c_2 = \lim_{s \to -3} \left[ \frac{2s + 5}{s + 2} \right] = \frac{2(-3) + 5}{-3 + 2} = 1$

Queda:
$$\frac{Y(s)}{U(s)} = \frac{1}{s + 2} + \frac{1}{s + 3}$$

### Paso 3: Distribuir la entrada U(s)
$$Y(s) = 1 \cdot \left[ \frac{1}{s + 2} U(s) \right] + 1 \cdot \left[ \frac{1}{s + 3} U(s) \right]$$

### Paso 4: Definición de estados (por polo desacoplado)
* $X_1(s) \triangleq \frac{1}{s + 2} U(s)$
* $X_2(s) \triangleq \frac{1}{s + 3} U(s)$

### Paso 5: Pasaje al tiempo
* Para $X_1$:
  $$(s + 2)X_1(s) = U(s) \implies s X_1 + 2X_1 = U \implies \dot{x}_1(t) = -2x_1(t) + u(t)$$
* Para $X_2$:
  $$(s + 3)X_2(s) = U(s) \implies s X_2 + 3X_2 = U \implies \dot{x}_2(t) = -3x_2(t) + u(t)$$
* Salida:
  $$Y(s) = X_1(s) + X_2(s) \implies y(t) = x_1(t) + x_2(t)$$

### Paso 6: Matrices finales (FCD)
$$\begin{bmatrix} \dot{x}_1 \\ \dot{x}_2 \end{bmatrix} = \begin{bmatrix} -2 & 0 \\ 0 & -3 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} + \begin{bmatrix} 1 \\ 1 \end{bmatrix} u$$
$$y = \begin{bmatrix} 1 & 1 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix}$$

---

# 4. Forma Canónica de Jordan (FCJ) - Polos Múltiples

---

## 1. Planteo Teórico y Deducción Literal del Examen

### Enunciado Base
Dada la función de transferencia donde $N(s)$ es el numerador y $a \in \mathbb{R} \; (a \neq 0)$:
$$\frac{Y(s)}{U(s)} = \frac{N(s)}{(s + a)^2}$$

Se solicita definir las variables $x_i$ para obtener la **Forma Canónica de Jordan** y armar el sistema de ecuaciones de estado y salida.

---

### ¿Por qué se utiliza la Forma Canónica de Jordan?
Cuando un sistema posee polos repetidos (en este caso, un polo doble en $s = -a$), **no es posible desacoplar completamente el sistema en ramas independientes en paralelo** (no existe una base de autovectores linealmente independientes para diagonalizar la matriz $A$). 

La estructura desacoplada degenera en un **Bloque de Jordan**, donde los estados asociados a la misma raíz se encadenan entre sí mediante un integrador de acoplamiento. Esto se traduce en un elemento unitario ($1$) en la superdiagonal de la matriz $A$.

---

### Paso 1: Expansión en Fracciones Simples para Raíces Múltiples
Para un denominador con multiplicidad 2, la descomposición estándar de Heaviside se formula como:
$$\frac{Y(s)}{U(s)} = \frac{N(s)}{(s + a)^2} = \frac{d_1}{(s + a)^2} + \frac{d_2}{s + a}$$

Donde $d_1$ y $d_2$ son los residuos calculados analíticamente:
* $d_1 = \left. (s + a)^2 \frac{N(s)}{(s + a)^2} \right|_{s = -a} = N(-a)$
* $d_2 = \left. \frac{d}{ds} \left[ (s + a)^2 \frac{N(s)}{(s + a)^2} \right] \right|_{s = -a} = N'(-a)$

---

### Paso 2: Distribuir la entrada $U(s)$
Multiplicamos toda la expresión por la entrada $U(s)$:
$$Y(s) = d_1 \left[ \frac{1}{(s + a)^2} U(s) \right] + d_2 \left[ \frac{1}{s + a} U(s) \right]$$

Notar la relación de dependencia entre ambos factores dinámicos:
$$\frac{1}{(s + a)^2} U(s) = \frac{1}{s + a} \cdot \left[ \frac{1}{s + a} U(s) \right]$$

---

### Paso 3: Definición Formal de las Variables de Estado ($x_i$)
En la Forma de Jordan, el segundo estado procesa la entrada externa $U(s)$, mientras que el primer estado se alimenta de la salida del segundo (encadenamiento en cascada sobre la misma raíz):

* **Segundo estado ($X_2(s)$):** Bloque de primer orden que recibe la entrada directa:
  $$X_2(s) \triangleq \frac{1}{s + a} U(s)$$

* **Primer estado ($X_1(s)$):** Bloque de segundo orden, que equivale a pasar $X_2(s)$ por un polo idéntico:
  $$X_1(s) \triangleq \frac{1}{(s + a)^2} U(s) = \frac{1}{s + a} X_2(s)$$

---

### Paso 4: Despeje Temporal de las Ecuaciones de Estado
1. **Para la variable $X_1(s)$:**
   $$(s + a) X_1(s) = X_2(s)$$
   $$s X_1(s) + a X_1(s) = X_2(s)$$
   Antitransformando al dominio del tiempo ($s X_1(s) \to \dot{x}_1(t)$):
   $$\dot{x}_1(t) + a x_1(t) = x_2(t)$$
   Despejando $\dot{x}_1(t)$:
   $$\mathbf{\dot{x}_1(t) = -a x_1(t) + 1 \cdot x_2(t) + 0 \cdot u(t)}$$

2. **Para la variable $X_2(s)$:**
   $$(s + a) X_2(s) = U(s)$$
   $$s X_2(s) + a X_2(s) = U(s)$$
   Antitransformando al dominio del tiempo ($s X_2(s) \to \dot{x}_2(t)$):
   $$\dot{x}_2(t) + a x_2(t) = u(t)$$
   Despejando $\dot{x}_2(t)$:
   $$\mathbf{\dot{x}_2(t) = 0 \cdot x_1(t) - a x_2(t) + 1 \cdot u(t)}$$

---

### Paso 5: Ecuación de Salida en el Tiempo
Retomamos la expresión distribuida del Paso 2:
$$Y(s) = d_1 X_1(s) + d_2 X_2(s)$$

Antitransformando directamente:
$$\mathbf{y(t) = d_1 x_1(t) + d_2 x_2(t) + 0 \cdot u(t)}$$

---

### Paso 6: Estructuración Matricial Final (FCJ)
$$\begin{bmatrix} \dot{x}_1(t) \\ \dot{x}_2(t) \end{bmatrix} = \begin{bmatrix} -a & 1 \\ 0 & -a \end{bmatrix} \begin{bmatrix} x_1(t) \\ x_2(t) \end{bmatrix} + \begin{bmatrix} 0 \\ 1 \end{bmatrix} u(t)$$

$$y(t) = \begin{bmatrix} d_1 & d_2 \end{bmatrix} \begin{bmatrix} x_1(t) \\ x_2(t) \end{bmatrix} + [0] u(t)$$
## 4. Comparativa Rápida

| Forma   | Matriz $A$                                           | Matriz $B$                                 | Matriz $C$                                |
| :------ | :--------------------------------------------------- | :----------------------------------------- | :---------------------------------------- |
| **FCC** | $\begin{bmatrix} 0 & 1 \\ -a_0 & -a_1 \end{bmatrix}$ | $\begin{bmatrix} 0 \\ 1 \end{bmatrix}$     | $\begin{bmatrix} b_0 & b_1 \end{bmatrix}$ |
| **FCO** | $\begin{bmatrix} 0 & -a_0 \\ 1 & -a_1 \end{bmatrix}$ | $\begin{bmatrix} b_0 \\ b_1 \end{bmatrix}$ | $\begin{bmatrix} 0 & 1 \end{bmatrix}$     |
| **FCD** | $\begin{bmatrix} p_1 & 0 \\ 0 & p_2 \end{bmatrix}$   | $\begin{bmatrix} 1 \\ 1 \end{bmatrix}$     | $\begin{bmatrix} c_1 & c_2 \end{bmatrix}$ |