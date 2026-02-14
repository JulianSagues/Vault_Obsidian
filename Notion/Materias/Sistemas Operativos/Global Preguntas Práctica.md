---
notion-id: 2a7ac26b-dee7-8086-8950-ea75dcf68394
base: "[[Sistemas Operativos.base]]"
Sub-item: []
Blocked by: []
Parent item: []
Blocking: []
Categoria: []
---
1. En una máquina con sistema operativo Linux se desea utilizar strace para rastrear las llamadas al sistema realizadas por Is -la, guardando la salida en un archivo llamado "salida.txt".
La sintaxis del comando es:
a) strace -s salida.txt Is-la
b) strace Is-la > salida.txt
==c) strace -o salida.txt ls -la==
d) strace Is-la | salida.txt

2. Con el comando Is -l/dev se puede ver una lista de los dispositivos del sistema. ¿Cómo es posible identificar los dispositivos de carácter usando la salida del comando?


`ls -l /dev | grep '^c'`


3. ¿Qué comando usaría para listar solo los procesos del sistema?

**ps -e **

**ps -ef**

4. En una máquina que corre Linux se está ejecutando Firefox. ¿Qué comando usaría para obtener el ProcessID de Firefox? Como respuesta escriba la sintaxis

`pgrep firefox` —> Este es mejor


2. En un sistema Linux con el comando htop:
a) La cantidad de swapping generada por un proceso.
b) El tiempo total desde que el proceso se inició.
==c) Se puede visualizar el espacio de memoria virtual usado por un proceso.==
(d) Todas las respuestas anteriores son correctas.

6. Mencione dos comandos, utilizados en el práctico de administración de memoria distintos de top o htop, que permitan visualizar la cantidad de memoria RAM total y libre del sistema. Como respuesta escriba la sintaxis de cada comando.

`free`

`cat /proc/meminfo`

3. Con el comando Isblk -f se muestra:
a) Los dispositivos de bloque y el tamaño del bloque.
==b)Los dispositivos de bloque, el espacio utilizado y el espacio libre.==
c) Los dispositivos de bloque y el tamaño del dispositivo.
d)Todas las respuestas anteriores son correctas.

---

Resumen de comandos de los tps y llamadas al sistema:

---

## TP1

| **Parte del Comando** | **Qué es y Qué Hace** |
| --- | --- |
| `strace` | **El programa principal.** Es el "rastreador" (trace). Su trabajo es iniciar otro programa y espiar cada "llamada al sistema" (syscall) que ese programa le hace al kernel de Linux. |
| `-o output.txt` | **La opción de salida.** La `-o` (de *output*) le dice a `strace`: "No imprimas el rastreo en mi pantalla. Guárdalo todo, ordenadamente, en el archivo llamado `output.txt`". |
| `ls -la` | **El comando objetivo.** Este *no* es un parámetro de `strace`, es el programa que `strace` va a ejecutar y vigilar. Es la "víctima". `strace` lanza `ls -la` y registra todo lo que este hace. |

| **Elemento** | **Propósito** |
| --- | --- |
| **Comando** | `strace -o output.txt ls -la` |
| **Syscall: **`**openat()**` | Abrir el directorio actual (`.`) para poder inspeccionar su contenido. |
| **Syscall: **`**getdents64()**` | Leer la lista de nombres de archivos y carpetas *dentro* del directorio ya abierto. |
| **Syscall: **`**newfstatat()**` | Obtener los metadatos (permisos, dueño, tamaño, fecha) de *cada* archivo individual. Es el trabajo pesado de la opción `-l`. |
| **Syscall: **`**write()**` | Escribir la salida final formateada (el texto que ves) en la terminal (stdout, descriptor de archivo `1`). |
| **Syscall: **`**close()**` | "Colgar el teléfono". Cerrar los recursos (archivos, directorios) que se abrieron para liberar memoria y descriptores. |

---

## TP2

El comando `ps` (Process Status) es básicamente el "portero del edificio" de Linux: te dice quién está en el sistema y qué está haciendo en este preciso instante.

Para la parte a), al ejecutar `ps` solo (sin nada más), típicamente solo ves los procesos que *tú* has iniciado en *esa terminal específica*. Es una vista muy, muy limitada.

| **Comando** | **Qué Muestra** | **Formato** | **Columnas Clave que Verás** |
| --- | --- | --- | --- |
| `ps -e` | **E**very (Cada) proceso del sistema. | Corto (Default) | `PID`, `TTY`, `TIME`, `CMD` |
| `ps -ef` | **E**very (Cada) proceso del sistema. | **F**ull (Completo) | `UID`, `PID`, `PPID`, `C`, `STIME`, `TTY`, `TIME`, `CMD` |

**En resumen:** `ps -e` te dice *qué* está corriendo. `ps -ef` te dice *qué* está corriendo, *quién* lo empezó, *quién* es su "padre" y *cuándo* empezó.



Ah, el comando `pstree`. Es el "Quién es Quién" de tu sistema, pero en versión árbol genealógico.

Mientras que `ps -ef` te da una lista (como un directorio telefónico), `pstree` te da el organigrama familiar. Te muestra visualmente qué proceso es el "padre" de qué otro, lo cual es increíblemente útil para entender por qué algo se está ejecutando.

| **Característica** | **top (El Clásico)** | **htop (El Moderno)** |
| --- | --- | --- |
| **Interfaz** | Texto plano, estático, en blanco y negro. | Visual, con barras de progreso y colores. |
| **Interacción** | Requiere atajos de teclado arcanos (ej: `k` para matar, `r` para *nice*). | Intuitivo. Se maneja con flechas, mouse y Teclas de Función (ej: F9 para "Matar"). |
| **Visualización de CPU** | Muestra un uso de CPU total o promedio. | Muestra barras de uso **individuales** para cada núcleo/hilo de la CPU. |
| **Manejo de Procesos** | Hay que escribir el PID del proceso para interactuar con él. | Simplemente seleccionas el proceso de la lista con las flechas. |
| **Scrolling** | Sin scroll. Los comandos largos simplemente se cortan. | Permite scroll vertical *y horizontal* (ideal para ver comandos largos). |
| **Vista** | Solo lista plana, ordenada. | Puede alternar a "vista de árbol" (F5) para ver las relaciones padre-hijo. |
| **Instalación** | Viene preinstalado en (casi) todos los sistemas Linux. | Casi siempre hay que instalarlo (`sudo apt install htop`). |

Comandos para matar procesos:

| **Comando** | **Parámetro (Señal)** | **Qué Hace** |
| --- | --- | --- |
| `kill [PID]` | Ninguno (usa `SIGTERM` por defecto) | Pide educadamente al proceso con ese PID que termine. |
| `kill -9 [PID]` | `-9` (la señal `SIGKILL`) | Mata (destruye) al proceso con ese PID instantáneamente. |
| `killall [nombre]` | Ninguno (usa `SIGTERM` por defecto) | Pide educadamente a *todos* los procesos con ese nombre (ej: "firefox") que terminen. |
| `killall -9 [nombre]` | `-9` (la señal `SIGKILL`) | Mata (destruye) a *todos* los procesos con ese nombre instantáneamente. |

Ejemplo con firefox:

| **Comando** | **El Método (Qué Hace)** | **Cuándo Usarlo** |
| --- | --- | --- |
| `kill [PID]` | **El "Toque en el Hombro".** Envía la señal `SIGTERM` (15). Le pide *educadamente* al proceso principal (si aciertas el PID) que se cierre. | Rara vez. Es ineficiente porque Firefox tiene muchos procesos. |
| `killall firefox` | **La "Invitación a Retirarse".** Envía `SIGTERM` a *todos* los procesos de Firefox. Es la forma estándar y limpia de cerrar una app colgada. | Es la **primera opción**. Ideal cuando la app no responde pero el sistema sí. |
| `kill -9 [PID]` | **El "Tirador Solitario".** Envía `SIGKILL` (9). El Kernel "borra" ese PID específico de la memoria. | Cuando `killall` falla y sabes *exactamente* qué PID específico está causando el problema (raro). |
| `killall -9 firefox` | **El "Botón Rojo".** Envía `SIGKILL` a *todos* los procesos de Firefox. No hay negociación, simplemente mueren. | **La última opción.** Cuando `killall firefox` (el educado) es ignorado y el navegador está 100% congelado. |

---

## TP3

El comando `free` es el "contador" de memoria de tu sistema. Te da un informe rápido y sin rodeos de cuánta memoria RAM (y swap) tienes, cuánta estás usando y, lo más importante, cuánta te queda *realmente* disponible.

Es como preguntarle a tu sistema: "¿Qué tan lleno estás?"

Si ejecutas `free -h` (la `-h` es de *human-readable*, para que te muestre GB y MB en lugar de un número kilométrico de bytes), verás algo así:

Bash

`              total        used        free      shared  buff/cache   available
Mem:          7.8Gi       3.1Gi       1.2Gi       123Mi       3.5Gi       4.2Gi
Swap:         2.0Gi         0B        2.0Gi`

### El Desglose (La Parte Importante)

Aquí está la confusión que casi todos tienen la primera vez que ven esto.

| Columna | Qué Significa (La Verdad) |
| --- | --- |
| **total** | **Total:** La cantidad total de RAM física que tienes. Simple. |
| **used** | **Usada:** La memoria que está activamente en uso por programas (y el *buff/cache*). |
| **free** | **Libre (¡Engañosa!):** Memoria *totalmente* vacía, sin usar para nada. Este número suele ser **bajo** y asusta a la gente. **No te asustes.** |
| **shared** | **Compartida:** Memoria usada por múltiples procesos. Generalmente puedes ignorarla. |
| **buff/cache** | **¡La Clave!** Linux es inteligente. Usa la RAM "libre" para guardar copias de archivos usados recientemente (cache) y para buffers. Así, si vuelves a abrir algo, vuela. Esto es **buen uso** de la memoria, no un problema. |
| **available** | **Disponible:** **Esta es la columna que te importa.** Es la suma de la memoria `free` + la mayor parte de `buff/cache`. Es la cantidad real de memoria que tus aplicaciones pueden pedir y usar *ahora mismo*. El kernel simplemente le dirá al `buff/cache`: "Apártate, te necesito". |

**La Lección Más Importante:**
No mires la columna `free`. Mira la columna `available`.

### El Comando: `smem -r -k`

- `smem`: El programa de análisis de memoria.
- `r`: (Reverse). Invierte el orden de clasificación. Por defecto, `smem` muestra del *menor* consumo al *mayor*. Con `r`, pone a los procesos más "glotones" de memoria arriba de todo, que es casi siempre lo que quieres ver.
- `k`: (Kilo/Kibi). Muestra las unidades de forma legible (ej. `512M` en lugar de `524288000`), para que no tengamos que contar ceros.

**En resumen:** `smem -r -k` te da la lista de los procesos que más memoria consumen, ordenados por su **"uso justo" (PSS)**, que es la métrica más precisa para saber qué programa está realmente acaparando tu RAM.



`vmstat` (Virtual Memory Statistics) es como el electrocardiograma de tu servidor.

Mientras que `htop` te dice "qué" proceso está ocupado, `vmstat` te dice *por qué* el sistema está ocupado. Es la herramienta clásica para encontrar "cuellos de botella" (bottlenecks).

Si solo ejecutas `vmstat`, te da un promedio desde que arrancó la VM. Aburrido.
Si ejecutas `**vmstat 1**`, te da un reporte *cada segundo*. Mucho más útil.

La salida es una pared de texto críptico. Vamos a traducirla.

Bash

`procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 2  0      0 123456 789012 345678    0    0    10    20  100  200  5  2 90  3  0`


Al ejecutar `cat /proc/meminfo`, encuentras los datos *en crudo* que comandos como `free`, `htop` y `vmstat` usan para crear sus propios reportes.

**En resumen:** `cat /proc/meminfo` te da la "fuente de la verdad" de la memoria. Te da el desglose *exacto* de qué está haciendo el kernel con cada Kilobyte de RAM que administras.



---

## TP4

---

<u>**df -h**</u>

El comando `df` (viene de **d**isk **f**ree) se usa para mostrar el espacio **disponible y utilizado** en los sistemas de archivos (discos) de tu servidor.

La opción `-h` (de **h**uman-readable o "lectura humana") es clave: hace que los tamaños se muestren en un formato fácil de entender (como `12G` para Gigabytes o `250M` para Megabytes), en lugar de mostrarlos en bloques de bytes, que es el formato por defecto y es mucho más difícil de leer.

---

<u>**cat /etc/fstab**</u>

Este comando tiene dos partes:

4. `**cat**`: Es un comando básico que significa "con**cat**enate" (concatenar). Su uso más común es leer el contenido de uno o más archivos y mostrarlos directamente en la terminal.
5. `**/etc/fstab**`: Es la ruta a un archivo de configuración muy importante. Su nombre viene de "**f**ile **s**ystem **tab**le" (tabla de sistemas de archivos).

Este archivo `fstab` es básicamente **una lista de instrucciones que el sistema lee al arrancar** para saber qué discos (particiones, discos duros, SSDs, etc.) debe "montar" (es decir, hacer accesibles) y dónde debe montarlos dentro del árbol de directorios (por ejemplo, en `/`, `/home`, `/var`, etc.).

En resumen, `cat /etc/fstab` te permite **ver la configuración de todos los discos y particiones que se montan automáticamente** cuando tu servidor se enciende.

---

<u>**sblk -f**</u>

El comando `lsblk` significa "**l**i**s**t **bl**oc**k** devices" (listar dispositivos de bloque). Los dispositivos de bloque son tus discos duros, SSDs, particiones y cualquier otro dispositivo de almacenamiento.

Por sí solo, `lsblk` te da una **vista de árbol** que muestra qué particiones pertenecen a qué discos (ej. `sda` y debajo sus particiones `sda1`, `sda2`).

La opción `-f` (de **f**ilesystem) añade información clave a esa vista:

- `**FSTYPE**`: Muestra el tipo de sistema de archivos (ej. `ext4`, `xfs`, `swap`, `ntfs`).
- `**UUID**`: El identificador único de la partición, que es el que usa `fstab` para montar discos de forma segura.
- `**MOUNTPOINT**`: Muestra dónde está montada esa partición (si es que lo está).

A diferencia de `df -h` (que solo muestra sistemas montados y su *uso*), `lsblk -f` te da un mapa de *toda* la estructura de tu hardware de almacenamiento, esté montado o no.

---

<u>mkfs.ext4 mi_imagen.img</u>

`mkfs.ext4` es el comando para "**m**a**k**e **f**ile**s**ystem" (crear un sistema de archivos) del tipo `**ext4**`, que es el sistema de archivos estándar y moderno usado por Linux.

Lo interesante aquí es el destino: `mi_imagen.img`.

- Normalmente, uno formatea un dispositivo real, como una partición de disco (ej. `/dev/sdb1`).
- En este caso, estás formateando un **archivo**.

El comando trata al archivo `mi_imagen.img` como si fuera un disco duro completo. "Escribe" toda la estructura de un sistema de archivos `ext4` (el índice, los bloques, los inodos, etc.) *dentro* de ese único archivo.

**¿Para qué sirve esto?**
Este archivo `.img` ahora es un "disco virtual". El siguiente paso sería "montarlo" en una carpeta usando un dispositivo *loop* (un truco de Linux para tratar archivos como discos) y así poder usarlo como si fuera un pendrive o una partición separada.

> Importante: Este comando asume que el archivo mi_imagen.img ya existe y tiene un tamaño predefinido (generalmente creado antes con comandos como dd o fallocate). mkfs no crea el archivo, solo lo formatea por dentro.

---

<u>**sudo mkdir /mnt/mi_imagen **</u>

Aquí, estás usando `sudo` ("**s**uper**u**ser **do**") para ejecutar el comando `mkdir` ("**m**a**k**e **dir**ectory" o crear directorio) con permisos de administrador.

Necesitas `sudo` porque el directorio `/mnt` es un directorio raíz del sistema, y los usuarios normales no tienen permiso para crear carpetas dentro de él.

El directorio `/mnt` (abreviatura de **m**ou**nt** o "montaje") es el lugar estándar en Linux donde se "montan" (conectan) temporalmente los sistemas de archivos, como pendrives, discos externos o, en tu caso, la imagen de disco que creaste.

En resumen: Estás **creando una carpeta vacía llamada **`**mi_imagen**`** dentro de **`**/mnt**`. Esta carpeta servirá como el "punto de montaje" donde "engancharás" tu archivo `mi_imagen.img` para poder usarlo.

---

<u>**sudo mount -o loop mi_imagen.img /mnt/mi_imagen **</u>

Este comando usa `sudo` (permisos de admin) para ejecutar `mount` (montar).

Aquí es donde se une la magia:

6. `**o loop**`: Esta es la opción clave. `o` es por "options" (opciones), y `loop` le dice a Linux: "Oye, el 'disco' que te estoy pasando no es un dispositivo físico (como `/dev/sdb1`), sino que es un **archivo**. Por favor, trátalo como si fuera un disco." Esto se llama "loop device" o dispositivo de bucle.
7. `**mi_imagen.img**`: Es el **origen**. Es tu archivo de disco virtual, que ya está formateado con `ext4`.
8. `**/mnt/mi_imagen**`: Es el **destino**. Es la carpeta vacía que creaste en el paso anterior.

Después de ejecutar este comando, si entrás a la carpeta `/mnt/mi_imagen` (con `cd /mnt/mi_imagen`), cualquier archivo que crees o modifiques **se guardará en realidad *****dentro***** del archivo **`**mi_imagen.img**`. Has montado exitosamente tu disco virtual

---

<u>**df -h | grep mi_imagen  **</u>

Este comando introduce un concepto clave de Linux: el **"pipe" (tubería)**, representado por el símbolo `|`.

El pipe toma la **salida** del comando de la izquierda (`df -h`) y la usa como **entrada** para el comando de la derecha (`grep mi_imagen`).

El proceso es este:

9. `**df -h**`: Se ejecuta primero y genera la lista completa de *todos* los discos montados en el sistema (incluyendo `/`, `/home`, etc., y tu nuevo disco virtual).
10. `**|**`: Envía esa lista completa de texto al siguiente comando.
11. `**grep mi_imagen**`: Recibe la lista, la filtra y muestra **únicamente** la línea (o líneas) que contengan el texto "mi_imagen".

En resumen, es un filtro. Lo usás para **confirmar que tu imagen se montó correctamente** y ver su uso (tamaño, espacio usado, etc.), pero sin tener que ver el resto de los discos de tu sistema.

---

<u>**sudo umount /mnt/mi_imagen**</u>

El comando `umount` (fíjate que es **sin la 'n'** de "unmount") es la operación opuesta a `mount`.

Lo que hace es **desmontar** o **desconectar** el sistema de archivos del punto de montaje.

- `**sudo**`: Lo necesitás porque la operación de montaje/desmontaje requiere privilegios de administrador.
- `**umount**`: El comando para desmontar.
- `**/mnt/mi_imagen**`: El punto de montaje (la carpeta) que querés liberar.

Después de ejecutar esto, la carpeta `/mnt/mi_imagen` vuelve a estar vacía, y el archivo `mi_imagen.img` deja de estar "en uso". Ya es seguro moverlo, copiarlo o eliminarlo.

---

<u>**ln -s original.txt enlace_simbólico.txt **</u>

`ln` es el comando para crear **links** (enlaces).

La opción `-s` especifica que querés crear un **enlace simbólico** (symlink), que es la forma más común. Un enlace simbólico es básicamente un **acceso directo**.

- `**original.txt**`: Es el archivo de origen, el archivo real al que querés apuntar.
- `**enlace_simbólico.txt**`: Es el nombre del "acceso directo" que estás creando.

Después de ejecutar esto, `enlace_simbólico.txt` es un archivo nuevo muy pequeño que simplemente *apunta* a `original.txt`. Si abrís `enlace_simbólico.txt`, tu sistema operativo te mostrará el contenido de `original.txt`.

> Dato clave: Si borrás original.txt, el enlace_simbólico.txt se "romperá" y no apuntará a nada.

---

<u>**ls -l original.txt enlace_simbólico.txt **</u>

Este comando te permite ver la **diferencia clave** entre el archivo original y el enlace simbólico que creaste.

`ls` es el comando para **l**i**s**tar archivos. La opción `-l` pide el formato "largo", que muestra todos los detalles: permisos, propietario, tamaño y fecha.

Cuando ejecutás este comando, vas a ver dos líneas:

12. **Para **`**original.txt**`: Mostrará que es un archivo normal (la línea empezará con ), su tamaño real (ej. `45K`), y sus permisos.
13. **Para **`**enlace_simbólico.txt**`:
    - Mostrará que es un **enlace** (la línea empezará con la letra `l`).
    - Su tamaño será **muy pequeño** (ej. `12` bytes), que es solo el largo del *nombre* "original.txt", no el contenido.
    - Al final de la línea, te mostrará a dónde apunta: `enlace_simbólico.txt -> original.txt`.

Es el comando perfecto para verificar que tu enlace simbólico existe y que está apuntando al lugar correcto.

---

<u>**ln original.txt enlace_duro.txt **</u>

Al omitir la opción `-s`, estás creando un **enlace duro** (hard link).

A diferencia de un enlace simbólico (un "acceso directo" que apunta al *nombre*), un enlace duro es un **segundo nombre para los mismos datos** en el disco. Ambos, `original.txt` y `enlace_duro.txt`, se convierten en "pares" que apuntan directamente al mismo bloque de datos (el mismo inodo).

**Dato clave:** Si borrás `original.txt`, ¡`enlace_duro.txt` **sigue funcionando perfectamente**! El contenido del archivo no se borrará del disco hasta que el *último* enlace (o nombre) que apunta a él sea eliminado

---

| **Comando** | **Qué hace (Explicación)** |
| --- | --- |
| `df -h` | Muestra el espacio libre y utilizado de todos los discos montados, en un formato fácil de leer (KB, MB, GB). |
| `cat /etc/fstab` | Muestra el contenido del archivo `fstab`, que configura qué discos y particiones se montan automáticamente al arrancar el sistema. |
| `lsblk -f` | Lista todos los dispositivos de bloque (discos y particiones) en formato de árbol, mostrando su tipo de sistema de archivos (`FSTYPE`), `UUID` y punto de montaje (`MOUNTPOINT`). |
| `mkfs.ext4 mi_imagen.img` | Formatea un archivo (`mi_imagen.img`) con el sistema de archivos `ext4`. Lo prepara para ser montado y usado como un disco virtual (usando un "loop device"). |
| `sudo mkdir /mnt/mi_imagen` | Crea un directorio (carpeta) llamado `mi_imagen` dentro del directorio `/mnt`. Se usa `sudo` porque `/mnt` requiere permisos de administrador. Esta carpeta se usará como punto de montaje. |
| `sudo mount -o loop mi_imagen.img /mnt/mi_imagen` | Monta (conecta) el archivo de disco virtual `mi_imagen.img` en la carpeta `/mnt/mi_imagen`. La opción `-o loop` es crucial para tratar un archivo como si fuera un disco. |
| `df -h | grep mi_imagen` | Ejecuta `df -h` (ver uso de disco) y "filtra" la salida para mostrar únicamente la línea que contiene "mi_imagen". Sirve para confirmar que el disco virtual está montado. |
| `sudo umount /mnt/mi_imagen` | Desmonta (desconecta) el sistema de archivos que estaba montado en `/mnt/mi_imagen`. Libera el archivo `mi_imagen.img` para que pueda ser manipulado de forma segura. |
| `ln -s original.txt enlace_simbólico.txt` | Crea un **enlace simbólico** (un "acceso directo") llamado `enlace_simbólico.txt` que apunta al archivo `original.txt`. |
| `ls -l original.txt enlace_simbólico.txt` | Lista los detalles (formato largo) de ambos archivos. Permite ver que el enlace (`l...`) es diferente al archivo original (`-..`) y muestra a dónde apunta (`->`). |
| `ln original.txt enlace_duro.txt` | Crea un **enlace duro** (`hard link`). Ambos archivos se vuelven "pares" que apuntan a los mismos datos. Si se borra el original, el enlace duro **sigue conteniendo los datos**. |
