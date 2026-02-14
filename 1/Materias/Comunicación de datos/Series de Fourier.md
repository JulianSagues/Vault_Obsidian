---
Material de Estudio:
  - "[[6_Serie_de_Fourier_Conceptos.pdf]]"
Categoria:
  - Unidad 1
---
Este estudio es válido para ondas periódicas no senoidales o cosenoidales. Cualquier forma de onda periódica está formada por un componente promedio, valor constante, y una serie de ondas senoidales y cosenoidales relacionadas armónicamente. Una armónica es un múltiplo entero de la frecuencia fundamental. La frecuencia fundamental es la primera armónica.

![[Assets/image 433.png|image 433.png]]

**Simetría de onda.** Dicho en términos sencillos, la simetría de la onda describe la simetría de una forma de onda en el dominio del tiempo, esto es, su posición relativa con respecto a los ejes horizontal (tiempo) y vertical (amplitud).

![[Assets/image 1 26.png|image 1 26.png]]

**Simetría par.** Si una forma de onda periódica de voltaje es simétrica respecto al eje vertical (amplitud) se dice que tiene simetría especular, o de ejes, y se llama función par. Para todas las funciones pares, los coeficientes B de la ecuación de Fourier son cero. Por consiguiente, la señal sólo contiene un componente de cd y los términos cosenoidales.

La suma de una serie de funciones pares es una función par. Las funciones pares satisfacen la condición:

![[Assets/image 2 23.png|image 2 23.png]]

**Simetría impar.** Si una forma periódica de onda de voltaje es simétrica respecto a una línea intermedia entre el eje vertical y el horizontal negativo (es decir, a los ejes en el segundo y cuarto cuadrantes) y pasa por el origen de las coordenadas, se dice que tiene una simetría puntual o que es antisimétrica, y se le llama función impar. Para todas las funciones impares, los coeficientes A de la ecuación de Fourier son cero. Por consiguiente, la señal tan sólo contiene un componente de cd y los términos senoidales (nótese que la misma onda seno es una función impar). A esta forma primero se le debe reflejar en el eje Y y después en el eje X para sobreponerla consigo misma.

![[Assets/image 3 19.png|image 3 19.png]]

**Simetría de media onda**. Si una forma de onda periódica de voltaje es tal que la onda del primer medio ciclo (t = 0 a t = T/2) se repite, pero con signo contrario, durante el segundo medio ciclo (t = T/2 a t = T), se dice que tiene simetría de media onda. Para todas las formas de onda con simetría de media onda, las armónicas pares de la serie, en los términos en seno y en coseno, son cero. Por consiguiente, las funciones de media onda cumplen con la condición:

![[Assets/image 4 15.png|image 4 15.png]]

Los coeficientes A0, B1 a Bn, y A1 a An se pueden evaluar con las siguientes fórmulas integrales :

![[Assets/image 5 9.png|image 5 9.png]]

La solución para la onda cuadrada es:

![[Assets/image 6 8.png|image 6 8.png]]

![[Assets/image 7 7.png|image 7 7.png]]