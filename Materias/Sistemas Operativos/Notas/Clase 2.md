---
Parent item:
  - "[[Materias/Sistemas Operativos/Procesos e hilos\\|Procesos e hilos]]"
---
Al planificador lo dispara el S.O

  

Cuando tengo un proceso, divido el proceso en varios hilos que cooperan entre sí.

  

Los procesos tienen su propio espacio de memoria. En cambio los hilos comparten el espacio entre sí.

  

Todos los hilos comparten código entre si.

  

Ahora hay un bloque de control para cada hilo

  

Los hilos tienen:

![[temp_image_1757107221910.jpg]]

  

Los hilos son como procesos ligeros y también tienen su planificador como los procesos.

  

El S.O lo ve como un proceso por separado.

  

Cuando tengo mas de un núcleo, cada hilo va a correr en un núcleo distinto.

  

Buscar videos del mexicano: José Luis Elvira ———> Hilos

  

Que es un recurso?

Algo por lo cual se compite

  

Tenemos dos: De software y de Hardware.

  

Ej de recursos de Hardware: La memoria.

  

Ej de recurso de software:

  

Dos procesos no pueden modificar algo a la vez, pero si pueden leerlo.

Para evitar que esto suceda sale el concepto de REGION CRITICA. La cual es una porción de código que tiene que ENTRAR, HACER Y SALIR sin que nadie lo interrumpa, ósea debe ejecutarse de forma atómica. Esto se aplica cuando quiero modificar algo.

  

Condición de carrera: Cuando dos o mas procesos compiten por un recurso.

  

  

## **Comunicación entre procesos——→ leer del libro**

  

  

**Exclusión mutua y espera ocupada →**Si deshabilito las interrupciones

  

  

  

Instrucción TSL: Hace todas las instrucciones a nivel ISA → lo demas del libro

  

  

  

Semáforo→ Funciona igual que un semaforo, indica cuando y no puede pasar un proceso.

  

  

La region critica (codigo a nivel ISA) es una porcion de codigo que modifca un recurso compartido. Es esa porción de codigo que va a modificar algo y compite por el recurso para poder modificarlo a eso se lo llama condición de carrera.

  

![[temp_image_1757109174411.jpg]]

  

TODO HILOS LEER DEL LIBRO.