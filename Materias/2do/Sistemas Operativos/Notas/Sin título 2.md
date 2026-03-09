---
Parent item:
  - "[[Materias/Sistemas Operativos/Comandos-Llamadas TP\\|Comandos-Llamadas TP]]"
---
`strace -o output.txt ls -la`

|   |   |
|---|---|
|**Llamada al Sistema**|**Descripción de la Acción en el Log**|
|`**execve**`|Ejecuta el comando `/usr/bin/ls` con los argumentos `["ls", "-la"]`. Es el inicio del programa.|
|`**brk**`|Gestiona la memoria del heap (datos dinámicos). Se usa al inicio para reservar espacio básico.|
|`**mmap**`|Mapea archivos en memoria. Se usa intensivamente para cargar las librerías compartidas (`libc.so.6`, `libselinux.so.1`, etc.).|
|`**access**`|Comprueba si existen archivos de configuración antes de intentar abrirlos (ej. `/etc/ld.so.preload`, `/etc/selinux/config`).|
|`**openat**`|Abre archivos o directorios. Aquí abre librerías, archivos de configuración (`/etc/passwd`) y el directorio actual (`.`).|
|`**fstat**`|Obtiene información (tamaño, permisos) de un archivo que ya está abierto (identificado por un número descriptor).|
|`**close**`|Cierra un archivo abierto para liberar recursos.|
|`**read**`|Lee el contenido de los archivos abiertos (cabeceras de librerías, contenido de `/etc/passwd`, etc.).|
|`**pread64**`|Similar a `read`, pero lee desde una posición específica sin mover el puntero del archivo (usado en `libc.so.6`).|
|`**munmap**`|Des-mapea (libera) memoria que ya no se necesita (ej. `/etc/ld.so.cache` después de leerlo).|
|`**arch_prctl**`|Configura el estado específico de la arquitectura (x86_64) para el manejo de hilos (threads).|
|`**set_tid_address**`|Establece el puntero al ID del hilo (TID). Parte de la inicialización de la librería de C.|
|`**set_robust_list**`|Configura una lista de "futexes robustos", usado para manejar bloqueos en caso de fallos de hilos.|
|`**rseq**`|(Restartable sequences) Una optimización del kernel para operaciones rápidas en espacio de usuario.|
|`**mprotect**`|Cambia los permisos de una región de memoria (ej. hace que las librerías cargadas sean de solo lectura por seguridad).|
|`**prlimit64**`|Consulta o establece límites de recursos (aquí verifica el tamaño del stack).|
|`**statfs**`|Obtiene estadísticas del sistema de archivos (usado aquí para comprobar si SELinux está montado).|
|`**getrandom**`|Obtiene números aleatorios seguros del kernel (para inicialización de seguridad).|
|`**ioctl**`|Control de dispositivos de entrada/salida. Aquí consulta las características de la terminal (salida estándar).|
|`**futex**`|Mecanismo de sincronización rápida. Aquí se asegura de que no haya bloqueos pendientes.|
|`**getdents64**`|**La llamada clave de** `**ls**`. Lee las entradas del directorio (los archivos que se van a listar).|
|`**statx**`|Una versión moderna y extendida de `stat`. Obtiene metadatos detallados de cada archivo listado (`output.txt`, `..`).|
|`**lgetxattr**`|Intenta obtener atributos extendidos de un enlace simbólico (específicamente etiquetas de seguridad SELinux).|
|`**listxattr**`|Lista los atributos extendidos de un archivo.|
|`**socket**`|Crea un punto de comunicación de red (intenta crear un socket UNIX).|
|`**connect**`|Intenta conectarse a un socket (intenta hablar con el demonio `nscd` para resolver nombres de usuario, pero falla).|
|`**newfstatat**`|Obtiene información de un archivo relativo a un directorio (similar a `fstat` pero usando ruta).|
|`**lseek**`|Mueve el puntero de lectura dentro de un archivo (usado en `/etc/passwd` y archivos de zona horaria).|
|`**write**`|Escribe los datos finales en la pantalla (stdout). Es lo que ves como resultado del comando.|
|`**exit_group**`|Termina la ejecución de todos los hilos del proceso. Fin del programa.|

---

`ps -e`

![[Assets/image 6.png|image 6.png]]

### 1. **PID (Process ID)**

- **Significado:** Es el **Identificador de Proceso**.

- **Qué hace:** Es un número único que el sistema operativo asigna a cada proceso para identificarlo.

- **En tu imagen:**
    
    - El **PID 1** es siempre `systemd` (en sistemas modernos como Ubuntu). Es el proceso "padre" de todos los demás; es el primero que arranca cuando enciendes la máquina.
    
    - Los PIDs bajos (2, 3, 4...) suelen ser procesos del kernel o del sistema que arrancan muy temprano.
    

### 2. **TTY (TeleTYpewriter)**

- **Significado:** Indica la **terminal** desde la cual se ejecutó el proceso.

- **Qué significa el** `**?**`**:** En tu captura, todos tienen un signo de interrogación `?`. Esto significa que esos procesos **no están asociados a ninguna terminal**.
    
    - Son procesos que se ejecutan en segundo plano (background), conocidos como **demonios** (daemons) o hilos del kernel (como `kthreadd`), y no requieren interacción directa con un usuario a través de una ventana de comandos.
    
    - Si vieras algo como `pts/0` o `tty1`, significaría que ese proceso fue lanzado por un usuario desde una terminal específica.
    

### 3. **TIME**

- **Significado:** Es el **Tiempo Acumulado de CPU**.

- **Qué hace:** Muestra cuánto tiempo total ha estado el procesador trabajando _exclusivamente_ para ese proceso desde que se inició.

- **Formato:** `HH:MM:SS` (Horas:Minutos:Segundos).

- **En tu imagen:** La mayoría dice `00:00:00` porque, aunque están activos, son procesos muy eficientes o están "dormidos" esperando a que pase algo, por lo que apenas han consumido fracciones de segundo de la CPU.

### 4. **CMD (Command)**

- **Significado:** Es el **Nombre del Comando** o ejecutable.

- **Qué hace:** Indica qué programa o servicio se está ejecutando.

- **Ejemplos en tu imagen:**
    
    - `systemd`: El gestor del sistema y servicios.
    
    - `kthreadd`: Un proceso del kernel que gestiona otros hilos del kernel.
    
    - `kworker/...`: Son "trabajadores" del kernel que realizan tareas internas del sistema operativo.
    

---

`ps -ef`

![[Assets/image 1 4.png|image 1 4.png]]

- **UID (User ID)**
    
    - **Significado:** Es el **Usuario** dueño del proceso.
    
    - **En tu imagen:** Dice `root`, lo que significa que estos procesos fueron iniciados por el administrador del sistema (superusuario). Esto es crucial para saber quién está ejecutando qué.
    

- **PPID (Parent Process ID)**
    
    - **Significado:** Es el **ID del Proceso Padre**.
    
    - **Por qué es importante:** En Linux, los procesos crean otros procesos. El PPID te dice _quién_ creó al proceso actual.
    
    - **Ejemplo en tu imagen:** Mira los procesos con PID 3, 4, 5, 6 y 7. Todos tienen un **PPID de 2**. Esto significa que el proceso 2 (`kthreadd`) es el "padre" de todos ellos. Esto forma el árbol de procesos que verás luego con el comando `pstree`.
    

- **C**
    
    - **Significado:** Uso de CPU (factor de planificación).
    
    - **Descripción:** Es un valor entero que representa el porcentaje de uso de CPU reciente. El planificador del sistema operativo usa este número para decidir qué proceso debe ejecutarse a continuación. "0" significa que está usando muy poca o nada de CPU actualmente.
    

- **STIME (Start Time)**
    
    - **Significado:** Hora de inicio.
    
    - **Descripción:** Indica la hora exacta en que comenzó el proceso (en tu caso, a las 22:50). Si el proceso se inició hace más de 24 horas, aquí suele aparecer la fecha.
    

---

`pstree`

![[Assets/image 2 5.png|image 2 5.png]]

---

`top`

![[Assets/image 3 3.png|image 3 3.png]]

### **Parte 1: Resumen del Sistema (Cabecera)**

Las primeras 5 líneas te dan el estado global de la máquina.

**Línea 1: Tiempo y Carga**`top - 23:00:47 up 10 min, 1 user, load average: 0.00, 0.10, 0.12`

- **23:00:47**: Hora actual.

- **up 10 min**: Tiempo que la máquina lleva encendida (Uptime).

- **1 user**: Cantidad de usuarios logueados.

- **load average**: La carga media del procesador en el último **1 minuto**, **5 minutos** y **15 minutos**.
    
    - _Dato:_ Como tus valores son casi 0 (0.00, 0.10...), tu CPU está "relajada" y sin trabajo acumulado.
    

**Línea 2: Tareas (Procesos)**`Tasks: 216 total, 1 running, 215 sleeping, 0 stopped, 0 zombie`

- **Running (corriendo):** Procesos usando la CPU activamente ahora mismo (en tu foto es 1, probablemente el mismo comando `top`).

- **Sleeping (durmiendo):** Procesos cargados en memoria pero esperando que pase algo (un clic, datos de red, etc.) para despertar.

- **Zombie:** Procesos "muertos" que terminaron pero su padre no ha "limpiado" su salida. (Concepto importante en la teoría de Sistemas Operativos).

**Línea 3: Estado de la CPU (%)**`%Cpu(s): 0.1 us, 0.7 sy, 0.0 ni, 99.0 id, ...`  
Esta línea es crucial para ver "quién" gasta tu CPU:

- **us (user):** Tiempo gastado en programas de usuario (navegador, terminal, `gnome-shell`).

- **sy (system):** Tiempo gastado por el Kernel (núcleo del sistema).

- **id (idle):** Tiempo **libre**. Tienes **99.0%** libre, tu PC no está haciendo casi nada.

- **wa (wait):** Tiempo esperando al disco (E/S). Si esto es alto, tu disco es lento.

**Líneas 4 y 5: Memoria (TP 3)**  
Aquí ves la RAM física (Mem) y la memoria virtual/intercambio (Swap).

- **MiB Mem:** Tienes casi 12 GB (11961.8 MiB) totales, de los cuales 10 GB están libres.

- **Buff/cache:** Linux usa la RAM libre para guardar archivos frecuentes y acelerar el sistema. No es memoria "perdida", se libera si las aplicaciones la piden.

**Parte 2: Lista de Procesos (Columnas)**

|   |   |   |
|---|---|---|
|**Columna**|**Significado**|**Explicación de tu imagen**|
|**PID**|**Process ID**|El DNI del proceso. Fíjate que `gnome-shell` es el 2149.|
|**USER**|**Usuario**|Quién lanzó el proceso (`julian` o `root`).|
|**PR**|**Priority**|Prioridad del proceso para el kernel. (20 es estándar).|
|**NI**|**Nice**|Valor "Nice". Permite ajustar la prioridad manualmente.|
|**VIRT**|**Virtual Image**|Toda la memoria que el proceso "cree" tener (incluye librerías compartidas y swap). Es un número inflado. (Relacionado con TP3).|
|**RES**|**Resident Size**|**¡Esta es la importante!** La memoria RAM física real que está ocupando el proceso. `gnome-shell` usa unos 403 MB (403312 KiB).|
|**SHR**|**Shared Mem**|Memoria compartida con otros procesos.|
|**S**|**Status**|Estado: **R** (Running/Corriendo), **S** (Sleeping/Durmiendo), **I** (Idle/Inactivo). Fíjate que `top` está en **R** y el resto en **S**.|
|**%CPU**|**Uso CPU**|Porcentaje de procesador que usa. `gnome-shell` está usando un 4.3%.|
|**%MEM**|**Uso MEM**|Porcentaje de RAM física que usa.|
|**TIME+**|**Tiempo Total**|Tiempo total de CPU que ha consumido desde que arrancó (minutos:segundos.centésimas).|
|**COMMAND**|**Comando**|El nombre del programa.|

---

`htop`

![[Assets/image 4 2.png|image 4 2.png]]

### **Parte 1: Cabecera (Recursos del Sistema)**

En la parte superior izquierda ves el estado del hardware de forma gráfica:

- **0, 1, 2, 3:** Representan los **Núcleos (Cores) de tu CPU**. Tienes 4 núcleos. Las barras muestran cuánto se está usando cada uno (en tu imagen, muy poco, entre 1.3% y 2.0%).

- **Mem:** Barra de **Memoria RAM**.
    
    - Estás usando **919 MB** de **11.7 GB** disponibles.
    

- **Swp:** Barra de **Memoria Swap** (intercambio).
    
    - Está en **0K**, lo cual es excelente; significa que no estás usando el disco duro como RAM (lo que haría todo más lento).
    

En la parte superior derecha:

- **Tasks:** Resumen de procesos (118 total, 1 corriendo).

- **Load average:** La carga promedio del sistema (igual que en `top`).

- **Uptime:** Tiempo encendido (11 minutos).

**Parte 2: Lista de Procesos (Columnas)**

|   |   |   |
|---|---|---|
|**Columna**|**Significado**|**Detalle en tu imagen**|
|**PID**|Process ID|Identificador único. El proceso seleccionado (barra celeste) es el **3295**.|
|**USER**|Usuario|Dueño del proceso (`julian`).|
|**PRI / NI**|Prioridad/Nice|Igual que en `top`. Determina la prioridad para el procesador.|
|**VIRT**|Virtual|Memoria virtual asignada.|
|**RES**|Resident|**Memoria RAM real** que usa. `gnome-shell` usa unos 408M.|
|**SHR**|Shared|Memoria compartida.|
|**S**|Estado (State)|**R** (Running - Corriendo), **S** (Sleeping - Durmiendo).|
|**CPU%**|Uso CPU|Porcentaje de procesador. `htop` (PID 3295) usa 2.7%.|
|**MEM%**|Uso MEM|Porcentaje de memoria RAM.|
|**TIME+**|Tiempo|Tiempo total de CPU acumulado.|
|**Command**|Comando|El programa ejecutado. **Nota:** `htop` muestra la ruta completa y los argumentos en colores distintos, lo que facilita la lectura.|

### **Parte 3: Pie de Página (Menú Interactivo)**

Esta es la gran diferencia y **ventaja clave para tu TP**. En lugar de memorizar teclas raras, tienes un menú abajo que puedes usar con las teclas **F** (Function Keys) o haciendo **clic con el mouse**:

- **F1 Help:** Ayuda.

- **F2 Setup:** Configuración (cambiar colores, columnas, etc.).

- **F3 Search:** Buscar un proceso por nombre.

- **F4 Filter:** Filtrar la lista (muy útil para ver solo procesos que contengan cierta palabra).

- **F5 Tree: ¡Muy importante!** Muestra los procesos en forma de árbol (padre-hijo), similar a `pstree`.

- **F6 SortBy:** Ordenar por otra columna (ej. por memoria en lugar de CPU).

- **F9 Kill: Matar proceso.** Permite enviar señales (como SIGKILL) para cerrar programas trabados seleccionándolos primero.

- **F10 Quit:** Salir.

---

  
`ls /proc/<PID>/`

![[Assets/image 5 2.png|image 5 2.png]]

### Archivos clave para identificar el proceso:

- `**cmdline**`: Contiene el **comando completo** con el que se inició el proceso, incluyendo sus argumentos. Si le haces un `cat cmdline`, verás exactamente qué programa es (útil si solo tienes el número PID y no sabes qué es).

- `**cwd**` (Current Working Directory): Es un **enlace simbólico** (por eso está en azul cian) que apunta a la carpeta donde está "parado" el proceso actualmente.

- `**exe**`: Es un **enlace simbólico** al archivo ejecutable real en el disco. Si el proceso es `firefox`, este enlace apunta a `/usr/bin/firefox`.

- `**environ**`: Contiene las **variables de entorno** que tiene cargadas este proceso (como el `PATH`, el usuario `USER`, etc.).

### Archivos de estado y recursos:

- `**status**`: **El más importante para lectura humana.** Contiene un resumen legible del estado del proceso: su nombre, estado (Running, Sleeping), PID del padre (PPID), uso de memoria, usuario que lo ejecutó (Uid), etc.

- `**fd**` (File Descriptors): Es un **directorio** que contiene enlaces a todos los archivos, conexiones de red (sockets) o dispositivos que el proceso tiene **abiertos**. Si el proceso está escribiendo un log o leyendo un archivo, aparecerá aquí.

- `**maps**`: Muestra cómo está distribuida la memoria del proceso (dónde están cargadas las librerías, el stack, el heap). Es vital para entender la gestión de memoria (Guía 3).

- `**stat**`: Información de estado similar a `status` pero solo con números, diseñada para ser leída por programas (como `ps` o `top`), no por humanos.

---

`pidstat -p $(pgrep -u username firefox) 1`

![[Assets/image 6 2.png|image 6 2.png]]

|   |   |   |
|---|---|---|
|**Columna**|**Significado**|**Explicación**|
|**UID**|**User ID**|El identificador del usuario dueño del proceso. `0` corresponde a **root** (administrador)2.|
|**PID**|**Process ID**|El identificador único del proceso. Aquí es **1**, que es el proceso padre del sistema (`systemd`).|
|**%usr**|**User CPU**|Porcentaje de tiempo que la CPU dedicó a ejecutar código de la aplicación (nivel usuario).|
|**%system**|**Kernel CPU**|Porcentaje de tiempo que la CPU dedicó a ejecutar tareas del sistema operativo (kernel) solicitadas por este proceso.|
|**%guest**|**Guest CPU**|Porcentaje de CPU usado para correr una máquina virtual (si la hubiera).|
|**%wait**|**Wait Time**|Porcentaje de tiempo que el proceso pasó **esperando** a que la CPU se liberara para poder ejecutarse.|
|**%CPU**|**Total CPU**|La suma total del uso del procesador (%usr + %system). En tu imagen es **0.12%**, muy bajo.|
|**CPU**|**Core ID**|Indica en qué núcleo (número de procesador) se ejecutó el proceso. En este caso, el núcleo **3**.|
|**Command**|**Comando**|El nombre del proceso o comando que se está monitoreando (`systemd`).|

---

`free`

![[image 7.png]]

### **Filas (Tipos de Memoria)**

1. **Mem:** Se refiere a la **Memoria RAM física** instalada en tu equipo.

1. **Swap:** Se refiere al **Espacio de Intercambio**. Es una parte del disco duro que el sistema usa como si fuera RAM cuando la física se llena.
    
    - **Nota:** En tu imagen, todos los valores de Swap son **0**. Esto significa que **no tienes configurada una partición o archivo de Swap**, o está desactivada.
    

### **Columnas (Estado de la Memoria)**

Los valores en tu imagen están expresados en **Kilobytes (KB)** (el formato por defecto si no usas `-h`).

|   |   |   |
|---|---|---|
|**Columna**|**Significado**|**Explicación**|
|**total**|**Memoria Total**|Es la cantidad total de RAM que el sistema operativo ve (excluyendo una pequeña parte reservada por el kernel). Tienes aprox. **12 GB** (12,248,900 KB).|
|**used**|**Usada**|La memoria que está siendo **activamente utilizada** por los procesos y no puede ser liberada inmediatamente.|
|**free**|**Libre**|Memoria que está completamente **vacía** y sin asignar. Tienes aprox. **9.6 GB** libres.|
|**shared**|**Compartida**|Memoria usada principalmente por `tmpfs` (sistemas de archivos temporales en memoria). Es memoria que puede ser accedida por varios procesos.|
|**buff/cache**|**Búfer y Caché**|**¡Muy importante!** Es memoria que Linux usa para almacenar datos de disco leídos recientemente. Esto acelera el sistema. **No es memoria desperdiciada**; si una aplicación necesita más RAM, el sistema libera esta memoria instantáneamente.|
|**available**|**Disponible**|**Esta es la cifra real de "memoria libre" para aplicaciones nuevas.** Es una estimación de cuánta memoria está disponible para iniciar nuevos programas sin tener que recurrir al Swap. Suma la memoria `free` más la parte de `buff/cache` que se puede reclamar.|

---

`smem -r -k`

![[image 8.png]]

### **Columnas Generales**

- **PID:** El identificador único del proceso (ej. `2149` para `gnome-shell`).

- **User:** El usuario que ejecuta el proceso (`julian`).

- **Command:** El nombre del programa o comando ejecutado.

- **Swap:** Cantidad de memoria de intercambio usada. En tu imagen es **0**, lo que indica que no se está usando disco como RAM.

### **Columnas de Memoria (¡Lo más importante!)**

La gran ventaja de `smem` es que distingue entre memoria única y compartida. Fíjate cómo los números crecen de izquierda a derecha (USS < PSS < RSS):

|   |   |   |   |
|---|---|---|---|
|**Columna**|**Nombre Completo**|**Significado**|**Análisis en tu imagen**|
|**USS**|**Unique Set Size**|**Memoria Única.** Es la memoria privada que **solo** usa ese proceso. Si matas el proceso, esta es la cantidad exacta de RAM que recuperarás inmediatamente.|Para `gnome-shell`, recuperarías **315.7M** inmediatamente.|
|**PSS**|**Proportional Set Size**|**Tamaño Proporcional.** Es la métrica más "justa". Suma la memoria única (USS) + una **parte proporcional** de la memoria compartida. Si 10 procesos comparten una librería de 10MB, a cada uno se le suma 1MB en su PSS.|`gnome-shell` "consume" realmente **348.6M** si consideramos su parte de las librerías compartidas.|
|**RSS**|**Resident Set Size**|**Tamaño Residente.** Es la métrica estándar que usan `top` y `ps`. Suma la memoria única + **toda** la memoria compartida. Suele exagerar el consumo porque cuenta las librerías compartidas completas para cada proceso.|`ps` te diría que `gnome-shell` usa **433.8M**, lo cual es un poco engañoso.|

---

`vmstat`

![[image 9.png]]

### **1. Procs (Procesos)**

Esta sección te dice qué están haciendo los procesos en este preciso instante.

- `**r**` **(runnable):** Número de procesos que están esperando ejecutarse o ejecutándose.
    
    - _En tu imagen:_ Tienes **6**. Esto significa que hay 6 procesos "compitiendo" por la CPU en este momento.
    

- `**b**` **(blocked):** Número de procesos en sueño ininterrumpible (bloqueados), generalmente esperando a que el disco duro responda (E/S).
    
    - _En tu imagen:_ **0**, lo cual es bueno; nada está trabado esperando al disco.
    

### **2. Memory (Memoria)**

Información sobre el uso de la RAM (en Kilobytes por defecto).

- `**swpd**`**:** Cantidad de memoria virtual (Swap) usada.
    
    - _En tu imagen:_ **0**, no estás usando swap.
    

- `**free**`**:** Memoria física completamente libre (inactiva).
    
    - _En tu imagen:_ ~9.1 GB libres.
    

- `**buff**`**:** Memoria usada como "búferes" (almacenamiento temporal para escritura de datos crudos de disco).

- `**cache**`**:** Memoria usada como "caché" (almacenamiento de archivos leídos del disco para acceso rápido).
    
    - _Nota:_ Linux usa la RAM libre para caché (`2030624` KB en tu caso) para acelerar el sistema.
    

### **3. Swap (Intercambio)**

Muestra el movimiento de datos entre la RAM y el disco de swap.

- `**si**` **(swap in):** Cantidad de memoria leída desde el disco de swap hacia la RAM (/s).

- `**so**` **(swap out):** Cantidad de memoria llevada desde la RAM hacia el disco de swap (/s).
    
    - _En tu imagen:_ Ambos son **0**, lo que confirma que no hay paginación activa (tu RAM es suficiente).
    

### **4. IO (Entrada/Salida)**

Muestra la actividad de lectura/escritura en tus discos.

- `**bi**` **(blocks in):** Bloques recibidos desde un dispositivo de bloques (lectura de disco).
    
    - _En tu imagen:_ **731**, indica actividad de lectura moderada.
    

- `**bo**` **(blocks out):** Bloques enviados a un dispositivo de bloques (escritura en disco).

### **5. System (Sistema)**

Muestra la actividad de interrupciones y cambios de contexto del kernel.

- `**in**` **(interrupts):** Número de interrupciones por segundo, incluyendo el reloj.

- `**cs**` **(context switches):** Número de cambios de contexto por segundo (cuántas veces la CPU cambió de un proceso a otro).

### **6. CPU (Procesador)**

Muestra en qué gasta el tiempo tu procesador (en porcentajes del tiempo total de CPU).

- `**us**` **(user):** Tiempo ejecutando código de usuario (tus programas).

- `**sy**` **(system):** Tiempo ejecutando código del kernel (sistema operativo).

- `**id**` **(idle):** Tiempo inactivo/ocioso.
    
    - _En tu imagen:_ **98%**. Tu sistema está casi totalmente "descansando".
    

- `**wa**` **(wait):** Tiempo esperando a entrada/salida (disco/red). Si este número es alto, tienes un "cuello de botella" en el disco.

- `**st**` **(stolen):** Tiempo "robado" por una máquina virtual (si tu Linux fuera una VM y el anfitrión no le diera CPU).

- `**gu**` **(guest):** Tiempo gastado ejecutando una CPU virtual para sistemas invitados (si tu Linux fuera el anfitrión de otras VMs)

---

`cat /proc/meminfo`

![[image 10.png]]

---

`cat /etc/fstab/`

![[image 11.png]]

|   |   |   |
|---|---|---|
|**Columna**|**Valor en tu imagen**|**Significado**|
|**1. Sistema de Archivos**|`/dev/disk/by-uuid/...`|**¿Qué se monta?** Identifica la partición. En lugar de usar nombres antiguos como `/dev/sda1`, usa un **UUID** (Identificador Único Universal). Es más seguro porque el UUID no cambia si conectas el disco en otro puerto.|
|**2. Punto de Montaje**|`/`|**¿Dónde aparece?** Es el directorio donde se verán los archivos. La barra `/` indica que esta es la partición **Raíz** (donde está instalado todo el sistema operativo).|
|**3. Tipo**|`ext4`|**¿Qué formato tiene?** Indica el sistema de archivos. `ext4` es el estándar actual en la mayoría de las distribuciones Linux (como Ubuntu).|
|**4. Opciones**|`defaults`|**¿Cómo se monta?** Aplica la configuración estándar: lectura/escritura (`rw`), permite ejecutar binarios (`exec`), se monta al inicio (`auto`), etc.|
|**5. Dump**|`0`|**¿Copia de seguridad?** Es una opción antigua para la herramienta de backup `dump`. `0` significa "no hacer backup".|
|**6. Pass**|`1`|**¿Chequeo de errores?** Indica el orden en que la herramienta `fsck` revisa el disco al arrancar.  <br>• `1`: Se usa solo para la raíz (`/`), indicando que se revisa **primero**.  <br>• `2`: Se usa para otras particiones.  <br>• `0`: No revisar.|

---

`lsblk -f`

![[image 12.png]]

**1. Columnas Principales:**

- **NAME:** El nombre del dispositivo (`sda`, `loop0`, etc.).

- **FSTYPE (File System Type):** El tipo de formato. Aquí ves `**ext4**`, `squashfs` e `iso9660`.

- **UUID:** El identificador único universal (clave para el archivo `/etc/fstab` que vimos antes).

- **MOUNTPOINTS:** Dónde está montado en tu árbol de directorios.

**2. Desglose de tus dispositivos:**

- `**sda**` **y** `**sda2**` **(Tu Disco Principal):**
    
    - `**sda2**` es tu partición principal.
    
    - **FSTYPE:** `**ext4**`. Aquí confirmas que está formateada como ext4.
    
    - **MOUNTPOINTS:** `**/**`. Es la raíz de tu sistema.
    
    - **Lo que FALTA:** Mira atentamente todas las columnas. **En ningún lado dice "4096" o "Block Size"**. Muestra el tamaño total de la partición (17.2G en `FSAVAIL` implícito en el tamaño total), pero no el tamaño del bloque lógico. **Por esto el punto 5 del examen estaba mal.**
    

- `**loop0**` **a** `**loop8**` **(Paquetes Snap):**
    
    - Son dispositivos de bucle (ver TP 5, Ejercicio 2 ).
    
    - **FSTYPE:** `squashfs`. Es un sistema de archivos comprimido de solo lectura, muy usado por Ubuntu para los paquetes "Snap" (aplicaciones contenidas).
    
    - Están montados en `/snap/...`.
    

- `**sr0**` **(Tu unidad de CD/DVD virtual):**
    
    - **FSTYPE:** `iso9660`. Es el formato estándar de CD-ROMs.
    
    - **Label:** `VBox_GAs...`. Son las "Guest Additions" de VirtualBox que tienes insertadas para mejorar la integración con la máquina virtual.
    

---

`ls -l /dev | grep '^c’`

![[image 13.png]]

Tomemos como ejemplo la línea:  
`crw-rw-rw- 1 root root 1, 7 Nov 27 22:50 full`

- `**c**` **(Primera letra):** Esto es lo más importante. Indica que es un **Dispositivo de Carácter** (Character Device). A diferencia de los dispositivos de bloque (que empiezan con `b`, como los discos duros), estos transmiten datos byte a byte, como un flujo (stream).

- `**rw-rw-rw-**`: Permisos de lectura y escritura.

- `**root root**`: Usuario y grupo propietario (generalmente root).

- `**1, 7**` **(Números Mayor y Menor):** Fíjate que en lugar del "tamaño del archivo" (bytes), aquí aparecen dos números separados por coma.
    
    - **Mayor (**`**1**`**):** Identifica al **driver** (controlador) del kernel que maneja este dispositivo.
    
    - **Menor (**`**7**`**):** Identifica al dispositivo específico dentro de ese driver.
    

- `**full**`: El nombre del dispositivo.

### **3. Ejemplos en tu imagen**

- `**console**`: La consola del sistema (teclado/pantalla) para mensajes del kernel.

- `**full**`: Un dispositivo curioso; si intentas leer de él, te da ceros, pero si intentas escribir en él, el sistema te devuelve un error de "disco lleno" (útil para probar cómo reaccionan los programas ante falta de espacio).

- `**fuse**`: (Filesystem in Userspace) Permite montar sistemas de archivos virtuales sin tocar el código del kernel.

- `**hwrng**`: (Hardware Random Number Generator) Generador de números aleatorios por hardware, usado para criptografía.

---

`cat /proc/devices`

![[image 14.png]]

### **1. Estructura de la Salida**

La lista está dividida en dos categorías principales (aunque en tu captura solo se ve la primera):

1. **Character devices (Dispositivos de Caracteres):** Los que ves en la imagen. Son dispositivos que transmiten datos como un flujo continuo (byte a byte), sin búfer. Ejemplos: teclados, ratones, puertos serie, consolas.

1. **Block devices (Dispositivos de Bloque):** (Estarían más abajo si hicieras scroll). Son dispositivos que almacenan datos y transfieren información en bloques de tamaño fijo. Ejemplos: discos duros, RAM disks.

### **2. Significado de las Columnas**

- **Número (Izquierda):** Es el **Número Mayor (Major Number)**.
    
    - Este número es el identificador interno que usa el Kernel para saber qué **driver** (controlador de software) debe manejar ese dispositivo.
    
    - Por ejemplo, ves que el número **4** está asociado a `tty` y `ttyS`. Esto significa que cualquier archivo en `/dev` que tenga el número mayor 4 será manejado por el driver de la terminal.
    

- **Nombre (Derecha):** Es el nombre del dispositivo o del controlador asociado.
    
    - `mem` (1): Acceso a la memoria física.
    
    - `tty` / `console` (4, 5): Terminales y consolas para interactuar con el sistema.
    
    - `input` (13): Dispositivos de entrada como teclados y ratones.
    
    - `fb` (29): Framebuffer, usado para mostrar gráficos en pantalla.