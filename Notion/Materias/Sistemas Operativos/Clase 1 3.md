---
base: "[[Sistemas Operativos.base]]"
Sub-item: []
Blocked by: []
Parent item:
  - "[[Notion/Materias/Sistemas Operativos/Archivos|Archivos]]"
Blocking: []
Categoria: []
---
## <u>Sistemas de archivos</u>

- Un archivo esta compuesto por registros y tiene una key.

- Longitud de un archivo: id, descripción del item, etc…

- Varios procesos pueden acceder al mismo archivo, los registros del archivo son el recurso que quieren los procesos.

- Todos los programas se suponen que son secuenciales.

- una lectura me traigo varios registros.

- Vamos a estar bloqueando un bloque de registros.

Supongamos que tenemos bloques de 10 registros, vienen 1000 de esos bloques y los registros que queremos estan en varios bloques. Es un problema porque habrá que buscarlos en los bloques necesarios.

Como se que bloques estan ocupados y cuales disponibles? → mapa de bits y lista enlazada igual que memoria.

Que es un archivo?

Un conjunto de registros, colección logica de info, unidad de almacenando, conj de datos y CONJUNTO DE BITS → ESA LE GUSTA AL PROFE LA DEF.

UNIX-like es POSIX

Win32 es de windows

POSIX → Portable Open System For Unix.

Tipos de archivos en windows:

.doc

.docx

.xls

.xlsx

Windows mira la extension y lo abre con el programa que abre esa extensión.

Un archivo Tar es un archivo que tiene archivos dentro.

En linux, se trabaja con los nodos indice o i-nodos:

![[image 76.png]]



![[0c9b7a46-6882-47c2-a2a8-b94b780e80bd.png]]

- El primer corchete son los permisos de usuario
- El segundo son los permisos del grupo
- El tercero  es el permiso de los otros, el numero son los links
- El cuarto el propietario
- El quinto el grupo
- El sexto es la ultima fecha de modificacion
- El septimo es el peso del archivo en bytes
- El octavo es el tipo de archivo

Los archivos en su encabezado tienen algo que se llama magic number que identifica que tipo de archivo es, eso permite que linux lea archivos de windows.

VFS—> virtual file system, gracias a eso puedo manipular archivos de windows en linux.

VSF Es un subsistema que me permite leer archivos de windows en linux

VSF→ ESTUDIAR

# <u>Directorios</u>

Es un archivo Tar

Es una tabla que tiene nombres de archivos y índices, root es el padre de todos los archivos.

Directorios de un solo nivel:

![[image 77.png]]

Directorios de dos niveles

![[image 78.png]]

Sistema jerárquico

![[image 79.png]]

Global:  introduccion, procesos, hilos, concurrencia, interbloqueo, gestion de memoria, archivos, e/s.

PATH—> direccion de un archivo User/documents/Cars

Master Boot Record → Es un registro de booteo, prendes la compu ejecuta el CMOS ESTUDIAR EL MBR. El MBR me permite buscar la partición activa para arrancar el sistema operativo.

MBR me dice a donde tengo que ir a botear.

Cada partición puede tener un bloque de booteo, este va a tener un direcctorio |boot 

Mi gestor de archivos para poder accerderlos debe saber que file-system es ese archivo que quiero acceder.

UPS es una unidad de suministro de energía por si se corta la electricidad.

La UPS tiene un tiempo de vida. Esta tiene un puerto serie conectado al servidor.

Es como un seguro para el servidor el UPS.

NUMERO MAGICO DEL SISTEMA DE ARCHIVOS—>

MBR→ estudiar el grafico de otro lado.

SISTEMAS DE ARCHIVOS:

FAT —> File Access Table

NTFS—> **New Technology File System**

LINUX no tiene extension.

SISTEMA DE ARCHIVOS MS-DOS:

![[77c0380a-77bc-492f-9a7f-799c663ef561.png]]

![[image 80.png]]

El defragmentador de disco ordena para hacer una lectura mas rápida.

El problema de ms-dos y sus sistema de archivos era que se fragmentaba mucho el disco.

La fragmentación se genera siempre

Fragmentacion es cuando tenes un segmento de 4k y tenia que ponerle algo de 3k, me generaba una fragmentación de un 1k.

## <u>Nodos Índice</u>

Por cada file system voy a tener una tabla de archivos esa tabla tiene:

![[temp_image_1759530411534.jpg]]

puntero simple apunto a un bloque de datos.

puntero doble apunto a una dirección.

puntero triple apunto a un bloque con punteros que  apuntan a un bloque  que apunta a direcciones.

Las condiciones que estan al costado es para saber la longitud máxima de un archivo.

El nro de nodo me ayuda a identificar a un archivo (file system), ese archivo tiene metadatos y punteros que apuntan a bloques de datos.

Cual es la ventaja de usar nodos índice → **acelerar la búsqueda y el acceso a los datos.**


<u>EJEMPLO DEL PROFE</u>

Como montar un file system a otro

![[temp_image_1759531730109.jpg]]


## <u>Archivos compartidos (links)</u> → siempre lo toma

Links   |—HARD (dentro del mismo sistema de archivos)

            |——-SOFT (esta en varios sistemas de archivos)

<u>HARD LINK</u>

![[temp_image_1759532581872.jpg]]

Tenemos HARD link cuando dos o más punteros apuntan al mismo i-nodo.

<u>SOFT LINK</u>

![[temp_image_1759532790402.jpg]]

El i-nodo 50 (Pedro) que apunta a los metadatos, después en la tabla de los metadatos lo punteros de esa tabla apuntan a un bloque que tiene el PATH (ruta) al archivo de Luis o i-nodo de Luis

<u>No puedo poder cadenas en los punteros porque estos son numéricos</u> → va en el examen.
