# Cheat Sheet: MATLAB para Tecnologías para la Automatización (Guías 1 a 4)

## 1. Entorno, Limpieza y Gráficos
- `clear all`: Borra todas las variables del Workspace en memoria.
- `clc`: Limpia la pantalla de la consola (Command Window).
- `close all`: Cierra todas las ventanas de figuras abiertas.
- `figure`: Abre una ventana nueva para graficar.
- `hold on` / `hold off`: Permite superponer múltiples gráficos en los mismos ejes.
- `grid on`: Activa la cuadrícula en el gráfico actual.
- `xlabel('...')` / `ylabel('...')` / `title('...')`: Agrega etiquetas a los ejes y título al gráfico.

---

## 2. Álgebra de Polinomios
- `conv(p1, p2)`: Multiplica dos polinomios representados por sus vectores de coeficientes.
- `deconv(p1, p2)`: Realiza la división polinomial (cociente y residuo).
- `poly(r)`: Genera el polinomio característico a partir de un vector con sus raíces o de una matriz cuadrada.
- `roots(p)`: Calcula las raíces de un polinomio (usado para obtener polos/ceros a mano).

---

## 3. Modelado y Conversiones (Espacio de Estados y Laplace)
- `s = tf('s')`: Define la variable simbólica/objeto de Laplace para escribir funciones de transferencia algebraicamente.
- `sys = tf(num, den)`: Construye un modelo de Función de Transferencia a partir de los vectores de coeficientes.
- `sys = ss(A, B, C, D)`: Construye un modelo en Espacio de Estados a partir de sus cuatro matrices.
- `[num, den] = ss2tf(A, B, C, D)`: Transforma la representación en Espacio de Estados a Función de Transferencia.
- `[A, B, C, D] = tf2ss(num, den)`: Transforma una Función de Transferencia a Espacio de Estados (Forma Canónica).
- `sys_mod = canon(sys, 'modal')`: Transforma el modelo a la Forma Canónica Diagonal (FCD / Modal).
- `sys_fcc = canon(sys, 'companion')`: Transforma el modelo a la Forma Canónica de Control (FCC).
- `[r, p, k] = residue(num, den)`: Descompone el cociente polinomial en fracciones parciales (residuos, polos y ganancia directa).
- `[num, den] = residue(r, p, k)`: Reconstruye la función de transferencia a partir de sus fracciones parciales.

---

## 4. Diagramas de Bloques y Reducción
- `feedback(G, H)`: Calcula el lazo cerrado equivalente con realimentación negativa: `G / (1 + G*H)`.
- `feedback(G, 1)`: Lazo cerrado con realimentación unitaria negativa: `G / (1 + G)`.
- `feedback(G, H, +1)`: Lazo cerrado con realimentación positiva: `G / (1 - G*H)`.
- `series(G1, G2)` (o `G1 * G2`): Conexión de bloques en serie / cascada.
- `parallel(G1, G2)` (o `G1 + G2`): Conexión de bloques en paralelo.
- `minreal(sys)`: Simplifica cancelando polos y ceros redundantes para obtener la realización mínima.

---

## 5. Análisis Temporal y Respuesta Transitoria/Permanente
- `step(sys)`: Grafica la respuesta temporal del sistema frente a una entrada escalón unitario.
- `[y, t] = step(sys)`: Devuelve los vectores numéricos de salida y tiempo de la respuesta al escalón (sin graficar).
- `stepinfo(sys)`: Calcula las métricas del transitorio (tiempo de establecimiento, sobrepico, tiempo de subida, etc.).
- `impulse(sys)`: Grafica la respuesta temporal a una entrada impulso unitario.
- `initial(sys, x0)`: Grafica la respuesta libre del sistema a partir del vector de condiciones iniciales `x0`.
- `lsim(sys, u, t)`: Simula la respuesta temporal ante una entrada arbitraria `u` (rampa `u=t`, parábola `u=t.^2`, etc.) evaluada en el vector temporal `t`.
- `dcgain(sys)`: Calcula la ganancia en estado estacionario (límite cuando $s \to 0$), útil para constantes de error estático ($K_p$, $K_v$, $K_a$).

---

## 6. Polos, Ceros y Estabilidad
- `pole(sys)`: Extrae los polos del sistema.
- `zero(sys)`: Extrae los ceros del sistema.
- `eig(A)`: Calcula los autovalores de la matriz de estados $A$ (coincidentes con los polos).
- `pzmap(sys)`: Dibuja el mapa de polos (`x`) y ceros (`o`) en el plano complejo $s$.
- `isstable(sys)`: Comprueba si el sistema es estable; devuelve `1` (estable) o `0` (inestable).
- `damp(sys)`: Muestra en consola una tabla con polos, coeficiente de amortiguamiento ($\xi$) y frecuencia natural ($\omega_n$).

---

## 7. Plano de Fase y Métodos Numéricos (ODE)
- `[t, x] = ode45(f, tspan, x0)`: Resuelve numéricamente el sistema continuo $\dot{x} = f(t,x)$ mediante Runge-Kutta.
  - `f = @(t, x) [f1(x); f2(x)]`: Función anónima con las ecuaciones de estado en vector columna.
  - `tspan = [t0 tf]`: Rango de integración temporal.
  - `x0 = [x1_0; x2_0]`: Vector columna con las condiciones iniciales.
- `plot(x(:,1), x(:,2))`: Grafica la trayectoria paramétrica en el plano de fase ($x_1$ vs $x_2$).
- `[X1, X2] = meshgrid(rango1, rango2)`: Crea una grilla bidimensional de coordenadas para evaluar las derivadas.
- `quiver(X1, X2, dX1, dX2)`: Traza el campo vectorial de direcciones con flechas sobre el plano de fase.