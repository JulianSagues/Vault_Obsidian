# Machete Definitivo: Sistemas de Control (Guías 1 a 4)

---

## GUÍA 1: Propiedades de los Sistemas

Para clasificar un sistema a partir de su función matemática:

*   **Linealidad:** Debe cumplir simultáneamente:
    *   *Homogeneidad:* $f(a \cdot x) = a \cdot f(x)$.
    *   *Superposición:* $f(x_1 + x_2) = f(x_1) + f(x_2)$.
*   **Invarianza en el Tiempo (TI):** Si la entrada se retarda un tiempo $t_0$, la salida se desplaza en la misma magnitud sin alterar su forma:
    $$ \mathcal{T}\{x(t - t_0)\} = y(t - t_0) $$
*   **Causalidad:** La salida actual no depende de valores futuros de la entrada ($y(t)$ no depende de $x(t+\tau)$ con $\tau > 0$).
*   **Memoria:** Si la salida $y(t)$ depende de instantes previos (ej: $x(t-1)$), tiene memoria. Si depende solo del instante actual $t$, es sin memoria.
*   **Inversibilidad:** Distintas entradas producen distintas salidas y existe una operación inversa tal que $\mathcal{T}^{-1}\{y(t)\} = x(t)$.

---

## GUÍA 2: Representación Interna, Externa y Realización

### 1. Representación Interna (Espacio de Estados)
Ecuaciones diferenciales de primer orden vectorizadas:
$$ \mathbf{\dot{x}}(t) = A\mathbf{x}(t) + B u(t) $$
$$ y(t) = C\mathbf{x}(t) + D u(t) $$

Para un sistema de segundo orden ($n=2$):
$$ \begin{bmatrix} \dot{x}_1(t) \\ \dot{x}_2(t) \end{bmatrix} = \begin{bmatrix} a_{11} & a_{12} \\ a_{21} & a_{22} \end{bmatrix} \begin{bmatrix} x_1(t) \\ x_2(t) \end{bmatrix} + \begin{bmatrix} b_1 \\ b_2 \end{bmatrix} u(t) $$
$$ y(t) = \begin{bmatrix} c_1 & c_2 \end{bmatrix} \begin{bmatrix} x_1(t) \\ x_2(t) \end{bmatrix} + [d] u(t) $$

### 2. Representación Externa (Función de Transferencia)
Relación entrada-salida en Laplace con condiciones iniciales nulas:
$$ G(s) = \frac{Y(s)}{U(s)} = \frac{N(s)}{D(s)} $$

*   **Pasaje de Interna a Externa:**
    $$ G(s) = C(sI - A)^{-1}B + D $$
    Donde la matriz resolvente es:
    $$ (sI - A)^{-1} = \frac{\text{Adj}(sI - A)}{\det(sI - A)} $$

### 3. Realización (De Externa a Interna)
Dado el sistema general de orden 2:
$$ G(s) = \frac{b_1 s + b_2}{s^2 + a_1 s + a_2} $$

*   **FCC (Forma Canónica Controlable):**
    $$ A = \begin{bmatrix} 0 & 1 \\ -a_2 & -a_1 \end{bmatrix}, \quad B = \begin{bmatrix} 0 \\ 1 \end{bmatrix}, \quad C = \begin{bmatrix} b_2 & b_1 \end{bmatrix} $$

*   **FCO (Forma Canónica Observable):**
    $$ A = \begin{bmatrix} 0 & -a_2 \\ 1 & -a_1 \end{bmatrix}, \quad B = \begin{bmatrix} b_2 \\ b_1 \end{bmatrix}, \quad C = \begin{bmatrix} 0 & 1 \end{bmatrix} $$

*   **FCD (Forma Canónica Diagonal):**
    A partir de la descomposición en fracciones simples con polos distintos $p_1 \neq p_2$:
    $$ G(s) = \frac{c_1}{s - p_1} + \frac{c_2}{s - p_2} $$
    $$ A = \begin{bmatrix} p_1 & 0 \\ 0 & p_2 \end{bmatrix}, \quad B = \begin{bmatrix} 1 \\ 1 \end{bmatrix}, \quad C = \begin{bmatrix} c_1 & c_2 \end{bmatrix} $$

*   **FCJ (Forma de Jordan):**
    Para polos múltiples repetidos (ej: polo doble $p_1$ y polo simple $p_2$):
    $$ A = \begin{bmatrix} p_1 & 1 & 0 \\ 0 & p_1 & 0 \\ 0 & 0 & p_2 \end{bmatrix}, \quad B = \begin{bmatrix} 0 \\ 1 \\ 1 \end{bmatrix}, \quad C = \begin{bmatrix} d_1 & d_2 & d_3 \end{bmatrix} $$

---

## RESOLUCIÓN TEMPORAL

### 1. Método Escalar (Por Sustitución Analítica)
Para un sistema con condiciones iniciales $x_1(0), x_2(0)$ y entrada $u(t)$:
$$
\begin{cases} 
\dot{x}_1(t) = a_{11}x_1(t) + a_{12}x_2(t) + b_1 u(t) \\ 
\dot{x}_2(t) = a_{21}x_1(t) + a_{22}x_2(t) + b_2 u(t) 
\end{cases}
$$
1.  **Transformar por Laplace:**
    $$ sX_1(s) - x_1(0) = a_{11}X_1(s) + a_{12}X_2(s) + b_1U(s) $$
    $$ sX_2(s) - x_2(0) = a_{21}X_1(s) + a_{22}X_2(s) + b_2U(s) $$
2.  **Agrupar en sistema algebraico:**
    $$ (s - a_{11})X_1(s) - a_{12}X_2(s) = x_1(0) + b_1U(s) $$
    $$ -a_{21}X_1(s) + (s - a_{22})X_2(s) = x_2(0) + b_2U(s) $$
3.  **Sustitución y despeje:** Despejar $X_2(s)$ de una ecuación y sustituir en la otra para aislar $X_1(s)$ (o viceversa).
4.  **Antitransformación:** Expandir en fracciones simples y aplicar $\mathcal{L}^{-1}$ para obtener $x_1(t)$ y $x_2(t)$.
5.  **Salida temporal:** $y(t) = c_1 x_1(t) + c_2 x_2(t) + d \cdot u(t)$.

### 2. Método Interno Matricial (Resolvente)
$$ \mathbf{X}(s) = \underbrace{(sI - A)^{-1} \mathbf{x}_0}_{\text{Respuesta a Entrada Cero}} + \underbrace{(sI - A)^{-1} B U(s)}_{\text{Respuesta a Estado Cero}} $$

*   **Fórmula directa para resolvente $2 \times 2$:**
    Si $A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}$, entonces $(sI - A) = \begin{bmatrix} s-a & -b \\ -c & s-d \end{bmatrix}$:
    $$ (sI - A)^{-1} = \frac{1}{(s-a)(s-d) - bc} \begin{bmatrix} s-d & b \\ c & s-a \end{bmatrix} $$
*   **Vector temporal:**
    $$ \mathbf{x}(t) = \begin{bmatrix} x_1(t) \\ x_2(t) \end{bmatrix} = \mathcal{L}^{-1}\{\mathbf{X}(s)\} $$
    $$ y(t) = C\mathbf{x}(t) + D u(t) $$

---

## GUÍA 3: Álgebra de Bloques

*   **Serie:** $G_{eq}(s) = G_1(s) \cdot G_2(s)$
*   **Paralelo:** $G_{eq}(s) = G_1(s) \pm G_2(s)$
*   **Lazo Cerrado:**
    $$ G_{eq}(s) = \frac{G(s)}{1 \mp G(s)H(s)} $$
    *(Signo opuesto: si la realimentación entra con $-$, en el denominador se suma $+$; si entra con $+$, se resta $-$)*.

*   **Reglas de Desplazamiento de Nodos:**
    *   Bifurcación tras un bloque $G(s)$: Colocar $\frac{1}{G(s)}$ en la rama derivada.
    *   Bifurcación antes de un bloque $G(s)$: Colocar $G(s)$ en la rama derivada.
    *   Sumador tras un bloque $G(s)$: Multiplicar la rama entrante por $G(s)$.
    *   Sumador antes de un bloque $G(s)$: Multiplicar la rama entrante por $\frac{1}{G(s)}$.

---

## GUÍA 4: Estabilidad y Plano de Fase

### 1. Sistema Estándar de 2do Orden
$$ G(s) = \frac{K \omega_n^2}{s^2 + 2\xi\omega_n s + \omega_n^2} $$
Polos del sistema:
$$ s_{1,2} = -\xi\omega_n \pm \omega_n \sqrt{\xi^2 - 1} $$

*   $\xi > 1$: Sobreamortiguado (2 polos reales negativos distintos).
*   $\xi = 1$: Críticamente amortiguado (2 polos reales negativos iguales).
*   $0 < \xi < 1$: Subamortiguado (polos complejos conjugados con parte real negativa).
*   $\xi = 0$: Marginalmente estable (polos imaginarios puros $\pm j\omega_n$).
*   $\xi < 0$: Inestable (polos con parte real positiva).

### 2. Criterio de Estabilidad de Routh-Hurwitz
Para el polinomio denominador $D(s) = a_0 s^n + a_1 s^{n-1} + a_2 s^{n-2} + a_3 s^{n-3} + \dots = 0$:

| Potencia | Columna 1 | Columna 2 | Columna 3 |
| :--- | :--- | :--- | :--- |
| $s^n$ | $a_0$ | $a_2$ | $a_4$ |
| $s^{n-1}$ | $a_1$ | $a_3$ | $a_5$ |
| $s^{n-2}$ | $b_1$ | $b_2$ | $\dots$ |
| $s^{n-3}$ | $c_1$ | $c_2$ | $\dots$ |

Cálculo de pivotes:
$$ b_1 = \frac{a_1 a_2 - a_0 a_3}{a_1}, \quad b_2 = \frac{a_1 a_4 - a_0 a_5}{a_1}, \quad c_1 = \frac{b_1 a_3 - a_1 b_2}{b_1} $$

*Condición:* Estable si todos los términos de la primera columna ($a_0, a_1, b_1, c_1, \dots$) tienen el mismo signo positivo.

### 3. Estabilidad Interna: Plano de Fase y Autovalores
Para sistemas autónomos de orden 2: $\mathbf{\dot{x}} = A\mathbf{x}$.

**A. Punto de Equilibrio ($x_e$):**
Se anulan las variaciones temporales:
$$ \mathbf{\dot{x}} = \begin{bmatrix} 0 \\ 0 \end{bmatrix} \implies \begin{cases} a_{11}x_1 + a_{12}x_2 = 0 \\ a_{21}x_1 + a_{22}x_2 = 0 \end{cases} \implies \mathbf{x}_e = \begin{bmatrix} 0 \\ 0 \end{bmatrix} \quad (\text{si } \det(A) \neq 0) $$

**B. Autovalores ($\lambda$):**
$$ \det(\lambda I - A) = 0 \implies \lambda^2 - \text{tr}(A)\lambda + \det(A) = 0 $$

**C. Clasificación del Punto Crítico:**
*   **Nodo Estable:** $\lambda_1, \lambda_2 \in \mathbb{R}$ con $\lambda_1 \neq \lambda_2 < 0$. Trayectorias directas al origen.
*   **Nodo Inestable:** $\lambda_1, \lambda_2 \in \mathbb{R}$ con $\lambda_1 \neq \lambda_2 > 0$. Trayectorias directas que escapan del origen.
*   **Punto de Silla:** $\lambda_1, \lambda_2 \in \mathbb{R}$ con $\lambda_1 \cdot \lambda_2 < 0$ (signos opuestos).
*   **Centro:** $\lambda_{1,2} = \pm j\beta$ (imaginarios puros). Órbitas cerradas elípticas.
*   **Foco Estable:** $\lambda_{1,2} = \alpha \pm j\beta$ con $\alpha < 0$. Espirales convergentes al origen.
*   **Foco Inestable:** $\lambda_{1,2} = \alpha \pm j\beta$ con $\alpha > 0$. Espirales divergentes.

### 4. Construcción Práctica del Plano de Fase (Paso a Paso)

El plano de fase es el gráfico de $x_2$ (eje vertical) vs. $x_1$ (eje horizontal), donde el tiempo $t$ es el parámetro implícito.

1.  **Obtener las funciones temporales:** Disponer de las soluciones temporales analíticas $x_1(t)$ y $x_2(t)$ calculadas a partir de una condición inicial dada $\mathbf{x}_0 = [x_1(0), x_2(0)]^T$.
2.  **Marcar el punto de equilibrio:** Ubicar el punto crítico $\mathbf{x}_e = (0,0)$ en el plano cartesiano.
3.  **Construir la tabla de valores de estado:** Evaluar $x_1(t)$ y $x_2(t)$ para instantes de tiempo incrementales partiendo desde $t=0$:

| Tiempo ($t$) | Estado $x_1(t)$ | Estado $x_2(t)$ | Coordenada $(x_1, x_2)$ |
| :--- | :--- | :--- | :--- |
| $t = 0$ | $x_1(0)$ | $x_2(0)$ | $(x_1(0), x_2(0))$ (Inicio) |
| $t = t_1$ | $x_1(t_1)$ | $x_2(t_1)$ | $(x_1(t_1), x_2(t_1))$ |
| $t = t_2$ | $x_1(t_2)$ | $x_2(t_2)$ | $(x_1(t_2), x_2(t_2))$ |
| $t \to \infty$ | $\lim_{t\to\infty} x_1(t)$ | $\lim_{t\to\infty} x_2(t)$ | Punto final asintótico |

1.  **Trazar la trayectoria:** Unir secuencialmente los pares ordenados $(x_1, x_2)$ con una curva suave.
2.  **Indicar el sentido temporal:** Añadir flechas sobre la curva orientadas desde $t=0$ hacia $t \to \infty$.
3.  **Dictamen de estabilidad visual:**
    *   *Estable:* Si la trayectoria y las flechas convergen hacia $\mathbf{x}_e = (0,0)$.
    *   *Inestable:* Si la trayectoria y las flechas se alejan de $\mathbf{x}_e$.
