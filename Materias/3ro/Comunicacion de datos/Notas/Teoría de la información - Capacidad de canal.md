---
Material de Estudio:
  - "[[Assets/2_Teora_de_Informacin_-_Capacidad_de_Canal.pdf|2_Teora_de_Informacin_-_Capacidad_de_Canal.pdf]]"
Categoria:
  - Unidad 2
---
### Ancho de banda “B”

- Es una característica importante del canal de comunicación, ya que determina la capacidad del canal, para la transferencia de información dentro de una gama de frecuencias .

- Estará limitado por un rango de frecuencias, en el cual se determina el canal de comunicación.

- También podemos decir que nuestro B es la porción del espectro de frecuencia en el cual se dimensiona el canal de comunicaciones.

- El ancho de banda está determinado por dos frecuencias externas, denominadas frecuencias límites. Una es 𝒇𝟏 frecuencia límite inferior y 𝒇𝟐 frecuencia límite superior. La diferencia entre ambas es B:

$B=f1-f2 [Hertz]$

![[Assets/image 45.png|image 45.png]]

### Capacidad de Canal – Límite de la velocidad de datos

Cuando realizamos transmisión de datos sobre una canal de comunicación, se requiere de algunos parámetros para determinar cuál es su velocidad límite:

- Ancho de Banda.

- Cantidad de niveles de señal, M.

- Nivel de ruido. Relación señal/ruido “S/N”

Vamos a considerar dos opciones posibles, en cuanto a las condiciones del canal de comunicación:

- Canal Sin Ruido – Capacidad de Canal de Nyquist

- Canal Con Ruido – Capacidad de Canal de Shannon

Ambos casos se tendrán en cuenta en función de Anchos de Banda comparables.

### Capacidad de Canal de Nyquist

El teorema de Nyquist establece que la velocidad máxima de transmisión de datos en bps viene limitada por la siguiente expresión:

$C=2 B.log_2M$

Donde:

- C: Capacidad de canal en bps.

- B: Ancho de Banda en Hertz

- M: Número de niveles posibles de la señal. Es decir, corresponde al número de señales diferentes que sale de un modulador digital. Es decir la cantidad de símbolos del mismo.

**Caso Binario :**

En este caso tan solo se emplean dos niveles de señal, o dos símbolos, teniendo en cuenta que:

$M=2^N$

Donde 𝑁 es la cantidad de bits, en este caso 𝑀 = 2, entonces 𝑁 = 1, de esta forma:

$C=2B$

Donde:

- C: Capacidad de canal en bps.

- B: Ancho de Banda en Hertz

**Caso Multinivel:**

Este caso es utilizado cuando las señales tienen más de 2 niveles

$M=2^N$

$C=2B.log_2M$

Donde 𝑁 es la cantidad de bits, en este caso 𝑀 > 2, entonces 𝑁 > 1, de esta forma:

Donde:

- C: Capacidad de canal en bps.

- B: Ancho de Banda en Hertz

- M: Cantidad de niveles, señales o símbolos

Para aumentar la capacidad de canal se deben incrementar la cantidad niveles de tensión (señales) o símbolos del modulador, M.

Por lo que el receptor debe ser capaz de diferenciar estos niveles de tensión en la señal recibida, lo cual es dificultado por el ruido. Además, cuanto mayor es la velocidad de transmisión, mayor es el daño que puede ocasionar el ruido.

De esta forma vemos que la expresión de Nyquits no representa los efectos causados por el ruido, en un canal de comunicaciones real.

### Teorema de Shannon

En la siguiente imagen se muestra la representación del propio Shannon de dicho sistema general de comunicaciones.

![[Assets/image 1 21.png|image 1 21.png]]

$C= B .log_2(1+s/n)$

- C: es la velocidad máxima en bits por segundo.

- B: es el ancho de banda en Hz.

- s/n es la relación señal a ruido (signal/noise), sin unidades (adimensional)

> [!important]
> 
> Para cualquier sistema de comunicación con un determinado ancho de banda “B” y con una relación dada de señal/ruido (S/N), Shannon limita la velocidad máxima en bps que se puede tener en el canal de comunicación, sea cual sea la técnica de transmisión utilizada.

![[Assets/image 2 20.png|image 2 20.png]]

### Comparación Teorema de Shannon con Nyquist

Comparando la capacidad del canal de Shannon con la tasa de información de Nyquist, podemos encontrar el número eficaz de los niveles distinguibles o estados de modulación M.

![[Assets/image 3 16.png|image 3 16.png]]

Determina que modulador se debe usar