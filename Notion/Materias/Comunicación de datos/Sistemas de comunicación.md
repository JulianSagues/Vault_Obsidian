---
notion-id: 1c7ac26b-dee7-80fc-b622-ec02d66b236d
base: "[[Comunicación de datos.base]]"
Parent item: []
Blocking: []
Sub-item: []
Blocked by: []
Material de Estudio:
  - "[[Assets/1_Sistemas de Comunicaciones.pdf]]"
  - "[[Assets/2_Modulacion de señales - Ejemplos.pdf]]"
Categoria:
  - Unidad 1
---
El objetivo fundamental de un sistema de comunicaciones, es transferir información de un lugar a otro.

Comunicación es la transmisión, recepción y procesamiento de información entre dos o más lugares, mediante circuitos electrónicos.

La fuente original de información puede estar en forma analógica (continua), ejemplo la voz humana o la música, o en forma digital (discreta), como por ejemplo los números codificados binario.

### Esquema Sistemas de Comunicaciones (diagrama simplificado)

El diagrama en bloques simplificado de un sistema electrónico de comunicaciones lo compone un transmisor, un medio de transmisión y un receptor

![[image 243.png]]

- Transmisor: Es un conjunto de uno o más dispositivos o circuitos electrónicos que convierte la información de la fuente original en una señal que se presta más a su transmisión a través de determinado medio de transmisión.
- Medio de transmisión: Transporta las señales desde el transmisor hasta el receptor, y puede ser tan sencillo como un par de conductores de cobre que propaguen las señales en forma de flujo de corriente eléctrica. También se puede convertir la información a ondas luminosas, propagarlas a través de cables de fibra óptica hechas de vidrio o de plástico, o bien se puede usar el espacio libre para transmitir ondas electromagnéticas de radio, a grandes distancias o sobre terreno donde sea difícil o costoso instalar un cable físico.
- Receptor: es un conjunto de dispositivos y circuitos electrónicos que acepta del medio de transmisión las señales transmitidas y las reconvierte a su forma original.

### Tipos básicos de Sistemas de Comunicaciones

- **Sistema analógico de Comunicaciones:** Es aquel en el cual la energía se transmite y se recibe en forma analógica, una señal de variación continua, como por ejemplo una onda senoidal. En los sistemas analógicos de comunicaciones, tanto la información como la portadora son señales analógicas.
- **Sistema digital de Comunicaciones:** Abarca una amplia variedad de técnicas de comunicación, que incluyen transmisión digital y radio digital. La transmisión digital es un sistema digital verdadero, donde los pulsos digitales (con valores discretos, como +5V y tierra) se transfieren entre dos o más puntos en un sistema de comunicaciones.

### MODULACIÓN Y DEMODULACIÓN

No resultará práctico propagar señales de información a través de cables metálicos o de fibra óptica, o a través de la atmósfera terrestre. Para transportar estas señales de información (nuestra fuente de mensaje) con frecuencia es necesario modular la información de la fuente, con una señal analógica de mayor frecuencia, llamada “portadora”.

De esta forma la señal portadora transporta la información a través del sistema.

La señal de información modula a la portadora, cambiando su amplitud, su frecuencia o su fase.

Modular es el proceso de cambiar una o más propiedades de la portadora, en proporción con la señal de información.

La modulación se hace en un transmisor mediante un circuito llamado modulador.

Una portadora sobre la que ha actuado una señal de información se llama onda modulada o señal modulada.

La demodulación es el proceso inverso a la modulación, y reconvierte a la portadora modulada en la información original (es decir, quita la información de la portadora). La demodulación se hace en un receptor, con un circuito llamado demodulador.

### Tipos de Modulación/Demodulación

La expresión es la descripción general de una onda senoidal de voltaje, variable en el tiempo, como puede ser una señal portadora de alta frecuencia.

![[image 244.png]]

- Si la señal de información es analógica, y la amplitud (V) de la portadora es proporcional a ella, se produce la modulación de Amplitud (AM, por amplitude modulation).
- Si se varía la frecuencia (f ) en forma proporcional a la señal de información, se produce la modulación de frecuencia (FM, de frequency modulaion).
- Finalmente si se varía la fase (𝜃) en proporción con la señal de información, se produce la modulación de fase (PM, de phase modulation)

![[image 245.png]]

- Si la señal de información es digital, y la amplitud (V) de la portadora se varía proporcionalmente a la señal de información, se produce una señal modulada digitalmente, llamada modulación por conmutación de amplitud (ASK, de amplitude shift keying).
- Si la frecuencia (f ) varía en forma proporcional a la señal de información digital se produce la modulación por conmutación de frecuencia (FSK, de frequency shift keying). 
- Si la fase (𝜃 ) varía de manera proporcional a la señal de información digital, se produce la modulación por conmutación de fase (PSK, de phase shift keying).
- Si se varían al mismo tiempo la amplitud y la fase en proporción con la señal
de información, resulta la modulación de amplitud en cuadratura (QAM, de
quadrature amplitude modulation)

![[image 246.png]]

### Diagrama en bloques de un Sistema de Comunicaciones (simplificado)

![[image 247.png]]

El diagrama simplificado de bloques de un sistema de comunicaciones, donde se ven las relaciones entre la señal moduladora, la portadora de alta frecuencia y la onda modulada.

La señal de información se combina con la portadora en el modulador, y se produce la onda modulada.

La información puede estar en forma analógica o digital, y el modulador puede efectuar modulación analógica o digital.

En el transmisor se hace una conversión elevadora de las señales de información, de bajas frecuencias a altas frecuencias, y se hace una conversión descendente en el receptor, de altas frecuencias a bajas frecuencias.

El proceso de convertir una frecuencia, o banda de frecuencias, y pasarla a otro lugar en el espectro total de frecuencias, se llama translación de frecuencia.

La señal modulada se transporta hasta el receptor a través de un sistema de transmisión. En el receptor se amplifica la señal modulada, se convierte en frecuencia menor y a continuación se demodula, para reproducir la información original de la fuente.
