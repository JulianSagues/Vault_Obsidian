---
base: "[[Comunicación de datos.base]]"
Parent item: []
Blocking: []
Sub-item: []
Blocked by: []
Categoria:
  - Unidad 5
---
### Local Area Network (LAN)

Si una red está formada por más de un ordenador, esta recibe el nombre de Local Area Network (LAN). Una red local de tales características puede incluir a dos ordenadores en una vivienda privada o a varios miles de dispositivos en una empresa. Asimismo, las redes en instituciones públicas como administraciones, colegios o universidades también son redes LAN. Un estándar muy frecuente para redes de área local por cable es Ethernet. Otras opciones menos comunes y algo obsoletas son las tecnologías de red ARCNET, FDDI y Token Ring. La transmisión de datos tiene lugar o bien de manera electrónica a través de cables de cobre o mediante fibra óptica.

Si se conectan más de dos ordenadores en una red LAN, se necesitan otros componentes de red como hubs, bridges y switches, es decir, concentradores, puentes de red y conmutadores, los cuales funcionan como elementos de acoplamiento y nodos de distribución. El tipo de red conocido como LAN o red de área local fue desarrollado para posibilitar la rápida transmisión de cantidades de datos más grandes. En función de la estructura de la red y del medio de transmisión utilizado se puede hablar de un rendimiento de 10 a 1.000 Mbit/s. Asimismo, las redes LAN permiten un intercambio de información cómodo entre los diversos dispositivos conectados a la red. Por ello, en el entorno empresarial es habitual que varios equipos de trabajo puedan acceder a servidores de archivos comunes, a impresoras de red o a aplicaciones por medio de la red LAN.

### Wireless Local Area Network (WLAN)

Si la red local tiene lugar de manera inalámbrica, se puede hablar en este caso de una Wireless Local Area Network (WLAN) o red de área local inalámbrica y los fundamentos básicos de los estándares de la red WLAN quedan definidos por la familia de normas IEEE 802.11. Las redes locales inalámbricas ofrecen la posibilidad de integrar terminales cómodamente en una red doméstica o empresarial y son compatibles con redes LAN Ethernet, aunque el rendimiento es, en este caso, algo menor que el de una conexión
Ethernet.

### Topologías físicas

- Bus: una topología de bus usa solo un cable backbone que debe terminarse en ambos extremos. Todos los elementos de red se conectan directamente a este backbone. Su funcionamiento es simple y es muy fácil de instalar, pero es muy sensible a problemas de tráfico, y un fallo o una rotura en el cable interrumpe todas las transmisiones. Esto hace que se dificulte el mantenimiento de la red.
- Estrella: la topología en estrella conecta todos los nodos con un nodo central. El nodo central conecta directamente con los nodos, enviándoles la información del nodo de origen, constituyendo una red punto a punto. Si falla un nodo, la red sigue funcionando, excepto si falla el nodo central, que las transmisiones quedan interrumpidas.
- Anillo: La topología de anillo conecta los nodos punto a punto, formando un anillo físico y consiste en conectar varios nodos a una red que tiene una serie de repetidores. Cuando un nodo transmite información a otro, la información pasa por cada repetidor hasta llegar al nodo deseado. De esta manera en el caso que se interrumpa un enlace, es posible continuar con la conexión, utilizando el otro camino alternativo.
- Árbol: la topología de árbol tiene varias terminales conectadas de forma que la red se ramifica desde un servidor base. Un fallo o rotura en el cable interrumpe las transmisiones.
- Malla: la topología de malla se implementa para proporcionar la mayor protección posible para evitar una interrupción del servicio. En esta topología, cada host tiene sus propias conexiones con los demás hosts.
- Mixta: la topología mixta es aquella en la que se aplica una mezcla entre alguna de las otras topologías: bus, estrella o anillo. Principalmente las podemos encontrar dos topologías mixtas: EstrellaBus y Estrella-Anillo. Los cables más utilizados son el cable de par trenzado, el cable coaxial y la fibra óptica.

### Topologías lógicas

La topología lógica de una red es la forma en que los hosts se comunican a través del medio. Los dos tipos más comunes de topologías lógicas son:

- Broadcast: la topología broadcast simplemente significa que cada host envía sus datos hacia todos los demás hosts del medio de red. No existe un orden que las estaciones deban seguir para utilizar la red. Es por orden de llegada, es cómo funciona el protocolo Ethernet.
- Token: La topología transmisión de tokens controla el acceso a la red mediante la transmisión de un token electrónico a cada host de forma secuencial. Cuando un host recibe el token, ese host puede enviar datos a través de la red. Si el host no tiene ningún dato para enviar, transmite el token al siguiente host y el proceso se vuelve a repetir. Ejemplo de redes que utilizan la transmisión de tokens son Token Ring.
