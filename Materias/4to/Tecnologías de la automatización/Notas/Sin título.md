# Guía Maestra Consolidada: Sistemas Lineales, Variables de Estado, Diagramas de Bloques y Estabilidad
*(Tecnologías para la Automatización - UTN)*

---

## 1. Fundamentos: Representación Interna vs. Externa

Cualquier sistema dinámico lineal e invariante en el tiempo (LTI) se modela mediante dos representaciones matemáticas complementarias[cite: 5, 6]:

### Representación Interna (Variables de Estado)
Describe la memoria física y las dinámicas internas del sistema a través de ecuaciones diferenciales de primer orden acopladas:
$$\begin{cases} \mathbf{\dot{x}}(t) = A\mathbf{x}(t) + B u(t) & \text{(Ecuación de Estado)} \\ y(t) = C\mathbf{x}(t) + D u(t) & \text{(Ecuación de Salida)} \end{cases}$$

#### Dimensiones y Anatomía de Variables (para orden $n$, 1 entrada, 1 salida)
* $\mathbf{x}(t) \in \mathbb{R}^{n \times 1}$ **(Vector de Estado):** Conjunto mínimo de variables internas $(x_1, x_2, \dots, x_n)$ que almacenan la energía del sistema en un instante $t$.
* $\mathbf{\dot{x}}(t) \in \mathbb{R}^{n \times 1}$ **(Vector de Derivadas):** Variación temporal de los estados $(\frac{dx_1}{dt}, \dots, \frac{dx_n}{dt})$.
* $u(t) \in \mathbb{R}$ **(Entrada):** Excitación, fuerza, tensión o señal externa inyectada al sistema.
* $y(t) \in \mathbb{R}$ **(Salida):** Variable física que efectivamente se mide o controla.
* $A \in \mathbb{R}^{n \times n}$ **(Matriz Dinámica del Sistema):** Modela cómo interactúan los estados entre sí en ausencia de estímulos externos. Sus autovalores determinan la estabilidad natural del sistema.
* $B \in \mathbb{R}^{n \times 1}$ **(Matriz de Entrada):** Pondera qué variables de estado son afectadas directamente por $u(t)$.
* $C \in \mathbb{R}^{1 \times n}$ **(Matriz de Salida):** Vector fila que combina linealmente los estados para formar la medición $y(t)$.
* $D \in \mathbb{R}^{1 \times 1}$ **(Matriz de Transmisión Directa):** Acoplamiento directo de $u(t)$ a $y(t)$ sin pasar por los integradores. En sistemas estrictamente propios de orden físico real, $D = 0$[cite: 6].

### Representación Externa (Función de Transferencia)
Relaciona la entrada y la salida en el dominio de Laplace bajo condiciones iniciales nulas ($\mathbf{x}(0) = \mathbf{0}$)[cite: 5]:
$$G(s) = \frac{Y(s)}{U(s)} = \frac{N(s)}{D(s)}$$[cite: 5]
* $N(s) = 0 \implies$ Ceros del sistema[cite: 5].
* $D(s) = 0 \implies$ Polos del sistema y **Ecuación Característica**[cite: 5].

### Nexo Analítico entre Ambas Representaciones
Para pasar de las matrices $(A, B, C, D)$ a la función de transferencia $G(s)$[cite: 6]:
$$G(s) = C(sI - A)^{-1}B + D$$[cite: 6]

---

## 2. Las Tres Formas Canónicas y sus Diagramas de Bloques

Dada una función de transferencia de orden $n$ estrictamente propia[cite: 6]:
$$G(s) = \frac{b_1 s^{n-1} + b_2 s^{n-2} + \dots + b_n}{s^n + a_1 s^{n-1} + a_2 s^{n-2} + \dots + a_n}$$

> **Regla de Normalización:** El coeficiente de la potencia más alta del denominador ($s^n$) debe ser obligatoriamente $1$[cite: 6]. Si tiene un valor multiplicando, se debe dividir todo el numerador y denominador por dicho coeficiente antes de armar las matrices[cite: 6].

---

### A. Forma Canónica Controlable (FCC)
* **Concepto:** Toda la señal de control $u(t)$ entra exclusivamente por la última derivada de estado ($\dot{x}_n$)[cite: 6]. Las demás variables forman una cadena horizontal de integradores en serie[cite: 6].
* **Estructura de Matrices:**
  $$A = \begin{bmatrix} 0 & 1 & 0 & \dots & 0 \\ 0 & 0 & 1 & \dots & 0 \\ \vdots & \vdots & \vdots & \ddots & \vdots \\ -a_n & -a_{n-1} & -a_{n-2} & \dots & -a_1 \end{bmatrix}, \quad B = \begin{bmatrix} 0 \\ 0 \\ \vdots \\ 1 \end{bmatrix}, \quad C = \begin{bmatrix} b_n & b_{n-1} & \dots & b_1 \end{bmatrix}$$[cite: 6]
* **Topología del Diagrama:**

```mermaid
flowchart LR
    U((u)) -->|"+"| SumEntrada((+))
    SumEntrada --> IntN["∫ (xn)"]
    IntN --> IntN1["∫ (xn-1)"]
    IntN1 --> Dots[...]
    Dots --> Int2["∫ (x2)"]
    Int2 --> Int1["∫ (x1)"]

    IntN --> Bn["bn"]
    IntN1 --> Bn1["bn-1"]
    Int2 --> B2["b2"]
    Int1 --> B1["b1"]

    Bn --> SumY((+))
    Bn1 --> SumY
    B2 --> SumY
    B1 --> SumY
    SumY --> Y((y))

    IntN --> An["a1"]
    IntN1 --> An1["a2"]
    Int2 --> A2["an-1"]
    Int1 --> A1["an"]

    A1 --> SumFb((+))
    A2 --> SumFb
    An1 --> SumFb
    An --> SumFb
    SumFb -->|"-"| SumEntrada