# Guía Maestra de Realizaciones Canónicas (FCC, FCO, FCD, FCJ)

Representación analítica en espacio de estados:
$$\mathbf{\dot{x}}(t) = A\,\mathbf{x}(t) + B\,u(t)$$
$$y(t) = C\,\mathbf{x}(t) + D\,u(t)$$

---

## 1. Forma Canónica Controlable (FCC)

### Justificación
Modela la dinámica mediante una cadena de integradores en serie. Se separa el sistema en dos bloques consecutivos:
1. Bloque con los polos del denominador que genera una variable interna $V(s)$.
2. Bloque con el numerador que combina linealmente $V(s)$ y sus derivadas para formar la salida $Y(s)$.

### Ejemplo Base
$$G(s) = \frac{Y(s)}{U(s)} = \frac{2s + 5}{s^2 + 5s + 6}$$
* Polinomio denominador: $s^2 + 5s + 6 \implies a_1 = 5, \quad a_0 = 6$
* Polinomio numerador: $2s + 5 \implies b_1 = 2, \quad b_0 = 5$

### Paso 1: Variable auxiliar V(s)
$$Y(s) = (2s + 5) \cdot \underbrace{\left[ \frac{1}{s^2 + 5s + 6} U(s) \right]}_{V(s)}$$
* Dinámica interna: $(s^2 + 5s + 6)V(s) = U(s)$
* Salida: $Y(s) = (2s + 5)V(s) = 2s V(s) + 5 V(s)$

### Paso 2: Pasaje al tiempo
$$(s^2 + 5s + 6)V(s) = U(s) \implies \ddot{v}(t) + 5\dot{v}(t) + 6v(t) = u(t)$$
$$\ddot{v}(t) = -6v(t) - 5\dot{v}(t) + u(t)$$

### Paso 3: Definición de variables de estado (en cadena)
* $x_1(t) \triangleq v(t)$
* $x_2(t) \triangleq \dot{v}(t)$

### Paso 4: Derivadas de los estados
* $\dot{x}_1(t) = \dot{v}(t) = x_2(t) \implies \mathbf{\dot{x}_1 = 0\,x_1 + 1\,x_2 + 0\,u}$
* $\dot{x}_2(t) = \ddot{v}(t) = -6v - 5\dot{v} + u \implies \mathbf{\dot{x}_2 = -6\,x_1 - 5\,x_2 + 1\,u}$

### Paso 5: Ecuación de salida
$$y(t) = 5v(t) + 2\dot{v}(t) \implies \mathbf{y = 5\,x_1 + 2\,x_2 + 0\,u}$$

### Paso 6: Matrices finales (FCC)
$$\begin{bmatrix} \dot{x}_1 \\ \dot{x}_2 \end{bmatrix} = \begin{bmatrix} 0 & 1 \\ -6 & -5 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} + \begin{bmatrix} 0 \\ 1 \end{bmatrix} u$$
$$y = \begin{bmatrix} 5 & 2 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix}$$

---

## 2. Forma Canónica Observable (FCO)

### Justificación
Estructura dual de la FCC basada en el desanidado de integradores: se divide por potencias de $s$ para que los estados aparezcan a la salida de integradores sucesivos $\frac{1}{s}$.

### Ejemplo Base
$$G(s) = \frac{Y(s)}{U(s)} = \frac{2s + 5}{s^2 + 5s + 6}$$

### Paso 1: Multiplicar cruzado
$$(s^2 + 5s + 6)Y(s) = (2s + 5)U(s)$$
$$s^2 Y(s) + 5s Y(s) + 6Y(s) = 2s U(s) + 5U(s)$$

### Paso 2: Aislar mayor potencia y agrupar
$$s^2 Y(s) = s[2U(s) - 5Y(s)] + [5U(s) - 6Y(s)]$$
Dividiendo todo por $s^2$:
$$Y(s) = \frac{1}{s} \left( [2U(s) - 5Y(s)] + \frac{1}{s}[5U(s) - 6Y(s)] \right)$$

### Paso 3: Definición de variables de estado (de adentro hacia afuera)
* $X_1(s) \triangleq \frac{1}{s}[5U(s) - 6Y(s)]$
* $X_2(s) \triangleq \frac{1}{s}[X_1(s) - 5Y(s) + 2U(s)]$
* Salida directa: $Y(s) = X_2(s) \implies \mathbf{y(t) = x_2(t)}$

### Paso 4: Despeje temporal
* Para $X_1$:
  $$s X_1(s) = -6Y(s) + 5U(s) \implies \mathbf{\dot{x}_1 = 0\,x_1 - 6\,x_2 + 5\,u}$$
* Para $X_2$:
  $$s X_2(s) = X_1(s) - 5Y(s) + 2U(s) \implies \mathbf{\dot{x}_2 = 1\,x_1 - 5\,x_2 + 2\,u}$$

### Paso 5: Matrices finales (FCO)
$$\begin{bmatrix} \dot{x}_1 \\ \dot{x}_2 \end{bmatrix} = \begin{bmatrix} 0 & -6 \\ 1 & -5 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} + \begin{bmatrix} 5 \\ 2 \end{bmatrix} u$$
$$y = \begin{bmatrix} 0 & 1 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix}$$

---

## 3. Forma Canónica Diagonal (FCD)

### Justificación
Desacopla el sistema en subsistemas de primer orden en paralelo. Requiere polos reales y distintos ($p_1 \neq p_2$) y se basa en la descomposición en fracciones simples.

### Ejemplo Base
$$G(s) = \frac{Y(s)}{U(s)} = \frac{2s + 5}{s^2 + 5s + 6} = \frac{2s + 5}{(s + 2)(s + 3)}$$
* Polos: $p_1 = -2, \quad p_2 = -3$

### Paso 1: Fracciones simples (residuos)
$$\frac{2s + 5}{(s + 2)(s + 3)} = \frac{c_1}{s + 2} + \frac{c_2}{s + 3}$$
* $c_1 = \lim_{s \to -2} \left[ \frac{2s + 5}{s + 3} \right] = \frac{2(-2) + 5}{-2 + 3} = 1$
* $c_2 = \lim_{s \to -3} \left[ \frac{2s + 5}{s + 2} \right] = \frac{2(-3) + 5}{-3 + 2} = 1$

$$\frac{Y(s)}{U(s)} = \frac{1}{s + 2} + \frac{1}{s + 3}$$

### Paso 2: Distribuir U(s)
$$Y(s) = 1 \cdot \left[ \frac{1}{s + 2} U(s) \right] + 1 \cdot \left[ \frac{1}{s + 3} U(s) \right]$$

### Paso 3: Definición de variables de estado
* $X_1(s) \triangleq \frac{1}{s + 2} U(s)$
* $X_2(s) \triangleq \frac{1}{s + 3} U(s)$

### Paso 4: Despeje temporal
* Para $X_1$:
  $$(s + 2)X_1(s) = U(s) \implies s X_1 + 2X_1 = U \implies \mathbf{\dot{x}_1 = -2\,x_1 + 0\,x_2 + 1\,u}$$
* Para $X_2$:
  $$(s + 3)X_2(s) = U(s) \implies s X_2 + 3X_2 = U \implies \mathbf{\dot{x}_2 = 0\,x_1 - 3\,x_2 + 1\,u}$$
* Para la salida:
  $$Y(s) = 1\,X_1(s) + 1\,X_2(s) \implies \mathbf{y = 1\,x_1 + 1\,x_2 + 0\,u}$$

### Paso 5: Matrices finales (FCD)
$$\begin{bmatrix} \dot{x}_1 \\ \dot{x}_2 \end{bmatrix} = \begin{bmatrix} -2 & 0 \\ 0 & -3 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} + \begin{bmatrix} 1 \\ 1 \end{bmatrix} u$$
$$y = \begin{bmatrix} 1 & 1 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix}$$

---

## 4. Forma Canónica de Jordan (FCJ)

### Justificación
Se aplica obligatoriamente cuando existen polos repetidos (raíces múltiples). Los estados correspondientes al mismo polo no pueden quedar totalmente en paralelo y se conectan en cascada formando un Bloque de Jordan, lo que genera un $1$ en la superdiagonal de $A$.

### Ejemplo Base
$$G(s) = \frac{Y(s)}{U(s)} = \frac{3s + 7}{(s + 2)^2}$$
* Polo doble: $p_1 = p_2 = -2$

### Paso 1: Fracciones simples para raíz repetida
$$\frac{3s + 7}{(s + 2)^2} = \frac{d_1}{(s + 2)^2} + \frac{d_2}{s + 2} = \frac{d_1 + d_2(s + 2)}{(s + 2)^2} = \frac{d_2 s + (d_1 + 2d_2)}{(s + 2)^2}$$
* Igualando coeficientes:
  * $d_2 = 3$
  * $d_1 + 2d_2 = 7 \implies d_1 + 2(3) = 7 \implies d_1 = 1$

$$\frac{Y(s)}{U(s)} = \frac{1}{(s + 2)^2} + \frac{3}{s + 2}$$

### Paso 2: Distribuir U(s) y notar el encadenamiento
$$Y(s) = 1 \cdot \left[ \frac{1}{(s + 2)^2} U(s) \right] + 3 \cdot \left[ \frac{1}{s + 2} U(s) \right]$$
El término cuadrático equivale a aplicar dos veces el polo:
$$\frac{1}{(s + 2)^2} U(s) = \frac{1}{s + 2} \cdot \left[ \frac{1}{s + 2} U(s) \right]$$

### Paso 3: Definición de variables de estado
* Estado que recibe la entrada directa:
  $$X_2(s) \triangleq \frac{1}{s + 2} U(s)$$
* Estado encadenado en cascada desde $X_2$:
  $$X_1(s) \triangleq \frac{1}{s + 2} X_2(s)$$

### Paso 4: Despeje temporal
* Para $X_1$:
  $$(s + 2)X_1(s) = X_2(s) \implies s X_1 + 2X_1 = X_2 \implies \mathbf{\dot{x}_1 = -2\,x_1 + 1\,x_2 + 0\,u}$$
* Para $X_2$:
  $$(s + 2)X_2(s) = U(s) \implies s X_2 + 2X_2 = U \implies \mathbf{\dot{x}_2 = 0\,x_1 - 2\,x_2 + 1\,u}$$
* Para la salida:
  $$Y(s) = 1\,X_1(s) + 3\,X_2(s) \implies \mathbf{y = 1\,x_1 + 3\,x_2 + 0\,u}$$

### Paso 5: Matrices finales (FCJ)
$$\begin{bmatrix} \dot{x}_1 \\ \dot{x}_2 \end{bmatrix} = \begin{bmatrix} -2 & 1 \\ 0 & -2 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} + \begin{bmatrix} 0 \\ 1 \end{bmatrix} u$$
$$y = \begin{bmatrix} 1 & 3 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix}$$

---

## 5. Tabla Comparativa

| Forma | Condición de Polos | Matriz $A$ | Matriz $B$ | Matriz $C$ |
| :--- | :--- | :--- | :--- | :--- |
| **FCC** | Cualquier polo | $\begin{bmatrix} 0 & 1 \\ -a_0 & -a_1 \end{bmatrix}$ | $\begin{bmatrix} 0 \\ 1 \end{bmatrix}$ | $\begin{bmatrix} b_0 & b_1 \end{bmatrix}$ |
| **FCO** | Cualquier polo | $\begin{bmatrix} 0 & -a_0 \\ 1 & -a_1 \end{bmatrix}$ | $\begin{bmatrix} b_0 \\ b_1 \end{bmatrix}$ | $\begin{bmatrix} 0 & 1 \end{bmatrix}$ |
| **FCD** | Polos simples ($p_1 \neq p_2$) | $\begin{bmatrix} p_1 & 0 \\ 0 & p_2 \end{bmatrix}$ | $\begin{bmatrix} 1 \\ 1 \end{bmatrix}$ | $\begin{bmatrix} c_1 & c_2 \end{bmatrix}$ |
| **FCJ** | Polos repetidos ($p_1 = p_2 = p$) | $\begin{bmatrix} p & 1 \\ 0 & p \end{bmatrix}$ | $\begin{bmatrix} 0 \\ 1 \end{bmatrix}$ | $\begin{bmatrix} d_1 & d_2 \end{bmatrix}$ |