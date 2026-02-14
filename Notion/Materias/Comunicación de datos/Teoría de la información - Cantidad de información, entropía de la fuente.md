---
base: "[[Comunicación de datos.base]]"
Parent item: []
Blocking: []
Sub-item: []
Blocked by: []
Material de Estudio:
  - "[[Assets/1_Teoría de Información - Introducción.pdf]]"
Categoria:
  - Unidad 2
---
- Se ocupa de la medición de la información
- La capacidad de los sistemas para transmitir y procesar información
- Garantiza el transporte masivo de datos sin merma de la calidad

### **Información** 

Es simplemente lo que produce la fuente para transferir al usuario

### **Transmisión de información**

- **Fuente (Emisor): U**na fuente es todo aquello que emite mensajes, es un dispositivo de transmisión de datos.
- **Mensajes**: Los datos enviados.
- **Tipos de fuente
**Por la relación entre los mensajes emitidos, una fuente puede ser **estructurada** o **no estructurada**. Interesan las fuentes aleatorias y estructuradas.
    - Una fuente es estructurada cuando posee un cierto nivel de redundancia.
    - Una fuente no estructurada o de información pura es aquella en que todos los mensajes son absolutamente aleatorios sin relación alguna. Este tipo de fuente emite mensajes que no se pueden comprimir. Es decir la información pura no puede ser comprimida sin que haya una pérdida de mensaje.

### **Mensaje Digital**

- Un mensaje es un conjunto de ceros y unos.
- Un archivo, un paquete de datos que viaja por una red y cualquier cosa que
tenga una representación binaria puede considerarse un mensaje.
- Mensaje se aplica también a alfabetos de más de dos símbolos, pero nos
referiremos casi siempre a mensajes binarios.

### **Código**

- Un código es un conjunto de unos y ceros que se usan para representar un cierto
mensaje.
- Un mensaje puede representarse con un código de longitud L(S) bits.
- Definimos la información contenida en el mensaje S, como la cantidad mínima de bits para codificar un mensaje.

### **Información**

- La información contenida en un mensaje es proporcional a la cantidad de bits
- Concepto de Información:
    - Supongamos que estamos leyendo un mensaje y hemos leído “trata"; la probabilidad de que el mensaje continúe con “miento" es muy alta. Por lo tanto, cuando realmente leemos “miento" la cantidad de información que recibimos es muy baja, estábamos en condiciones de predecir lo que sigue.
    - La ocurrencia de mensajes de alta probabilidad de aparición aporta menos información que la ocurrencia de mensajes menos probables. A medida que la probabilidad de ocurrencia del mensaje sea mayor, menor información contendrá el mismo.

### **Cantidad de Información “I”**

- La cantidad de información, relacionada con la probabilidad “p” de ocurrencia, esta dada por la expresión:

$I= logn (1/p)$

==Para: n = 2, I está dada en Bits.==

### **Entropía de la Fuente**

- De acuerdo a la teoría de la información, el nivel de información de una fuente se puede  medir según la entropía de la misma. Los estudios sobre la entropía son de suma importancia en la teoría de la información y se deben principalmente a C. E. Shannon.
- Para codificar los mensajes de una fuente se utilizará:
    - Menor cantidad de bits → para los mensajes más probables
    - Mayor cantidad de bits → para los mensajes menos probables
- La entropía de la fuente es la base de la compresión de datos.
- Supongamos que 𝒑𝒋 es la probabilidad de ocurrencia del mensaje j, y supongamos que 𝑰𝒋 es la longitud del código utilizado de dicho mensaje (es decir su cantidad de información).
- La entropía de los mensajes codificados de la fuente H se puede obtener como:

![[image 218.png]]

- De esta forma definimos la fuente en términos de la información promedio producida.
- **Al número "H" se lo denomina "Entropía de la fuente"**
- La entropía de la fuente determina la compresión que podemos aplicar.
- Se demuestra que no es posible comprimir un mensaje más allá de su entropía.
- El objetivo de la compresión de datos es encontrar los 𝑰𝒋 que minimizan a "H“.
- Los 𝑰𝒋 se determinan en función de las 𝒑𝒋, pues la longitud de los códigos dependen de la probabilidad de ocurrencia de los mismos.
- De aquí se deduce que la entropía de la fuente depende únicamente de la probabilidad de ocurrencia de cada mensaje de la misma.
- Shannon demostró, oportunamente que no es posible comprimir una fuente más allá de su entropía.