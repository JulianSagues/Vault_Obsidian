---
base: "[[Sistemas Operativos.base]]"
Sub-item: []
Blocked by: []
Parent item:
  - "[[Notion/Materias/Sistemas Operativos/Memoria|Memoria]]"
Blocking: []
Categoria: []
---
## <u>**Paginación**</u>

![[temp_image_1757710402142.jpg]]


El pedacito que sobra es la fragmentación interna

saber diferencia entre frag interna e externa

Con lo que sobra en los pedazos podría meter otro proceso, pero el direccionamiento que estoy usando no me lo permite.

Saber cuanta memoria tengo → mapa de bits (esta es mas fácil) o listas enlazadas

Memoria virtual → Para ejecutar más procesos

Es bueno que sistema sea capaz de procesar mas de lo que puede?

Si lo es para no perder tiempo de cpu.

Si un proceso en un marco de pagina esta dormido debo expulsarlo (gestor de memoria) para permitir que otro proceso se ejecute.

la parte del proceso que se encuentra en memoria se llama parte residente en memoria

Area de swap → mientras mas grande sea el swap mas procesos voy a poder correr.

El área de **swap** (o espacio de intercambio) en sistemas operativos es como una especie de “memoria de respaldo” que se guarda en el disco rígido. Sirve para complementar la memoria RAM cuando esta se llena.

¿Qué hace el área de swap?

- **Almacena procesos inactivos**: Si hay procesos que no se están usando activamente, el sistema los mueve del RAM al swap para liberar espacio.
- **Simula más memoria**: Junto con la RAM, el swap forma la llamada *memoria virtual*, dando la ilusión de que hay más memoria disponible de la que realmente existe.
- **Evita cuelgues**: En situaciones de alta demanda, el swap puede evitar que el sistema se quede sin memoria y se bloquee.

trashing / hiperpaginacion→ cuando tenes muchismas paginas en el área de swap y el sistema se pasa mucho tiempo sacando y metiendo paginas de la RAM (swap in/ swap out). Esto hace que se pierda tiempo de cpu porque hay que buscar las partes del proceso que faltan.

## <u>**Direccionamiento**</u>

Ejemplo de programa:

a = 1

b = 2

c = 3

a+b+c

Con a,b y c el compilador les va asignar direcciones relativas 

Mi compilador genera direcciones relativas al programa ejecutable en nivel ISA porque no sabe cuanta memoria tiene.

Maquina multinivel→ cuando se compila bajamos de nivel, va bajando niveles hasta nivel ISA en ese nivel van a generarse las direcciones relativas de las variables y el programa en relación al programa ejecutable. El que se encarga de la direcciones real es el gestor de memoria


## <u>**Paginación Simple**</u>

![[temp_image_1757712671377.jpg]]

Para poder administrar memoria virtual necesito hardware de mmu (memory megnament unit).

Necesitamos una tabla de paginas por proceso y voy a tener mi memoria principal y la divido en marcos de pagina.

Parte izquierda los bits mas significativas y me dicen la entrada a mi tabla de paginas, donde tendre hasta 15 entradas 2 a la 4.

Los bits mas significativos son la entrada y dentro de la tabla de pagina tendre un apuntador (pointer) que apunta al numero del marco de pagina en mi memoria principal y a eso le sumo la parte derecha de los bits que es el desplazamiento.

El mmu va a recibir una direccion virtual o logica y la va convertir a una direccion fisica

tomo los primeros 4 bits que me dicen la direccion de la tbala de paginas, dentro de la direccion de la tabla me dice la direccion del marco de pagina.

El numero decimal del pointer lo transformamos de acuerdo a la cantidad de marcos de pagina y le sumamos el desplazamiento.

La tabla de paginas esta en memoria



Como el proceso sabe donde esta la tabla de paginas?s de donde saca el dato?

La tabla de procesos BCP dentro tendra un indice a la TABLA DE PAGINAS que le corresponde a ese proceso, cada proceso tiene su propia tabla de paginas SOLO EN PAGINACION SIMPLE.

El 5 en decimal es un apuntador  donde esta la direccion real en la memoria principal 

Que hay en la tabla de paginas?

Bit presente ausente si esta en 1 la pag esta en la mem y si esta en 0 no esta y hay que buscarla.

Bit referenciada si el proceso apunto a esa pagina

Bit modificada si la pagina ha sido modificada a la pagina que esta en memoria

Algoritmos de particiones y ubicaciones—>Lo toma estudiar de la diapositiva

Cuando se busca TLB y no esta es fallo suave, y si ademas en la tabla de pagina indica que no esta en memoria, es fallo duro

![[1000148058.jpg]]


Cuando la pagina no esta es un fallo de pagina suave, entonces le agregamos un hardware llamado TLB (tralation lookaside buffer). Solo sirve para ver si esta

Acierto de pag el bit p/a esta en 1→ cada vez que pasa eso el tlb

Algoritmos basicos de reemplazo → Estudiar diapositivas/libro

Consulta Jueves a las de 21:00 hs a 22:00hs virtual.

Parcial aula grande de dibujo 45mins teoría y práctica → preguntas de opción múltiple en la teoría.