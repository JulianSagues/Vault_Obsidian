### TP 3

- **Para saber cuántos bits se necesitan para representar este número de páginas,** se debe encontrar el número n tal que 2^n sea igual o mayor que 4028 que es la cantidad de páginas.

- **Bits para el desplazamiento:** El tamaño de cada página es de **1024 bytes**. Se debe encontrar el número n tal que 2^n sea igual o mayor a 1024.

- **Total de bits para la dirección lógica: Bits Numero Pagina + Bits Desplazamiento**

- **Bits para el número de marco de página:** La memoria física tiene 2048 marcos de página. Se debe encontrar el número n tal que 2^n sea igual o mayor que 2048.

- **Total de bits para la dirección fisica: Bits Marco+ Bits Desplazamiento**

- Tamaño Entrada Tabla Pagina: Bit presente/ausente + Bit referenciado + Bit modificado + Bit Marco

- Tamaño máximo de un proceso: 2^N, donde N es la arquitectura (32 o 64)

- Cantidad de entradas de la tabla de páginas = tamaño del espacio lógico/tamaño de cada página

- Espacio tabla de páginas = Cant de entradas * tamaño de cada entrada

- Espacio total de las tablas = Espacio tabla de páginas * Nro de procesos concurentes