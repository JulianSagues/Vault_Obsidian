---
Categoria:
  - Unidad 3
---
Las señales analógicas pueden convertirse en digitales, y viceversa. Venimos analizando las bondades de las señales digitales, en cuanto a la conveniencia para la transmisión de las mismas a través de todo tipo de medio de comunicación de datos.

Para convertir una señal analógica en digital, se utiliza un dispositivo llamado conversor Analógico / Digital (o conversor A/D).

### Modulación por codificación de pulsos(PCM)

Una de las técnicas más habituales para cambiar una señal analógica a digital es la que se denomina Modulación por Codificación de Pulsos (PCM). El codificador PCM tiene tres procesos:

1. Se Muestrea la señal analógica.

1. Se Cuantifica la señal muestreada.

1. Los valores cuantificados son Codificados como flujos de bits

![[Assets/image 436.png|image 436.png]]

![[Assets/image 1 29.png|image 1 29.png]]

### Muestreo

En esta etapa la señal analógica es muestreada cada Ts, donde Ts es el intervalo de muestreo o período de muestreo. La inversa de este es la frecuencia o tasa de muestreo fs.

Esta fs (frecuencia de muestreo) lo define el Teorema de Nyquist. Este teorema nos dice que para muestrear y luego reproducir la señal analógica original, es necesario que la tasa de muestreo sea al menos el doble de la frecuencia más alta de la señal original.

![[Assets/image 2 26.png|image 2 26.png]]

Conclusión del teorema de Nyquist, también denominado teorema del muestreo:

- En primer lugar nos establece que la señal a muestrear debe estar en una banda finita. Es decir debemos poder identificar una 𝑓𝑚𝑎𝑥 de valor finito.

- La frecuencia de muestreo 𝑓𝑠 , debe ser al menos 2 veces la  
    frecuencia más alta contenida en la señal a muestrear, 𝑓𝑚𝑎𝑥. De esta manera la señal muestreada contiene toda la información de la señal original.

![[Assets/image 3 22.png|image 3 22.png]]

![[Assets/image 4 18.png|image 4 18.png]]

Recuperación de una señal sinusoidal muestreada con diferentes tasas de muestreo.

![[Assets/image 5 11.png|image 5 11.png]]

### Cuantificación

![[Assets/image 6 10.png|image 6 10.png]]

![[Assets/image 7 9.png|image 7 9.png]]

Error de cuantificación:

![[Assets/image 8 7.png|image 8 7.png]]

### Codificación

La codificación es la última etapa en PCM. Luego de que la muestra ha sido cuantificada, y se ha decidido el número de bits a utilizar por muestra, a cada muestra se le asigna una palabra de un código de “n bits”.

![[Assets/image 9 6.png|image 9 6.png]]