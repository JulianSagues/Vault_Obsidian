---
base: "[[Sistemas Operativos.base]]"
Sub-item: []
Blocked by: []
Parent item:
  - "[[Notion/Materias/Sistemas Operativos/Introduccion|Introduccion]]"
Blocking: []
Categoria: []
---
Sergio faccio: sdfaccio@yahoo.com.ar

Leer capitulo de PROCESOS←——- De tanenbaum

<u>**Leer las paginas de Org de computadoras un enfoque estructurado con los comentarios del profe**</u>

Global: ultimos temas puede ser.Global: ultimos temas puede ser.

<u>**Historia de los sistemas operativos ←—— Leer o ver video de youtube ←—— no lo toma**</u>

[[U1 - Sistemas operativos 1.pdf]]

## <u>**Introducción**</u>

**Funciones de un sistema operativo: Administrar recursos de la compu**

> [!tip] 💡
> 
> - Gestión de recursos de a computadora
> - Ejecución de servicios para os programas/maquina extendida
> - Ejecución de os mandatos de os usuarios/ interfaz de usuario

Recursos fisicos:

Recursos lógicos:

Programa en ejecución ——> se vuelve un proceso

Ejecutar ordenes de usuario: El usuario ejecuta el programa ——> es un proceso

<u>**¿Que es un S.O?**</u>

Interfaz entre usuario y kernel

> [!tip] 💡
> Un sistema operativo (SO es un programa que tiene encomendadas una serie de funciones diferentes cuyo objetivo es simplificar el manejo y la utilización de la computadora, haciéndolo seguro y eficiente

kernel—→ nucleo

Kernel: gestiona procesos, E/S, Memoria, Archivos directorio. Es un administrador de procesos del S.O.

Shell: interfaz de usuario, es como me comunico con el s.o. Es la GUI (Graphical interface)

Shell va casi de la mano con el S.O.

CUIDADO QUE ACA NO PUSO EL KERNEL, EL PROFE ORTIZ LO HIZO MAS COMPLETO ABAJO.

![[1000143615.jpg]]

En linux el mas usado para shell es sh (interfaz mas simple).

95% de los nucleos esta en programado en C. Lo demas es assembler.

Andrew tannenbaum creo MINIX.

Linus torvalds crea linux.

**Linus torvalds se la picanteo a andrew diciendo que linux era mejor que minix.**

La interfaz me ayuda a usar me ayuda a usar el S.O, me ayuda a comunicarme con el S.O.

Interfaces: sh, ksh, csh, bash (Esta ultima es la más usada).

> [!tip] 💡
> El módulo del sistema operativo que permite que los usuarios dialoguen de forma interactiva con ecosistema es el intérprete de mandatos o shell. Este se comporta como un bucle infinito que está repitiendo constantemente la siguiente secuencia:
> - Espera la orden de usuario
> - Analiza y la ejecuta
> - Concluye la orden y vuelve a esperar

Shell le pide al S.O, mediante una llamada al sist (call system), para usar el hardware es una petición.

<u>**Arquitectura de Vonn Newman**</u>

CPU trabaja a nivel ISA

![[1000143616.jpg]]

Los procesadores intel de 14va Gen comparten set de 

Que es ISA? ——> leer doc de guia org de computadoras y el libro 

## <u>**Tipos de S.O**</u>

Interactivos: Cualquier windows, le digo yo que tiene que hacer el S.O/Máquina.

Ejemplo: piloto automático de un avión

En tiempo real: S.O para ver bajadas o subidas de presión en un sist de GAS.

S.O MonoUsario: El s.o ejecuta una sola tarea a la vez

Ej: DOS, MS-DOS (primer windows)

S.O multitarea: Depende de los nucleos que tenga el procesador, Ejecuto mas de una tarea a la vez

Ej: windows en multitarea monousuario, ese usuario ejecuta varias tareas a la vez con el s.o multitarea

> [!tip] 💡
> <u>**Tipos S.O**</u>
> 1. Sistemas Operativos Interactivos
> 
> Un sistema operativo interactivo permite la interacción directa del usuario con el sistema en tiempo real. Estos sistemas responden inmediatamente a las entradas de usuario y son comunes en computadoras personales y otros dispositivos donde el usuario da comandos o realiza tareas y el sistema responde de inmediato.
> 
> 2. Sistemas Operativos Batch (Trabajo por Lotes)
> 
> En un sistema operativo por lotes, las tareas se agrupan en lotes que luego son procesados sin interacción directa de usuario. Este tipo de sistema operativo se utilizaba principalmente en los primeros días de la informática, donde un operador recopilaba varios trabajos, los introducía al sistema, y luego e sistema los procesaba uno tras otro.
> 
> 3. Sistemas Operativos Monousuario
> 
> Un sistema operativo monousuario permite que solo un usuario acceda a sistema a la vez. Aunque varias aplicaciones pueden ejecutarse simultáneamente, solo un usuario interactúa con el sistema en un momento dado.
> 
> 4.  Sistemas Operativos Monotarea
> 
> En los sistemas operativos monotarea, solo se puede ejecutar una tarea o proceso a la vez. Una vez que se completa una tarea, se puede comenzar con la siguiente.
> 
> 5. Sistemas Operativos Multitarea – Monousuario
> 
> Este tipo de sistema operativo permite que un único usuario ejecute múltiples tareas o programas simultáneamente. Aunque solo hay un usuario interactuando con el sistema, este puede abrir varias apllicaciones y cambiar entre ellas.
> 
> 6. Sistemas Operativos Multitarea - Multiusuario
> 
> Los sistemas operativos multitarea multiusuario permiten que varios usuarios interactúen con el sistema al mismo tiempo, y cada uno puede ejecutar múltiples tareas simultáneamente. Estos sistemas son comunes en entornos de servidores, donde varios usuarios pueden acceder y utilizar los recursos del sistema simutáneamente.

Lo que estudiamos como ejecutar mas de un proceso CON UN SOLO PROCESADOR DE ESO TRATA LA MATERIA.

¿Como con solo procesador ejecuto mas de un proceso?

Un programa se convierte en proceso cuando lo corre, le asigna un espacio de memoria.

Ten un procesador———>PROCESOS———> primero se uso tiempo compartido (Los procesos se turnan para ejecutarse)             |

                                                        |

                                                   A,B,C

Swap: area de intercambio del disco

Porque tiene que estar en memoria—→ lo ejecuta el procesador (CPU)

Tiempo compartido, para eso esta swap para tener procesos en memoria y despues expulsarlo, para ejecutar varios a la vez

![[1000143622.jpg]]

Swap es una sensación de multitarea.

Otra forma, HACERLO POR COLAS

<u>**Diagrama de proceso**</u> LO TOMAAAAA EN FINALES (no va a ser necesario porque no vamos a ir a final)

<u>**Se supone un cpu con un solo nucleo**</u>. Los procesos nuevos van a una cola y el s.o lo admite, porque tiene recursos para admitirlo. Si no tiene los recursos no puede admitir al proceso.

Los procesos van a una cola de procesos nuevos, se ejecuta en la cola, lo demas se bloquean en una nube de procesos bloqueados, todo se hace con solicitudes de E/S.

La cpu y el disco trabajan, porque el S.O se comunica con el disco mediante drivers para buscar y traer lo necesario del disco.

Concurrencia: la cpu trabaja y otro componente tambien esta trabajando cpu/disco y cualquier otro dispositivo.

Se ejecutan los procesos dependiendo de los recursos que necesite para ejecutarse.

supongamos que el proceso A solicita algo de internet en la web y B algo en disco—→ se ejecuta B y busca en el disco primero..

Para pedir algo USA MECANISMO DE INTERRUPCIONES——→ repasar porque lo toma.

![[1000143624.jpg]]

Mecanismo de interrupciones:

Hay tres metodos de E/S…

1. E/S programado: Su sistema esta programado para manejar los dispositivos. Hay equipos de IMB osea DOS, usaba disco y no tarjeta perforada, con un s.o que estaba en el disco. Aca la CPU se encargaba de todo, tenia que parar para ir a buscar al disco se encargaba de la E/S era MONOPROCESO. La CPU es avisada mediante una interrupción para poder seguir ejecutando un proceso. Hace varias interrupciones.
2. DMA (acceso directo a memoria): pueden acceder cpu, memoria y ciertos dispositivos. Es un hardware y software——> se va a estudiar mejor en la UNIDAD de E/S. Con DMA se hace con solo una interrupcion.
3. Este ni idea preguntar…

## <u>**Máquina Multinivel**</u>

![[image 72.png]]

Tenemos un programa (secuencia de instrucciones)

Pseudo código (profe):

![[1000143631.jpg]]

Esto se convierte a nivel ISA, despues de largos pasos. Lo tiene que procesar el procesador en binario, antes pasando por lenguaje ensamblador.

Esto se hace con:

<u>**Compilación:**</u> Tomo todo, lo paso por un proceso con un compilador, asignando posiciones de memoria para a,b,c. Todas son direcciones de memoria, Toma todas las instrucciones y la convierte a un nivel mas bajo. Por ejemplo de lvl 1 a lvl 2. 

<u>**Traducción: **</u>toma una instrucción y hace todo el proceso anterior (compilación), solo para esa instrucción.

Un proceso compilado es mas rápido que uno traducido.

Interpretación: Se usa por un tema de compatibilidad, por ejemplo se hace interpretado para poder usarlo en linux y en windows.

.com usa un segmento y .exe usa mas de un segmento.

ESTUDIAR MÁQUINA MULTINIVEL——→

## <u>**Modo usuario y Modo kernel**</u>

![[1000143634.jpg]]

MS DOS, no tenía modo supervisor ni modo usuario.

Modo usuario: usa llamadas al sistema para traer la info. Solo ejecuta instrucciones de usuario, necesita si o si para terminarla poder usar al kernel, osea pide permiso al kernel

Modo kernel/Supervisor: Busca la info en la memoría y se la devuelve al usuario.

Linux usuarios: comunes, superuser, especiales.


superuser———> Podes dar instrucciones con llamadas al sistema, matar procesos con /kill. Como tal no puede entrar en modo kernel.


## <u>**Jerarquía de memoría**</u>

![[1000143634 1.jpg]]

“Todos los dispositivos tienen cache”

Funcionamiento de disco (imagen): Consultar por la imagen despues.

![[1000143637.jpg]]

¿Cuantos registros tiene un cpu?

8 para arq de 32 y 16 para arq de 32.

Estudiar los titulos de la ultima diapositiva UNIDAD 1, de los libros.


---

---

---

---

---

---

---

---

## PRACTICA

Prof: Italo Ortiz

<u>**Va a pedir presentar un tema, para compensar los días que no cursamos es ORAL**</u>

Formato: Pregunta y luego la respuesta.

Consultas:

Lunes 17:45 a 18:45 Presencial


***Ejercicios de Gabinete ——→ verificar las respuestas en libro.***

4. **Explicar el concepto de sistema operativo como una máquina extendida.**

Un S.O como una máquina extendida es una capa de abstracción que simplifica el uso del hardware, es decir, permite que los usuarios no interactuen con el hardware físico si no con con interfaces gráficas que proveen los S.O.


RTA-PROF:

Un S.O como una máquina extendida es un abstracción, abstrae todo lo que que esta abajo, osea la parte fea, mediante una interfaz visual para que el usuario no interactue con el hardware. En un S.O sin interfaz donde hay que poner comandos, se tiene mas control del sistema operativo con líneas de comandos y en las cuales no te podes equivocar, porque corres el riesgo de poner un comando inadecuado y romper el S.O. En cambio con una interfaz gráfica tenemos menos control, pero menos riesgo de romper S.O.


**2.   Explicar el concepto de sistema operativo como un administrador de recursos. Mencionar y explicar brevemente los recursos que administra.**

El S.O como administrador de recursos se refiere a como el mismo administra los recursos del sistema para que los usuarios y los programas puedan utilizarlo de una manera óptima.

Los recursos que administras son:

- Procesador (CPU): Es el encargado de ejecutar las instrucciones del sistema. El sistema operativo se encarga de decidir que se ejecuta, en que orden y cuanto tiempo, ademas de cambiar los procesos entre sí en el procesador.
- Memoría: Incluye a la RAM y el disco. La RAM es el lugar donde se cargan los programas que se van a ejecutar.

RTA-PROF: El S.O admistra el procesador (el más importantes) donde se ejecutan los procesos (el cual tiene un nombre).

Un proceso es un programa en ejecución, es una instancia de un programa en ejecución y estos pueden ser múltiples. Las instrucciones se van ejecutando en el procesador.

En un procesador podemos tener varios nucleos para poder ejecutar varios procesos.

Tambien admistra la Memoría RAM, mediante un contador de programa, haciendo un preprocesamiento (procesadores actuales). La RAM es un recurso limitado, porque puede tener cuello de botella si hay muchos procesos con una sola cpu. Hay un admistrador de procesos y un administrador de la RAM.

Tambien administra el Disco, donde se guardan programas información y el S.O (el cual es un programa tambien). Tenemos que guardar las cosa en el disco de forma que podamos recuperarlo, usando algo llamado FileSystem, este nos permite dentro de la estructura del disco nos permite almacenar información y luego recuperarla. Para llevar y traer cosas al disco se hacen operaciones de Entrada/Salida (E/S). El administrador de memoría usa E/S


3.  Describa la información relevante del Kernel del sistema operativo, detallando su arquitectura,
	funciones principales, modos de operación, gestión de recursos y componentes internos.

RTA PROF: ——→ Completar con el libro

<u>**Arquitectura de capas de un sistema operativo:**</u>

La interfaz visual es un complemento para el S.O.

![[1000143654.jpg]]

El rectangulo entre el KERNEL y el HARDWARE SON LOS DRIVERS.

El kernel es el nucleo, puede ejecutar procesos mediante un set de instrucciones. Las instrucciones no deben romper el S.O.

Cuando opera el kernel son instrucciones reservadas (no las hace el usuario), porque son potencialmente peligrosas, el kernel trabaja en modo protegido. 

Los drivers (son programas) están preparados para trabajar con el S.O.