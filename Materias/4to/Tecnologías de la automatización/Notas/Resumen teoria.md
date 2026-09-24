# Realizaciones Canónicas en Formato General (FCC, FCO, FCD, FCJ)

Función de transferencia general de segundo orden estrictamente propia:

$$G(s) = \frac{Y(s)}{U(s)} = \frac{b_1 s + b_0}{s^2 + a_1 s + a_0}$$

---

## 1. Forma Canónica Controlable (FCC)

### Justificación
La FCC descompone el sistema en dos etapas en cascada: primero se procesa la dinámica del denominador generando una variable interna $V(s)$, y luego se aplica el numerador sobre dicha variable y sus derivadas para construir la salida $Y(s)$.

### Paso 1: Introducir la variable intermedia $V(s)$
$$Y(s) = (b_1 s + b_0) \cdot \underbrace{\left[ \frac{1}{s^2 + a_1 s + a_0} U(s) \right]}_{V(s)}$$

Se obtienen dos ecuaciones:
1. Dinámica interna: $(s^2 + a_1 s + a_0) V(s) = U(s)$
2. Salida: $Y(s) = (b_1 s + b_0) V(s) = b_1 s V(s) + b_0 V(s)$

### Paso 2: Pasaje al dominio del tiempo
Distribuyendo en la dinámica interna:
$$s^2 V(s) + a_1 s V(s) + a_0 V(s) = U(s)$$

Aplicando Transformada Inversa de Laplace con condiciones iniciales nulas:
$$\ddot{v}(t) + a_1 \dot{v}(t) + a_0 v(t) = u(t)$$

Despejando la derivada de mayor orden:
$$\ddot{v}(t) = -a_0 v(t) - a_1 \dot{v}(t) + u(t)$$

### Paso 3: Definición de variables de estado (en cadena)
* $x_1(t) \triangleq v(t)$
* $x_2(t) \triangleq \dot{v}(t)$

### Paso 4: Derivadas de los estados
* $\dot{x}_1(t) = \dot{v}(t) = x_2(t) \implies \mathbf{\dot{x}_1 = 0 \cdot x_1 + 1 \cdot x_2 + 0 \cdot u}$
* $\dot{x}_2(t) = \ddot{v}(t) = -a_0 v(t) - a_1 \dot{v}(t) + u(t) \implies \mathbf{\dot{x}_2 = -a_0 x_1 - a_1 x_2 + 1 \cdot u}$

### Paso 5: Ecuación de salida temporal
Antitransformando la ecuación de salida:
$$y(t) = b_0 v(t) + b_1 \dot{v}(t) \implies \mathbf{y = b_0 x_1 + b_1 x_2 + 0 \cdot u}$$

### Paso 6: Estructuración matricial final (FCC)
$$\begin{bmatrix} \dot{x}_1 \\ \dot{x}_2 \end{bmatrix} = \begin{bmatrix} 0 & 1 \\ -a_0 & -a_1 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} + \begin{bmatrix} 0 \\ 1 \end{bmatrix} u$$

$$y = \begin{bmatrix} b_0 & b_1 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} + [0] u$$

---

## 2. Forma Canónica Observable (FCO)

### Justificación
Estructura dual de la FCC basada en el método de desanidado de integradores: se divide por potencias decrecientes de $s$ para aislar integradores $\frac{1}{s}$ sucesivos acoplados a la salida.

### Paso 1: Multiplicar cruzado entrada y salida
$$(s^2 + a_1 s + a_0) Y(s) = (b_1 s + b_0) U(s)$$
$$s^2 Y(s) + a_1 s Y(s) + a_0 Y(s) = b_1 s U(s) + b_0 U(s)$$

### Paso 2: Despejar $s^2 Y(s)$ y agrupar por potencias de $s$
$$s^2 Y(s) = s [b_1 U(s) - a_1 Y(s)] + [b_0 U(s) - a_0 Y(s)]$$

Dividiendo todo por $s^2$:
$$Y(s) = \frac{1}{s} [b_1 U(s) - a_1 Y(s)] + \frac{1}{s^2} [b_0 U(s) - a_0 Y(s)]$$

Factorizando un $\frac{1}{s}$ global:
$$Y(s) = \frac{1}{s} \left( [b_1 U(s) - a_1 Y(s)] + \frac{1}{s}[b_0 U(s) - a_0 Y(s)] \right)$$

### Paso 3: Definición de estados (de adentro hacia afuera)
* $X_1(s) \triangleq \frac{1}{s} [b_0 U(s) - a_0 Y(s)]$
* $X_2(s) \triangleq \frac{1}{s} [X_1(s) - a_1 Y(s) + b_1 U(s)]$
* Salida directa del corchete exterior: $\mathbf{Y(s) = X_2(s) \implies y(t) = x_2(t)}$

### Paso 4: Despeje temporal de las derivadas
* Para $X_1(s)$:
  $$s X_1(s) = -a_0 Y(s) + b_0 U(s) \implies \mathbf{\dot{x}_1 = 0 \cdot x_1 - a_0 x_2 + b_0 u}$$
* Para $X_2(s)$:
  $$s X_2(s) = X_1(s) - a_1 Y(s) + b_1 U(s) \implies \mathbf{\dot{x}_2 = 1 \cdot x_1 - a_1 x_2 + b_1 u}$$

### Paso 5: Estructuración matricial final (FCO)
$$\begin{bmatrix} \dot{x}_1 \\ \dot{x}_2 \end{bmatrix} = \begin{bmatrix} 0 & -a_0 \\ 1 & -a_1 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} + \begin{bmatrix} b_0 \\ b_1 \end{bmatrix} u$$

$$y = \begin{bmatrix} 0 & 1 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} + [0] u$$

---

## 3. Forma Canónica Diagonal (FCD) - Polos Simples

Aplica cuando el sistema posee polos reales y distintos ($p_1 \neq p_2$):
$$G(s) = \frac{Y(s)}{U(s)} = \frac{b_1 s + b_0}{(s - p_1)(s - p_2)}$$

### Paso 1: Expansión en fracciones simples
$$\frac{Y(s)}{U(s)} = \frac{c_1}{s - p_1} + \frac{c_2}{s - p_2}$$

Donde $c_1$ y $c_2$ son los residuos de Heaviside:
* $c_1 = \left. (s - p_1) G(s) \right|_{s = p_1} = \frac{b_1 p_1 + b_0}{p_1 - p_2}$
* $c_2 = \left. (s - p_2) G(s) \right|_{s = p_2} = \frac{b_1 p_2 + b_0}{p_2 - p_1}$

### Paso 2: Distribuir la entrada $U(s)$
$$Y(s) = c_1 \cdot \left[ \frac{1}{s - p_1} U(s) \right] + c_2 \cdot \left[ \frac{1}{s - p_2} U(s) \right]$$

### Paso 3: Definición de variables de estado
Cada estado se define a la salida del polo aislado correspondiente:
* $X_1(s) \triangleq \frac{1}{s - p_1} U(s)$
* $X_2(s) \triangleq \frac{1}{s - p_2} U(s)$

### Paso 4: Despeje temporal de las derivadas
* Para $X_1(s)$:
  $$(s - p_1) X_1(s) = U(s) \implies s X_1 - p_1 X_1 = U \implies \mathbf{\dot{x}_1 = p_1 x_1 + 0 \cdot x_2 + 1 \cdot u}$$
* Para $X_2(s)$:
  $$(s - p_2) X_2(s) = U(s) \implies s X_2 - p_2 X_2 = U \implies \mathbf{\dot{x}_2 = 0 \cdot x_1 + p_2 x_2 + 1 \cdot u}$$

### Paso 5: Ecuación de salida temporal
$$Y(s) = c_1 X_1(s) + c_2 X_2(s) \implies \mathbf{y = c_1 x_1 + c_2 x_2 + 0 \cdot u}$$

### Paso 6: Estructuración matricial final (FCD)
$$\begin{bmatrix} \dot{x}_1 \\ \dot{x}_2 \end{bmatrix} = \begin{bmatrix} p_1 & 0 \\ 0 & p_2 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} + \begin{bmatrix} 1 \\ 1 \end{bmatrix} u$$

$$y = \begin{bmatrix} c_1 & c_2 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} + [0] u$$

*(Si los factores en el denominador vienen dados como $(s + a)(s + b)$, los polos sobre la diagonal principal resultan $-a$ y $-b$)*.

---

## 4. Forma Canónica de Jordan (FCJ) - Polos Repetidos

Aplica a funciones de transferencia con raíz de multiplicidad 2 (polo doble en $s = -a$):
$$\frac{Y(s)}{U(s)} = \frac{N(s)}{(s + a)^2}$$

### Paso 1: Expansión en fracciones simples para polos múltiples
$$\frac{Y(s)}{U(s)} = \frac{d_1}{(s + a)^2} + \frac{d_2}{s + a}$$

Donde $d_1$ y $d_2$ representan los residuos calculados analíticamente sobre el polinomio $N(s)$:
* $d_1 = \left. (s + a)^2 \frac{N(s)}{(s + a)^2} \right|_{s = -a} = N(-a)$
* $d_2 = \left. \frac{d}{ds} \left[ (s + a)^2 \frac{N(s)}{(s + a)^2} \right] \right|_{s = -a} = N'(-a)$

### Paso 2: Distribuir la entrada $U(s)$
$$Y(s) = d_1 \cdot \left[ \frac{1}{(s + a)^2} U(s) \right] + d_2 \cdot \left[ \frac{1}{s + a} U(s) \right]$$

El término de segundo orden equivale al encadenamiento en serie de dos etapas de primer orden idénticas:
$$\frac{1}{(s + a)^2} U(s) = \frac{1}{s + a} \cdot \left[ \frac{1}{s + a} U(s) \right]$$

### Paso 3: Definición de variables de estado (Bloque de Jordan)
* $X_2(s)$ recibe la entrada externa $U(s)$ de forma directa:
  $$X_2(s) \triangleq \frac{1}{s + a} U(s)$$
* $X_1(s)$ recibe la señal generada por $X_2(s)$ en cascada:
  $$X_1(s) \triangleq \frac{1}{s + a} X_2(s)$$

### Paso 4: Despeje temporal de las derivadas
* Para $X_1(s)$:
  $$(s + a) X_1(s) = X_2(s) \implies s X_1 + a X_1 = X_2 \implies \mathbf{\dot{x}_1 = -a x_1 + 1 \cdot x_2 + 0 \cdot u}$$
* Para $X_2(s)$:
  $$(s + a) X_2(s) = U(s) \implies s X_2 + a X_2 = U \implies \mathbf{\dot{x}_2 = 0 \cdot x_1 - a x_2 + 1 \cdot u}$$

### Paso 5: Ecuación de salida temporal
$$Y(s) = d_1 X_1(s) + d_2 X_2(s) \implies \mathbf{y = d_1 x_1 + d_2 x_2 + 0 \cdot u}$$

### Paso 6: Estructuración matricial final (FCJ)
$$\begin{bmatrix} \dot{x}_1 \\ \dot{x}_2 \end{bmatrix} = \begin{bmatrix} -a & 1 \\ 0 & -a \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} + \begin{bmatrix} 0 \\ 1 \end{bmatrix} u$$

$$y = \begin{bmatrix} d_1 & d_2 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} + [0] u$$

---

## 5. Cuadro Comparativo Estructural

| Característica         | Controlable (FCC)                                    | Observable (FCO)                                     | Diagonal (FCD)                                     | Jordan (FCJ)                                     |
| :--------------------- | :--------------------------------------------------- | :--------------------------------------------------- | :------------------------------------------------- | :----------------------------------------------- |
| **Condición de polos** | General                                              | General                                              | Reales distintos ($p_1 \neq p_2$)                  | Reales repetidos ($p_1 = p_2 = -a$)              |
| **Matriz $A$**         | $\begin{bmatrix} 0 & 1 \\ -a_0 & -a_1 \end{bmatrix}$ | $\begin{bmatrix} 0 & -a_0 \\ 1 & -a_1 \end{bmatrix}$ | $\begin{bmatrix} p_1 & 0 \\ 0 & p_2 \end{bmatrix}$ | $\begin{bmatrix} -a & 1 \\ 0 & -a \end{bmatrix}$ |
| **Matriz $B$**         | $\begin{bmatrix} 0 \\ 1 \end{bmatrix}$               | $\begin{bmatrix} b_0 \\ b_1 \end{bmatrix}$           | $\begin{bmatrix} 1 \\ 1 \end{bmatrix}$             | $\begin{bmatrix} 0 \\ 1 \end{bmatrix}$           |
| **Matriz $C$**         | $\begin{bmatrix} b_0 & b_1 \end{bmatrix}$            | $\begin{bmatrix} 0 & 1 \end{bmatrix}$                | $\begin{bmatrix} c_1 & c_2 \end{bmatrix}$          | $\begin{bmatrix} d_1 & d_2 \end{bmatrix}$        |

---
# Ejercicio 2 (Modelo 1): Análisis Completo del Plano Complejo

---

## 1. Enunciado Base
En el plano complejo $s$ se identifican polos potenciales sobre el eje real:
* Semiplano izquierdo (reales negativos): $-a, -b, -c$ (con constantes $a, b, c > 0$).
* Eje imaginario (origen): polo en $s = 0$.
* Semiplano derecho (reales positivos): $+d, +e, +f$ (con constantes $d, e, f > 0$).

Entrada de prueba: Función escalón unitario $u(t) = 1(t) \iff U(s) = \frac{1}{s}$.

---

## 2. Caso A: Selección en el Semiplano Izquierdo (Sistema Estable)

### Selección del polo
Se elige un polo sobre el eje real negativo: $s = -p$ (por ejemplo, $s = -a$, con $a > 0$).

### Función de Transferencia $G(s)$
Adoptando ganancia estática unitaria para la forma canónica:
$$G(s) = \frac{a}{s + a}$$

### Cálculo de la salida $Y(s)$
$$Y(s) = G(s) \cdot U(s) = \frac{a}{s + a} \cdot \frac{1}{s} = \frac{a}{s(s + a)}$$

### Expansión en fracciones simples y residuos
$$\frac{a}{s(s + a)} = \frac{A}{s} + \frac{B}{s + a}$$
* $A = \lim_{s \to 0} \left[ s \cdot \frac{a}{s(s + a)} \right] = \frac{a}{0 + a} = 1$
* $B = \lim_{s \to -a} \left[ (s + a) \cdot \frac{a}{s(s + a)} \right] = \frac{a}{-a} = -1$

$$Y(s) = \frac{1}{s} - \frac{1}{s + a}$$

### Respuesta temporal $y(t)$
Aplicando Transformada Inversa de Laplace ($\mathcal{L}^{-1}$):
$$y(t) = 1 - e^{-at} \quad (t \ge 0)$$

### Análisis de estabilidad y valor en régimen permanente $y(\infty)$
* **Modo dinámico:** El término transitorio es $e^{-at}$. Como $a > 0$, el exponente es negativo y tiende asintóticamente a cero:
  $$\lim_{t \to \infty} e^{-at} = 0$$
* **Estabilidad:** El sistema es **asintóticamente estable** y cumple el criterio **BIBO** (salida acotada ante entrada acotada).
* **Salida estacionaria:**
  $$y(\infty) = \lim_{t \to \infty} (1 - e^{-at}) = 1 - 0 = 1$$

---

## 3. Caso B: Selección sobre el Eje Imaginario / Origen (Marginalmente Estable)

### Selección del polo
Se elige el polo ubicado en el origen: $s = 0$.

### Función de Transferencia $G(s)$
El sistema degenera en un integrador puro:
$$G(s) = \frac{1}{s}$$

### Cálculo de la salida $Y(s)$
$$Y(s) = G(s) \cdot U(s) = \frac{1}{s} \cdot \frac{1}{s} = \frac{1}{s^2}$$

### Respuesta temporal $y(t)$
Aplicando Transformada Inversa de Laplace:
$$y(t) = t \quad (t \ge 0)$$

### Análisis de estabilidad y valor en régimen permanente $y(\infty)$
* **Modo dinámico:** La salida es una rampa lineal que crece indefinidamente con el tiempo.
* **Estabilidad:** Para entrada escalón, la salida no permanece acotada. El sistema es **inestable en sentido BIBO** ante esta entrada (el polo de la planta en el origen coincide con el polo de la señal de entrada, generando un polo doble en $s=0$).
* **Salida estacionaria:**
  $$y(\infty) = \lim_{t \to \infty} (t) = +\infty \quad \text{(No acotada)}$$

---

## 4. Caso C: Selección en el Semiplano Derecho (Sistema Inestable)

### Selección del polo
Se elige un polo sobre el eje real positivo: $s = +p$ (por ejemplo, $s = +d$, con $d > 0$).

### Función de Transferencia $G(s)$
$$G(s) = \frac{d}{s - d}$$

### Cálculo de la salida $Y(s)$
$$Y(s) = G(s) \cdot U(s) = \frac{d}{s - d} \cdot \frac{1}{s} = \frac{d}{s(s - d)}$$

### Expansión en fracciones simples y residuos
$$\frac{d}{s(s - d)} = \frac{A}{s} + \frac{B}{s - d}$$
* $A = \lim_{s \to 0} \left[ s \cdot \frac{d}{s(s - d)} \right] = \frac{d}{0 - d} = -1$
* $B = \lim_{s \to d} \left[ (s - d) \cdot \frac{d}{s(s - d)} \right] = \frac{d}{d} = 1$

$$Y(s) = -\frac{1}{s} + \frac{1}{s - d}$$

### Respuesta temporal $y(t)$
Aplicando Transformada Inversa de Laplace:
$$y(t) = -1 + e^{+dt} \quad (t \ge 0)$$

### Análisis de estabilidad y valor en régimen permanente $y(\infty)$
* **Modo dinámico:** El término $e^{+dt}$ posee exponente positivo. Conforme $t$ avanza, la función exponencial diverge:
  $$\lim_{t \to \infty} e^{+dt} = +\infty$$
* **Estabilidad:** El sistema es **inestable**. Una entrada acotada genera una salida no acotada.
* **Salida estacionaria:**
  $$y(\infty) = \lim_{t \to \infty} (-1 + e^{+dt}) = +\infty \quad \text{(Divergente)}$$

---

## 5. Tabla Resumen del Ejercicio del Plano Complejo

| Ubicación del Polo      | Polo $s_1$         | Respuesta Temporal $y(t)$ | Valor Final $y(\infty)$ | Condición de Estabilidad            |
| :---------------------- | :----------------- | :------------------------ | :---------------------- | :---------------------------------- |
| **Semiplano Izquierdo** | $s = -a$ ($a > 0$) | $1 - e^{-at}$             | $1$                     | Asintóticamente estable (BIBO)      |
| **Origen**              | $s = 0$            | $t$ (rampa)               | $+\infty$               | Inestable ante escalón              |
| **Semiplano Derecho**   | $s = +d$ ($d > 0$) | $-1 + e^{+dt}$            | $+\infty$               | Inestable (divergencia exponencial) |

---
# Ejercicio 2 (Modelo 2): Análisis Completo del Lazo Cerrado con Ganancia K

---

## 1. Topología del Diagrama en Bloques
* **Trayectoria directa:** Integrador puro $\left[\frac{1}{s}\right]$ en cascada con bloque de ganancia ajustable $[K]$.
* **Trayectoria de realimentación:** Lazo unitario negativo directo ($H(s) = 1$).
* **Entrada:** Escalón unitario $u(t) = 1(t) \iff U(s) = \frac{1}{s}$.

---

## 2. Reducción Analítica a Lazo Cerrado
1. Ganancia directa de la trayectoria de ida:
   $$G(s) = \frac{1}{s} \cdot K = \frac{K}{s}$$
2. Función de transferencia a lazo cerrado:
   $$G_{lc}(s) = \frac{Y(s)}{U(s)} = \frac{G(s)}{1 + G(s)H(s)} = \frac{\frac{K}{s}}{1 + \frac{K}{s} \cdot 1}$$
3. Resolviendo algebraicamente el cociente:
   $$G_{lc}(s) = \frac{\frac{K}{s}}{\frac{s + K}{s}} = \mathbf{\frac{K}{s + K}}$$

### Determinación del Polo a Lazo Cerrado
El polo del sistema es la raíz del polinomio del denominador:
$$s + K = 0 \implies \mathbf{s = -K}$$

El valor y signo del parámetro de ganancia $K$ determinan la posición del polo en el plano $s$ y su régimen dinámico.

---

## 3. Caso A: Ganancia Positiva ($K > 0$) - Régimen Estable

### Ubicación del Polo
Al ser $K > 0$, el polo se sitúa sobre el eje real negativo (semiplano izquierdo):
$$s = -K < 0$$

### Salida en Laplace $Y(s)$
$$Y(s) = G_{lc}(s) \cdot U(s) = \frac{K}{s + K} \cdot \frac{1}{s} = \frac{K}{s(s + K)}$$

### Expansión en fracciones simples y residuos
$$\frac{K}{s(s + K)} = \frac{A}{s} + \frac{B}{s + K}$$
* Coeficiente $A$:
  $$A = \lim_{s \to 0} \left[ s \cdot \frac{K}{s(s + K)} \right] = \frac{K}{0 + K} = 1$$
* Coeficiente $B$:
  $$B = \lim_{s \to -K} \left[ (s + K) \cdot \frac{K}{s(s + K)} \right] = \frac{K}{-K} = -1$$

$$Y(s) = \frac{1}{s} - \frac{1}{s + K}$$

### Respuesta temporal $y(t)$
Aplicando Transformada Inversa de Laplace ($\mathcal{L}^{-1}$):
$$y(t) = 1 - e^{-Kt} \quad (t \ge 0)$$

### Estabilidad y valor en régimen permanente $y(\infty)$
* **Comportamiento dinámico:** El término transitorio es $e^{-Kt}$. Dado que $K > 0$, el exponente es estrictamente negativo y decrece asintóticamente hacia cero:
  $$\lim_{t \to \infty} e^{-Kt} = 0$$
* **Estabilidad:** El sistema es **asintóticamente estable** y satisface el criterio **BIBO** (salida acotada ante entrada escalón acotada).
* **Salida estacionaria:**
  $$y(\infty) = \lim_{t \to \infty} (1 - e^{-Kt}) = 1 - 0 = 1$$

---

## 4. Caso B: Ganancia Nula ($K = 0$) - Polo en el Origen

### Ubicación del Polo
$$K = 0 \implies s = 0$$

### Función de Transferencia y Salida en Laplace
Con $K = 0$, la ganancia de lazo directo es nula ($G(s) = 0$):
$$G_{lc}(s) = 0 \implies Y(s) = 0 \cdot \frac{1}{s} = 0$$
$$y(t) = 0 \quad (t \ge 0)$$

*(En caso de considerar la apertura del lazo antes del integrador sin realimentación, el sistema actuaría como integrador puro $\frac{1}{s}$, produciendo ante un escalón $Y(s) = \frac{1}{s^2} \implies y(t) = t$, lo que generaría una rampa no acotada).*

* **Estabilidad:** Sistema nulo o **marginalmente inestable ante escalón**.

---

## 5. Caso C: Ganancia Negativa ($K < 0$) - Régimen Inestable

### Ubicación del Polo
Definiendo $K = -|K|$ con $|K| > 0$, el polo queda ubicado en el semiplano derecho:
$$s = -K = -(-|K|) = +|K| > 0$$

### Salida en Laplace $Y(s)$
$$Y(s) = \frac{-|K|}{s(s - |K|)}$$

### Expansión en fracciones simples
$$\frac{-|K|}{s(s - |K|)} = \frac{A}{s} + \frac{B}{s - |K|}$$
* Coeficiente $A$:
  $$A = \lim_{s \to 0} \left[ \frac{-|K|}{s - |K|} \right] = \frac{-|K|}{-|K|} = 1$$
* Coeficiente $B$:
  $$B = \lim_{s \to |K|} \left[ \frac{-|K|}{s} \right] = \frac{-|K|}{|K|} = -1$$

$$Y(s) = \frac{1}{s} - \frac{1}{s - |K|}$$

### Respuesta temporal $y(t)$
Aplicando Transformada Inversa de Laplace:
$$y(t) = 1 - e^{+|K|t} \quad (t \ge 0)$$

### Estabilidad y valor en régimen permanente $y(\infty)$
* **Comportamiento dinámico:** El término $e^{+|K|t}$ posee exponente positivo. Conforme $t \to \infty$, dicho término crece de forma exponencial sin límite:
  $$\lim_{t \to \infty} e^{+|K|t} = +\infty$$
* **Estabilidad:** El sistema es **inestable**. Una entrada acotada produce una salida divergente.
* **Salida estacionaria:**
  $$y(\infty) = \lim_{t \to \infty} (1 - e^{+|K|t}) = -\infty \quad \text{(Divergente)}$$

---

## 6. Cuadro Resumen del Lazo Cerrado con Ganancia K

| Condición de $K$ | Posición del Polo | Respuesta Temporal $y(t)$ | Salida Estacionaria $y(\infty)$ | Clasificación de Estabilidad |
| :--- | :--- | :--- | :--- | :--- |
| **$K > 0$** | $s = -K < 0$ (Semiplano Izquierdo) | $1 - e^{-Kt}$ | $1$ | Asintóticamente estable (BIBO) |
| **$K = 0$** | $s = 0$ (Eje imaginario / Origen) | $0$ (o rampa $t$ a lazo abierto) | $0$ (o $+\infty$) | Lazo inoperativo / Marginal |
| **$K < 0$** | $s = +\|K\| > 0$ (Semiplano Derecho) | $1 - e^{+\|K\|t}$ | $-\infty$ | Inestable (divergencia exponencial) |

---
# Ejercicio 2 (Modelo 3): Análisis Completo del Sistema de 2do Orden (Todos los Regímenes)

---

## 1. Enunciado Base y Función General

Función de transferencia de segundo orden sujeta a una entrada escalón de amplitud general $C > 0$ ($U(s) = \frac{C}{s}$)[cite: 1]:

$$G(s) = \frac{Y(s)}{U(s)} = \frac{1}{s^2 + a_1 s + a_0} = \frac{\omega_n^2}{s^2 + 2\zeta\omega_n s + \omega_n^2}$$

Salida en el dominio de Laplace:
$$Y(s) = G(s) \cdot \frac{C}{s} = \frac{C\,\omega_n^2}{s(s^2 + 2\zeta\omega_n s + \omega_n^2)}$$

Las raíces del polinomio característico (polos del sistema) son:
$$s_{1,2} = -\zeta\omega_n \pm \omega_n\sqrt{\zeta^2 - 1}$$

---

## 2. Caso A: Sobreamortiguado Estable ($\zeta > 1$ o $p_1 \neq p_2 > 0$)[cite: 1]

### Naturaleza de los Polos
Discriminante $\zeta^2 - 1 > 0$. Dos raíces reales, distintas y ubicadas en el semiplano izquierdo[cite: 1]:
$$s_1 = -p_1, \quad s_2 = -p_2 \quad (p_1 > 0, \; p_2 > 0, \; p_1 \neq p_2)$$[cite: 1]

La función queda factorizada como en el examen[cite: 1]:
$$G(s) = \frac{1}{(s + p_1)(s + p_2)} \implies Y(s) = \frac{C}{s(s + p_1)(s + p_2)}$$[cite: 1]

### Fracciones Simples y Salida Temporal $y(t)$
$$Y(s) = \frac{A}{s} + \frac{B}{s + p_1} + \frac{D}{s + p_2}$$
* Coeficiente estacionario $A$:
  $$A = \lim_{s \to 0} \left[ s \cdot \frac{C}{s(s + p_1)(s + p_2)} \right] = \frac{C}{p_1 p_2}$$
* Coeficientes transitorios:
  $$B = \frac{C}{p_1(p_1 - p_2)}, \qquad D = \frac{C}{p_2(p_2 - p_1)}$$

Antitransformando mediante Laplace:
$$\mathbf{y(t) = \frac{C}{p_1 p_2} + B\,e^{-p_1 t} + D\,e^{-p_2 t}} \quad (t \ge 0)$$

### Estabilidad y Salida Estacionaria
* **Modo dinámico:** Suma de dos exponenciales puramente decrecientes sin oscilaciones.
* **Estabilidad:** Como $p_1 > 0$ y $p_2 > 0$, $\lim_{t \to \infty} e^{-p_1 t} = 0$ y $\lim_{t \to \infty} e^{-p_2 t} = 0$. El sistema es **asintóticamente estable**[cite: 1].
* **Salida estacionaria:**
  $$\mathbf{y(\infty) = \lim_{t \to \infty} y(t) = \frac{C}{p_1 p_2}}$$

---

## 3. Caso B: Críticamente Amortiguado ($\zeta = 1$ o $p_1 = p_2 = \omega_n > 0$)

### Naturaleza de los Polos
Discriminante $\zeta^2 - 1 = 0$. Dos raíces reales e idénticas (polo doble negativo en el semiplano izquierdo)[cite: 1]:
$$s_1 = s_2 = -\omega_n$$

$$Y(s) = \frac{C\,\omega_n^2}{s(s + \omega_n)^2} = \frac{A}{s} + \frac{B}{s + \omega_n} + \frac{D}{(s + \omega_n)^2}$$
Con residuos: $A = C, \quad B = -C, \quad D = -C\,\omega_n$.

### Respuesta Temporal $y(t)$
Antitransformando mediante Laplace:
$$\mathbf{y(t) = C\left[1 - e^{-\omega_n t}(1 + \omega_n t)\right]} \quad (t \ge 0)$$

### Estabilidad y Salida Estacionaria
* **Modo dinámico:** Respuesta aperiódica monótona (la más rápida sin presentar sobrepico).
* **Estabilidad:** Como $\omega_n > 0$, tanto $e^{-\omega_n t}$ como la rampa amortiguada $t\,e^{-\omega_n t}$ tienden a cero. El sistema es **asintóticamente estable**.
* **Salida estacionaria:**
  $$\mathbf{y(\infty) = C(1 - 0) = C}$$

---

## 4. Caso C: Subamortiguado ($0 < \zeta < 1$)

### Naturaleza de los Polos
Discriminante $\zeta^2 - 1 < 0$. Dos raíces complejas conjugadas con parte real negativa:
$$s_{1,2} = -\zeta\omega_n \pm j\omega_d = -\sigma \pm j\omega_d$$
Donde $\sigma = \zeta\omega_n > 0$ es la atenuación y $\omega_d = \omega_n\sqrt{1 - \zeta^2}$ es la frecuencia amortiguada.

### Respuesta Temporal $y(t)$
Completando cuadrados y antitransformando por Laplace:
$$\mathbf{y(t) = C\left[ 1 - \frac{e^{-\zeta\omega_n t}}{\sqrt{1 - \zeta^2}}\sin(\omega_d t + \phi) \right]} \quad (t \ge 0)$$
Con $\phi = \arccos(\zeta)$.

### Estabilidad y Salida Estacionaria
* **Modo dinámico:** Oscilaciones sinusoidales contenidas dentro de una envolvente exponencial decreciente $\pm \frac{C}{\sqrt{1 - \zeta^2}} e^{-\zeta\omega_n t}$.
* **Estabilidad:** Como $\zeta\omega_n > 0$, la envolvente decae a cero. El sistema es **asintóticamente estable**.
* **Salida estacionaria:**
  $$\mathbf{y(\infty) = C(1 - 0) = C}$$

---

## 5. Caso D: No Amortiguado / Oscilatorio Puro ($\zeta = 0$)

### Naturaleza de los Polos
Polos imaginarios puros sobre el eje vertical ($s_{1,2} = \pm j\omega_n$):
$$Y(s) = \frac{C\,\omega_n^2}{s(s^2 + \omega_n^2)} = \frac{C}{s} - C\,\frac{s}{s^2 + \omega_n^2}$$

### Respuesta Temporal $y(t)$
$$\mathbf{y(t) = C\left[1 - \cos(\omega_n t)\right]} \quad (t \ge 0)$$

### Estabilidad y Salida Estacionaria
* **Modo dinámico:** Oscilación armónica sostenida permanente de frecuencia $\omega_n$ entre $0$ y $2C$.
* **Estabilidad:** **Marginalmente estable** (la salida es acotada pero no converge a un valor constante).
* **Salida estacionaria:**
  $$\mathbf{y(\infty) \quad \text{No existe (oscilación continua)}}$$

---

## 6. Caso E: Regímenes Inestables ($\zeta < 0$ o polos con parte real positiva)

### 1. Oscilatorio Inestable (Subamortiguado Inestable, $-1 < \zeta < 0$)
* **Polos:** Complejos conjugados en el semiplano derecho ($\text{Re}(s) = +|\zeta|\omega_n > 0$).
* **Respuesta Temporal:**
  $$y(t) = C\left[ 1 - \frac{e^{+|\zeta|\omega_n t}}{\sqrt{1 - \zeta^2}}\sin(\omega_d t + \phi) \right]$$
* **Estabilidad:** La envolvente crece exponencialmente al infinito, provocando oscilaciones de amplitud divergente. **Inestable**.
* **Salida estacionaria:** $y(\infty) \to \pm\infty$.

### 2. Aperiódico Inestable (Sobreamortiguado Inestable, $\zeta \le -1$ o $p_1 < 0$)
* **Polos:** Raíces reales con al menos un polo positivo en el semiplano derecho ($s_1 = -p_1 > 0 \implies p_1 < 0$).
* **Respuesta Temporal:**
  $$y(t) = \frac{C}{p_1 p_2} + B\,e^{+|p_1|t} + D\,e^{-p_2 t}$$
* **Estabilidad:** El término $e^{+|p_1|t}$ diverge monótonamente al infinito conforme $t \to \infty$. **Inestable**.
* **Salida estacionaria:** $y(\infty) \to \pm\infty$.

---

## 7. Tabla Comparativa Resumen

| Régimen | Condición de Parámetros | Ubicación de Polos | Forma de $y(t)$ | $y(\infty)$ | Estabilidad |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Sobreamortiguado**[cite: 1] | $\zeta > 1$ ($p_1 \neq p_2 > 0$)[cite: 1] | Reales distintos en semiplano izquierdo[cite: 1] | Exponenciales puras decrecientes[cite: 1] | $\frac{C}{p_1 p_2}$[cite: 1] | Asintóticamente estable |
| **Críticamente amortiguado** | $\zeta = 1$ ($p_1 = p_2 = \omega_n > 0$) | Real doble en semiplano izquierdo | Exponencial y rampa atenuada | $C$ | Asintóticamente estable |
| **Subamortiguado** | $0 < \zeta < 1$ | Complejos conjugados con $\text{Re}(s) < 0$ | Senoide amortiguada con envolvente decreciente | $C$ | Asintóticamente estable |
| **No amortiguado** | $\zeta = 0$ | Imaginarios puros ($s = \pm j\omega_n$) | Cosenoide pura sostenida | No existe | Marginalmente estable |
| **Inestable oscilatorio** | $-1 < \zeta < 0$ | Complejos conjugados con $\text{Re}(s) > 0$ | Senoide con envolvente exponencial creciente | $\pm\infty$ | Inestable |
| **Inestable aperiódico** | $\zeta \le -1$ (o $p_1 < 0$) | Reales con al menos una raíz positiva | Exponencial creciente al infinito | $\pm\infty$ | Inestable |