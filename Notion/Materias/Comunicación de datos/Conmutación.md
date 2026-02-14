---
base: "[[Comunicación de datos.base]]"
Parent item: []
Blocking: []
Sub-item: []
Blocked by: []
Categoria:
  - Unidad 4
---
El conmutador es un dispositivo importante en toda red de comunicación, porque cumple la función de conectar los usuarios entre sí. Esta conmutación debe ser rápida, confiable y no cometer errores de direccionamiento, es decir que el usuario A se comunique con el B, y no por error con el C

### Objetivos de la Conmutación

- Debe garantizar que llegue la información.
- Debe ser transparente al usuario.
- Debe ser rápida

![[image 314.png]]

### Conmutación de Circuitos:

- Este tipo de conmutación se utiliza cuando se necesita que los datos sean transmitidos en tiempo real. Se caracteriza porque crea un canal dedicado en la transmisión. Cuando se finaliza la comunicación el canal es desocupado y puede ser utilizado por otro usuario. Ejemplo de este tipo de conmutación son las llamadas Telefónicas.
- Ventajas:
    - Conexión dedicada, utilizo el BW disponible.
    - No necesita protocolo.
    - Es muy seguro, ya que no es compartido.
    - Trabaja en tiempo real.
- Desventajas:
    - En los tiempos de silencio desperdicio BW.
    - Mala administración del BW disponible.
    - Me tarifan por tiempo y distancia de enlace.

### Conmutación de Mensajes:

Consiste en compartir los enlaces. Aparece el concepto de Nodo, porque comparto enlaces. En este tipo de conmutación, el emisor debe primero enviar el mensaje completo a un Nodo intermedio, donde es encolado en un Buffer. Y luego este nodo se lo envía a otro y así sucesivamente, hasta llegar al receptor. Cada Nodo debe esperar su turno para poder transmitir.

- Ventajas:
    - Compartimos Enlaces.
    - Me cobran solo por tiempo (no por distancia).
    - Aprovechamos los tiempos de silencio.
- Desventajas:
    - Usa un algoritmo de cola en el orden que llega se envía.
    - El Buffer limita el tamaño del mensaje.
    - Se requieren protocolos para identificar los mensajes.
    - No se trabaja en tiempo real.

### Conmutación de Paquetes:

Para solucionar el problema de la Conmutación de Mensajes del encolamiento, se dividió a los mensajes en paquetes (a cada paquete se le agregó un encabezado). En este tipo de conmutación el canal es compartido por muchos usuarios, se caracteriza principalmente porque los datos son ensamblados en forma de paquetes. Estos paquetes pueden tomar distintas rutas para llegar a destino. Cuando llegan, los paquetes son reensamblados.

Encontramos dos tipos de conmutación de paquetes:

- Circuitos Virtuales (Orientado a la conexión)
    - En esta técnica, el emisor envía un paquete de control, conocido como paquete de llamada, éste será el encargado de establecer un camino virtual por donde pasaran todos los paquetes de datos. De esta manera llegan en orden establecido por el emisor.
- Datagramas (No orientados a la conexión)
    - En esta técnica el emisor enumera cada paquete, se caracteriza porque cada paquete puede tomar rutas distintas, y por lo tanto pueden llegar en distinto orden, o también se pueden perder paquetes. El trabajo del receptor es ordenar los paquetes.
- Ventajas:
    - Comparte enlaces.
    - Se tarifa por tiempo de utilización.
    - Respecto a la conmutación por Mensajes, los tiempos de
conmutación son más rápidos, puesto que los mensajes son
más pequeños.
    - Se trabaja casi en tiempo real.
- Desventaja:
    - Hace falta un protocolo de comunicación.
    - Se puede perder paquetes, en el caso de los datagramas

### Aplicaciones de los sistemas de conmutación

Uno de los más importantes es el modelo OSI, el cual es un modelo de siete capas. Este modelo define la forma en la cual se Encapsulara y Desencapsulara los Datos, en el momento de ser Transmitidos y Recibidos, respectivamente.

El proceso de Encapsulamiento consiste en agregar a la información (Datos) el encabezamiento correspondiente a cada capa, para finalmente ser transmitido al medio de enlace físico. El Desencapsular es el proceso inverso.

### Equivalencia entre el Modelo OSI y Modelo TCP/IP 

![[image 315.png]]

### Aplicación MPLS

Como aplicación final, en la cual se aprovechan las bondades de los dos sistemas de conmutación de paquetes, Circuitos virtuales y Datagramas, mencionamos la aplicación del protocolo MPLS. MPLS (MultiProtocol Label Switching) es un protocolo de conmutación por etiquetas definido para funcionar sobre múltiples protocolos como Sonet, Frame Realy, ATM, Ethernet, aprovechando las eficiencias de cada uno de ellos.

MPLS se intercala entre la capa 2 y 3 del Modelo OSI y TCP /IP.

![[image 316.png]]

La idea del MPLS es combinar los algoritmos de re-envío usados en ATM e IP.

En conclusión, la idea es Rutear en los bordes y Conmutar en el Núcleo de la red en cuestión. De esta forma, en los bordes tenemos Datagramas y en el Nucleo Circuitos Virtuales. Esta aplicación es la que hoy en día hace posible la implementación de redes de datos de alta capacidad, como LTE referido a 4G y 5G en redes móviles.