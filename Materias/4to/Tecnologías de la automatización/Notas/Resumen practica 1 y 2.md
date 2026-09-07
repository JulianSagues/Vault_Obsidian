# Guía Maestra: Variables de Estado y Sistemas Lineales

---

## 1. Fundamentos: ¿Qué representan las matrices?

Cualquier sistema dinámico lineal e invariante en el tiempo (LTI) se modela mediante dos ecuaciones vectoriales básicas:

$$\begin{cases} 
\dot{\mathbf{x}}(t) = A \mathbf{x}(t) + B u(t) & \text{(Ecuación de Estado)} \\ 
y(t) = C \mathbf{x}(t) + D u(t) & \text{(Ecuación de Salida)} 
\end{cases}$$

### Anatomía de las variables y dimensiones (para orden $n$, 1 entrada, 1 salida)
* **$\mathbf{x}(t) \in \mathbb{R}^{n \times 1}$ (Vector de Estado):** Conjunto mínimo de variables internas ($x_1, x_2, \dots, x_n$) que almacenan la energía o memoria del sistema (tensiones en capacitores, corrientes en inductores, posiciones, velocidades, tanques de líquido). Conocerlas en un instante $t_0$ permite predecir todo el comportamiento futuro.
* **$\dot{\mathbf{x}}(t) \in \mathbb{R}^{n \times 1}$:** Vector de derivadas temporales de los estados ($\frac{dx_1}{dt}, \frac{dx_2}{dt}, \dots$).
* **$u(t) \in \mathbb{R}$ (Señal de Entrada):** La fuerza, tensión o estímulo externo que se inyecta activamente desde afuera.
* **$y(t) \in \mathbb{R}$ (Señal de Salida):** La variable física que realmente medimos con un sensor o nos interesa monitorear.
* **Matriz $A \in \mathbb{R}^{n \times n}$ (Matriz del Sistema / Dinámica):** Modela cómo interactúan y se acoplan los estados internos entre sí en ausencia de fuerzas externas. Sus autovalores definen la estabilidad natural y la velocidad de respuesta del proceso.
* **Matriz $B \in \mathbb{R}^{n \times 1}$ (Matriz de Entrada):** Modela por qué ecuaciones entra la señal externa $u(t)$ y con qué peso o ganancia afecta a cada variable de estado.
* **Matriz $C \in \mathbb{R}^{1 \times n}$ (Matriz de Salida):** Vector fila que combina linealmente los estados internos para conformar lo que ve el sensor a la salida.
* **Matriz $D \in \mathbb{R}^{1 \times 1}$ (Matriz de Transmisión Directa):** Ganancia directa desde la entrada hacia la salida sin pasar por la dinámica interna. En sistemas físicos reales (estrictamente propios) casi siempre es **$D = 0$**, porque ninguna masa o circuito reacciona instantáneamente sin demora física.

---

## 2. Las Cuatro Formas Canónicas (Construcción desde $G(s)$)

Dada una función de transferencia de orden 2 estrictamente propia:
$$G(s) = \frac{Y(s)}{U(s)} = \frac{b_1 s + b_0}{s^2 + a_1 s + a_0}$$

> **Regla de normalización:** El coeficiente de la potencia más alta del denominador ($s^n$) SIEMPRE debe ser $1$. Si tuviera un número multiplicando (ej. $2s^2$), se debe dividir todo el numerador y denominador por ese número antes de empezar.

---

### Forma Canónica Controlable (FCC)
* **Concepto:** Toda la señal de control $u(t)$ entra exclusivamente por la última variable de estado ($\dot{x}_n$). Las demás variables son integradores en cascada ($x_1' = x_2$, $x_2' = x_3$).
* **Estructura de $A$:** Unos en la superdiagonal (desplazamiento a la derecha de la diagonal principal). La última fila contiene los coeficientes del denominador ordenados de menor a mayor potencia y **con el signo invertido**.
* **Estructura de $B$:** Columna con ceros en todas las filas salvo un $1$ en la última.
* **Estructura de $C$:** Fila con los coeficientes del numerador en orden ascendente ($b_0, b_1, \dots$).

$$A = \begin{bmatrix} 0 & 1 \\ -a_0 & -a_1 \end{bmatrix}, \quad B = \begin{bmatrix} 0 \\ 1 \end{bmatrix}, \quad C = \begin{bmatrix} b_0 & b_1 \end{bmatrix}$$

---

### Forma Canónica Observable (FCO)
* **Concepto:** Es la versión geométrica "espejada" (dual traspuesta) de la FCC. La salida $y(t)$ solo mide directamente el último estado ($y = x_n$).
* **Propiedad de construcción:** 
  $$A_{FCO} = A_{FCC}^T, \quad B_{FCO} = C_{FCC}^T, \quad C_{FCO} = B_{FCC}^T$$
* **Estructura:**
  * En $A$, la última columna lleva los coeficientes del denominador cambiados de signo.
  * En $B$, entran los coeficientes del numerador.
  * En $C$, es un vector fila con ceros y un $1$ al final.

$$A = \begin{bmatrix} 0 & -a_0 \\ 1 & -a_1 \end{bmatrix}, \quad B = \begin{bmatrix} b_0 \\ b_1 \end{bmatrix}, \quad C = \begin{bmatrix} 0 & 1 \end{bmatrix}$$

---

### Forma Canónica Diagonal (FCD)
* **Concepto:** Desacopla completamente las variables. Cada ecuación diferencial depende únicamente de su propio estado ($\dot{x}_i = p_i x_i + u$). El sistema equivale a tener subsistemas de primer orden funcionando en paralelo.
* **Condición de uso:** Todos los polos del denominador deben ser **reales y distintos**.

#### Procedimiento paso a paso:
1. Hallar los polos $p_1, p_2$ resolviendo el denominador $s^2 + a_1 s + a_0 = 0$.
2. Descomponer $G(s)$ en fracciones simples:
   $$G(s) = \frac{d_1}{s - p_1} + \frac{d_2}{s - p_2}$$
3. Calcular los residuos $d_i$ con el método de Heaviside (tapar con el dedo el factor correspondiente y evaluar en la raíz).
4. Armar las matrices:
   * **$A$:** Diagonal principal con los polos $p_i$ tal cual son (con su signo real). El resto ceros.
   * **$B$:** Vector columna de unos: $[1 \quad 1 \dots 1]^T$.
   * **$C$:** Vector fila con los residuos $d_i$ en el mismo orden que pusiste los polos en $A$.

$$A = \begin{bmatrix} p_1 & 0 \\ 0 & p_2 \end{bmatrix}, \quad B = \begin{bmatrix} 1 \\ 1 \end{bmatrix}, \quad C = \begin{bmatrix} d_1 & d_2 \end{bmatrix}$$

---

### Forma Canónica de Jordan (FCJ)
* **Concepto:** Aparece cuando hay **polos repetidos (multiplicidad algebraica mayor a 1)**. Como las fracciones simples no se pueden separar en polos aislados, el sistema no se puede diagonalizar por completo; se debe conectar a los polos gemelos mediante una pequeña "cadena" llamada **bloque de Jordan**.

#### Procedimiento paso a paso:
1. Identificar la multiplicidad. Supongamos un polo doble en $p_1$ y un polo simple en $p_2$:
   $$Denominador = (s - p_1)^2 (s - p_2)$$
2. Descomponer abriendo potencias sucesivas:
   $$G(s) = \frac{d_1}{s - p_1} + \frac{d_2}{(s - p_1)^2} + \frac{d_3}{s - p_2}$$
3. Armar las matrices:
   * **$A$:** Colocar los polos en la diagonal principal. En el grupo repetido, colocar un **$1$** inmediatamente por encima de la diagonal (superdiagonal) para encadenar las variables.
   * **$B$:** Para el bloque repetido, **solo la última fila lleva un $1$**; las filas anteriores del bloque llevan **$0$**. Para los polos simples que no se repiten, llevan su $1$ habitual.
   * **$C$:** Vector fila con los numeradores $d_i$ asociados a cada estado.

$$A = \begin{bmatrix} p_1 & \mathbf{1} & 0 \\ 0 & p_1 & 0 \\ 0 & 0 & p_2 \end{bmatrix}, \quad B = \begin{bmatrix} \mathbf{0} \\ \mathbf{1} \\ 1 \end{bmatrix}, \quad C = \begin{bmatrix} d_1 & d_2 & d_3 \end{bmatrix}$$

---

## 3. De Matrices $(A, B, C, D)$ a Función de Transferencia $G(s)$

Dada una cuádrupla cualquiera de matrices numéricas, para extraer la función $G(s)$ analíticamente se aplica:

$$G(s) = C(sI - A)^{-1}B + D$$

### Algoritmo práctico de cálculo manual:
1. **Calcular $(sI - A)$:** A la matriz identidad multiplicada por la variable compleja $s$, restarle la matriz numérica $A$.
   $$sI - A = \begin{bmatrix} s & 0 \\ 0 & s \end{bmatrix} - \begin{bmatrix} a_{11} & a_{12} \\ a_{21} & a_{22} \end{bmatrix} = \begin{bmatrix} s - a_{11} & -a_{12} \\ -a_{21} & s - a_{22} \end{bmatrix}$$

2. **Calcular el determinante $\det(sI - A)$:**
   $$\det(sI - A) = (s - a_{11})(s - a_{22}) - (-a_{12})(-a_{21})$$
   > Este polinomio del denominador es exactamente el **polinomio característico** del sistema; sus raíces son los polos.

3. **Invertir la matriz $(sI - A)$:** Para $2 \times 2$, aplicar la regla clásica: permutar los términos de la diagonal principal, cambiar de signo los otros dos, y dividir por el determinante:
   $$(sI - A)^{-1} = \frac{1}{\det(sI - A)} \begin{bmatrix} s - a_{22} & a_{12} \\ a_{21} & s - a_{11} \end{bmatrix}$$

4. **Multiplicar por $B$ y $C$:**
   * Primero multiplicar la matriz por la columna $B$: $V(s) = (sI - A)^{-1} B$ (da un vector columna).
   * Luego premultiplicar por la fila $C$: $G(s) = C \cdot V(s)$ (da un escalar en función de $s$).
   * Dejar siempre el $\det(sI - A)$ en el denominador común.

---

## 4. Métodos de Resolución Temporal Completa

Resolver el sistema implica encontrar las funciones matemáticas del tiempo continuo $x_1(t), x_2(t)$ e $y(t)$ a partir de:
* Matrices dinámicas $A, B, C$.
* Condiciones iniciales $\mathbf{x}_0 = [x_1(0), x_2(0)]^T$ (energía almacenada en $t=0$).
* Señal de entrada $u(t)$ (estímulo externo para $t \ge 0$).

---

### Método A: Desarmado en Sistema de Ecuaciones Diferenciales (Laplace Escalar)
Se utiliza cuando se prefiere manipular ecuaciones algebraicas escalares en lugar de matrices.

1. **Desdoblar la matriz:** Realizar el producto matricial fila por fila para obtener el sistema de ecuaciones:
   $$\begin{cases} 
   x_1'(t) = a_{11}x_1(t) + a_{12}x_2(t) + b_1 u(t) \\ 
   x_2'(t) = a_{21}x_1(t) + a_{22}x_2(t) + b_2 u(t) 
   \end{cases}$$
   $$y(t) = c_1 x_1(t) + c_2 x_2(t)$$

2. **Aplicar la Transformada de Laplace con condiciones iniciales:**
   Recordar la propiedad de la derivada: $\mathcal{L}\{x'(t)\} = s X(s) - x(0)$.
   $$\begin{cases} 
   s X_1(s) - x_1(0) = a_{11}X_1(s) + a_{12}X_2(s) + b_1 U(s) \\ 
   s X_2(s) - x_2(0) = a_{21}X_1(s) + a_{22}X_2(s) + b_2 U(s) 
   \end{cases}$$

3. **Despejar las funciones en $s$:** Agrupar los términos de $X_1(s)$ y $X_2(s)$ a la izquierda y pasar los valores numéricos $x_i(0)$ y la entrada $U(s)$ a la derecha. Resolver por sustitución o regla de Cramer.

4. **Calcular la salida:** Reemplazar las expresiones obtenidas en la ecuación de salida:
   $$Y(s) = c_1 X_1(s) + c_2 X_2(s)$$

5. **Antitransformar:** Llevar $X_1(s), X_2(s)$ e $Y(s)$ al dominio del tiempo usando fracciones simples y tablas básicas:
   * $\mathcal{L}^{-1}\left\{\frac{1}{s}\right\} = 1(t)$ (Escalón)
   * $\mathcal{L}^{-1}\left\{\frac{1}{s + a}\right\} = e^{-at}$ (Exponencial)

---

### Método B: Resolución Matricial Directa (Fórmula General)
Es el método estándar en ingeniería porque no requiere despejes manuales término a término.

En el dominio de Laplace, el sistema completo se despeja directamente:
$$s \mathbf{X}(s) - \mathbf{x}_0 = A \mathbf{X}(s) + B U(s)$$
$$(sI - A) \mathbf{X}(s) = \mathbf{x}_0 + B U(s)$$
$$\mathbf{X}(s) = \underbrace{(sI - A)^{-1} \mathbf{x}_0}_{\text{Respuesta a Entrada Cero (REC)}} + \underbrace{(sI - A)^{-1} B \, U(s)}_{\text{Respuesta a Estado Cero (RECero)}}$$

Y la salida en el dominio de Laplace:
$$Y(s) = C \mathbf{X}(s) = C(sI - A)^{-1} \mathbf{x}_0 + C(sI - A)^{-1} B \, U(s)$$

#### Diferencia conceptual entre términos:
* **Respuesta a Entrada Cero ($u(t) = 0$):** El sistema se mueve libremente disipando la energía que tenía guardada en sus condiciones iniciales $\mathbf{x}_0$.
* **Respuesta a Estado Cero ($\mathbf{x}_0 = \mathbf{0}$):** El sistema arranca totalmente descargado/en reposo y reacciona únicamente empujado por la señal externa $u(t)$.

---

## 5. Matriz de Transición de Estados ($\Phi(t)$ o $e^{At}$)

La matriz de transición de estados $\Phi(t) \in \mathbb{R}^{n \times n}$ es el operador que traslada el estado del sistema desde el instante inicial $t=0$ hasta cualquier instante futuro $t$, en régimen libre:

$$\mathbf{x}(t) = \Phi(t) \cdot \mathbf{x}_0$$

### Cómo se calcula analíticamente:
$$\Phi(t) = e^{At} = \mathcal{L}^{-1}\left[ (sI - A)^{-1} \right]$$

1. Se obtiene la matriz simbólica $(sI - A)^{-1}$.
2. A cada una de sus posiciones se le aplica descomposición en fracciones simples.
3. Se aplica $\mathcal{L}^{-1}$ celda por celda usando la tabla $\frac{1}{s+a} \to e^{-at}$.
4. El resultado final es una matriz de funciones temporales.

### Propiedades fundamentales (Verificación en parciales):
1. **Condición de identidad inicial:** Al evaluar el tiempo en cero, la matriz debe dar obligatoriamente la matriz identidad:
   $$\Phi(0) = e^{A \cdot 0} = I$$
   *(Si al reemplazar $t=0$ no te da unos en la diagonal y ceros afuera, alguna cuenta de fracciones simples quedó mal).*
2. **Propiedad de grupo / Composición temporal:**
   $$\Phi(t_2 - t_0) = \Phi(t_2 - t_1) \cdot \Phi(t_1 - t_0)$$
3. **Matriz inversa:** La transición hacia el pasado es la inversa:
   $$\Phi(-t) = [\Phi(t)]^{-1} = e^{-At}$$

---

## 6. Transformación de Similitud (Cambio de Base)

Un mismo circuito o planta física puede ser descripto por infinitos sistemas de variables de estado distintos (por ejemplo, midiendo corrientes de malla en lugar de voltajes de nodo). La transformación de similitud permite cambiar la base matemática sin alterar la física del sistema.

Se define un cambio de coordenadas lineal:
$$\mathbf{x}(t) = T \mathbf{z}(t) \quad \iff \quad \mathbf{z}(t) = T^{-1} \mathbf{x}(t)$$

Donde:
* $\mathbf{x}(t)$ es el vector de estados antiguo.
* $\mathbf{z}(t)$ es el nuevo vector de estados.
* $T$ es una matriz de transformación cuadrada ($n \times n$) no singular ($\det(T) \neq 0$).

### Deducción de las nuevas matrices $(\tilde{A}, \tilde{B}, \tilde{C}, \tilde{D})$:
1. Reemplazando $\mathbf{x} = T\mathbf{z}$ en la ecuación de estados:
   $$T \dot{\mathbf{z}}(t) = A (T \mathbf{z}(t)) + B u(t)$$
   Multiplicando ambos miembros por $T^{-1}$ a izquierda:
   $$\dot{\mathbf{z}}(t) = (T^{-1} A T) \mathbf{z}(t) + (T^{-1} B) u(t)$$

2. Reemplazando en la ecuación de salida:
   $$y(t) = C (T \mathbf{z}(t)) + D u(t) = (C T) \mathbf{z}(t) + D u(t)$$

### Fórmulas directas de transformación:
$$\tilde{A} = T^{-1} A T$$
$$\tilde{B} = T^{-1} B$$
$$\tilde{C} = C T$$
$$\tilde{D} = D$$

### Invariantes del sistema (Propiedades que se conservan)
Bajo cualquier cambio de base $T$:
1. **La Función de Transferencia es idéntica:**
   $$\tilde{G}(s) = \tilde{C}(sI - \tilde{A})^{-1}\tilde{B} + \tilde{D} = C(sI - A)^{-1}B + D = G(s)$$
   *(La relación entrada/salida externa es independiente de la base elegida).*
2. **El polinomio característico y autovalores son los mismos:**
   $$\det(sI - \tilde{A}) = \det(sI - A)$$
   Los polos del sistema no cambian de lugar.
3. **La estabilidad se mantiene:** Si el sistema original era asintóticamente estable, el transformado también lo es.

---

## 7. Tabla Resumen de Fórmulas y Procedimientos

| Objetivo | Fórmula / Procedimiento Clave | Resultado Obtenido |
| :--- | :--- | :--- |
| **Modelar en FCC** | Denominador cambiado de signo en última fila de $A$; $B = [0 \dots 1]^T$; $C = [b_0 \dots b_n]$ | Matrices $A, B, C$ |
| **Modelar en FCO** | Traspuesta de FCC: $A_{FCO} = A_{FCC}^T$, $B_{FCO} = C_{FCC}^T$, $C_{FCO} = B_{FCC}^T$ | Matrices $A, B, C$ |
| **Modelar en FCD** | Polos en diagonal de $A$; $B = [1 \dots 1]^T$; $C = [d_1 \dots d_n]$ (residuos) | Matrices $A, B, C$ |
| **Modelar en FCJ** | Bloques de Jordan en $A$ con $1$ arriba; $B$ con $1$ solo al final del bloque | Matrices $A, B, C$ |
| **Hallar $G(s)$** | $G(s) = C(sI - A)^{-1}B + D$ | Cociente de polinomios |
| **Polinomio Característico** | $P(s) = \det(sI - A) = 0$ | Raíces = Polos del sistema |
| **Transición de Estados** | $\Phi(t) = \mathcal{L}^{-1}\left[ (sI - A)^{-1} \right]$, verificar que $\Phi(0) = I$ | Matriz de exponenciales |
| **Evolución Libre ($u=0$)** | $\mathbf{x}(t) = \Phi(t) \cdot \mathbf{x}_0$ | Vector de funciones temporales |
| **Respuesta Completa** | $\mathbf{X}(s) = (sI - A)^{-1}\mathbf{x}_0 + (sI - A)^{-1}B U(s)$ | Estados en Laplace |
| **Cambio de Base ($T$)** | $\tilde{A} = T^{-1}AT, \quad \tilde{B} = T^{-1}B, \quad \tilde{C} = CT$ | Sistema equivalente $(\tilde{A}, \tilde{B}, \tilde{C})$ |