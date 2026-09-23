![[Parcial 2025.png]]
# Procedimiento General: De Función de Transferencia a Forma Canónica Controlable (FCC) y Diagrama de Bloques

Este método sirve para deducir analíticamente las matrices de estado y el diagrama de bloques para cualquier sistema lineal de orden 2 expresado como función de transferencia o diagrama de bloques en serie[cite: 1, 2].

---

## 1. Deducción Analítica del Sistema de Estados (Punto 1a)

### Paso 1: Separar la variable intermedia
Cuando el sistema viene en serie con una ganancia o bloque a la salida, se separa la relación en la variable auxiliar intermedia $V(s)$ y la salida final $Y(s)$[cite: 2]:
* Bloque dinámico[cite: 2]:
  $$\frac{V(s)}{U(s)} = \frac{1}{s^2 + a_1 s + a_0}$$
* Bloque de salida[cite: 2]:
  $$Y(s) = c \cdot V(s)$$

### Paso 2: Pasar al dominio del tiempo (Ecuación Diferencial)
1. Se multiplica cruzado el denominador del bloque dinámico[cite: 2]:
   $$(s^2 + a_1 s + a_0) V(s) = U(s) \implies s^2 V(s) + a_1 s V(s) + a_0 V(s) = U(s)$$
2. Se aplica la propiedad de Laplace ($s^k V(s) \iff \frac{d^k v}{dt^k}$)[cite: 1, 2]:
   $$\ddot{v}(t) + a_1 \dot{v}(t) + a_0 v(t) = u(t)$$
3. Se despeja la derivada de mayor orden ($\ddot{v}(t)$):
   $$\ddot{v}(t) = -a_0 v(t) - a_1 \dot{v}(t) + u(t)$$

### Paso 3: Definición de variables de estado ($x_i$)
En la Forma Canónica Controlable (FCC), el sistema no admite derivadas de segundo orden en el vector de estados[cite: 1, 2]. Se asignan variables escalares en cadena:
* $x_1(t) \triangleq v(t)$ (señal base sin derivar)
* $x_2(t) \triangleq \dot{v}(t) = \dot{x}_1(t)$ (primera derivada)

### Paso 4: Armado de las ecuaciones de estado y salida
Se calcula la derivada temporal de cada variable definida:
* **Para $x_1$:** $\dot{x}_1(t) = \dot{v}(t) = x_2(t)$
* **Para $x_2$:** $\dot{x}_2(t) = \ddot{v}(t) = -a_0 x_1(t) - a_1 x_2(t) + u(t)$
* **Para la salida $y(t)$:** $y(t) = c \cdot v(t) = c \cdot x_1(t)$[cite: 2]

### Paso 5: Estructuración matricial final
Se agrupan los coeficientes en el formato canónico $\mathbf{\dot{x}} = A\mathbf{x} + B u$ e $y = C\mathbf{x} + D u$[cite: 1]:
$$ \begin{bmatrix} \dot{x}_1(t) \\ \dot{x}_2(t) \end{bmatrix} = \begin{bmatrix} 0 & 1 \\ -a_0 & -a_1 \end{bmatrix} \begin{bmatrix} x_1(t) \\ x_2(t) \end{bmatrix} + \begin{bmatrix} 0 \\ 1 \end{bmatrix} u(t) $$
$$ y(t) = \begin{bmatrix} c & 0 \end{bmatrix} \begin{bmatrix} x_1(t) \\ x_2(t) \end{bmatrix} + [0] u(t) $$

---

## 2. Construcción del Diagrama de Bloques (Punto 1b)

A partir de las ecuaciones de estado obtenidas, el diagrama se construye mediante integradores en cascada[cite: 2]:

1. **Cadena de integradores:**
   Como el sistema es de segundo orden ($n=2$), se dibujan dos bloques integradores $\left[\frac{1}{s}\right]$ conectados en serie[cite: 2]:
   $$\dot{x}_2(t) \longrightarrow \left[ \frac{1}{s} \right] \xrightarrow{x_2(t)} \left[ \frac{1}{s} \right] \longrightarrow x_1(t)$$
   * La entrada al primer integrador es la derivada más alta: $\dot{x}_2(t)$.
   * La salida del primer integrador es $x_2(t)$.
   * La salida del segundo integrador es $x_1(t)$.

2. **Nodo sumador de entrada ($\dot{x}_2$):**
   A la entrada del primer integrador se ubica un sumador que reconstruye la ecuación $\dot{x}_2 = u - a_1 x_2 - a_0 x_1$:
   * Flecha entrante con la señal externa $u(t)$ con signo $(+)$.
   * Realimentación tomada desde $x_2(t)$, que pasa por un bloque de ganancia $a_1$ y entra con signo $(-)$.
   * Realimentación tomada desde $x_1(t)$, que pasa por un bloque de ganancia $a_0$ y entra con signo $(-)$.

3. **Rama de salida ($y(t)$):**
   * Desde la salida del segundo integrador ($x_1(t)$), se extrae una derivación hacia un bloque con ganancia $c$, cuya salida final es $y(t) = c \cdot x_1(t)$[cite: 2].