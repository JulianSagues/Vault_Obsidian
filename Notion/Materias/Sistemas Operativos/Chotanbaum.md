---
notion-id: 2aaac26b-dee7-80f9-b27f-fcd3473d0977
base: "[[Sistemas Operativos.base]]"
Sub-item: []
Blocked by: []
Parent item: []
Blocking: []
Categoria: []
---
### Preguntas del Examen

**La memoria virtual permite que:**

- ==a) Los programas sean más grandes que la memoria física.==
- b) El sistema operativo sea más grande que la memoria física.
- c) Los programas se ejecuten más rápido.
- d) Ninguna de las anteriores.

**El planificador de largo plazo:**

- a) Decide qué proceso de la cola de listos pasa a ejecución.
- b) Decide qué proceso de la cola de listos pasa a la cola de espera.
- ==c) Decide qué proceso del disco pasa a la cola de listos.==
- d) Ninguna de las anteriores.

**El bit R (referencia) de la tabla de páginas se utiliza para:**

- a) Seleccionar la página a reemplazar.
- b) Saber si la página está en memoria principal o secundaria.
- c) Saber si la página fue modificada.
- ==d) Ninguna de las anteriores.==

**Un programa en ejecución, también llamado:**

- a) Programa Ejecutable.
- b) Programa fuente.
- ==c) Proceso.==
- d) Ninguna de las anteriores.

**En un sistema con paginación, una dirección virtual está compuesta por:**

- a) Nro de página y nro de marco.
- ==b) Nro de página y desplazamiento.==
- c) Nro de marco y desplazamiento.
- d) Ninguna de las anteriores.

**Los algoritmos de planificación expropiativos (preemptive) son aquellos que:**

- a) Asignan la CPU a un proceso y este no la libera hasta que termina.
- ==b) El SO puede quitarle la CPU a un proceso en ejecución para asignársela a otro.==
- c) Se basan en la prioridad de los procesos.
- d) Ninguna de las anteriores.

**El grado de multiprogramación es:**

- a) La cantidad de procesos en memoria principal.
- b) La cantidad de procesos en la cola de listos.
- c) La cantidad de procesos en la cola de espera.
- ==d) Ninguna de las anteriores.==

**Una política expropiativa (preemptive) es aquella que:**

- a) Permite que un proceso sea interrumpido por el SO.
- b) No permite que un proceso sea interrumpido por el SO.
- c) Permite que un proceso se ejecute hasta que termine.
- ==d) Ninguna de las anteriores.==

**¿Para qué sistema operativo fue desarrollado inicialmente el sistema de archivos FAT?**

- ==a) Windows.==
- b) Unix.
- c) MS-DOS.
- d) Ninguna de las anteriores.

**¿Cuál de las siguientes afirmaciones es verdadera acerca de la tabla de archivos abiertos (AF T)?**

- a) Es una estructura por proceso.
- b) Es una estructura global del sistema.
- ==c) Almacena el modo de acceso (lectura, escritura).==
- d) Ninguna de las anteriores.

**Para que un proceso no sufra muerte por inanición, y suponiendo que no existen procesos "sucios", el algoritmo de planificación debe ser:**

- a) FIFO
- b) FCFS con prioridades dinámicas
- ==c) Round Robin==
- d) Ninguna de las anteriores

**Para evitar que un proceso sea monopólico el procesador, y además esos procesos no idealicen el sistema el planificador debe ser:**

- a) FIFO
- b) FCFS con prioridades dinámicas
- ==c) Round Robin==
- d) Ninguna de las anteriores

**Cuando una interrupción debe ser atendida, el proceso que se está efectuando:**

- a) Se bloquea
- b) Se coloca en cola de listos
- ==c) Se suspende==
- d) Ninguna de las anteriores

**Cuando se habla de direcciones virtuales se relaciona a:**

- a) La memoria principal
- ==b) Lo que indique la tabla de páginas del proceso==
- c) A la memoria de disco
- d) Ninguna de las anteriores

**Un proceso interactivo puede ser creado por:**

- a) El sistema operativo
- b) Una petición de usuario
- c) Unción (sic) de las anteriores
- d) Ninguna de las anteriores

**Los algoritmos de expulsión de páginas, que NO analizan a la hora de seleccionar una página a ser expulsada?**

- a) El bit de modificado
- b) El bit de referencia
- c) El bit de presente/ausente
- ==d) Analizan todos los bits==

**Al utilizar paginación simple, cual es el equivalente al registro límite:**

- a) El número de página de la dirección lógica
- b) El puntero al marco de página
- ==c) Los bits menos significativos de la dirección lógica==
- d) Ninguna de las anteriores

**Qué aserción es verdadera respecto de los hilos:**

- a) Los hilos de un mismo proceso no comparten los recursos del mismo
- ==b) Si un hilo modifica un dato, otro hilo del mismo proceso no puede acceder a ese dato modificado inmediatamente==
- c) Los hilos de un mismo proceso comparten PC, PSW y Stack
- d) Todas las anteriores son correctas

**Para agilizar la cantidad de la fragmentación o thrashing se deben tomar las siguientes acciones:**

- a) Minimizar la cantidad de procesos por usuario
- ==b) Aumentar la memoria RAM==
- c) Evitar particiones de swap demasiado grandes
- d) Todas las anteriores son correctas

**Al utilizar paginación simple, cuando se produce un fallo de página duro:**

- a) Se busca la dirección del marco de página en la TLB
- b) Se busca la dirección del marco de página en la tabla de páginas para llegar a la dirección de memoria
- ==c) Se debe acceder al disco a partir de la tabla de páginas del proceso==
- d) Ninguna de la anteriores

**Los drivers:**

- ==a) Establecen una interfaz entre el SSOO y la controladora de dispositivos==
- b) Se puede programar independientemente del entorno (POSIX o WIN32)
- c) Todas pueden correr en modo Kernel
- d) Todas las anteriores

**¿Qué datos no contiene un nodo índice?**

- a) ID del grupo
- ==b) Nombre del archivo==
- c) Tamaño del archivo
- d) Contiene todos los datos mencionados

**La fragmentación interna de archivos se produce porque:**

- a) Los bloques de datos están dispersos en el disco
- ==b) La información para almacenar no ocupa un bloque completo==
- c) La estructura de nodos índice y las tablas de archivos son muy grandes
- d) Ninguna de las anteriores

**Al transferir datos utilizando DMA por robo de ciclos:**

- a) Se utiliza solo el bus hasta finalizar toda la transferencia
- ==b) El bus del sistema está la mayor parte a disposición de la CPU==
- c) Se transfieren grandes cantidades de bloques entre los dispositivos
- d) Todas las anteriores

**Al montar un sistema de archivos:**

- a) El directorio donde se monta debe estar necesariamente vacío, de lo contrario arroja error
- ==b) Para hacer referencia a un archivo dentro del sistema de archivos montado se debe incluir en la ruta el directorio donde se montó el sistema de archivos==
- c) El sistema de archivos queda montado hasta que se apague el sistema
- d) Todas las anteriores

**Dada una arquitectura de discos RAID 5 compuesta por 3 discos mecánicos, cada uno de 250 Gb:**

- a) Puedo almacenar hasta 750 Gb
- b) No se puede implementar porque no dispongo de una controladora con soporte RAID
- c) Si se rompe un disco se pierde toda la información
- ==d) Puedo almacenar 500 Gb==

**Los SSOO POSIX implementan VFS, esto es posible porque VFS es capaz de:**

- a) Leer el MBR
- ==b) Leer el superbloque==
- c) Leer el sistema de archivos /boot
- d) Ninguna de las anteriores

**Un sistema de archivo POSIX contiene:**

- a) Nodos índice
- b) Tabla de archivos
- c) Mapa de bits
- ==d) Todas las anteriores==

**Un hard link:**

- a) Se puede implementar solamente dentro del mismo sistema de archivos
- b) Pueden existir tantos links como desee
- c) Al ser más de 1 link es imposible conocer cuál es el archivo original
- ==d) Todas las anteriores==

**Qué afirmación es correcta respecto a DMA?**

- ==a) Se utiliza para minimizar el uso de las interrupciones==
- b) Puede ralentizar el flujo de información desde la CPU a Memoria y viceversa
- c) Accede a porciones de memoria del proceso que está bloqueado
- d) Todas las anteriores

**La gestión de E/S dirigida por interrupciones:**

- a) El flujo de información dispositivo/memoria se maneja por un demonio que lee o escribe de y hacia el controlador
- b) El CPU se mantiene en espera activa (idle)
- c) El CPU espera que el bus de datos esté lo suficientemente lleno para efectuar las transferencias
- d) Todas las anteriores
- ==ninguna cldo==

**Un sistema operativo utiliza Round Robin para planificar sus procesos y emplea memoria virtual paginada. Cuando se produce un fallo de página, ¿qué le ocurre al proceso causante mientras se recupera del disco la página afectada?**

- a) Pasa al estado de listo
- ==b) Pasa al estado de bloqueado==
- c) Pasa al estado terminado
- d) Ninguna de las anteriores

**Es preferible una tabla de páginas multinivel en comparación con una tabla de páginas de un solo nivel para traducir direcciones virtuales a dirección física porque:**

- a) Reduce la cantidad de accesos a la memoria principal al buscar una ubicación de memoria
- ==b) Ayuda a reducir el tamaño de la tabla de páginas necesaria para implementar el espacio de direcciones virtuales de un proceso==
- c) Es requerido para utilizar el TLB
- d) Reduce el número de fallos de página en los algoritmos de sustitución de páginas

**Por qué no se pueden crear enlaces duros (hard) hacia archivos que están ubicados en otra partición/sistema de archivo?**

- a) Si es posible ya que dentro de la estructura del i-nodo se encuentra la ruta absoluta hacia el archivo que se esta enlazado
- ==b) Porque los i-nodos identifican a un archivo, y esta numeración es propia de cada partición a la que se hace referencia==
- c) Si es posible, pero debe ser montado el sistema de archivo correspondiente para luego realizar el enlace
- d) Ninguna de las anteriores

**Generalmente un driver forma parte del kernel, pero podría encontrarse en espacio de usuario, esto implica:**

- a) El driver debe apropiarse de la CPU hasta terminar lo que está haciendo
- ==b) Hacer llamadas al sistema para acceder a los registros del dispositivo==
- c) Bajo una política de planificación expropiativa se corre el riesgo de monopolizar el CPU
- d) Ninguna de las anteriores

**La hiperpaginación o thrashing se produce cuando hay demasiados intercambio de páginas de y hacia el swap. ¿Cómo se puede mitigar esta situación?**

- a) Aumentar el tamaño del swap
- b) Utilizar marcos de página más pequeños
- ==c) Agregando RAM a la computadora==
- d) Todas las anteriores

**Independientemente del tipo de implementación ya sea nodo-i o listas enlazadas, será necesario tener estructuras de datos para representar a las mismas. Estas estructuras de datos donde se encuentran?**

- a) En memoria principal
- b) Se almacenan en el MBR ya que es quien se encarga de administrar las particiones
- ==c) En los bloques destinados para cada sistema de archivo dentro las particiones==
- d) Ninguna de las anteriores

**Se utiliza una tubería con nombre (named pipe) para comunicar dos procesos:**

- a) El proceso productor se bloquea cuando la tubería está vacía
- b) El proceso consumidor se bloquea cuando la tubería está llena
- ==c) Si se borra la tubería ambos procesos se abortan==
- d) Todas las anteriores

**El uso de listas enlazadas simples en los bloques de un archivo garantiza:**

- a) Que la búsqueda de los datos sea muy rápida
- b) La recuperación de los datos es eficiente en caso que se pierda un link
- c) Que no se cargue en memoria cuando sea necesario acceder a un archivo determinado
- ==d) Ninguna de las anteriores==

**Un proceso en background puede ser creado por:**

- a) El sistema operativo
- b) Una petición de usuario
- c) Otro proceso
- ==d) TODAS SON CORRECTAS==

**El algoritmo de planificación FCFS (Primero en llegar, primero en ser atendido):**

- a) Es adecuado para procesos Batch
- b) No optimiza el tiempo de espera
- c) No optimiza el rendimiento
- ==d) Todas son correctas==

**Una Trampa**

- ==a) todas son correctas==
- b) Es detectada por el hardware o el microprograma
- c) Es síncrona con el proceso
- d) Es iniciada por una condición especial causada por el proceso que se está ejecutando

**Cuando ocurre una trampa:**

- ==a) todas son correctas==
- b) Pasa a ejecutarse el manejador de trampas
- c) Es iniciada por una condición del programa en ejecución
- d) Se produce un cambio de contexto

**En un sistema operativo multiusuario multitarea, cuando se completa el quantum de tiempo dado a un proceso, el proceso pasa del estado de ejecución a:**

- a) Estado terminado
- b) Estado bloqueado
- ==c) Ninguna es correcta==
- d) Estado suspendido

**Una entrada a la tabla de vectores de interrupción contiene:**

- ==a) El nombre de la rutina de tratamiento.==
- b) El número de la interrupción.
- c) Ninguna es correcta
- d) El ID del proceso que trata la interrupción.

**El nivel ISA**

- a) Es la interfaz entre el software y el hardware
- b) Se ubica entre el sistema operativo y la microprograma
- c) Define la interfaz entre los compiladores y el hardware
- ==d) TODAS SON CORRECTAS==

**El nodo índice no posee:**

- ==a) El nombre del archivo==
- b) Tipo de Fichero y Protección
- c) Número de Nombres
- d) Propietario

**La implementación del DMA permite que:**

- a) La transferencia de datos entre el controlador y la memoria no la haga la CPU.
- b) La transferencia de datos entre el controlador y la memoria genere menos interrupciones.
- c) La transferencia de datos entre el controlador y la memoria la haga un controlador de DMA.
- ==d) Las tres anteriores son válidas.==

**Cuál de las siguientes afirmaciones es correcta sobre los drivers de un dispositivo:**

- ==a) Todas son correctas==
- b) Proporciona una interfaz entre el SSOO y la controladora del dispositivo.
- c) Está en espacio de kernel o usuario, dependiendo de la implementación
- d) Un driver escrito para un ambiente de programación POSIX no funciona en Windows.

**Un enlace blando o soft link:**

- a) Permite enlazar archivos de un sistema de archivo a otro
- b) Permite enlazar varios archivos
- c) Permite enlazar archivos del tipo dispositivos
- ==d) TODAS SON CORRECTAS==

**Un soft link o link simbólico:**

- a) No duplica la información almacenada en un dispositivo
- b) Se conoce cuál es el archivo original
- c) Se puede utilizar para enlazar archivos del mismo file system.
- ==d) todas son correctas==

**Un hard link o link duro:**

- a) Duplica la información almacenada en un dispositivo
- b) Se utiliza para enlazar archivos de distintos file systems
- c) Se conoce cuál es el archivo original
- ==d) Ninguna es correcta==

**El uso de listas enlazadas garantiza:**

- a) Se puede usar todo el bloque para los datos
- b) El acceso aleatorio será más sencillo, aunque se recorra toda la cadena.
- ==c) Solo se almacena el número de bloque inicial==
- d) Desventajas de listas enlazadas: Toda la tabla debe estar en memoria todo el tiempo para que funcione

**Al utilizar nodos índice, la longitud o tamaño de un archivo:**

- a) Se actualiza constantemente.
- b) Depende del tamaño del dispositivo que contenga el archivo.
- c) Depende de la cantidad de punteros que posea y la longitud de bloques del sistema de archivos.
- ==d) TODAS ESTAS SON CORRECTAS==

**En relación con el fraccionamiento de la memoria, ese fraccionamiento puede ser interno o externo a los bloques en que se divide un espacio de direccionamiento. Cuál de las siguientes afirmaciones es correcta:**

- a) La paginación puede generar fraccionamiento interno en los cuadros o marcos de página.
- b) La segmentación puede generar fraccionamiento externo en el espacio de direccionamiento físico.
- c) El modo de direccionamiento real puede generar fraccionamiento externo en el espacio de direccionamiento físico.
- ==d) Las tres anteriores son correctas==

**¿Cuál es la ventaja de utilizar DMA (acceso directo a memoria) respecto de E/S controlada por interrupciones?**

- a) DMA permite la ejecución simultánea de múltiples transferencias entre dispositivos
- ==b) DMA permite realizar transferencias de datos a mayor velocidad porque no requiere intervención del CPU==
- c) DMA reduce la latencia de respuesta del sistema a las operaciones de E/S
- d) Ninguna de las anteriores

**¿Qué información no se almacena en el nodo índice?:**

- a) El propietario del archivo
- ==b) El nombre del archivo si se trata de un link simbólico==
- c) El tipo de archivo
- d) Ninguna de las anteriores

**¿Qué afirmación es correcta respecto de un driver:**

- a) Se ejecuta cuando un dispositivo está utilizando el buffer
- ==b) En un sistema monolítico al incorporar un nuevo driver al kernel, éste debe ser recompilado==
- c) Permite el acceso directo del hard con el sistema operativo
- d) Ninguna de las anteriores

**Sabemos que los sistemas de archivos se identifican con el denominado número mágico. El mismo se almacena en:**

- a) El MBR
- b) El directorio raíz
- c) En el sector 0 del disco
- ==d) Ninguna de las anteriores==

**Al utilizar nodos índice, la fragmentación interna de un archivo se evita con la/s siguiente/s acciones:**

- a) Reutilizar bloques fragmentados de otros archivos
- b) Utilizar herramientas para desfragmentar el dispositivo donde se aloja el archivo
- c) Formatear el sistema de archivos con tamaños de bloques pequeños
- ==d) Ninguna de las anteriores==

**Al utilizar nodos índice, la longitud o tamaño de un archivo:**

- a) Se actualiza constantemente
- b) Depende de la cantidad de punteros que posea y la longitud del bloque del sistema de archivos
- c) Depende del tamaño del dispositivo que contenga el archivo
- ==d) Todas las anteriores==

**¿Qué sucede si se produce una interrupción mientras el CPU está atendiendo otra interrupción?**

- a) Se detiene el bloqueo hasta que ambas interrupciones se resuelvan
- b) La nueva interrupción se ignora
- ==c) La nueva interrupción se pone en cola o se atiende si tiene mayor prioridad que la actual==
- d) Ninguna de las anteriores

**¿Qué componente del sistema operativo gestiona la comunicación entre diferentes sistemas de archivos y los dispositivos de almacenamiento?**

- a) Controlador del dispositivo
- ==b) Sistema de archivos virtual (VFS)==
- c) Tabla de nodos índice
- d) Ninguna de las anteriores

**¿Cuál es el principal propósito de un sistema de E/S en un sistema operativo moderno?**

- a) Asegurar la comunicación directa entre el CPU y los dispositivos periféricos
- ==b) Proporcionar una interfaz abstracta entre el software y el hardware para gestionar dispositivos de manera eficiente==
- c) Permitir que los dispositivos de hardware funcionen a velocidades más rápidas que la CPU
- d) Garantizar que los dispositivos periféricos nunca interfieran con la ejecución del proceso principal

**Un enlace blando o soft link:**

- a) Permite enlazar archivos del mismo sistema de archivos
- b) Permite enlazar archivos de distintos sistemas de archivos
- c) Permite enlazar directorios
- ==d) Todas las anteriores==

**¿Qué información se almacena en el nodo índice?:**

- a) El tamaño del archivo
- b) El propietario del archivo
- c) La fecha y hora de última modificación
- ==d) Todas las anteriores==

**Al utilizar 3 discos de 2 Tb. cada uno dispuestos en RAID 5, el espacio disponible es de:**

- a) 2 Tb
- b) 3 Tb
- c) 6 Tb
- ==d) Ninguna de las anteriores==

**¿Cuál afirmación es correcta sobre el mecanismo de interrupciones?**

- a) El CPU y la controladora de dispositivos deben sincronizarse para realizar la(s) E/S
- b) La controladora de dispositivos (hardware) no interrumpe directamente al CPU
- c) El PIC prioriza todas las interrupciones ya sean enmascarables o no enmascarables
- ==d) Todas las anteriores==

**Un driver:**

- a) Se ejecuta cuando un dispositivo está utilizando el buffer
- b) En un sistema monolítico al incorporar un nuevo driver al Kernel no requiere ser recompilado el mismo
- c) Siempre está en espacio de usuario
- ==d) Ninguna de las anteriores==

**El número mágico que identifica un sistema de archivos se encuentra en:**

- a) El MBR
- b) El directorio raíz
- c) En el sector 0 del disco
- ==d) Ninguna de las anteriores==

**¿Cuál de las siguientes acciones evita la fragmentación interna en archivos?**

- a) Utilizando herramientas para desfragmentar el disco
- b) Reutilizando los bloques fragmentados con otros archivos
- c) Reutilizando el espacio sobrante dentro del bloque del archivo con datos de otro archivo
- ==d) Ninguna de las anteriores==

**En los sistemas UNIX-LIKE los dispositivos pueden ser denegados a ciertos usuarios, esto se logra porque:**

- a) El controlador del dispositivo bloquea a los usuarios
- b) El driver es el encargado de asignar o no dispositivos a los procesos de usuarios
- c) Los dispositivos no son tratados como archivos
- ==d) Ninguna de las anteriores==

**El uso de listas enlazadas garantiza:**

- a) Que la búsqueda de los datos sea muy rápida
- b) Que la recuperación de los datos es eficiente en caso que se pierda un link
- c) Que la FAT se cargue en memoria cuando sea necesario acceder a un archivo determinado
- ==d) Ninguna de las anteriores==

**Al utilizar tablas de nodos índice (i-node). El tamaño máximo de un archivo depende de:**

- a) La capas de software de F/S
- b) La cantidad de File Systems que posea el sistema
- c) La controladora del dispositivo
- ==d) Ninguna de las anteriores==

**Un proceso sucio entra a ejecución. Para evitar que monopolice el procesador el planificador debe ser:**

- a) El que primero llega es el primero que se ejecuta
- ==b) Round Robin==
- c) El de menor tiempo restante
- d) Ninguna de las anteriores es correcta

**Se dispone de un recurso y 10 procesos necesitan modificar el valor del mismo. ¿Cuántos semáforos son necesarios para evitar el acceso concurrente de todos los procesos al recurso?**

- ==a) Un semáforo para los 10 procesos==
- b) 10 semáforos, uno por proceso
- c) 11 semáforos, uno para cada proceso y uno por recurso
- d) Ninguna de las anteriores es correcta

**La TLB (Translation Lookaside Buffer):**

- a) Es una caché especial para las entradas de acierto de página en la tabla de páginas
- b) Se utiliza para acelerar el proceso de traducción de direcciones virtuales a direcciones lógicas
- c) Es gestionada por el MMU
- ==d) Todas las anteriores son correctas==

**En un ambiente monousuario mono tarea sin memoria virtual ¿Cuál es el intercambio (swapping) en la gestión de memoria?**

- ==a) El proceso de mover todo el proceso entre la memoria RAM y el disco duro==
- b) El proceso de mover todo el proceso entre la memoria RAM y el disco duro
- c) El proceso de mover marcos de páginas entre la RAM y el disco duro
- d) Ninguna de las anteriores es correcta

**Suponga que la BCP contiene información sobre los procesos. ¿En qué instancias NO se modifica el mismo?**

- a) Finalización del proceso
- ==b) Ejecutar hilos a nivel usuario==
- c) Planificación de la prioridad del proceso
- d) Cambio de contexto del proceso

**Cuando utilizamos segmentos para asignar memoria a los procesos se dispone del registro base y el registro límite para garantizar que el proceso no realice saltos a direcciones que no son propias. ¿Al utilizar paginación simple cuáles son los equivalentes a esos registros?**

- a) Los bits más significativos de la dirección virtual y los bits menos significativos de la dirección virtual
- b) La dirección almacenada en la tabla de páginas y el puntero al marco de página virtual leído por la CPU al MMU
- ==c) La dirección física del marco de página y los bits menos significativos de la dirección virtual==
- d) Ninguna de las anteriores es correcta

**Un proceso genera un programa con direcciones:**

- a) Relativas al programa
- ==b) Relativas al proceso==
- c) Relativas a la memoria principal
- d) Ninguna de las anteriores es correcta

**Un proceso está ejecutando pero debe atender una rutina de tratamiento de interrupción, entonces:**

- a) El proceso pasa a la cola de listos
- ==b) El proceso se suspende==
- c) El proceso se bloquea
- d) El proceso se sigue ejecutando hasta que solicite E/S

**¿Cuál es una de las principales desventajas de la espera ocupada?**

- a) Minimiza el uso de la CPU
- ==b) Consume una cantidad significativa de tiempo de CPU==
- c) Aumenta la eficiencia del sistema al permitir que varios procesos se ejecuten simultáneamente
- d) Mejora la velocidad de ejecución de los procesos en espera

**¿Cuál es el principal beneficio de usar una tabla de páginas multinivel?**

- a) Reduce la fragmentación externa de la memoria
- b) Aumenta el tiempo de acceso a la memoria
- ==c) Reduce la cantidad de memoria necesaria para almacenar las tablas de páginas==
- d) Permite que las tablas de páginas estén completamente cargadas en la memoria física

**Un compilador:**

- ==a) Genera direcciones relativas al ejecutable==
- b) Genera direcciones relativas al proceso
- c) Genera direcciones relativas al disco donde se alojará el ejecutable
- d) Ninguna de las anteriores

**¿Cuál de estos mecanismos no es indispensable para construir un SSOO con multiprogramación y protección entre usuarios?**

- ==a) Memoria virtual==
- b) Instrucciones de E/S que solo pueden ejecutarse en modo kernel
- c) Modos de operación: usuario y kernel
- d) Protección de memoria

**Al utilizar sistema de archivos ext2:**

- a) Se cargan en memoria todos los nodos índice de todos los sistemas de archivos que tiene montado antes de acceder a alguno de los archivos
- b) Disminuye la fragmentación interna de los archivos
- c) Existe un número de nodo índice exclusivo para cada archivo, aún cuando tenga más de un FS montado sobre un VFS
- ==d) Ninguna de las anteriores==

**Al utilizar TLB:**

- a) Se garantiza que no se produzcan fallos de página
- b) Incrementa el grado de multiprogramación
- c) No es necesaria el área de swap
- ==d) Ninguna de las anteriores==

**Al utilizar 2 discos de 2 Tb. dispuestos en RAID 0, el espacio disponible es de:**

- a) 2 Tb
- ==b) 4 Tb==
- c) 8 Tb
- d) Ninguna de las anteriores

**Un enlace duro o hard link:**

- a) Solo permite enlazar archivos del mismo sistema de archivos
- b) Permite enlazar varios archivos
- c) Permite enlazar archivos del tipo dispositivos
- ==d) Todas las anteriores==

**Que ventaja logra la independencia del dispositivo:**

- a) Que modela los dispositivos como si fuesen archivos
- ==b) Que al momento de escribir un programa no es necesario conocer el dispositivo==
- c) Los errores son manejados por el driver
- d) Ninguna de las anteriores

**¿Cuántas operaciones de disco se necesitan para obtener el nodo-i /home/os/cursos/2k13/parcial.sh? Suponga resolución completa y que todos los contenidos de los directorios caben en un bloque de disco.**

- a) 7
- ==b) 6==
- c) 5
- d) Ninguna de las anteriores

---

<u>**Preguntas sin opciones**</u>

---

**¿Para qué se usa un semáforo binario en el problema del productor y consumidor?** 2

• a. Para que el recurso sea solo obtenido por un solo proceso 3


**¿Cuál de estas técnicas sirve para evitar que tengamos en la memoria física varias copias duplicadas del mismo código?** 4

• a. Bibliotecas de enlace dinámico (DLL) o bibliotecas compartidas 5


**El intercambio de procesos consiste en:** 6

• a. Copiar todo el proceso al disco para darle lugar a otro proceso en la memoria principal 7


**La TLB (Translation Loockaside Buffer)** 8

• a. Es una caché especial para las entradas de la tabla de páginas 9


**El algoritmo de sustitución de páginas de segunda oportunidad:** 10

• a. Requiere de una tabla adicional para contener una cola con las páginas 11


Para una dirección lógica de 32 bits con el formato $$número de página (22 bits), desplazamiento de la página (10 bits)$$
: 12

• a. Hay un total de 2^22 páginas de tamaño 1 Kbytes 13


**El sistema operativo y los otros procesos están protegidos de ser modificados por otro proceso porque:** 14

• a. Cada dirección generada por la CPU se está comprobando contra los registros de base y límite 15


**En un sistema multiusuario multitarea con memoria paginada se ejecutan varios procesos e hilos ¿Cuántas tablas de páginas diferentes existen en un momento dado?** 16

• a. Tantas como procesos hay 17


**Dada una dirección virtual, los bits menos significativos identifican a:** 18

• a. El desplazamiento dentro del marco de pagina en la memoria principal. 19


**El proceso de interpretación consiste en:** 20

• a. Las instrucciones en L1 son examinadas una por una por un programa el LO y se ejecutan en LO. 21


**La tabla de página contiene:** 22

• a. La dirección base de cada página en la memoria física. 23


**El MMU busca en el TLB una pagina determinada pero no es encontrada, entonces:** 24

• a. Si se encuentra la pagina en la tabla de paginas se actualiza la TLB con la página encontrada. 25


**¿Cuál de las siguientes es una diferencia entre una memoria paginada y la segmentada?** 26

• a. La memoria paginada divide la memoria en bloques de tamaño fijo, mientras que la segmentada divide la memoria en segmentos de diferentes tamaños. 27


**¿Qué es la fragmentación externa en la gestión de memoria?** 28

• a. La acumulación de pequeños espacios libres entre bloques de memoria asignados 29

**¿Qué es un hilo?**
• a. Una porción de un proceso que puede ser ejecutada en paralelo con otros hilos 30


**¿Qué es el intercambio o swapping en la gestión de memoria?** 31

• a. El proceso de mover todo el proceso entre la memoria Ram y el disco duro 32


**¿Qué es un proceso en estado bloqueado?** 33

• a. Un proceso que esta esperando un recurso, como un archivo o un dispositivo. 34


**¿Qué es el algoritmo de reemplazo de página LRU (Least recenty used)?** 35

• a. Reemplaza la página que ha estado en memoria por mas tiempo sin ser utilizada. 36


**¿Qué es la TLB en la gestión de memoria virtual?** 37

• a. Una tabla que almacena direcciones físicas correspondientes a direcciones virtuales. 38


**¿Qué es el cambio de contexto?** 39

• a. Cambiar de un proceso a otro en la CPU 40


**¿Cuál de las siguientes es una ventaja de la memoria virtual?** 41

• a. Permite que los programas utilicen mas memoria de la que realmente está disponible en la memoria RAM 42


**Después de concluida la transferencia DMA el procesador es notificado por:** 43

• (Respuesta): Señal de interrupción 44


**DMA transmite o recibe de memoria hasta que el conteo sea cero, en ese momento quien genera la interrupción:** 45

• (Respuesta): El propio DMA 46


**En la E/S sin asignación de memoria, la transferencia de datos entre el registro del controlador y la CPU la hace:** 47

• (Respuesta): Una función especial desarrollado en el nivel ISA de la máquina. 48


**¿Cuál afirmación NO es correcta sobre el mecanismo de interrupciones?** 49

• (Respuesta): La controladora de dispositivos interrumpe directamente al CPU. 50


**(Una vez que se ha terminado una operación de E/S...) En este caso la interrupción la genera:** 51

• (Respuesta): El controlador del dispositivo que estaba realizando la operación de E/S 52


**Si las interrupciones se producen constantemente como se logra que la CPU se la pase todo el tiempo atendiéndolas:** 53

• (Respuesta): Deshabilitando el bit IF del PSW 54


**Si las interrupciones se producen constantemente, ¿cómo se evita que el CPU entre en un loop infinito de atención de interrupciones?:** 55

• (Respuesta): Deshabilitando el IF de la PSW 56


**El vector de interrupción contiene:** 57

• (Respuesta): La dirección de la rutina de tratamiento de la interrupción. 58

En los estratos del software de E/S, uno de los niveles es el manejador de interrupciones. Con relación a este nivel, cuál de las siguientes afirmaciones es correcta: 59

• a. La función que cumple este nivel depende de las particularidades de cada dispositivo. 60


**En relación con la maquina multinivel el sistema operativo... ello implica que todos los niveles que están sobre el nivel del sistema operativo:** 61

• a. Invocan servicios del sistema operativo a través de las llamadas al sistema. 62


**Cuando se realiza un cambio de contexto a raíz de una interrupción:** 63

• (Respuesta): Se almacena el psw y el pc del programa en ejecución en una pila 64


**Los drivers en espacio de kernel:** 65

• (Respuesta): Es más eficiente que tenerlo en espacio de usuario 66


**Asignar o liberar dispositivos dedicados es tarea de:** 67

• (Respuesta): Software independiente del dispositivo 68


**Un driver en espacio de usuario implica que:** 69

• (Respuesta): Se deben realizar llamadas al sistema cada vez que se necesite I/O. 70


**¿Cuál es la importancia de contar con una interfaz uniforme para los drivers?** 71

• (Respuesta): Para que los drivers se adapten al sistema operativo 72


**En un entorno de programación POSIX, el nodo índice:** 73

• (Respuesta): Contiene el contador de links 74


**Para implementar un soft link o link simbólico:** 75

• (Respuesta): Es necesario utilizar una entrada adicional en la tabla de archivos 76

En una implementación de Sistemas de archivos UNIX-LIKE. Como se representan los directorios. 77

• (Respuesta): CON EL NODO INDICE 78


**Un sistema de archivos se monta sobre un directorio que no está vacío entonces:** 79

• a. Se ocultan los archivos del directorio donde se monta el sistema de archivos. 80


**Un punto de montaje es:** 81

• (Respuesta): un directorio vacío o no en el que se adjuntará el sistema de archivos montado 82


**(En el mecanismo de segmentación...) Quien se encarga de ajustar el tamaño del segmento es:** 83

• (Respuesta): El descriptor de segmento (de la tabla de segmentos) que indica la posición en memoria donde se ubica el segmento y el tamaño que posee cada segmento. 84


**La ventaja de la paginación frente a la segmentación es que:** 85

• (Respuesta): PUEDEN DISTINGUIRSE LOS PROCEDIMIENTOS Y LOS DATOS Y ADEMAS ESTOS DE AQUELLOS EN FORMA INDEPENDIENTE 86


**En relación con la paginación, quien establece la relación entre direcciones virtuales y direcciones de memoria física es:** 87

• (Respuesta): Las tablas de pagina 88


**La implementación de la paginación multinivel... permite:** 89

• (Respuesta): Que el cuadro de página se acceda sin tener que cargar la totalidad de las tablas en memoria 90


**La segmentación al tener un tamaño variable del segmento permite** 91

• (Respuesta): Evitar el fraccionamiento interno de la memoria 92


**Uno de los fundamentos del diseño de software de E/S es la denominación Uniforme, esto significa que:** 93

• a. Dispositivos de un mismo tipo, como almacenamiento secundario, sean direccionados de la misma forma. 94


**Cuando desde un proceso de usuario se ejecuta una llamada al sistema, implica que el sistema operativo** 95

• a. Ejecute el planificador de procesos para establecer cuál es el próximo proceso para ejecutarse 96


**Los dispositivos de E/S pueden estar delineados... La diferencia entre estos dos modos de implementación es:** 97

• (Respuesta): Que, al no estar delineados en memoria, los datos que se leen o escriben en los registros de los controladores requieren de la ejecución de instrucciones que lean o escriban en los puertos de E/S. 98


**Los dispositivos de E/S se pueden dividir en dos categorías, dispositivos de bloque y dispositivos de carácter:** 99

• a. Un dispositivo de bloque almacena información en bloques de tamaño fijo, cada uno con su propia dirección 100


**En el mecanismo de segmentación los segmentos tienen un límite de tamaño máximo... Este tamaño máximo queda determinado por:** 101101101101

• (Respuesta): La cantidad de bits (según la arquitectura) que poseen los registros apuntadores de la CPU 102


**En relación con el mecanismo de paginación, la cantidad de entradas que posee la tabla de paginación queda determinado por:** 103

• (Respuesta): la cantidad total de bits asignados a la dirección virtual 104


**En relación con el mecanismo de paginación, el espacio total de direccionamiento virtual queda determinado por:** 105

• (Respuesta): la cantidad de bits (según la arquitectura) que poseen los registros apuntadores de la CPU 106


**La implementación de mecanismos de direccionamiento virtual... Una de esas desventajas es:** 107

• (Respuesta): Que se requiere mucho espacio de disco para almacenar las tablas de páginas o de segmentos. 108


**La implementación de mecanismos de direccionamiento virtual... Una de esas ventajas es:** 109

• (Respuesta): El espacio de direccionamiento virtual puede ser mayor que el espacio de memoria física. 110


**La forma que tiene el sistema operativo de evitar el interbloqueo es:** 111

• a. Asignado un recurso a un proceso, cuando esa asignación lleva a un estado seguro. 112

Para que haya estancamiento... una de ellas es la de contención y espera. En este caso se cumple esta condición cuando: 113

• a. Un proceso A posee un recurso R y solicita otro recurso S que lo posee otro proceso B, y este ultimo a su vez solicita el recurso R 114

Para que haya estancamiento... una de ellas es la "No apropiativa". En qué caso se cumple esta condición: 115

• a. Cuando un proceso A posee un recurso no apropiativo, otro proceso B no se lo puede extraer por la fuerza. 116

Si bien semáforos y mutex se utilizan para sincronizar procesos existe una diferencia entre ellos. Indique cuales son las diferencias. 117

• (Respuesta): Los semáforos pueden contar, los mutex solo toman 2 valores 118


**Una ventaja de los mecanismos de exclusión mutua sin espera ocupada es que:** 119

• a. El S.O. bloquea el acceso a una variable para impedir que un proceso entre en su región critica. 120


**El mecanismo de exclusión con semáforos debe implementarse con acciones atómicas... cual de las siguientes afirmaciones es cierta:** 121

• a. La acción atómica se aplica cuando se modifica cualquiera de los semáforos. 122


**Se dispone de una RAID 1+0 Cual de estos disminuye la performance del RAID:** 123

• a. NINGUNA ya que esta combinación de raid es la más rápida pero la más cara 124