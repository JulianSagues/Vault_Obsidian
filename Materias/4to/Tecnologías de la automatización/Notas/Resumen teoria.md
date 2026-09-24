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
# Análisis de Respuesta Temporal, Polos y Estabilidad (Puntos 2 de Examen)

Resolución analítica en formato general para los tres modelos de examen, desarrollada paso a paso sin saltear etapas algebraicas.

---

## 1. Modelo 1: Selección de Polos en el Plano Complejo y Respuesta Temporal

### Enunciado General
En el plano complejo $s$ se presentan raíces sobre el eje real:
* Semiplano izquierdo (reales negativos): $-a, -b, -c$ (con constantes reales positivas $a, b, c > 0$).
* Eje imaginario (origen): polo en $0$.
* Semiplano derecho (reales positivos): $d, e, f$ (con constantes reales positivas $d, e, f > 0$).

---

### Inciso a: Selección de polos y expresión de $Y(s)$

#### 1. Justificación teórica del polo
* **Condición de estabilidad asintótica:** Todos los polos de la función de transferencia deben poseer parte real estrictamente negativa ($\text{Re}(p_i) < 0$).
* **Selección:** Se escoge un polo ubicado en el semiplano izquierdo (por ejemplo, en $s = -a$, con $a > 0$). Los polos en el origen o en el semiplano derecho ($d, e, f$) se descartan por inducir comportamientos marginalmente estables o divergentes.

#### 2. Definición de la función de transferencia de primer orden
Adoptando ganancia estática unitaria:
$$G(s) = \frac{a}{s + a}$$

#### 3. Salida en el dominio de Laplace ante escalón unitario
* Entrada: $U(s) = \frac{1}{s}$
* Salida:
  $$Y(s) = G(s) \cdot U(s) = \frac{a}{s + a} \cdot \frac{1}{s} = \frac{a}{s(s + a)}$$

---

### Inciso b: Obtención de $y(t)$ y valor final $y(\infty)$

#### 1. Expansión en fracciones simples
$$\frac{a}{s(s + a)} = \frac{A}{s} + \frac{B}{s + a}$$

Cálculo de residuos:
* $A = \lim_{s \to 0} \left[ s \cdot \frac{a}{s(s + a)} \right] = \frac{a}{0 + a} = 1$
* $B = \lim_{s \to -a} \left[ (s + a) \cdot \frac{a}{s(s + a)} \right] = \frac{a}{-a} = -1$

Sustituyendo:
$$Y(s) = \frac{1}{s} - \frac{1}{s + a}$$

#### 2. Antitransformación de Laplace
Aplicando $\mathcal{L}^{-1}$ a cada término:
* $\mathcal{L}^{-1}\left\{\frac{1}{s}\right\} = 1$
* $\mathcal{L}^{-1}\left\{\frac{1}{s + a}\right\} = e^{-at}$

$$\mathbf{y(t) = 1 - e^{-at}} \quad (t \ge 0)$$

#### 3. Cálculo del valor en régimen permanente $y(\infty)$
Evaluando el límite cuando $t \to \infty$:
$$y(\infty) = \lim_{t \to \infty} (1 - e^{-at})$$
Dado que $a > 0$, el exponente tiende a $-\infty$ y la exponencial decae a cero:
$$\mathbf{y(\infty) = 1 - 0 = 1}$$

---

### Inciso c: Conclusiones de estabilidad
1. La respuesta transitoria está gobernada por el modo exponencial $e^{-at}$. Como el polo se ubicó en el semiplano izquierdo ($\text{Re}(s) = -a < 0$), este modo se extingue asintóticamente con el tiempo.
2. Ante una entrada escalón acotada, la salida converge a un valor finito acotado ($y(\infty) = 1$), verificando que el sistema es **asintóticamente estable** y cumple el criterio **BIBO**. Si se hubiese elegido un polo derecho ($+d$), la solución presentaría el término $e^{+dt}$, haciendo divergir la salida al infinito.

---
---

## 2. Modelo 2: Lazo Cerrado con Integrador y Ganancia $K$

### Diagrama en Bloques
* Rama de ida directa: integrador puro $\left[\frac{1}{s}\right]$ en cascada con ganancia $[K]$.
* Rama de realimentación: unitaria negativa directa ($H(s) = 1$).

---

### Paso Previo: Reducción algebraica a lazo cerrado
1. Ganancia directa: $G(s) = \frac{1}{s} \cdot K = \frac{K}{s}$
2. Ganancia de realimentación: $H(s) = 1$
3. Función de transferencia equivalente:
   $$G_{lc}(s) = \frac{Y(s)}{U(s)} = \frac{G(s)}{1 + G(s)H(s)} = \frac{\frac{K}{s}}{1 + \frac{K}{s} \cdot 1} = \frac{\frac{K}{s}}{\frac{s + K}{s}} = \mathbf{\frac{K}{s + K}}$$

---

### Inciso a: Respuesta temporal $y(t)$ ante escalón unitario
1. Entrada: $U(s) = \frac{1}{s}$
2. Salida en Laplace:
   $$Y(s) = \frac{K}{s + K} \cdot \frac{1}{s} = \frac{K}{s(s + K)}$$
3. Descomposición en fracciones simples:
   $$\frac{K}{s(s + K)} = \frac{A}{s} + \frac{B}{s + K}$$
   * $A = \lim_{s \to 0} \left[ \frac{K}{s + K} \right] = \frac{K}{K} = 1$
   * $B = \lim_{s \to -K} \left[ \frac{K}{s} \right] = \frac{K}{-K} = -1$
   $$Y(s) = \frac{1}{s} - \frac{1}{s + K}$$
4. Antitransformando al dominio del tiempo:
   $$\mathbf{y(t) = 1 - e^{-Kt}} \quad (t \ge 0)$$

---

### Inciso b: Determinación del polo, demostración de estabilidad y $y(\infty)$

#### 1. Determinación del polo
El polo del sistema es la raíz de su denominador:
$$s + K = 0 \implies \mathbf{s = -K}$$

#### 2. Demostración analítica de estabilidad
A partir de la solución temporal obtenida:
$$y(t) = 1 - e^{-Kt}$$
* **Caso $K > 0$ (polo en semiplano izquierdo, $s = -K < 0$):**
  El exponente temporal resulta estrictamente negativo. Al evaluar el límite temporal:
  $$\lim_{t \to \infty} e^{-Kt} = 0 \implies \lim_{t \to \infty} y(t) = 1$$
  El término transitorio desaparece y la salida permanece acotada. El sistema es **asintóticamente estable**.
* **Caso $K < 0$ (polo en semiplano derecho, $s = -K > 0$):**
  Definiendo $K = -|K|$, la ecuación resulta $y(t) = 1 - e^{+|K|t}$.
  $$\lim_{t \to \infty} (1 - e^{+|K|t}) = -\infty$$
  La salida diverge y el sistema es **inestable**.
* **Caso $K = 0$ (polo en el origen):**
  Se pierde la acción del lazo cerrado.

* **Conclusión formal:** El polo debe ubicarse en el semiplano izquierdo ($s = -K < 0$), lo que exige la condición obligatoria de diseño:
  $$\mathbf{K > 0}$$

#### 3. Cálculo de la salida final $y(\infty)$
Cumpliéndose la condición de estabilidad ($K > 0$):
$$\mathbf{y(\infty) = \lim_{t \to \infty} (1 - e^{-Kt}) = 1 - 0 = 1}$$

---
---

## 3. Modelo 3: Sistema Sobreamortiguado de Segundo Orden con Entrada Escalón $C$

### Enunciado General
Dada la función de transferencia con polos reales y distintos ($p_1 \neq p_2$):
$$\frac{Y(s)}{U(s)} = \frac{1}{(s + p_1)(s + p_2)}$$

Sujeta a una entrada escalón de amplitud general $C > 0$:
$$U(s) = \frac{C}{s}$$

---

### Inciso a: Obtención analítica de la salida $y(t)$

#### 1. Planteo general en Laplace
$$Y(s) = \frac{1}{(s + p_1)(s + p_2)} \cdot \frac{C}{s} = \frac{C}{s(s + p_1)(s + p_2)}$$

#### 2. Descomposición literal en fracciones simples
Planteamos la suma de términos de primer orden:
$$Y(s) = \frac{A}{s} + \frac{B}{s + p_1} + \frac{D}{s + p_2}$$

Cálculo del coeficiente estacionario $A$:
$$A = \lim_{s \to 0} \left[ s \cdot \frac{C}{s(s + p_1)(s + p_2)} \right] = \frac{C}{(0 + p_1)(0 + p_2)} = \frac{C}{p_1 p_2}$$

Dejamos expresados $B$ y $D$ como los coeficientes asociados a los modos transitorios:
$$B = \lim_{s \to -p_1} \left[ \frac{C}{s(s + p_2)} \right] = \frac{C}{p_1(p_1 - p_2)}$$
$$D = \lim_{s \to -p_2} \left[ \frac{C}{s(s + p_1)} \right] = \frac{C}{p_2(p_2 - p_1)}$$

Sustituyendo en $Y(s)$:
$$Y(s) = \frac{C}{p_1 p_2} \cdot \frac{1}{s} + B \cdot \frac{1}{s + p_1} + D \cdot \frac{1}{s + p_2}$$

#### 3. Antitransformación al dominio del tiempo
Aplicando la transformada inversa de Laplace directa:
$$\mathbf{y(t) = \frac{C}{p_1 p_2} + B\,e^{-p_1 t} + D\,e^{-p_2 t}} \quad (t \ge 0)$$

---

### Inciso b: Análisis de Polos, Régimen Sobreamortiguado y Estado Estacionario

#### 1. Justificación de sistema sobreamortiguado
Un sistema de segundo orden es **sobreamortiguado** cuando sus polos son **reales y distintos** (sin parte imaginaria), garantizando una respuesta temporal puramente exponencial, monótona y sin componentes oscilatorias. Esto se satisface formalmente dado que el denominador presenta la estructura $(s + p_1)(s + p_2)$ con la condición explícita $p_1 \neq p_2$.

#### 2. Condición analítica sobre los polos para asegurar estabilidad
Los polos del sistema corresponden a las raíces del denominador:
$$(s + p_1)(s + p_2) = 0 \implies s_1 = -p_1, \quad s_2 = -p_2$$

Analizando los modos dinámicos en la solución temporal $y(t)$:
* Los términos transitorios son $B\,e^{-p_1 t}$ y $D\,e^{-p_2 t}$.
* Para que el sistema sea asintóticamente estable, ambos términos deben decaer a cero conforme el tiempo tiende a infinito ($t \to \infty$):
  $$\lim_{t \to \infty} e^{-p_1 t} = 0 \iff p_1 > 0$$
  $$\lim_{t \to \infty} e^{-p_2 t} = 0 \iff p_2 > 0$$

* **Conclusión formal:** Los polos $s_1$ y $s_2$ deben ubicarse estrictamente en el **semiplano izquierdo** ($\text{Re}(s) < 0$), lo que exige que los coeficientes satisfagan:
  $$\mathbf{p_1 > 0, \quad p_2 > 0 \quad (con \;\; p_1 \neq p_2)}$$

#### 3. Salida en estado estacionario $y(\infty)$
Bajo la condición de estabilidad demostrada ($p_1 > 0$ y $p_2 > 0$):
$$y(\infty) = \lim_{t \to \infty} y(t) = \lim_{t \to \infty} \left[ \frac{C}{p_1 p_2} + B\,e^{-p_1 t} + D\,e^{-p_2 t} \right]$$

Al tender las exponenciales a cero:
$$\mathbf{y(\infty) = \frac{C}{p_1 p_2}}$$

*(Verificación por Teorema del Valor Final)*:
$$y(\infty) = \lim_{s \to 0} \left[ s \cdot Y(s) \right] = \lim_{s \to 0} \left[ s \cdot \frac{C}{s(s + p_1)(s + p_2)} \right] = \frac{C}{p_1 p_2}$$