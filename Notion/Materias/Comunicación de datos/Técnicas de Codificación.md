---
base: "[[Comunicación de datos.base]]"
Parent item: []
Blocking: []
Sub-item: []
Blocked by: []
Categoria:
  - Unidad 4
---
### Clasificación

- Códigos de Bloque: Se utilizan para la detección y corrección de errores
- Códigos de Línea: Se utilizan para la transmisión

### Códigos de línea

Los códigos de línea son la representación de la banda base digital, para la transmisión de una fuente a un destino. Los unos y ceros binarios, se representan en varios formato de señalización de bits (código de línea), dependiendo del medio de propagación de la señal para evitar errores en la comunicación. Esta conversión se realiza por medio de circuitos "conversores de código"

### Codificación de línea binaria

Algunas de las propiedades de los códigos de línea:

- Auto sincronización: Contenido suficiente de señal de temporización (reloj) que permita identificar el tiempo correspondiente a un bit. Es decir tiene que permitir recuperar el sincronismo.
- Nivel de continua bajo: En lo posible cero, o lo más bajo posible. El objetivo es evitar una interpretación errónea por cambio de nivel, que genere un dato erróneo.
- Capacidad de detección de errores: Debe ser posible detectar y si es viable, corregir el error en la detección.
- Baja probabilidad de error de bits: inmunidad al ruido (problema de interferencia intersímbolos.
- Transparencia: Independencia de las características del código en relación a la secuencia de unos y ceros que se transmita.
- Eficiencia: La eficiencia puede ser determinada comparando la capacidad de la información original y de su código equivalente. (Probabilidad de cada evento; Probabilidad de cada nivel del código)

![[image 294.png]]

### Codificación Unipolar

![[image 295.png]]

### Codificación Unipolar – Desventajas

- Componente de Continua DC: La amplitud media de una señal con codificación unipolar no es cero, eso crea lo que se llama una componente de corriente continua (señal de frecuencia cero). Cuando una señal contiene una componente continua, no puede viajar a través de medios que no pueden gestionar este tipo de componentes.
- Sincronización: Cuando una señal no varía, el receptor no puede determinar el principio y el final de cada bit, por tanto puede tener problemas de sincronización siempre que el flujo de datos contenga una larga serie ininterrumpida de ceros y unos.
- No son convenientes para aplicaciones de transmisión de señales.

### Unipolar Sin Retorno a Cero – NRZ (Nonreturn to zero)

El nivel de tensión se mantiene constante durante la duración del bit y no hay transiciones, es decir, no hay retorno al nivel cero de tensión

![[image 296.png]]

### Unipolar Con Retorno a Cero - RZ (Return to zero)

El nivel de tensión se mantiene constante y a la mitad de la del bit hay una transición, es decir, hay retorno al nivel cero de tensión.

![[image 297.png]]

### Codificación POLAR

- La codificación POLAR usa dos niveles de tensión, uno positivo y uno negativo, de ésta manera se reduce el nivel de tensión medio de la línea y se alivia el problema de la componente DC existente en la codificación UNIPOLAR, incluso anulándose completamente.
- De sus variantes, las más populares son :
    - NRZ Non Return to Zero
        - NRZ-L - Por Nivel
        - NRZ-I - Invertida o Por Cambio de Nivel.
    - RZ Return to Zero,
    - Bifásica: Manchester y Manchester Diferencial

### NRZ – L : Non Return to ZERO - Level

Trabaja por Nivel, es decir, dando un valor de nivel positivo al bit 1 y un valor de nivel negativo al bit 0 (o viceversa).

![[image 298.png]]

### NRZ – I : Non Return to ZERO - Inverted

Una inversión del nivel de voltaje representa un bit 1. Es la transición entre el valor de voltaje positivo y negativo, no los voltajes en sí mismos, lo que representa un bit 1. Un bit 0 se representa sin ningún cambio.

![[image 299.png]]

NRZ-I es mejor que el NRZ-L: debido a la sincronización implícita provista por el cambio de señal cada vez que se encuentra un 1.

### Códigos NRZ – Desventajas

- La principal limitación de las señales NRZ:
    - La presencia de una componente de continua DC.
    - La ausencia de capacidad de sincronización. Estos métodos no ofrecen al receptor un medio para determinar el ritmo con el que el emisor envía los bits, es decir, el ritmo del reloj del emisor.
- Las secuencias de ceros todavía pueden causar problemas, pero debido a que los ceros son menos frecuentes, el problema es menor.
- Estos códigos se usan con frecuencia en las grabaciones magnéticas, pero no son convenientes para aplicaciones de transmisión de señales.

### RZ – Return to zero

Se lo conoce como autosincronizante ya que indica al receptor cuando se está transmitiendo un bit (0 o 1) durante el tiempo de transmisión, haciendo una transición para volver al valor cero.

![[image 300.png]]

El problema con estos códigos es que las secuencias largas de ceros todavía pueden causar problemas.

### Codificación Bifásica – Código Manchester

- Estos códigos son muy utilizados en la transmisión de redes Ethernet.
- Codificación Manchester :
    - Hacen un cambio de nivel a la mitad del período del bit, de esa manera mantienen el sincronismo. Se utiliza un patrón para representar el bit 1 y otro para representar el bit 0.

![[image 301.png]]

### Codificación Bifásica – Código Manchester Diferencial

Este código es igual al Manchester con la diferencia de que en lugar de seguir un patrón para indicar el bit 1 y el 0, hace una transición de positivo a negativo, o viceversa, al comienzo del período del bit para indicar que es un bit 1, y si se trata de un bit 0, no cambia el valor de voltaje que traía del período anterior. La transición a la mitad del período del bit se mantiene
siempre.

![[image 302.png]]

### Codificación Bipolar

- Este tipo de codificación usa tres niveles de tensión :POSITIVO, NEGATIVO Y NULO.
- Los objetivos en el diseño de estas técnicas, como hemos comentado para las anteriores también, son:
    - Evitar la componente en continua.
    - Evitar las secuencias largas que correspondan a señales de tensión nula.
    - No reducir la velocidad de datos.

### AMI (Alternate Mark Inversion)

- Codifica sólo los bits 1, en forma alternada y no codifica los bits 0.
- Una secuencia larga de ceros puede causar problema.

![[image 303.png]]

### AMI (Alternate Mark Inversion) - RZ

![[image 304.png]]

### HDB-3 (High Density Bipolar 3 zeros)

- Este tipo de codificación se basa en el AMI, es decir, codifica sólo los bits 1 en forma alternada, los bits 0 no se codifican, es decir van con valor de voltaje 0.
- Cada 4 bits 0 consecutivos se evalúan y aplican en su construcción tres reglas, con el objetivo de que no se transmitan más de 3 ceros consecutivos y de esa manera mantener el nivel de continua a cero, el sincronismo y un buen espectro de frecuencia:
- Reglas:
    - Al 4to bit 0 consecutivo se debe insertar un BIT DE VIOLACIÓN, es decir , se debe codificar ese 4to bit 0 con la misma polaridad que el último bit 1 codificado, antes de los 4 bits ceros.
    - Los BIT DE VIOLACION deben tener polaridad alternada entre sí. Es decir, que si tenemos un BIT DE VIOLACIÓN que por la primer regla, queda con polaridad positiva, y existe un BIT DE VIOLACIÓN anterior con polaridad positiva, se debe cambiar la polaridad del nuevo BIT DE VIOLACIÓN a negativa.
    - Si al colocar el BIT DE VIOLACION, por cumplir con la segunda regla, no se llegara a cumplir la primer regla, es decir, que la polaridad del BIT DE VIOLACIÓN no fuese la misma que la del último bit 1 codificado, se deberá codificar el primero de los bits 0 del cuarteto, con la misma polaridad que la que le ha quedado al BIT DE VIOLACIÓN. Este bit se llama BIT DE RELLENO.
- De ésta manera se establece un patrón que indica al receptor la secuencia de 4 bits ceros consecutivos.

HDB-3 basado en un AMI Sin Retorno a Zero.

![[image 305.png]]

HDB-3 basado en un AMI Con Retorno a Zero.

![[image 306.png]]

### MLT-3

- Trabaja en forma escalonada codificando solamente los bits 1.
- Es un código de cambio de nivel, codifica el bit 1 cambiando de nivel positivo a cero, de cero a negativo y luego en el sentido inverso, solamente si se trata de un bit 1. Los bits 0 no se codifican, es decir no se cambia el valor de voltaje que traía.

![[image 307.png]]

### Codificación en placas de red

- Codificar: Significa asignar un valor de tensión al uno binario, y otro distinto al cero. Estos valores deben ser perfectamente detectados por el receptor, para no confundirlos. Ej: La placa de red codifica
- En las transmisiones digitales es necesario transmitir los datos y la señal de sincronismo (clock), lo cual nos implicaba hacer 2 enlaces. Una alternativa a esto, para hacer solo un enlace, era poder extraer el clock de los mismos datos.

### CLASIFICACIÓN DE LOS CÓDIGOS SEGÚN LOS NIVELES DE TENSIÓN

- Códigos UNIPOLARES
    - Tienen sólo un nivel de tensión (+ o -) y necesitan una línea adicional para el clock.
    - Clasificación:
        - Unipolar RZ (con retorno a Cero)
        - Unipolar NRZ (sin retorno a Cero)

- Códigos POLARES
    - Tienen 2 niveles de tensión, positiva y negativa (excepto RZ, que usa la transición al 0 para sincronismo).
    - Clasificación:
        - Polar RZ (con retorno a Cero)
        - Polar NRZ (sin retorno a Cero)
        - BIFÁSICO
            - Manchester
            - Manchester Diferencia

### CLASIFICACIÓN DE LOS CÓDIGOS SEGÚN LOS NIVELES DE TENSIÓN

- Códigos BIPOLARES
    - Tienen 3 niveles de tensión: +1v, 0 y -1v
    - El 0 se representa con 0v.
    - Ejemplos (usados en redes WAN)
- AMI
- HDB-3.

### FORMAS DE CODIFICACIÓN

- Códigos de línea: Son códigos para la transmisión. Se llaman de línea, porque a medida que los datos se van generando, se van codificando.
    - Ej: Manchester (10Mbps), MLT-3 (100Mbps), AMI y HDB-3
    - Condiciones para ser de Código de línea:
        - Permitir extraer el código de los datos.
        - Que el nivel de corriente continua en el enlace, sea constante, en lo posible, 0 Volts. Es decir, conviene que el código sea polar.
        - Que el espectro de energía sea adecuado, y reducido.

### FORMAS DE ENVÍO DE CÓDIGOS

Códigos de Nivel

![[image 308.png]]

De las formas de envío de códigos conviene usar el polar con retorno a cero, porque el nivel de continua permanece aproximadamente igual a 0.

### Códigos de Línea para redes LAN

Código Manchester:

- Este código es por cambio de nivel y bipolar. Lo utiliza la placa de red cuando transmite a 10Mbps.

![[image 309.png]]

- Si tengo un 1, en la mitad del tiempo de bit se produce el cambio. Si sube, tengo un uno, y si baja, tengo un 0. El receptor, detecta cambios de nivel, y no niveles absolutos.
- Existe la variante, llamada Manchester Diferencial. Difiere en lo siguiente:
    - Si el próximo bit es 1, no invierte
    - Si el próximo bit es 0, inviert

Código MLT-3:

- Es un código de 3 niveles: positivo, 0 y negativo. Cada vez que viene un 1, cambia. Si viene un 0 no cambia. Va de arriba hacia abajo, y de abajo hacia arriba. En la principio del tiempo de bit se produce la transición. Se utilizó en redes LAN de 100 Mbps.

![[image 310.png]]

### Códigos de Línea para redes WAN

AMI (Inversión de Marcas Alternadas)

- Codifica solamente los 1, y lo hace de forma alternada. El nivel de continua en este código es 0. Tiene como problema, que cuando vienen muchos ceros seguidos perdemos el clock. El código AMI fue usado extensamente en la primera generación de redes PCM, Más utilizado por las normas norteamericanas, la trama TDM T1 (1.544 Mbps).

![[image 311.png]]

HDB-3 (Alta Densidad Bipolar – 3 Ceros)

- Deriva del AMI, y no permite más de 3 ceros consecutivos. Al 4º cero, le coloca un bit llamado “bit de violación”, que tiene la misma polaridad que el último bit 1 anterior. Las violaciones se colocan en forma alternada, es decir, una violación debe tener la polaridad invertida respecto de la violación anterior, de manera de mantener la corriente continua 0. En algunos casos, habrá que colocar un “bit de relleno“, que se coloca en el primero de los 4 ceros para que el patrón pueda distinguirse.
- El receptor, para analizar lo leído, toma la decisión 3 tiempos después, para poder distinguir entre violación, relleno, y bit común.

![[image 312.png]]

### Códigos de Bloque

- Aquí codificamos de a bloques de bits, es decir, voy a tomar un conjunto de bits y recién ahí los voy a enviar. Se dividen en:
    - Para transmisión: Ej: 4B/5B, 8B/10B 

4B/5B

- Al código de 4 bits, le agrega un bit y lo transforma en uno de 5 bits, a fin de utilizar 2 niveles en vez de a 3. Hay una tabla predefinida de conversión. Lo utiliza la fibra óptica a 100 Mbps.

8B/10B

- Hace lo mismo que el 4B/5B, pero para la fibra óptica cuando transmite a 1000 Mbps.

### 4B5B

- Se sustituyen bloques de 4 bits por bloques de 5 bits que no tienen más de 2 bits 0 consecutivos, de esta manera se evitan las secuencias largas de ceros.
- Se puede utilizar antes de aplicar el MLT – 3, por ejemplo.
- Para la sustitución se utiliza una tabla de doble entrada pre-armada, con la correspondencia de un código de 5 dígitos binarios por cada código de 4 dígitos binarios.
- Ej: de Sustitución por 4B5B y aplicación de MLT-3 al tren de pulsos
resultante

![[image 313.png]]