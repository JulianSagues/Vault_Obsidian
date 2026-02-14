---
base: "[[Sistemas Operativos.base]]"
Sub-item:
  - "[[Notion/Materias/Sistemas Operativos/Untitled|Untitled]]"
Blocked by: []
Parent item: []
Blocking: []
Categoria: []
---
## Guía Práctica N°1 – Generalidades de Sistemas Operativos

| **Comando** | **Desglose** | **Descripción breve** |
| --- | --- | --- |
| `strace -o output.txt ls -la` | `-o output.txt`: guarda el resultado en un archivo. <br>`ls -la`: lista todos los archivos (incluidos ocultos). | Ejecuta `ls -la` registrando las llamadas al sistema. |

---

## Guía Práctica N°2 – Procesos y Administración del Procesador

| **Comando** | **Desglose** | **Descripción breve** |
| --- | --- | --- |
| `ps` | Muestra los procesos actuales del usuario. | Lista procesos activos. |
| `ps -e` | `-e`: muestra todos los procesos del sistema. | Lista todos los procesos en ejecución. |
| `ps -ef` | `-f`: formato extendido (UID, PID, PPID, CMD). | Muestra información completa de los procesos. |
| `pstree` | Muestra jerarquía de procesos en forma de árbol. | Visualiza relaciones padre-hijo. |
| `htop` | Monitor interactivo de procesos. | Muestra uso de CPU, memoria y permite matar procesos. |
| `kill <PID>` | `kill`: envía señal de finalización. `<PID>`: identificador del proceso. | Cierra un proceso específico. |
| `kill -9 <PID>` | `-9`: señal SIGKILL (forzada). | Mata un proceso de inmediato. |
| `pkill <nombre>` | `pkill`: termina procesos por nombre. | Cierra todos los procesos que coincidan con ese nombre. |
| `watch -n 1 'ps -e'` | `watch`: ejecuta un comando periódicamente.<br> `-n 1`: intervalo de 1 segundo. | Monitorea procesos en tiempo real. |
| `strace -p <PID>` | `-p`: adjunta `strace` a un proceso existente. | Muestra las llamadas al sistema del proceso. |
| `pidstat -p $(pgrep -u usuario firefox) 1` | `pidstat`: muestra estadísticas. <br>`-p`: indica PID. <br>`$(pgrep -u usuario firefox)`: obtiene el PID de Firefox. <br>`1`: refresca cada segundo. | Monitorea el uso de CPU y memoria del proceso. |

---

## Guía Práctica N°3 – Administración de Memoria

| **Comando** | **Desglose** | **Descripción breve** |
| --- | --- | --- |
| `free` | Sin parámetros muestra memoria total, usada, libre y swap. | Informa el estado general de la RAM. |
| `smem -r -k` | `-r`: recalcula estadísticas. <br>`-k`: muestra valores en KB. | Da un detalle del uso de memoria por proceso. |
| `vmstat` | Muestra procesos, memoria, swap, CPU y E/S. | Brinda estadísticas en vivo del sistema. |
| `cat /proc/meminfo` | `cat`: muestra contenido de archivo. <br>`/proc/meminfo`: archivo del kernel con info de memoria. | Muestra detalles del uso de memoria y caché. |

---

## Guía Práctica N°4 – Sistema de Archivos

| **Comando** | **Desglose** | **Descripción breve** |
| --- | --- | --- |
| `cat /etc/fstab` | `/etc/fstab`: archivo de configuraciones de montajes automáticos. | Muestra los sistemas de archivos montados al inicio. |
| `lsblk -f` | `-f`: muestra tipo de FS, UUID y etiqueta. | Lista discos, particiones y su formato. |
| `dd if=/dev/zero of=mi_imagen.img bs=1M count=100` | `if=/dev/zero`: genera ceros. `of=mi_imagen.img`: destino. `bs=1M`: bloque de 1 MB. `count=100`: 100 bloques. | Crea una imagen vacía de 100 MB. |
| `mkfs.ext4 mi_imagen.img` | `mkfs`: crea un FS. `ext4`: tipo de sistema de archivos. | Formatea la imagen como EXT4. |
| `sudo mkdir /mnt/mi_imagen` | `mkdir`: crea un directorio. `/mnt/mi_imagen`: punto de montaje. | Crea la carpeta donde se montará la imagen. |
| `sudo mount -o loop mi_imagen.img /mnt/mi_imagen` | `-o loop`: monta archivo como dispositivo. | Monta la imagen como disco virtual. |
| `df -h | grep mi_imagen`  | `df -h`: muestra espacio usado (GB/MB). <br>`grep`: filtra coincidencias. | Verifica si la imagen está montada. |
| `sudo umount /mnt/mi_imagen` | `umount`: desmonta un FS. | Libera el punto de montaje. |
| `echo "$(pwd)/mi_imagen.img /mnt/mi_imagen ext4 loop 0 0" | sudo tee -a /etc/fstab ` | `echo`: genera texto. <br>`$(pwd)`: ruta actual. <br>`tee -a`: agrega al archivo. | Añade la entrada de montaje automático. |
| `ln -s original.txt enlace_simbólico.txt` | `-s`: crea enlace simbólico. | Crea un acceso simbólico (soft link). |
| `ln original.txt enlace_duro.txt` | Sin `-s`: enlace duro. | Crea un hard link (mismo inodo). |
| `rm original.txt` | Elimina el archivo original. | Permite ver el comportamiento de los enlaces. |

---

## Guía Práctica N°5 – Sistema de Entrada/Salida

| **Comando** | **Desglose** | **Descripción breve** |
| --- | --- | --- |
| `lsblk` | Lista todos los dispositivos de bloque. | Muestra discos, particiones y loops. |
| `ls -l /dev | grep '^c'` | `ls -l /dev`: lista dispositivos. `grep '^c'`: filtra de tipo carácter. | Muestra los dispositivos de carácter. |
| `cat /proc/devices` | Archivo del kernel con dispositivos registrados. | Lista los dispositivos de bloque y carácter. |
| `dd if=/dev/zero of=loopback.img bs=1M count=50` | `if=/dev/zero`: fuente de ceros. `of=loopback.img`: destino. `bs=1M`: bloque de 1 MB. `count=50`: 50 bloques. | Crea una imagen vacía de 50 MB. |
| `sudo losetup /dev/loop0 loopback.img` | `losetup`: vincula imagen con dispositivo. | Asocia la imagen al dispositivo de bucle. |
| `sudo mkfs.ext4 /dev/loop0` | `mkfs.ext4`: formatea en EXT4. | Crea FS en el dispositivo de bucle. |
| `sudo mkdir /mnt/loopback` | Crea directorio para montaje. | Prepara punto de montaje. |
| `sudo mount /dev/loop0 /mnt/loopback` | Monta el dispositivo en el punto indicado. | Permite acceder al contenido. |
| `df -h | grep loop0` | Verifica el estado de montaje. | Muestra espacio disponible del bucle. |
| `sudo umount /mnt/loopback` | Desmonta el FS. | Libera el recurso. |
| `sudo losetup -d /dev/loop0` | `-d`: detach (desasocia). | Libera el dispositivo de bucle. |
| `sudo mknod /dev/mychar c 240 0` | `mknod`: crea dispositivo. <br>`c`: carácter. <br>`240 0`: números mayor/menor. | Crea dispositivo de carácter personalizado. |
| `sudo mknod /dev/myblock b 241 0` | `b`: tipo bloque. <br>`241 0`: IDs. | Crea dispositivo de bloque personalizado. |
| `gcc -o char_device char_device.c` | `gcc`: compilador C. <br>`-o`: nombre de salida. | Compila el programa de prueba. |
| `sudo ./char_device` | Ejecuta el programa con permisos root. | Interactúa con el dispositivo creado. |
| `iostat -d 1 5` | `-d`: muestra solo discos. <br>`1 5`: actualiza cada 1 s, 5 veces. | Mide actividad de E/S de discos. |
| `sudo apt-get install -y sysstat` | Instala paquete `sysstat` (contiene iostat). | Habilita monitoreo de E/S. |
| `sudo iotop` | Muestra uso de E/S por proceso. | Indica qué procesos leen/escriben en disco. |

---

# Llamadas al sistemas

| **Llamada al Sistema** | **Descripción en el TP** |
| --- | --- |
| `**openat()**` | Utilizada para abrir directorios y archivos. |
| `**read()**` | Utilizada para leer contenido de archivos (o dispositivos). |
| `**write()**` | Utilizada para escribir la salida a la terminal o enviar datos a un dispositivo. |
| `**close()**` | Utilizada para cerrar archivos y liberar el descriptor de archivo. |
| `**getdents()**` | Utilizada para leer las entradas de un directorio (listar contenido). |
| `**open()**` | Variante estándar para abrir un archivo/dispositivo (usada en el código C de la Guía 5). |