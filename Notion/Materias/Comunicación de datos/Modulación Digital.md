---
notion-id: 1cbac26b-dee7-8026-823a-fb17c17e2223
base: "[[Comunicación de datos.base]]"
Parent item: []
Blocking: []
Sub-item: []
Blocked by: []
Categoria:
  - Unidad 3
---
¡La modulación digital es una técnica utilizada en telecomunicaciones para transmitir información digital a través de medios analógicos, como cables, ondas de radio o fibra óptica.

A diferencia de la modulación analógica, que toma una señal continua como señal modulante o moduladora, la modulación digital implica la manipulación de señales discretas.

### Ventajas

**Mayor Eficiencia Espectral:**

Permite transmitir más datos en el mismo ancho de banda en comparación con la modulación analógica. Ejemplo: Técnicas como QAM pueden transmitir múltiples bits por símbolo.

**Mejor Resistencia al Ruido:**

Las señales digitales son menos susceptibles a la degradación por ruido e interferencias. Se pueden implementar técnicas de corrección de errores para mejorar la calidad de la señal.

**Seguridad:**

Es más fácil cifrar y proteger la información en formato digital. Las técnicas de encriptación son más efectivas en señales digitales.

**Flexibilidad y Adaptabilidad:**

Las señales digitales pueden ser fácilmente procesadas y manipuladas por sistemas digitales. Facilita la implementación de sistemas de comunicación más complejos y adaptativos.

**Integración con Tecnologías Modernas:**

Compatible con tecnologías de procesamiento digital de señales (DSP). Facilita la integración con redes y sistemas de comunicación modernos, como Internet y redes móviles.

### Desventajas

**Complejidad del Sistema:**

Los sistemas de modulación digital suelen ser más complejos y costosos de implementar. Requieren hardware y software avanzados para el procesamiento de señales. Requisitos de

**Ancho de Banda:**

Algunas técnicas de modulación digital pueden requerir un mayor ancho de banda para transmitir la misma cantidad de información que una señal analógica.

**Sensibilidad a la Sincronización:**

Las señales digitales requieren una sincronización precisa entre el transmisor y el receptor. La pérdida de sincronización puede llevar a errores en la transmisión de datos.

**Latencia:**

El procesamiento digital puede introducir latencia en la transmisión de datos. Esto puede ser crítico en aplicaciones en tiempo real, como la transmisión de voz o video en vivo.

### Tipos de Modulaciones

![[image 248.png]]

### Modulación Digital

- Portadora continua: onda senoidal
- Banda base digital: moduladora

![[image 249.png]]

Si la banda base es digital, en tal caso tenemos modulación digital 

La modulación digital, es el proceso de cambiar una de las características de una portadora analógica modulando con señal digital.

### Modulación Digital binaria

La modulación digital binaria es una técnica de modulación digital en la que se utilizan dos estados distintos para representar los datos binarios (0 y 1). En la modulación digital binaria, cada bit de datos se representa mediante una señal que puede tener dos posibles valores

**¿Qué es el “bit”?**

Un bit (abreviatura de “binary digit” o “dígito binario”) es la unidad básica de información en informática y telecomunicaciones. Un bit puede tener uno de dos valores posibles: 0 o 1. Estos valores representan los estados de “apagado” y “encendido” en un sistema binario, que es la base del funcionamiento de los sistemas digitales.

Los tipos más comunes de modulación digital binaria son:

ASK Binaria (Binary Amplitude Shift Keying) Modulación por desplazamiento de amplitud: La amplitud de la señal portadora cambia entre dos niveles, uno para el bit 0 y otro para el bit 1.

FSK Binaria (Binary Frequency Shift Keying) Modulación por desplazamiento de frecuencia: La frecuencia de la señal portadora cambia entre dos valores, uno para el bit 0 y otro para el bit 1.

PSK Binaria (Binary Phase Shift Keying) Modulación por desplazamiento de fase: La fase de la señal portadora cambia entre dos valores, uno para el bit 0 y otro para el bit 1.

![[image 250.png]]

### Modulación Digital Multinivel

La modulación digital multinivel es una técnica utilizada en las comunicaciones digitales para transmitir información mediante la modificación de una señal portadora. A diferencia de las modulaciones binarias, donde cada símbolo representa un bit (0 o 1), en las modulaciones multinivel cada símbolo puede representar varios bits, lo que permite una mayor eficiencia en el uso del espectro.

### **Principales Tipos de Modulación **Multinivel**:**

QPSK (Quadrature Phase Shift Keying): En esta técnica, cada símbolo representa dos bits, utilizando cuatro fases diferentes de la portadora. Esto permite duplicar la tasa de transmisión de datos en comparación con la modulación BPSK (Binary Phase Shift Keying). 

N QAM (Quadrature Amplitude Modulation): Combina la modulación en amplitud y en fase. En QAM, cada símbolo puede representar múltiples bits (4, 8, 16, 64, etc.), dependiendo del número de niveles utilizados. Por ejemplo, en 16-QAM, cada símbolo representa 4 bits.

### Ventajas y Desventajas

**Ventajas:**

- Mayor eficiencia espectral: Al transmitir más bits por símbolo, se puede aumentar la tasa de datos sin necesidad de aumentar el ancho de banda.
- Flexibilidad: Permite ajustar la modulación según las condiciones del canal y los requisitos de la aplicación.

**Desventajas:**

- Complejidad: Los sistemas de modulación multinivel son más complejos de implementar y requieren un procesamiento de señal más avanzado.
- Sensibilidad al ruido: Al tener más niveles, las modulaciones multinivel son más susceptibles a errores debido al ruido y las interferencias.

**Aplicaciones**

Las modulaciones digitales multinivel se utilizan en una amplia variedad de aplicaciones, incluyendo:

- Telecomunicaciones: En sistemas de comunicación móvil y satelital.
- Redes de datos: En tecnologías como Wi-Fi y LTE.
- Televisión digital: En la transmisión de señales de televisión de alta definición.

### Tasa de Baudios y Tasa de Bits

**Tasa de Baudios**

- Definición: La tasa de baudios mide el número de cambios de señal (o símbolos) por segundo en una transmisión. Un baudio equivale a un cambio de señal por segundo.
- Unidad: Se mide en baudios (Bd).
- Ejemplo: Si una señal cambia 1000 veces por segundo, la tasa de baudios es 1000 Bd.

**Tasa de Bits**

- Definición: La tasa de bits mide el número de bits transmitidos por segundo. Es una medida de la cantidad de datos que se transfieren en un segundo.
- Unidad: Se mide en bits por segundo (bps).
- Ejemplo: Si se transmiten 1000 bits en un segundo, la tasa de bits es 1000 bps.

![[image 251.png]]

### **Relación entre Tasa de Baudios y Tasa de Bits**

La relación entre la tasa de baudios y la tasa de bits depende del número de bits que cada símbolo puede representar. En sistemas de modulación digital multinivel, un símbolo puede representar más de un bit. La fórmula general es:

**Tasa de bits (bps)=Tasa de baudios (Bd)×Número de bits por símbolo**

**Resumen de parámetros:**

- Tasa de baudios: Número de cambios de señal por segundo.
- Tasa de bits: Número de bits transmitidos por segundo.
- Relación: La tasa de bits es igual a la tasa de baudios multiplicada por el número de bits por símbolo.

### Diagramas de Constelación

Un diagrama de constelación es una representación gráfica utilizada en las modulaciones digitales para visualizar las señales moduladas. Este diagrama muestra los símbolos de modulación en un plano complejo, donde cada punto representa un símbolo específico con una determinada amplitud y fase.

**Componentes del Diagrama de Constelación**

1. Ejes I y Q:
    1. Eje I (In-phase): Representa la componente en fase de la señal.
    2. Eje Q (Quadrature): Representa la componente en cuadratura (90°) de la señal.
2. Puntos de la Constelación: Cada punto en el diagrama corresponde a un símbolo de modulación. La posición de estos puntos depende del esquema de modulación utilizado, como QAM (Modulación de Amplitud en Cuadratura) o PSK (Modulación por Desplazamiento de Fase).

![[image 252.png]]

**Interpretación del Diagrama**

- Distancia entre Puntos: La distancia entre los puntos de la constelación indica la diferencia de amplitud y fase entre los símbolos. Una mayor distancia generalmente implica una mejor resistencia al ruido y a las interferencias, es decir un mayor “Margen de Ruido”.
- Ruido y Distorsión: El diagrama de constelación también permite identificar el tipo de ruido o distorsión presente en la señal. Por ejemplo: o Ruido Gaussiano: Los puntos aparecen difusos.
    - Interferencia de Frecuencia: Los puntos forman círculos alrededor de su posición ideal.
    - Ruido de Fase: Los puntos se dispersan en forma rotacional.

### Eficiencia espectral

**Definición**

La eficiencia espectral es una medida de cuántos bits de información se pueden transmitir por segundo por cada hertzio de ancho de banda disponible. Es un parámetro importante en telecomunicaciones, ya que indica qué tan bien se está utilizando el espectro de frecuencia.

**Características y parámetros:**

- Bits por Hertzio (bps/Hz): La eficiencia espectral se expresa en bits por segundo por hertzio (bps/Hz). Cuanto mayor sea este valor, más eficiente es la modulación.
- Modulaciones de Orden Superior: Las modulaciones como 64-QAM, 256-QAM, y 1024 QAM ofrecen una mayor eficiencia espectral, pero son más sensibles al ruido y requieren condiciones de canal más favorables.
- Ancho de Banda: La eficiencia espectral también depende del ancho de banda utilizado. Modulaciones como PSK (Phase Shift Keying) y QAM (Quadrature Amplitude Modulation) son comunes debido a su balance entre eficiencia espectral y robustez frente al ruido.

**Ventajas y Desventajas**

- Ventajas: Mayor capacidad de transmisión de datos, mejor uso del espectro, y posibilidad de ofrecer servicios de alta velocidad.
- Desventajas: Mayor complejidad en el diseño de transmisores y receptores, y mayor sensibilidad a las condiciones del canal y al ruido.

### Modulación por desplazamiento de amplitud (ASK)

La Modulación por Desplazamiento de Amplitud (ASK, por sus siglas en inglés) es una técnica de modulación digital en la que la amplitud de una onda portadora varía en función de los datos digitales que se desean transmitir. Es una de las formas más simples de modulación digital.

En ASK, la amplitud de la portadora cambia entre dos valores posibles, uno para el bit 0 y otro para el bit 1. En su forma más simple, un bit 0 puede estar representado por una amplitud cero (ausencia de portadora) y un bit 1 por una amplitud constante (presencia de portadora).

ASK es una técnica fundamental en la comunicación digital, especialmente útil en aplicaciones de bajo costo y corto alcance. Aunque tiene limitaciones en términos de eficiencia espectral y resistencia al ruido, su simplicidad la hace adecuada para muchas aplicaciones prácticas.

![[image 253.png]]

### **Aplicaciones:**

**Controles Remotos**

Los controles remotos de dispositivos como puertas de garaje y sistemas de alarma a menudo utilizan ASK debido a su simplicidad y bajo costo. La señal ASK es adecuada para estas aplicaciones de corto alcance donde la interferencia y el ruido no son grandes problemas.

**Sistemas de Identificación por Radiofrecuencia (RFID)**

ASK se utiliza en algunas etiquetas RFID, especialmente en aplicaciones de baja frecuencia (LF) y alta frecuencia (HF). Estas etiquetas se emplean en sistemas de control de acceso, seguimiento de inventarios y gestión de activos.

**Modems**

Los primeros modems de línea telefónica utilizaban ASK para la transmisión de datos. Aunque hoy en día se utilizan técnicas más avanzadas, ASK fue fundamental en el desarrollo inicial de la comunicación de datos a través de líneas telefónicas.

**Comunicaciones Ópticas**

En algunas aplicaciones de comunicaciones ópticas, ASK se utiliza para modular la intensidad de la luz emitida por un láser o LED. Esto es común en sistemas de comunicación de corto alcance, como enlaces de fibra óptica en redes locales (LAN).

Modulación por desplazamiento de frecuencia (FSK)

FSK. Es un tipo de modulación de frecuencia cuya señal modulante es un flujo de pulsos binarios que varía entre valores predeterminados, en los sistemas de modulación por salto de frecuencia. La señal moduladora hace variar la frecuencia de la portadora, de modo que la señal modulada resultante codifica la información asociándola a valores de frecuencia diferentes. Es decir, FSK se basa en modular la portadora con la señal digital mediante modulación angular de frecuencia:

Esta señal puede tomar valores 0 y 1, de esta forma la señal modulada tomará los valores
respectivos:

![[image 254.png]]

En conclusión tendremos dos valores de frecuencia que conmutaran debido a la señal modulante.

![[image 255.png]]

![[image 256.png]]

### Ventajas y Desventajas

**Ventajas:**

- Mayor resistencia al ruido y a las interferencias en comparación con ASK.
- Adecuada para transmisiones a largas distancias.

**Desventajas:**

- Requiere un mayor ancho de banda en comparación con otras técnicas de modulación digital.
- Mayor complejidad en el diseño del transmisor y receptor.

### Modulación por desplazamiento de fase (PSK)

La modulación por desplazamiento de fase o PSK consiste en hacer variar la fase de la portadora entre dos valores discretos.

![[image 257.png]]

![[image 258.png]]

En este caso existe un desplazamiento de fase entre los símbolos de este sistema de modulación, ver diagrama de constelación.

- Vemos que existen solo dos puntos. Uno corresponde al 1 lógico que produce un desplazamiento de fase de 𝟏𝟖𝟎° 𝝅 . Otro corresponde al cero lógico, que no produce desfasaje de la portadora 𝟎°.
- Las zonas marcadas corresponden al área de decisión, y determinan el margen de ruido que tolera el sistema. Por los que vemos el margen de ruido es grande.

### Ventajas y Desventajas

**Ventajas:**

- Mayor resistencia al ruido en comparación con ASK.
- Mejor eficiencia espectral.
- Adecuada para transmisiones a largas distancias.

**Desventajas:**

- Mayor complejidad en el diseño del transmisor y receptor.
- Requiere una sincronización precisa de la fase.

Codificación M-aria

- M-ario (eme ario) es un término derivado de la palabra binario.
- M sólo es un número que representa la cantidad de combinaciones o estados posibles para N bits
- La cantidad de estados de salida se calcula con la ecuación: N = log2M
- donde 
N = cantidad de bits codificados 
y M = cantidad de estados posibles (símbolos) con N bits

### Modulación Digital Multinivel: m-PSK y m-QAM

- m_QAM este mecanismo combina los cambios en fase y amplitud.
- La modulación QAM resulta de combinar ASK y PSK:

![[image 259.png]]

### Modulación multinivel por desplazamiento de pase m-PSK

- La modulación MPSK (multilevel pase shift keying) funciona igual que PSK o BPSK, la única diferencia es que en esta oportunidad se utilizan varios niveles.
- En esta oportunidad se codificarán N bits para obtener M símbolos.
- Entre los sistemas más destacados tenemos los que codifican N=2 y M=4 4PSK o QPSK. Otro es N=3 y M=8 8PSK.

### **4PSK o QPSK**

Este es un sistema de modulación digital de amplitud constante con M=4, por ende N=2. En este caso se utilizan grupos de a 2 bits de la señal modulante, los cuales denominamos dibits, para realizar cambios en la portadora.

Puesto que utilizamos 2 bits para la codificación un símbolo a la salida, la rapidez de cambio en la salida (expresada en baudios) es la mitad de la rapidez de cambio de la señal modulante.

Para modular en QPSK se convierte el dibit en dos señales independientes en paralelo, cada una de las cuales modula en BPSK una portadora. Estas portadoras están defasadas 90° entre sí. Luego las señales moduladas se suman, y se obtiene QPSK.

![[image 260.png]]

![[image 261.png]]

En el diagrama de constelación de este sistemas vemos que existen 4 símbolos: 00, 01, 10 y 11. Lo que denominamos área de decisión, en línea punteada, se ha reducido respecto a PSK o BPSK. Esto significa que se ha reducido el margen de ruido. También se ve que se ha modulado en fase y no en amplitud, puesto que la distancia de los 4 símbolos al origen sigue siendo la unidad.

### 8PSK

8PSK es un sistema de modulación digital de amplitud constante, donde M=8, entonces N=3. En este caso se utilizan grupos de 3 bits de la señal modulante, llamados tribits para realizar cambios en la portadora.

Puesto que se utilizan 3 bits para la codificación de un símbolo en la salida, la rapidez de cambio en la salida (baudios) es 1/3 de la rapidez de la señal modulante.

Para el diagrama de constelación de este sistema tenemos 8 símbolos 000, 001, 010, 011, 100, 101, 110 y 111. El área de decisión se recude comparado con 4PSK, y más aún respecto a BPSK. Lo que significa que se ha reducido más el margen de ruido.

![[image 262.png]]

### MPSK

Modular en mayores niveles en PSK trae como ventaja reducir el BW mínimo necesario, pero en contra tenemos una disminución en el margen de ruido. En este punto es donde conviene pasar a otra técnica de conmutación.

![[image 263.png]]

### MQAM

Los sistemas MQAM ( multilevel quadrature amplitude modulation) combianan la modulación en amplitud con la modulación por desplazamiento de fase. De esta forma se optimiza el BW con un mejoramiento en el margen de ruido.

Se podrán utilizar sistemas que tengan M/2 o más ángulos de fase diferentes, y más de dos niveles de amplitud. Hay varias combinaciones, veremos los que tienen 2 niveles de amplitud y M/2 ángulos de fase distintos.

### 4QAM

En este sistema de modulación tenemos M=4 y N=2. Comparado con 4PSK, aparte de modularse en fase, la portadora también se modula en amplitud. Vemos en el diagrama de constelación que tenemos dos fases distintas y dos amplitudes posibles, lo cual equivale a dos sistemas BPSK de distinta amplitud combinados.

Lo importante es que variando las dos amplitudes posibles podemos obtener un mejor margen de ruido, respecto a igual nivel de MPSK.

![[image 264.png]]

- Al utilizar dibits (dos bits) el BW mínimo necesario :
- Este tipo de modulación provee una reducción del BM mínimo necesario y un buen control (mejor que en QPSK) sobre el margen de ruido

![[image 265.png]]

### 8QAM

- Es una modulación digital de 8 fases M=8 N=3,.
- La diferencia con 8PSK es que la portadora además de modularse en fase se modula en dos niveles de amplitud distintos.
- Por el diagrama de constelación vemos 4 fases distintas y 2 amplitudes posibles, lo cual equivale a dos sistemas 4PSK combinados. Es decir, logramos reducción el BW mínimo controlando mejor el margen de ruido que necesitamos.

![[image 266.png]]

### 16QAM

- La modulación 16QAM tiene 16 fases, M=16 N=4.
- En el diagrama de constelación vemos 8 fases distintas y dos amplitudes. Equivalente a dos sistemas 8PSK de distintas amplitudes combinados.
- En este caso se utilizan grupos de 4 bits
- De esta forma se reduce el BW mínimo necesario.
- Con buen control sobre el margen de ruido.

![[image 267.png]]

### Tabla comparativa – Sistemas de Modulación

![[image 268.png]]
