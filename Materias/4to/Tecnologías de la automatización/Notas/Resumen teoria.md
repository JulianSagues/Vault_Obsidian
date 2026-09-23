# Deducción Detallada de Realizaciones en Variables de Estado (FCC, FCO, FCD)

Guía analítica exhaustiva paso a paso, con todas las operaciones algebraicas intermedias explícitas, para pasar de una Función de Transferencia a las tres representaciones canónicas del Espacio de Estados.

---

## 0. Modelo Base de Trabajo

Trabajamos sobre la siguiente función de transferencia de segundo orden estrictamente propia:

$$G(s) = \frac{Y(s)}{U(s)} = \frac{2s + 5}{s^2 + 5s + 6}$$

### Elementos identificados por simple inspección
* **Polinomio del numerador:** $N(s) = 2s + 5 \implies b_1 = 2, \quad b_0 = 5$
* **Polinomio del denominador:** $D(s) = s^2 + 5s + 6 \implies a_1 = 5, \quad a_0 = 6$
* **Cálculo explícito de polos:**
  $$s^2 + 5s + 6 = 0 \implies s = \frac{-5 \pm \sqrt{5^2 - 4(1)(6)}}{2(1)} = \frac{-5 \pm \sqrt{1}}{2}$$
  $$p_1 = \frac{-5 + 1}{2} = -2, \qquad p_2 = \frac{-5 - 1}{2} = -3$$

---

## 1. Forma Canónica Controlable (FCC)

### Justificación de la estructura
La FCC modela el sistema físico mediante una **cadena de integradores en serie (cascada)**. Para no mezclar las derivadas de la entrada $u(t)$ con los estados, la transferencia se descompone en dos bloques en serie:
1. Un bloque con toda la dinámica (polos) que genera una variable interna $V(s)$.
2. Un bloque de salida que aplica los coeficientes del numerador sobre $V(s)$ y sus derivadas.

```text
U(s) ---> [  1 / (s² + 5s + 6)  ] ---> V(s) ---> [ 2s + 5 ] ---> Y(s)