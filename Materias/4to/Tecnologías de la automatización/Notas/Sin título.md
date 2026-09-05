# Resumen: Variables de Estado y Sistemas Lineales

---

## 1. Formas Canónicas a partir de $G(s)$

Dada una función de transferencia estrictamente propia de orden 2:
$$G(s) = \frac{b_1 s + b_0}{s^2 + a_1 s + a_0}$$

### Forma Canónica Controlable (FCC)
* **Matriz $A$:** Unos en la superdiagonal, última fila con coeficientes del denominador cambiados de signo.
* **Matriz $B$:** Vector columna con ceros y un uno al final.
* **Matriz $C$:** Vector fila con coeficientes del numerador en orden ascendente de potencias.

$$A = \begin{bmatrix} 0 & 1 \\ -a_0 & -a_1 \end{bmatrix}, \quad B = \begin{bmatrix} 0 \\ 1 \end{bmatrix}, \quad C = \begin{bmatrix} b_0 & b_1 \end{bmatrix}$$

---

### Forma Canónica Observable (FCO)
Es la traspuesta dual de la FCC:
$$A_{FCO} = A_{FCC}^T, \quad B_{FCO} = C_{FCC}^T, \quad C_{FCO} = B_{FCC}^T$$

$$A = \begin{bmatrix} 0 & -a_0 \\ 1 & -a_1 \end{bmatrix}, \quad B = \begin{bmatrix} b_0 \\ b_1 \end{bmatrix}, \quad C = \begin{bmatrix} 0 & 1 \end{bmatrix}$$

---

### Forma Canónica Diagonal (FCD)
Aplica cuando todos los polos son **reales y distintos**.
1. Descomponer en fracciones simples:
   $$G(s) = \frac{d_1}{s - p_1} + \frac{d_2}{s - p_2}$$
2. Armar las matrices:
   * **$A$:** Polos en la diagonal principal.
   * **$B$:** Vector columna de unos.
   * **$C$:** Vector fila con los residuos ($d_i$).

$$A = \begin{bmatrix} p_1 & 0 \\ 0 & p_2 \end{bmatrix}, \quad B = \begin{bmatrix} 1 \\ 1 \end{bmatrix}, \quad C = \begin{bmatrix} d_1 & d_2 \end{bmatrix}$$

---

### Forma Canónica de Jordan (FCJ)
Aplica cuando existen **polos repetidos (múltiples)**.
*Ejemplo:* Polo simple en $p_1$ y polo doble en $p_2$.
$$G(s) = \frac{d_1}{s - p_1} + \frac{d_2}{(s - p_2)^2} + \frac{d_3}{s - p_2}$$

* **Matriz $A$:** Polos en la diagonal; se coloca un **$1$** arriba del polo repetido (superdiagonal) para formar el bloque de Jordan.
* **Matriz $B$:** En el bloque repetido, solo la **última fila** lleva un $1$, las anteriores llevan $0$.
* **Matriz $C$:** Residuos ordenados en fila.

$$A = \begin{bmatrix} p_1 & 0 & 0 \\ 0 & p_2 & \mathbf{1} \\ 0 & 0 & p_2 \end{bmatrix}, \quad B = \begin{bmatrix} 1 \\ \mathbf{0} \\ \mathbf{1} \end{bmatrix}, \quad C = \begin{bmatrix} d_1 & d_2 & d_3 \end{bmatrix}$$

---

## 2. De Matrices $(A, B, C, D)$ a Función de Transferencia $G(s)$

Fórmula general:
$$G(s) = C(sI - A)^{-1}B + D$$

Si $D = 0$:
$$G(s) = C(sI - A)^{-1}B$$

### Algoritmo de cálculo
1. Armar la matriz $(sI - A)$.
2. Calcular la inversa:
   $$(sI - A)^{-1} = \frac{\text{Adj}(sI - A)^T}{\det(sI - A)}$$
3. Multiplicar matrices: primero $(sI - A)^{-1} B$ y premultiplicar el resultado por $C$.

> **Nota:** El polinomio característico del sistema (denominador de $G(s)$) es igual a $\det(sI - A)$.

---

## 3. Métodos de Resolución Temporal

### A. Método Escalar (Ecuaciones Diferenciales + Laplace)
1. Desarmar las matrices multiplicando fila por columna:
   $$\dot{\mathbf{x}} = A\mathbf{x} + Bu, \quad y = C\mathbf{x}$$
2. Aplicar la propiedad de la derivada de Laplace:
   $$\mathcal{L}\{x'(t)\} = s X(s) - x(0)$$
3. Incorporar la entrada $U(s)$ (si $u(t) = 0$, se anula).
4. Despejar algebraicamente $X_1(s), X_2(s), \dots$.
5. Sustituir en la ecuación de salida: $Y(s) = C \mathbf{X}(s)$.
6. Descomponer en fracciones simples y antitransformar:
   $$\mathcal{L}^{-1}\left\{\frac{1}{s + a}\right\} = e^{-at}$$

---

### B. Método Matricial (Fórmula Compacta)
Todo el sistema se resuelve en un solo paso matricial:

$$\mathbf{X}(s) = \underbrace{(sI - A)^{-1}\mathbf{x}_0}_{\text{Respuesta a Entrada Cero}} + \underbrace{(sI - A)^{-1}B \, U(s)}_{\text{Respuesta a Estado Cero}}$$

$$Y(s) = C \mathbf{X}(s)$$

1. Se invierte $(sI - A)$ una sola vez.
2. Se calculan los productos matriz-vector.
3. Se aplica $\mathcal{L}^{-1}$ a cada componente del vector resultante.

---

## 4. Matriz de Transición de Estados ($\Phi(t)$ o $e^{At}$)

Describe la evolución temporal libre del sistema:

$$\Phi(t) = e^{At} = \mathcal{L}^{-1}\left[ (sI - A)^{-1} \right]$$

* **Cálculo:** Se calcula $(sI - A)^{-1}$ en Laplace y se antitransforma término a término hacia el dominio temporal $t$.
* **Evolución sin entrada:** $\mathbf{x}(t) = \Phi(t) \cdot \mathbf{x}_0$.
* **Verificación obligatoria:** En $t = 0$, debe dar la identidad:
  $$\Phi(0) = I$$

---

## 5. Transformación de Similitud (Cambio de Base)

Dada una transformación $\mathbf{x} = T \mathbf{z}$ (con $T$ inversible):

$$\tilde{A} = T^{-1} A T$$
$$\tilde{B} = T^{-1} B$$
$$\tilde{C} = C T$$

### Invariantes del sistema
Bajo cualquier transformación de similitud $T$:
1. $G(s)$ se mantiene idéntica: $C(sI - A)^{-1}B = \tilde{C}(sI - \tilde{A})^{-1}\tilde{B}$.
2. Los polos/autovalores se conservan: $\det(sI - A) = \det(sI - \tilde{A})$.
3. La estabilidad del sistema no varía.
