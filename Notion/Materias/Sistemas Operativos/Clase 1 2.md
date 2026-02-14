---
base: "[[Sistemas Operativos.base]]"
Sub-item: []
Blocked by: []
Parent item:
  - "[[Notion/Materias/Sistemas Operativos/Procesos e hilos|Procesos e hilos]]"
Blocking: []
Categoria: []
---
## <u>**Procesos**</u>

Un proceso es un programa que se convirtio en proceso, algo hizo que se convertiera en proceso.

Un proceso es un programa que esta siendo gestionado por el S.O—→ esta def le gusta al profe.

Para que un programa se convierta en proceso debo asignarle recursos. Para eso la cpu le asigna espacio de memoria y genera una tabla de procesos (bcp) block control process.

No es necesario cargar todo el proceso en memoria, con un pedacito puedo empezar a ejecutar ya que son secuenciales. Pero depende del proceso.

Def: un proceso es un conjunto de instrucciones que tiene como objetivo hacer algo, el cual es gestionado por el s.o, necesita recurso de hardware y software.

> [!tip] 💡
> Un proceso es la ejecución de un programa junto con su estado. Es a entidad a a que esistema operativo asigna tiempo de CPU y otros recursos. Cada proceso tiene su propio
espacio de direcciones y contexto de ejecución, o que permite que varios programas o
procesos coexistan en el sistema sin interferir entre si

Concurrencia: Es cuando se ejecutan varios procesos a la vez.

Paralelismo: Es cuando tenes cpus con mas de un nucleo y cada uno ejecuta un proceso distinto.

Pseudoparalismo: Es cuando tengo un solo procesador mete varios procesos.

Multiprogrmación: Es cuando el cpu conmuta entre procesos.

> [!tip] 💡
> La concurrencia ocurre cuando varios procesos parecen estar ejecutándose a mismo tiempo. En un sistema concurrente, os procesos no necesariamente se ejecutan simultáneamente, pero el sistema operativo alterna entre ellos tan rápidamente que da la impresión de que están ejecutándose al mismo tiempo. Esta concurrencia se puede presentar de dos formas:
> - El **paralelismo real **se da en sistemas con múltiples procesadores o núcleos de CPU, donde varios procesos pueden ejecutarse verdaderamente al mismo tiempo, cada uno en su propio procesador o núcleo
> - El **pseudoparalelismo **es cuando un sistema con un solo procesador da la apariencia de que varios procesos están ejecutándose al mismo tiempo. Sin embargo, en realidad, el procesador alterna entre diferentes procesos muy rápidamente, ejecutando pequeñas porciones de cada uno (conmutación de procesos).

swap: area de intercambio, es donde se ponen partes del proceso para que s.o lo busque.

Partes del proceso: Datos, Código, Stack.

Lifo: Primero en entrar ultimo en salir.

Los datos son invariables en el código, porque una vez que lo compilo todo esta en lenguaje de máquina, no varia el CODIGO.

Los datos varian segun en la matriz en que se los lleve.

**Espacios de direcciones, tengo que saber el espacio de direcciones del proceso.**

![[temp_image_1756501188609.jpg]]

Memoria virtual: Uso pedacitos del proceso y los voy llamando cuando lo necesite.

![[temp_image_1756501434876.jpg]]

Contador de programa: Apunta a la proxima instrucción a ejecutar.

BCP: Contiene al PSW

PSW: Guarda el estado del proceso, guarda el contexto de los procesos, para despues seguir ejecutando.

## <u>*Creación de un proceso*</u>

Cuando arrancamos el s.o, se generan procesos para el arranque.

Como trabaja linux cuando bootea: Tiene partición con un archivo /boot y linux lo carga en memoria, una vexz que se cargo se empieza a ejecutar y me muestra unos archivos de configuración y tira un monton de procesos.

Cuando bootea corre un proceso que se llama init (es el padre de todos los procesos), que tiene un pid y un ppid. init disparo un monton de proceso de acuerdo como tenga configurado el s.o.

![[temp_image_1756503460357.jpg]]


Boot process:

CMOS—→ No es la bios, es donde puedo dar arranque a sistemas operativos.

BIOS es una extension de la ram, SE LLAMA ROM BIOS (BASIC IMPUT OUPUT SYSTEM). En está hay un vector de instrucciones que direcciones a programitas que hacen el servicio. La bios solo tiene direcciones.

QR: quick response.

Primer plano: Lo estoy viendo, por ejemplo el sonido de spotify. Al proceso puedo interactuar.

Segundo plano: No puedo ver al proceso, no interactua con el.

> [!tip] 💡
> 
> ![[image 73.png]]

Trabajo por lote:  Es cuando haces un backup.

Backup: Es una copia de seguridad por si algo falla. Gereralmente se hace en la noche, mediante un proceso que es disparado.

Como términa un proceso:

-Por un error fatal (división por cero).

-Señal de kills

> [!tip] 💡
> 
> ![[image 74.png]]

El que elige que procesos deben ejecutarse es el planificador de procesos.

## <u>**Estados de los procesos**</u>

La tabla de procesos no es infinita. Debo reutilizar el espacio de la tabla de procesos.

El proceso NUEVO, pasa a una cola de procesos LISTOS.

Hay componente del s.o que se llama planificador que selecciona uno de los proceso de la cola para que se ejecuten. Por ejemplo el proceso A se va al estado de LISTO y se va al de EJECUCION. El panificador selecciona el proceso y el despachador lo manda a ejecucion ese proceso elegido al estado de EJECUCION.

La cpu va estar cargada con datos del proceso A que se esta ejecutando. En un momento el proceso A solicita E/S como sumar dos numeros y pasa al estado de FIN. Despues el planificador elige otro proceso por ejemplo proceso J. J genera un pdf de una lista de alumnos, entonces j solicita E/S en un disco para buscar info y se bloquea J mientras se busca en el disco y se ejecuta otro proceso E mientras se busca en el disco para J, despues le manda los datos al area de memoria de J y tengo un fin de E/S.

E se esta ejecutando, entonces el controlador y los drivers hacen que E vuelva a la pila??? Esto lo hago guardando el contexto de E y despues con una interrupcion mando E a la pila.

Leer ORG DE COMPUTADORAS UN ENFOQUE ESTRUCTURADO ——> con las páginas que dice el profe. tambien carretero perez.

![[temp_image_1756505749406.jpg]]


> [!tip] 💡
> 
> ![[image 75.png]]


Proceso sucio: Es un proceso que molesta al cpu.



## <u>Jerarquía de procesos: Cuando hay proceso padre hijo</u>

Proceso zombie: Son los que pierden padre matan al padre. Los matamos.

Fork: Crea un clon del proceso.

EXEC: Se crea un nuevo proceso.


## <u>**Planificadores**</u>

Activador = Despachador

Selecciona de la cola un proceso para que se ejecute.

Categorias:

Con expulsion: El s.o tiene la capacidad de expulsar a un proceso. Por ejemplo un proceso sucio.

En tiempo real: 

interactivos:

Performance: Es el rendimiento.

Proceso demonio: Es un proceso que esta esperando que alguien solicite entrar a un por ej servidor web, cuando alguien lo solicita le tira la ip. Da vueltas y tiene baja prioridad esperando una solicitud.

Tipos de planificadores:

El planificador antes era un persona, despues lo simularon con programas.

-Primero en entrar primero en salir FCFS Sin expulsión.

-El trabajo mas corto primero SJF Sin expulsion.

-Menor tiempo restante a continuación SRTN.

-Round Robin 

Le da un tiempo de ejecución a cada proceso.


Planificador por prioridades: Ejecuta a los procesos de mayor prioridad. El proceso de menor prioridad puede morir por inanición. Para eso linux implemento poder nivelar la prioridad de cada proceso.

-Round Robin con prioridad
