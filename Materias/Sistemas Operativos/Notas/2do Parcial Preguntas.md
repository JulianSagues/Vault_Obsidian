1. ¿Qué información se almacena en el nodo indice?:  
    a) El tamaño del archivo.  
    b) El propietario del archivo.  
    c) La fecha y hora de última modificación.==(d) Todas las anteriores.==

  
2) Al utilizar 3 discos de 2 Tb. cada uno dispuestos en RAID 5, el espacio disponible es de:  
a) 2 Tb.  
b) 3 Tb.  
c) 6 Tb.==d) Ninguna de las anteriores.==

  
3) ¿Cual afirmación es correcta sobre el mecanismo de interrupciones?  
a) El CPU y la controladora de dispositivos deben sincronizarse para realizar la(s) E/S  
b) La controladora de dispositivos (hardware) no interrumpe directamente al CPU.  
c) EI PIC prioriza todas las interrupciones ya sean enmascarables o no enmascarables.==d) Todas las anteriores.==

  
4) Un driver:  
a) Se ejecuta cuando un dispositivo está utilizando el buffer.  
b) En un sistema monolitico al incorporar un nuevo driver al Kemel no requiere ser recompilado el mismo.  
c) Siempre está en espacio de usuario.==d) Ninguna de las anteriores.==

  
5) Un enlace blando o soft link:  
a) Permite enlazar archivos de un sistema de archivos a otro.  
b) Permite enlazar varios archivos  
c) Permite enlazar archivos del tipo dispositivos.==d) Todas las anteriores.==

  
6) El número mágico que identifica un sistema de archivos se encuentra en  
a) EI MBR.  
b) El directorio raiz  
c) En el sector 0 del disco.==d) Ninguna de las anteriores.==

ELNÚMERO MÁGICO ESTÁ EN EL SUPERBLOQUE

  
7) ¿Cuál de las siguientes acciones evita la fragmentación interna en archivos?  
a) Utilizando herramientas para desfragmentar el disco  
b) Reutilizando los bloques fragmentados con otros archivos.  
c) Reutilizando el espacio sobrante dentro del bloque del archivo con datos de otro archivo.==d) Ninguna de las anteriores.==

  
8) En los sistemas UNIX-LIKE los dispositivos pueden ser denegados a ciertos usuarios, esto se logra porque:  
a) El controlador del dispositivo bloquea a los usuarios.  
b ) El driver es el encargado de asignar o no dispositivos a los procesos de usuarios.  
c) Los dispositivos no son tratados como archivos.==d) Ninguna de las anteriores==

  
9) El uso de listas enlazadas garantiza  
a) Que la búsqueda de los datos sea muy rápida.  
b) Que la recuperación de los datos es eficiente en caso que se pierda un link.  
c) Que la FAT se cargue en memoria cuando sea necesario acceder a un archivo determinado==d) Ninguna de las anteriores.==

  
10) Al utilizar tablas de nodos indice (i-node). El tamaño máximo de un archivo depende de  
a) La capas de software de E/S.  
b) La cantidad de File Systems que posea el sistema.  
c) La controladora del dispositivo.==d) Ninguna de las anteriores.==

---

---

1. ¿Cuál es la ventaja de utilizar DMA (acceso directo a memoria) respecto de E/S controlada por interrupciones?  
    a) DMA permite la ejecución simultánea de múltiples transferencias entre dispositivos.
    
    ==b) DMA puede realizar transferencias de datos a mayor velocidad porque no requiere intervención del CPU.==
    
    c) DMA reduce la latencia de respuesta del sistema a las operaciones de E/S
    

1. ¿Qué información no se almacena en el nodo índice?:  
    a) El propietario del archivo.==b) El pathname del link si se trata de un link simbólico.  
    ==c) El tipo de archivo.  
    d) Ninguna de las anteriores.

1. Que afirmación es correcta respecto de un driver:  
    a) Se ejecuta cuando un dispositivo está utilizando el buffer.==b) En un sistema monolitico al incorporar un nuevo driver al kernel, éste debe ser recompilado.  
    ==c) Permite la sincronización del shell con el sistema operativo.  
    d) Ninguna de las anteriores.

1. Sabemos que los sistemas de archivos se identifican con el denominado número mágico. El mismo se almacena en  
    a) EI MBR  
    b) El directorio raíz  
    c) En el sector O del disco.==d) Ninguna de las anteriores.==

1. Al utilizar nodos índice, la fragmentación interna de un archivo se evita con la/s siguiente/s acciones:  
    a) Reutilizar bloques fragmentados de otros archivos.  
    b) Utilizar herramientas para desfragmentar el dispositivo donde se aloja el archivo  
    c) Formatear los sistemas de archivos con tamaños de bloques pequeños.==d) Ninguna de las anteriores. ACA TENGO DUDAS==

1. Al utilizar nodos indice, la longitud o tamaño de un archivo  
    a) Se actualiza constantemente.  
    b) Depende de la cantidad de punteros que posea y la longitud del bloque del sistema de archivos  
    c) Depende del tamaño del dispositivo que contenga el archivo.==d) Todas las anteriores.==

1. ¿Qué sucede si se produce una interrupción mientras el CPU está atendiendo otra interrupción?  
    a) El sistema se bloquea hasta que ambas interrupciones se resuelvan.  
    b) La nueva interrupción se ignora.==c) La nueva interrupción se pone en cola o se atiende si tiene mayor prioridad que la actual.==

1. ¿Qué componente del sistema operativo gestiona la comunicación entre diferentes sistemas de archivos y los dispositivos de almacenamiento?  
    a) Controlador del dispositivo==b) Sistema de archivos virtual (VFS)  
    ==c) Tabla de nodos índice  
    d) Ninguna de las anteriores

1. ¿Cuál es el principal propósito de un sistema de E/S en un sistema operativo moderno?  
    a) Asegurar la comunicación directa entre el CPU y los dispositivos periféricos.==b) Proporcionar una interfaz abstracta entre el software y el hardware para gestionar dispositivos de manera eficiente.  
    ==c) Permitir que los dispositivos de hardware funcionen a velocidades más rápidas que la CPU.  
    d) Garantizar que los dispositivos periféricos nunca interfieran con la ejecución del proceso principal,

1. Un enlace blando o soft link:  
    al Permite enlazar archivos del mismo sistema de archivos.  
    b) Permite enlazar archivos de distintos sistemas de archivos.  
    c) Permite enlazar directorios==d) Todas las anteriores==

---

---

1. ¿Qué información se almacena en el nodo Índice?:  
    a) El número de nodo índice.  
    b) El tipo de sistema de archivo.  
    c) Punteros indirectos a bloques de datos.==d) Todas las anteriores.==

1. Al utilizar 2 discos de 2 Tb. dispuestos en RAID 0, el espacio disponible es de:  
    a) 2 Tb.==b) 4 Tb. Para mi es esta, pero se la puso mal, se puede equivocar.  
    ==c) 1.5 Tb.  
    d) Ninguna de las anteriores

1. ¿Cual afirmación es correcta sobre el mecanismo de interrupciones?  
    a) El CPU y la controladora de dispositivos deben sincronizarse para realizar la(s) E/S.  
    b) La controladora de dispositivos (hardware) no interrumpe directamente al CPU.  
    c) EI PIC prioriza todas las interrupciones ya sean enmascarables o no enmascarables.==d)Todas las anteriores.==

1. Un driver:  
    a) Se ejecuta cuando un dispositivo está utilizando el buffer.  
    b) En un sistema monolitico al incorporar un nuevo driver al Kernel no requiere ser recompilado el mismo.==c) Sirve en definitiva para comunicar el SO con la controladora del dispositivo  
    ==d) Todas las anteriores.

1. Un enlace duro o hard link:  
    a Solo permite enlazar archivos del mismo sistema de archivos.  
    b) Permite enlazar varios archivos.==  
    ==c) Permite enlazar archivos del tipo dispositivos.==d) Todas las anteriores.==

1. El número mágico que identifica un sistema de archivos se encuentra en:  
    a) EI MBR.  
    b) El directorio raíz.==c) En el Superbloque  
    ==d) Ninguna de las anteriores.

1. ¿Cuál de las siguientes acciones evita la fragmentación interna en archivos?  
    a) Utilizando herramientas para desfragmentar el disco.  
    b) Reutilizando los bloques fragmentados con otros archivos.  
    c) Reutilizando el espacio sobrante dentro del bloque del archivo con datos de otro archivo.==d) Ninguna de las anteriores.==

1. Que ventaja logra la independencia del dispositivo.  
    a) Que modela los dispositivos como si fuesen archivos.==b) Que al momento de escribir un programa no es necesario conocer el dispositivo.  
    ==c) Los errores son manejados por el driver.  
    d) Ninguna de las anteriores.

1. ¿Cuántas operaciones de disco se necesitan para obtener el nodo-i /home/os/cursos/2k13/parcial.sh?. Suponga resolución completa y que todos los contenidos de los directorios caben en un bloque de disco.  
    a) 7==b) 6  
    ==c) 5  
    d) Ninguna de las anteriores
    
    NO LA SE, NOTEBOOKLM ME TIRA QUE ES NINGUNA
    

1. Al utilizar tablas de nodos Indice (i-node). El tamaño máximo de un archivo depende de:  
    a) La cantidad de File Systems que posea el sistema.  
    b) La controladora del dispositivo.==c) El diseño del nodo índice.  
    ==d) Ninguna de las anteriores.

---

---