---
Categoria:
  - Unidad 1
Parent item:
  - "[[Materias/Probabilidad y Estadística/Estadistica descriptiva\\|Estadistica descriptiva]]"
---
El método de regresión y correlación no me permite determinar la dependencia de las variables

---

### **CORRELACIÓN**

- **¿Qué es?**
    
    Mide **la fuerza y dirección** de la relación entre dos variables.
    

- **Coeficiente de correlación (r):**
    
    Va de -1 a 1.
    

|   |   |
|---|---|
|Valor de **r**|Interpretación|
|r ≈ 1|Correlación perfecta positiva|
|r ≈ -1|Correlación perfecta negativa|
|r ≈ 0|Sin relación lineal|
|r entre 0.7 y 1|Fuerte positiva|
|r entre -0.7 y -1|Fuerte negativa|
|r entre 0.3 y 0.7|Moderada|
|r entre 0 y 0.3|Débil|

- **Fórmula de r (Pearson):**

$$r = \frac{\sum (X_i - \bar{X})(Y_i - \bar{Y})}{\sqrt{\sum (X_i - \bar{X})^2 \sum (Y_i - \bar{Y})^2}}$$

- **No implica causalidad.**
    
    Ej: más helado ≠ más ahogos, pero están correlacionados (por el calor).
    

---

### **REGRESIÓN LINEAL**

- **¿Qué es?**
    
    Sirve para **predecir una variable (Y)** a partir de otra (X), con una recta.
    

- **Ecuación:**

Y=a+bXY = a + bX

Donde:

- **a**: intercepto (valor de Y cuando X = 0)

- **b**: pendiente (cuánto cambia Y si X sube 1)

- **Fórmulas:**

$$b=\frac{\sum (X_i - \bar{X})(Y_i - \bar{Y})}{\sum (X_i - \bar{X})^2}, \quad a = \bar{Y} - b\bar{X}$$

- **Coeficiente de determinación (R²):**

$$R^2 = r^2$$

Indica **qué porcentaje de la variación en Y se explica por X**.

Ej: r=0.8⇒R2=0.64=64%

---

### **RELACIONES ENTRE VARIABLES**

|   |   |   |
|---|---|---|
|Tipo|r|Comportamiento|
|Directa / Positiva|r > 0|X sube → Y sube|
|Inversa / Negativa|r < 0|X sube → Y baja|
|Fuerte||rcorrelacion|
|Débil||r|
|Nula|r ≈ 0|No hay relación lineal|

---

### DIFERENCIAS CLAVE

|   |   |   |
|---|---|---|
||**Correlación**|**Regresión**|
|¿Qué hace?|Mide relación|Predice una variable|
|¿Relación direccional?|No necesariamente|Sí, depende de X → Y|
|¿Fórmula matemática?|Solo un valor (r)|Sí: Y=a+bX|
|¿Causalidad?|No implica|Puede sugerirla (con contexto)|
|Representación|Un solo valor|Una recta|