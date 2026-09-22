# Machete Definitivo de Sistemas de Control (Guías 1 a 4)

## GUÍA 1: Propiedades de los Sistemas

Para saber qué tipo de sistema tenés, se evalúa su función matemática algebraicamente.

*   **Linealidad:** Debe cumplir dos condiciones simultáneas.
    *   **Homogeneidad:** Si multiplicás la entrada por una constante $a$, la salida debe multiplicarse por esa misma $a$. Es decir, $f(a \cdot x) = a \cdot f(x)$.
    *   **Superposición:** La función de una suma de entradas debe ser igual a las funciones separadas sumadas. $f(x_1 + x_2) = f(x_1) + f(x_2)$.
*   **Invarianza en el Tiempo (TI):** Un retardo en la entrada provoca exactamente el mismo retardo en la salida, sin alterar la fórmula. Si $y(t) = f(x(t))$, entonces la entrada desplazada $x(t-t_0)$ debe dar $y(t-t_0)$.
*   **Causalidad:** Un sistema es causal si la salida actual no depende de valores futuros de la entrada. Si la fórmula dice $y(t) = x(t+1)$, es no causal porque "adivina" el futuro.
*   **Memoria:** Si la salida $y(t)$ depende de un instante distinto a $t$ (ejemplo $x(t-1)$), tiene memoria. Si solo depende de la entrada en ese mismo instante $x(t)$, es sin memoria.
*   **Inversibilidad:** Si distintas entradas producen distintas salidas y podés despejar matemáticamente la entrada original a partir de la salida.

---

## GUÍA 2: Representación Interna, Externa y Formas Canónicas

### 1. Representación Interna (Matrices)
Modela la dinámica interna del sistema en el tiempo mediante ecuaciones de estado y salida.
$$ \dot{\mathbf{x}}(t) = A\mathbf{x}(t) + B u(t) $$
$$ y(t) = C\mathbf{x}(t) + D u(t) $$
**Variables:**
*   $\mathbf{x}(t)$: Vector de variables de estado (ej. $x_1, x_2$). Son las variables internas del sistema.
*   $\dot{\mathbf{x}}(t)$: Vector de derivadas. Es la velocidad de cambio de los estados.
*   $u(t)$: La señal de entrada o estímulo externo.
*   $y(t)$: La señal de salida.
*   $A$: Matriz dinámica (relaciona los estados entre sí).
*   $B$: Matriz de entrada (cómo afecta $u$ a los estados).
*   $C$: Matriz de salida o lectura (cómo se combinan los estados para formar $y$).
*   $D$: Matriz de transmisión directa (suele ser $0$ en sistemas estrictamente propios).

### 2. Representación Externa (Función de Transferencia)
Relaciona entrada y salida en el dominio de Laplace, asumiendo condiciones iniciales nulas.
$$ G(s) = \frac{Y(s)}{U(s)} = \frac{N(s)}{D(s)} $$
**Variables:**
*   $s$: Variable compleja de Laplace.
*   $N(s)$: Polinomio numerador. Al igualarlo a cero obtenés los **ceros** del sistema.
*   $D(s)$: Polinomio denominador (Ecuación característica). Al igualarlo a cero obtenés los **polos** del sistema.

**Fórmula de pasaje (De Interna a Externa):**
$$ G(s) = C(sI - A)^{-1}B + D $$
*   $I$: Matriz Identidad (unos en la diagonal, ceros en el resto).
*   $(sI - A)^{-1}$: Matriz Resolvente ($\Phi(s)$). A la matriz identidad por $s$ le restás $A$, y a eso le calculás la inversa.

### 3. Armado Práctico de Formas Canónicas
A partir de $G(s) = \frac{b_1 s + b_2}{s^2 + a_1 s + a_2}$. (El coeficiente de la mayor potencia del denominador $s^n$ debe ser siempre $1$).

*   **FCC (Forma Canónica Controlable):**
    *   $A$: Última fila tiene los coeficientes del denominador cambiados de signo ($-a_2, -a_1$). Arriba de esa fila, un $0$ y un $1$.
    *   $B$: Columna de ceros que termina con un $1$ abajo ($0, 1$).
    *   $C$: Fila con los coeficientes del numerador tal cual, ordenados de menor a mayor potencia de $s$ ($b_2, b_1$).$$A = \begin{bmatrix} 0 & 1 \\ -a_0 & -a_1 \end{bmatrix}, \quad B = \begin{bmatrix} 0 \\ 1 \end{bmatrix}, \quad C = \begin{bmatrix} b_0 & b_1 \end{bmatrix}$$
*   **FCO (Forma Canónica Observable):**
    *   Es la transpuesta de la FCC ($A_{FCO} = A_{FCC}^T$, $B_{FCO} = C_{FCC}^T$, $C_{FCO} = B_{FCC}^T$).
    *   $A$: Primera columna tiene los coeficientes del denominador cambiados de signo ($-a_2, -a_1$). A la derecha, un $0$ y un $1$.
    *   $B$: Columna con los coeficientes del numerador ($b_2, b_1$).
    *   $C$: Fila con un $0$ y un $1$ ($0, 1$).$$A = \begin{bmatrix} 0 & -a_0 \\ 1 & -a_1 \end{bmatrix}, \quad B = \begin{bmatrix} b_0 \\ b_1 \end{bmatrix}, \quad C = \begin{bmatrix} 0 & 1 \end{bmatrix}$$
*   **FCD (Forma Canónica Diagonal):**
    *   Se aplica cuando todos los polos son distintos. Requiere separar $G(s)$ en fracciones simples para sacar los polos ($p_1, p_2$) y los residuos de los numeradores ($c_1, c_2$).
    *   $A$: Diagonal principal con los polos ($p_1, p_2$), el resto en $0$.
    *   $B$: Columna de puros $1$.
    *   $C$: Fila con los residuos de las fracciones parciales ($c_1, c_2$).$$A = \begin{bmatrix} p_1 & 0 \\ 0 & p_2 \end{bmatrix}, \quad B = \begin{bmatrix} 1 \\ 1 \end{bmatrix}, \quad C = \begin{bmatrix} d_1 & d_2 \end{bmatrix}$$
*   **FCJ (Forma de Jordan):**
    *   Se usa si hay polos múltiples repetidos (ej: $(s-2)^2$).
    *   $A$: Diagonal con el polo repetido. Justo arriba de la diagonal, se coloca un $1$.
    *   $B$: Columna de puros $1$.
    *   $C$: Residuos calculados con el método de multiplicidad.$$A = \begin{bmatrix} p_1 & \mathbf{1} & 0 \\ 0 & p_1 & 0 \\ 0 & 0 & p_2 \end{bmatrix}, \quad B = \begin{bmatrix} \mathbf{0} \\ \mathbf{1} \\ 1 \end{bmatrix}, \quad C = \begin{bmatrix} d_1 & d_2 & d_3 \end{bmatrix}$$

---

## RESOLUCIÓN TEMPORAL (Hallar $x(t)$ e $y(t)$)

### 1. Método Externo (Escalar)
Busca la salida $y(t)$ usando Laplace.
$$ Y(s) = G(s) \cdot U(s) $$
1.  Multiplicar la función de transferencia $G(s)$ por la entrada $U(s)$. (Ej: escalón unitario $\implies U(s) = 1/s$).
2.  Descomponer el resultado en fracciones simples.
3.  Aplicar Antitransformada de Laplace a cada término para obtener $y(t)$.

### 2. Método Interno (Matricial)
Calcula cómo evolucionan todas las variables de estado ($x_1(t), x_2(t)$).
$$ \mathbf{X}(s) = (sI - A)^{-1} \mathbf{x}_0 + (sI - A)^{-1} B U(s) $$
*   $\mathbf{x}_0$: Vector de condiciones iniciales en $t=0$.
*   **Primer término:** Respuesta Libre (movimiento solo por condiciones iniciales).
*   **Segundo término:** Respuesta Forzada (movimiento provocado por la entrada $U(s)$).

**Pasos de cálculo:**
1.  Armar la matriz $(sI - A)$ y calcularle la inversa: $(sI - A)^{-1}$. Para matrices $2\times2$, se permuta la diagonal principal, se cambia el signo a la secundaria, y se divide todo por el determinante.
2.  Multiplicar la matriz resultante por $\mathbf{x}_0$.
3.  Multiplicar la matriz por $B$ y luego por $U(s)$.
4.  Sumar los resultados y aplicar Antitransformada de Laplace elemento por elemento para obtener el vector $\mathbf{x}(t)$.
5.  Reemplazar $\mathbf{x}(t)$ en la ecuación $y(t) = C\mathbf{x}(t)$ para sacar la salida final.

---

## GUÍA 3: Álgebra de Bloques

*   **Bloques en Serie (Cascada):** Se multiplican. $G_1 \cdot G_2$.
*   **Bloques en Paralelo:** Se suman algebraicamente. $G_1 \pm G_2$.
*   **Lazo Cerrado (Realimentación):** Camino de ida $G$, camino de vuelta $H$.
    $$ G_{eq} = \frac{G}{1 \mp G \cdot H} $$
    *Regla:* El signo del denominador es **opuesto** al signo con el que la rama de retroalimentación $H$ entra al comparador.
*   **Movimiento de nodos (para destrabar lazos cruzados):**
    *   Mover **bifurcación** para DESPUÉS de un bloque $G$: Multiplicar la rama por $\frac{1}{G}$.
    *   Mover **bifurcación** para ANTES de un bloque $G$: Multiplicar la rama por $G$.
    *   Mover **sumador** para DESPUÉS de un bloque $G$: Multiplicar la rama entrante por $G$.
    *   Mover **sumador** para ANTES de un bloque $G$: Multiplicar la rama entrante por $\frac{1}{G}$.

---

## GUÍA 4: Estabilidad y Plano de Fase

### 1. Parámetros de Sistemas de 2do Orden
$$ G(s) = \frac{K \omega_n^2}{s^2 + 2\xi\omega_n s + \omega_n^2} $$
**Variables:**
*   $K$: Ganancia en estado estacionario.
*   $\omega_n$: Frecuencia natural no amortiguada.
*   $\xi$: Coeficiente de amortiguamiento. Define la forma de la respuesta:
    *   $\xi > 1$: Sobreamortiguado (estable, raíces reales, sin oscilaciones).
    *   $\xi = 1$: Críticamente amortiguado (estable, raíces reales iguales).
    *   $0 < \xi < 1$: Subamortiguado (estable, raíces complejas, oscilaciones decrecientes).
    *   $\xi = 0$: Marginalmente estable (oscilación sostenida continua).
    *   $\xi < 0$: Inestable (oscilaciones de amplitud creciente o crecimiento exponencial puro).

### 2. Estabilidad Externa (Criterio de Routh-Hurwitz)
Determina la estabilidad sin calcular las raíces del denominador $D(s) = 0$.

**Procedimiento:**
1.  Verificar la Condición de Cardano: Todos los coeficientes del polinomio deben existir (no ser nulos) y tener el mismo signo. Si no se cumple, es inestable.
2.  Armar el arreglo tabular con los coeficientes alternados en las dos primeras filas ($s^n$ y $s^{n-1}$).
3.  Calcular las filas inferiores multiplicando cruzado (tipo determinante negativo) y dividiendo por el primer elemento de la fila anterior.
    $$ b_1 = \frac{a_1 a_2 - a_0 a_3}{a_1} $$
4.  **Veredicto:** El sistema es estable si **todos** los elementos de la primera columna tienen el mismo signo. El número de cambios de signo indica exactamente cuántas raíces inestables (parte real positiva) tiene el sistema.

### 3. Estabilidad Interna (Plano de Fase y Autovalores)
Para sistemas autónomos $\dot{\mathbf{x}} = A\mathbf{x}$ (sin entrada externa $u(t)$).

**A. Punto de Equilibrio ($x_e$):**
Se igualan las derivadas a cero ($\dot{x}_1 = 0, \dot{x}_2 = 0$) y se resuelve el sistema algebraico. En sistemas lineales LTI sin términos independientes, el único punto crítico es el origen $(0,0)$.

**B. Autovalores ($\lambda$):**
Se calculan resolviendo la ecuación determinante $\det(\lambda I - A) = 0$.

**C. Clasificación del Punto Crítico:**
*   **Nodo Estable:** Autovalores reales, distintos y negativos ($\lambda < 0$). Las trayectorias convergen al origen.
*   **Nodo Inestable:** Autovalores reales, distintos y positivos ($\lambda > 0$). Las trayectorias divergen.
*   **Punto de Silla / Ensilladura:** Autovalores reales de signos opuestos.
*   **Centro:** Autovalores complejos puros (sin parte real, $\lambda = \pm qi$). Trayectorias cerradas, oscilación sostenida.
*   **Foco Estable:** Autovalores complejos con parte real negativa. Trayectorias en espiral que convergen al origen.
*   **Foco Inestable:** Autovalores complejos con parte real positiva. Trayectorias en espiral que se alejan del origen.