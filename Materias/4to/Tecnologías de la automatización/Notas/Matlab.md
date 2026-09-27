# Cheat Sheet: MATLAB para Tecnologías para la Automatización (Guías 1 a 4)

## 1. Entorno, Limpieza y Gráficos
- `clear all`: Borra todas las variables del Workspace en memoria[cite: 1].
- `clc`: Limpia la pantalla de la consola (Command Window)[cite: 1].
- `close all`: Cierra todas las ventanas de figuras abiertas.
- `figure`: Abre una ventana nueva para graficar.
- `hold on` / `hold off`: Permite superponer múltiples gráficos en los mismos ejes.
- `grid on`: Activa la cuadrícula en el gráfico actual.
- `xlabel('...')` / `ylabel('...')` / `title('...')`: Agrega etiquetas a los ejes y título al gráfico[cite: 4].

---

## 2. Álgebra de Polinomios
- `conv(p1, p2)`: Multiplica dos polinomios representados por sus vectores de coeficientes.
- `deconv(p1, p2)`: Realiza la división polinomial (cociente y residuo).
- `poly(r)`: Genera el polinomio característico a partir de un vector con sus raíces o de una matriz cuadrada.
- `roots(p)`: Calcula las raíces de un polinomio (usado para obtener polos/ceros a mano)[cite: 2].

---

## 3. Modelado y Conversiones (Espacio de Estados y Laplace)
- `s = tf('s')`: Define la variable simbólica/objeto de Laplace para escribir funciones de transferencia algebraicamente[cite: 2].
- `sys = tf(num, den)`: Construye un modelo de Función de Transferencia a partir de los vectores de coeficientes[cite: 1, 2].
- `sys = ss(A, B, C, D)`: Construye un modelo en Espacio de Estados a partir de sus cuatro matrices[cite: 1, 2].
- `[num, den] = ss2tf(A, B, C, D)`: Transforma la representación en Espacio de Estados a Función de Transferencia[cite: 1, 2].
- `[A, B, C, D] = tf2ss(num, den)`: Transforma una Función de Transferencia a Espacio de Estados (Forma Canónica)[cite: 1, 2].
- `sys_mod = canon(sys, 'modal')`: Transforma el modelo a la Forma Canónica Diagonal (FCD / Modal)[cite: 2].
- `sys_fcc = canon(sys, 'companion')`: Transforma el modelo a la Forma Canónica de Control (FCC)[cite: 2].
- `[r, p, k] = residue(num, den)`: Descompone el cociente polinomial en fracciones parciales (residuos, polos y ganancia directa)[cite: 1, 2].
- `[num, den] = residue(r, p, k)`: Reconstruye la función de transferencia a partir de sus fracciones parciales[cite: 1, 2].

---

## 4. Diagramas de Bloques y Reducción
- `feedback(G, H)`: Calcula el lazo cerrado equivalente con realimentación negativa: `G / (1 + G*H)`[cite: 3].
- `feedback(G, 1)`: Lazo cerrado con realimentación unitaria negativa: `G / (1 + G)`[cite: 3, 4].
- `feedback(G, H, +1)`: Lazo cerrado con realimentación positiva: `G / (1 - G*H)`[cite: 3].
- `series(G1, G2)` (o `G1 * G2`): Conexión de bloques en serie / cascada[cite: 3].
- `parallel(G1, G2)` (o `G1 + G2`): Conexión de bloques en paralelo[cite: 3].
- `minreal(sys)`: Simplifica cancelando polos y ceros redundantes para obtener la realización mínima[cite: 3].

---

## 5. Análisis Temporal y Respuesta Transitoria/Permanente
- `step(sys)`: Grafica la respuesta temporal del sistema frente a una entrada escalón unitario[cite: 4].
- `[y, t] = step(sys)`: Devuelve los vectores numéricos de salida y tiempo de la respuesta al escalón (sin graficar).
- `stepinfo(sys)`: Calcula las métricas del transitorio (tiempo de establecimiento, sobrepico, tiempo de subida, etc.).
- `impulse(sys)`: Grafica la respuesta temporal a una entrada impulso unitario[cite: 1, 4].
- `initial(sys, x0)`: Grafica la respuesta libre del sistema a partir del vector de condiciones iniciales `x0`[cite: 1].
- `lsim(sys, u, t)`: Simula la respuesta temporal ante una entrada arbitraria `u` (rampa `u=t`, parábola `u=t.^2`, etc.) evaluada en el vector temporal `t`[cite: 4].
- `dcgain(sys)`: Calcula la ganancia en estado estacionario (límite cuando $s \to 0$), útil para constantes de error estático ($K_p$, $K_v$, $K_a$)[cite: 4].

---

## 6. Polos, Ceros y Estabilidad
- `pole(sys)`: Extrae los polos del sistema[cite: 2].
- `zero(sys)`: Extrae los ceros del sistema.
- `eig(A)`: Calcula los autovalores de la matriz de estados $A$ (coincidentes con los polos)[cite: 2, 4].
- `pzmap(sys)`: Dibuja el mapa de polos (`x`) y ceros (`o`) en el plano complejo $s$[cite: 2, 4].
- `isstable(sys)`: Comprueba si el sistema es estable; devuelve `1` (estable) o `0` (inestable)[cite: 2, 4].
- `damp(sys)`: Muestra en consola una tabla con polos, coeficiente de amortiguamiento ($\xi$) y frecuencia natural ($\omega_n$)[cite: 4].

---

## 7. Plano de Fase y Métodos Numéricos (ODE)
- `[t, x] = ode45(f, tspan, x0)`: Resuelve numéricamente el sistema continuo $\dot{x} = f(t,x)$ mediante Runge-Kutta[cite: 1, 4].
  - `f = @(t, x) [f1(x); f2(x)]`: Función anónima con las ecuaciones de estado en vector columna[cite: 1, 4].
  - `tspan = [t0 tf]`: Rango de integración temporal[cite: 4].
  - `x0 = [x1_0; x2_0]`: Vector columna con las condiciones iniciales[cite: 1, 4].
- `plot(x(:,1), x(:,2))`: Grafica la trayectoria paramétrica en el plano de fase ($x_1$ vs $x_2$)[cite: 4].
- `[X1, X2] = meshgrid(rango1, rango2)`: Crea una grilla bidimensional de coordenadas para evaluar las derivadas[cite: 4].
- `quiver(X1, X2, dX1, dX2)`: Traza el campo vectorial de direcciones con flechas sobre el plano de fase[cite: 4].