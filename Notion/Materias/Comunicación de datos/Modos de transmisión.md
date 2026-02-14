---
base: "[[Comunicación de datos.base]]"
Parent item: []
Blocking: []
Sub-item: []
Blocked by: []
Material de Estudio:
  - "[[Assets/5_Modos de Transmisión_E.pdf]]"
Categoria:
  - Unidad 1
---
Los sistemas electrónicos de comunicaciones se pueden diseñar para manejar la transmisión sólo en una dirección, en ambas direcciones, sólo en una a la vez, o en ambas direcciones al mismo
tiempo.

A éstos se les llama modos de transmisión. Hay tres modos de transmisión posibles: sílmplex, semidúplex o halfduplex y dúplex o full dúplex.

### Modo Símplex (SX)

Con el funcionamiento símplex, las transmisiones sólo se hacen en una dirección. A veces, a los sistemas símplex se les llama sólo en unsentido, sólo recibir o sólo transmitir. Una estación puede ser un transmisor o un receptor, pero no ambos a la vez. Como ejemplo de transmisión símplex está la emisión comercial de radio o televisión: la estación de radio sólo transmite a uno, y uno siempre recibe.

![[image 223.png]]

### Semidúplex (HDX, de half duplex)

En el funcionamiento semidúplex, las transmisiones se pueden hacer en ambas direcciones, pero no al mismo tiempo. A veces, a los sistemas semidúplex se les llama de alternar en ambos sentidos,
en uno de los sentidos, o de cambio y fuera. Una estación puede ser transmisora y receptora, pero no al mismo tiempo. Los sistemas de radio en dos sentidos que usan botones para hablar (PTT, de push-totalk) para conectar sus transmisores, como son los radios de banda civil y de policía, son ejemplos de transmisión en semidúplex.

![[image 224.png]]

### Dúplex total (FDX, de full dúplex)

Con el funcionamiento dúplex total, o simplemente dúplex, puede haber transmisiones en ambas direcciones al mismo tiempo. A veces, a los sistemas dúplex se les llama simultáneos de dos direcciones, dúplex completos o líneas bilaterales o en ambos sentidos. Una estación puede transmitir y recibir en forma simultánea; sin embargo, la estación a la que se transmite también debe ser de la que se recibe. Un sistema telefónico normal es un ejemplo de funcionamiento
dúplex.

![[image 225.png]]

### Modos de transmisión de datos binarios

La transmisión de datos binarios por un medio de enlace se puede realizar en Modo Paralelo o en Modo Serie.

### Transmisión Paralela

- Los datos binarios, formados por 1 y 0, se pueden organizar en grupos de n bits cada uno. Las computadoras producen/consumen datos en grupos de bits de forma similar a como se conciben y usan las palabras, y no las letras, en el lenguaje hablado. Agrupando los datos, se pueden enviar n bits al mismo tiempo en lugar de uno solo. Esto es denomina trasmisión paralela.
- El mecanismo de transmisión paralela es usar n hilos para enviar n bits cada vez. De esta forma cada bit tiene su propio hilo, o ruta. Todos los n bits de un grupo se pueden transmitir con cada pulso de reloj de un dispositivo a otro.
- La figura muestra cómo funciona la transmisión paralela para n=8.

![[image 226.png]]

### Transmisión Paralela (ventajas/desventajas)

- La ventaja de la transmisión paralela es la velocidad. A igualdad de condiciones, la transmisión paralela puede incrementar la velocidad de transferencia en un factor de n sobre la transmisión serie.
- La principal desventaja es el costo. La transmisión paralela requiere n líneas de comunicación para transmitir el flujo de datos. Por este motivo es que la transmisión paralela se limita a distancias cortas.

### Transmisión Serie

- En la transmisión serie un bit sigue a otro, por lo que solamente se necesita un solo canal de comunicación, en lugar de n, para transmitir datos entre dos dispositivos.

### Transmisión Serie (ventajas/desventajas)

- La ventaja de la transmisión serie sobre la transmisión paralela es que, al tener un único canal de comunicación, la transmisión serie reduce el costo de transmisión sobre la paralela en un factor n. Por reducir este costo es más conveniente para distancias largas.
- Como principal desventaja es que, como la comunicación dentro de los dispositivos es paralela, es necesario usar dispositivos de conversión de interfaz entre emisor y la línea (paralelo a serie) y entre la línea y el receptor (serie a paralelo).

![[image 227.png]]