---
Categoria:
  - Unidad 6
---
### Capas del modelo OSI (Open Systems Interconnection, Modelo de interconexión de sistemas abiertos)

El modelo OSI, de siete capas, es un modelo conceptual que caracteriza y estandariza la manera en la que los diferentes componentes de software y hardware involucrados en una comunicación de red deben dividir la mano de obra e interactuar entre sí.

![[Assets/image 443.png|image 443.png]]

La PDU (Protocol Data Unit) es un término utilizado en el modelo OSI para referirse a los bloques de datos que se intercambian entre capas. Cada capa del modelo OSI tiene su propia PDU, que contiene información específica para esa capa.

1. Capa Física:
    
    - PDU: Bits.
    
    - Función: Transmite bits individuales a través del medio físico.
    

1. Capa de Enlace de Datos:
    
    - PDU: Tramas.
    
    - Función: Agrupa bits en tramas y maneja la transmisión de estas tramas entre nodos en la misma red, incluyendo la detección y corrección de errores.
    

1. Capa de Red:
    
    - PDU: Paquetes.
    
    - Función: Encapsula tramas en paquetes y determina la ruta que deben seguir para llegar a su destino en diferentes redes.
    

1. Capa de Transporte:
    
    - PDU: Segmentos (TCP) o Datagramas (UDP).
    
    - Función: Gestiona la transferencia de datos entre sistemas finales, asegurando la entrega confiable y ordenada de segmentos o datagramas.
    

1. Capa de Sesión:
    
    - PDU: Datos de sesión.
    
    - Función: Maneja la creación, mantenimiento y terminación de sesiones entre aplicaciones.
    

1. Capa de Presentación:
    
    - PDU: Datos de presentación.
    
    - Función: Traduce los datos entre el formato de la red y el formato que las aplicaciones pueden usar, incluyendo la encriptación y compresión.
    

1. Capa de Aplicación:
    
    - PDU: Datos de aplicación.
    
    - Función: Proporciona servicios de red directamente a las aplicaciones del usuario, como correo electrónico, transferencia de archivos y navegación web.
    

Cada PDU contiene la información necesaria para que la capa correspondiente pueda realizar su función específica y se encapsula en la PDU de la capa inferior cuando se transmite a través de la red.

### Capas del modelo TCP(Protocolo de Control de Transmisión, por sus siglas en inglés Transmission Control Protocol)

El modelo TCP solamente tiene cuatro capas y es conocido generalmente como TCP/IP, ya que estos son sus dos protocolos más importantes.

![[Assets/image 1 36.png|image 1 36.png]]

### Capa 4: Capa de aplicación

La capa de aplicación del modelo TCP/IP ofrece a las aplicaciones la capacidad de acceder a los servicios de las otras capas y define los protocolos que utilizan las aplicaciones para intercambiar datos. Los protocolos de la capa de aplicación más conocidos son HTTP, FTP, SMTP, Telnet, DNS, SNMP y el Protocolo de información de enrutamiento (RIP).

### Capa 3: Capa de transporte

La capa de transporte se encarga de proporcionar comunicación de sesión y datagrama a la capa de aplicación de servicios . Los protocolos principales de esta capa son TCP y UDP. TCP proporciona un servicio de comunicaciones individual, fiable y orientado a la conexión. Es responsable de la secuenciación y detección de los paquetes enviados y de la recuperación de los paquetes perdidos en la transmisión. UDP proporciona un servicio de comunicaciones individual o grupal, sin conexión y poco fiable, pero rápido.

TCP (Transmission Control Protocol) y UDP (User Datagram Protocol) son dos protocolos fundamentales en la capa de transporte.

- TCP (Transmission Control Protocol):
    
    - Función: TCP es un protocolo orientado a la conexión que garantiza la entrega confiable y ordenada de datos entre sistemas finales.
    
    - Características:
        
        - Establecimiento de conexión: Antes de transmitir datos, TCP establece una conexión entre el emisor y el receptor mediante un proceso de tres pasos conocido como "handshake".
        
        - Control de flujo: TCP ajusta la velocidad de transmisión de datos para evitar la congestión de la red.
        
        - Corrección de errores: TCP utiliza números de secuencia y acuses de recibo (ACK) para asegurar que los datos se reciban correctamente y en el orden correcto.
        
        - Retransmisión: Si se detecta una pérdida de datos, TCP retransmite los segmentos perdidos.
        
        - Uso común: Aplicaciones que requieren alta fiabilidad y orden, como la transferencia de archivos (FTP), correo electrónico (SMTP), y navegación web (HTTP/HTTPS).
        
    

- UDP (User Datagram Protocol):
    
    - Función: UDP es un protocolo no orientado a la conexión que permite la transmisión rápida de datos sin garantizar la entrega ni el orden.
    
    - Características:
        
        - Sin conexión: UDP no establece una conexión antes de transmitir datos, lo que reduc la latencia.
        
        - Sin control de flujo ni corrección de errores: UDP no realiza control de flujo ni corrección de errores, lo que puede resultar en pérdida de datos o recepción fuera de orden.
        
        - Menor sobrecarga: UDP tiene una menor sobrecarga en comparación con TCP, lo que lo hace más rápido y eficiente para ciertas aplicaciones.
        
        - Uso común: Aplicaciones que requieren baja latencia y pueden tolerar pérdida de datos, como transmisión de video en tiempo real, juegos en línea, y consultas DNS.
        
    

El datagrama es una unidad de datos utilizada en la capa de red de ambos modelos (OSI y TCP), especialmente en el contexto del protocolo UDP (User Datagram Protocol).

- Características de un Datagrama:
    
    - Independencia: Cada datagrama es independiente y contiene toda la información necesaria para ser entregado al destino, sin necesidad de establecer una conexión previa.
    
    - Encapsulación: Un datagrama incluye tanto los datos que se están transmitiendo como la información de encabezado necesaria para la entrega, como las direcciones IP de origen y destino.
    
    - No garantizado: La entrega de datagramas no está garantizada. Pueden llegar fuera de orden, duplicados o incluso perderse sin que el protocolo UDP intente corregir estos problemas.
    
    - Eficiencia: Debido a la falta de mecanismos de control de flujo y corrección de errores, los datagramas permiten una transmisión rápida y eficiente, adecuada para aplicaciones que pueden tolerar cierta pérdida de datos.
    

Relación entre TCP y UDP:

- Ambos protocolos operan en la capa de transporte y permiten la comunicación entre sistemas finales, pero se utilizan en diferentes escenarios según las necesidades de la aplicación.

- TCP es ideal para aplicaciones que requieren fiabilidad y orden, mientras que UDP es preferido para aplicaciones que necesitan rapidez y pueden tolerar cierta pérdida de datos.

### Capa 2: Capa de red

La capa de red es responsable de las funciones de direccionamiento, empaquetado y enrutamiento del host. Los protocolos centrales de la capa de Internet son IP, Protocolo de resolución de direcciones (ARP), Protocolo de mensajes de control de Internet (ICMP) y Protocolo de administración de grupos de Internet (IGMP). En esta capa, el IP agrega la cabecera a los paquetes, lo que se conoce como dirección IP. En la actualidad existen tanto dirección IPv4 (32 bits) como dirección IP IPv6 (128 bits).

### Capa 1: Capa de acceso a la red

La capa de acceso a la red (o capa de enlace) es responsable de colocar los paquetes TCP/IP en el portador de datos de la red y recibir los paquetes TCP/IP situados fuera del mismo. El protocolo TCP/IP está diseñado para ser independiente del método de acceso a la red, el formato de la trama de red y el potador. En otras palabras, este protocolo es independiente de cualquier tecnología de red específica, lo que hace que este se pueda utilizar para conectar diferentes tipos de red, como Ethernet, Token Ring y Modo de transferencia asíncrono (ATM)

### Cómo se procesan los datos durante la transmisión

En un sistema de capas, los dispositivos de una capa intercambian datos en un formato diferente, lo que se conoce como unidad de datos de protocolo (PDU). La siguiente tabla muestra las PDU en las diferentes capas.

![[Assets/image 2 33.png|image 2 33.png]]

Por ejemplo, cuando un usuario solicita navegar por un sitio web en su ordenador, el software del servidor remoto primero entrega los datos solicitados a la capa de aplicación, donde se procesa de capa a capa con cada capa realizando sus funciones designadas. Los datos posteriormente se transmiten a través de la capa física de la red hasta ser recibidos por el servidor de destino u otro dispositivo. En este punto, los datos pasan nuevamente a través de las capas, cada capa realiza sus operaciones asignadas hasta que finalmente el software receptor utilice los datos.

Durante la transmisión, cada capa agrega una cabecera, pie de página o ambos a la PDU proveniente de la capa superior, el cual dirige e identifica el paquete. Este proceso se llama encapsulación. La cabecera (y el pie de página) y el cuerpo forman la PDU para la siguiente capa. El proceso continúa hasta llegar a la capa de nivel más bajo (capa física o capa de acceso a la red), desde la cual los datos se transmiten al dispositivo receptor. El dispositivo receptor invierte el proceso, desencapsulando los datos en cada capa con la información de la cabecera y pie de página que dirige las operaciones. Finalmente la aplicación utiliza los datos y el proceso continúa hasta que todos los datos son transmitidos y recibidos.

### Diferencias entre modelo OSI y modelo TCP/IP

![[Assets/image 3 27.png|image 3 27.png]]

La capa de aplicación del modelo TCP/IP es similar a las capas 5, 6, 7 combinadas del modelo OSI, el modelo TCP/IP no tiene una capa de sesión. La capa de transporte de TCP/IP abarca las responsabilidades de la capa de transporte OSI y algunas de las responsabilidades de la capa de sesión OSI. La capa de acceso a la red del modelo TCP/IP abarca el enlace de datos y las capas físicas del modelo OSI.

Importancia de TCP/IP y OSI para la resolución de problemas

Si tenemos en cuenta los significados de los dos modelos de referencia, el modelo OSI sería solo un modelo conceptual; este se utiliza principalmente para describir, discutir y comprender funciones de red individuales. Sin embargo, TCP/IP está diseñado para resolver un conjunto específico de problemas y no para funcionar como una descripción de generación para todas las comunicaciones de red, tal y como lo hace el modelo OSI. El modelo OSI es genérico e independiente del protocolo, aunque la mayoría de los protocolos y sistemas se adaptan a él,; mientras que el modelo TCP/IP se basa en protocolos estándar desarrollados por Internet. Otro factor a tener en cuenta en el modelo OSI es que, para las aplicaciones más simples, no todas las capas son utilizadas. Si bien las capas 1, 2, 3 son obligatorias para cualquier comunicación de datos, también existen aplicaciones que pueden usar ciertas capas de interfaz expecíficas en lugar de las capas superiores habituales del modelo

### Conclusiones

El modelo TCP/IP y el modelo OSI son modelos conceptuales utilizados para la descripción de todas las comunicaciones de la red, a su vez, TCP/IP también es un protocolo importante que se utiliza en todas las operaciones de Internet. Generalmente, cuando hablamos de capa 2, capa 3 o capa 7 en las que funciona un dispositivo de red, nos referimos al modelo OSI. El modelo TCP/IP se usa tanto para modelar la arquitectura actual de Internet como para proporcionar un conjunto de reglas seguidas por todas las formas de transmisión a través de la red.