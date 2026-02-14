---
base: "[[Sistemas Operativos.base]]"
Sub-item: []
Blocked by: []
Parent item: []
Blocking: []
Categoria: []
---
## ==Procesos==

- **fork()**: Crea un proceso hijo idéntico al padre.
- **waitpid()**: Espera a que un proceso hijo termine.
- **execve()** (o `exec`, `execl`, `execv`, `execle`): Reemplaza la imagen del núcleo de un proceso con un nuevo programa.
- **exit()**: Termina la ejecución de un proceso y devuelve el estado.

## ==Archivos==

- **open()**: Abre un archivo para lectura, escritura o ambas.
- **close()**: Cierra un archivo abierto, liberando el descriptor de archivo.
- **read()**: Lee datos de un archivo y los coloca en un búfer.
- **write()**: Escribe datos de un búfer a un archivo.
- **lseek()**: Desplaza el apuntador del archivo a una posición específica.
- **create()**: Una forma de crear un nuevo archivo.
- **stat()** / **fstat()**: Obtiene la información de estado de un archivo.
- **mount()**: Monta un sistema de archivos.
- **umount()**: Desmonta un sistema de archivos.
- **link()**: Crea un vínculo a un archivo existente (enlace duro).
- **unlink()**: Elimina una entrada de directorio (un vínculo de un archivo).

## ==Directorios==

- **mkdir()**: Crea un nuevo directorio.
- **rmdir()**: Elimina un directorio vacío.
- **chdir()**: Cambia el directorio de trabajo actual.
- **chmod()**: Modifica los bits de protección de un archivo.
- **time()**: Obtiene el tiempo transcurrido (desde Ene 1, 1970).
- **kill()**: Envía una señal a un proceso.
- **sigaction()**: Define la acción a realizar en las señales.
- **sigreturn()**: Regresa de una señal.
- **sigprocmask()**: Examina o cambia la máscara de la señal.
- **sigpending()**: Obtiene el conjunto de señales bloqueadas.
- **pause()**: Suspende el proceso que hizo la llamada hasta la siguiente señal.
- **alarm()**: Establece el reloj de alarma.
- **sleep()** / **wakeup()**: Primitivas para la sincronización entre procesos.
- **select()**: Permite al proceso saber si una llamada a `read` causará un bloqueo.
- **receive()**: Recibe un mensaje (utilizado en el pasaje de mensajes).
- **pipe()**: Crea una tubería (un pseudoarchivo para IPC).
- **fcntl()**: Utilizada para el bloqueo de archivos y otras operaciones.
- **ioctl()**: Llamada antigua para acciones específicas de un dispositivo.
- **opendir()**: Abre un directorio para leerlo.
- **closedir()**: Cierra un directorio.
- **readdir()**: Lee una entrada del directorio.
- **rewinddir()**: Rebobina un directorio para poder volverlo a leer.
- **brk**: Mencionada para la expansión explícita del segmento de datos.
- **cfsetospeed()**, **cfsetispeed()**, **cfgetospeed()**, **cfgtetispeed()**: Llamadas POSIX para establecer y obtener la velocidad de la terminal.
- **tcsetattr()**, **tcgetattr()**: Llamadas POSIX para establecer y leer los atributos de la terminal.

<u>***Llamadas de la API Win32 y API Nativa de NT (Windows Vista)***</u>

- **CreateProcess()**: Crea un proceso.
- **WaitForSingleObject()**: Puede esperar a que un proceso, semáforo o mutex termine.
- **ExitProcess()**: Termina la ejecución de un proceso.
- **CreateFile()**: Crea o abre un archivo existente.
- **CloseHandle()**: Cierra un manejador.
- **ReadFile()**: Lee datos de un archivo.
- **WriteFile()**: Escribe datos en un archivo.
- **SetFilePointer()**: Desplaza el apuntador del archivo.
- **GetFileAttributesEx()**: Obtiene varios atributos de un archivo.
- **CreateDirectory()**: Crea un nuevo directorio.
- **RemoveDirectory()**: Elimina un directorio vacío.
- **DeleteFile()**: Destruye un archivo existente.
- **SetCurrentDirectory()**: Cambia el directorio de trabajo actual.
- **GetLocalTime()**: Obtiene la hora actual.
- **CreateSemaphore()**: Crea un nuevo semáforo.
- **CreateMutex()**: Crea un nuevo mutex.
- **OpenSemaphore()**: Abre un semáforo existente.
- **OpenMutex()**: Abre un mutex existente.
- **WaitForMultipleObjects()**: Se bloquea en un conjunto de objetos.
- **PulseEvent()**: Establece un evento como señalado, y después como no señalado.
- **ReleaseMutex()**: Libera un mutex.
- **ReleaseSemaphore()**: Incrementa el conteo de semáforos.
- **EnterCriticalSection()**: Adquiere un bloqueo en una sección crítica.
- **LeaveCriticalSection()**: Libera el bloqueo en una sección crítica.
- **VirtualAlloc()**: Reserva o confirma una región de memoria.
- **VirtualFree()**: Libera o desconfirma una región de memoria.
- **VirtualProtect()**: Cambia la protección de una región.
- **VirtualQuery()**: Consulta el estado de una región.
- **VirtualLock()**: Hace a una región residente en la memoria.
- **VirtualUnlock()**: Hace a una región paginable.
- **CreateFileMapping()**: Crea un objeto de asignación de archivos.
- **MapViewOfFile()**: Asigna un archivo en el espacio de direcciones.
- **ExitFiber()**: Termina una fibra.
- **SwitchToFiber()**: Ejecuta una fibra distinta en el hilo actual.
- **SetPriorityClass()**: Establece la clase de prioridad para un proceso.
- **SetThreadPriority()**: Establece la prioridad para un hilo.
- **InitializeSecurityDescriptor()**: Prepara un nuevo descriptor de seguridad.
- **LookupAccountSid()**: Busca el SID para un nombre de usuario.
- **SetSecurityDescriptorOwner()**: Introduce el SID de propietario en el descriptor.
- **SetSecurityDescriptorGroup()**: Introduce el SID de grupo en el descriptor.
- **InitializeAcl()**: Inicializa la DACL o SACL.
- **AddAccessAllowedAce()**: Agrega nuevo ACE a una DACL o SACL para permitir el acceso.
- **AddAccessDeniedAce()**: Agrega nuevo ACE a una DACL o SACL para negar el acceso.
- **DeleteAce()**: Elimina un ACE de una DACL o SACL.
- **SetSecurityDescriptorDacl()**: Adjunta un DACL a un descriptor de seguridad.
- **NtCreateThread**: Llamada nativa utilizada para crear un subproceso.
- **NtAllocateVirtualMemory**: Permite a un proceso asignar direcciones virtuales.
- **NtMapViewOfSection**: Permite a un proceso asignar secciones de mapas.
- **NtReadVirtualMemory**: Permite a un proceso leer en la memoria virtual de otros procesos.
- **NtWriteVirtualMemory**: Permite a un proceso escribir en la memoria virtual de otros procesos.
- **NtCreateFile**: Llamada de la API nativa para crear o abrir un archivo.
- **NtDuplicateObject**: Duplica manejadores de un proceso a otro.
- **NtClose**: Llamada nativa genérica para cerrar manejadores.
- **NtReadFile**: Llamada nativa de E/S.
- **NtWriteFile**: Llamada nativa de E/S.
- **NtQueryDirectoryFile**: Solicita información sobre directorios.
- **NtQueryInformationFile**: Solicita información sobre un archivo.
- **NtSetInformationFile**: Modifica la información de un archivo.
- **NtLockFile**: Bloquea un rango de bytes en un archivo.
- **NtUnlockFile**: Elimina un bloqueo de rango.
- **NtFsControlFile**: Varias operaciones en un archivo.
- **NtFlushBuffersFile**: Vacía los búferes de archivos en memoria al disco.
- **NtCancelIoFile**: Cancela las operaciones de E/S pendientes.
- **NtDeviceIoControlFile**: Operaciones especiales en un dispositivo.

<u>***Primitivas Pthreads (Hilos y Sincronización)***</u>

- **pthread_create**: Crea un hilo.
- **pthread_exit**: Termina el hilo.
- **pthread_join**: Espera a que el hilo termine.
- **pthread_yield**: Cede voluntariamente la CPU a otro hilo.
- **pthread_mutex_init**: Crea un mutex.
- **pthread_mutex_destroy**: Destruye un mutex existente.
- **pthread_mutex_lock**: Adquiere un mutex o se bloquea.
- **pthread_mutex_trylock**: Adquiere un mutex o falla.
- **pthread_mutex_unlock**: Libera un mutex.
- **pthread_cond_broadcast**: Se utiliza cuando hay varios hilos esperando una señal.
- **pthread_cond_wait**: Espera en una variable de condición.
- **pthread_cond_signal**: Despierta a otro hilo esperando en una variable de condición.
- **pthread_cond_init**: Inicializa una variable de condición.
- **pthread_cond_destroy**: Destruye una variable de condición.