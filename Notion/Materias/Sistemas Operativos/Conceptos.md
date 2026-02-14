---
notion-id: 2adac26b-dee7-802a-a4cb-fd20aaa8d8a7
base: "[[Sistemas Operativos.base]]"
Sub-item: []
Blocked by: []
Parent item: []
Blocking: []
Categoria: []
---
**El multiplexaje **es una técnica que permite **compartir un recurso único entre múltiples procesos, usuarios o datos**, de manera ordenada y eficiente.

La idea central es **"intercalar" **o **"dividir" **el uso de un recurso para que varios lo utilicen **como si lo tuvieran en exclusiva**, cuando en realidad lo están compartiendo.

**1. Multiplexaje en el Tiempo**

Cuando un recurso se multiplexa en el tiempo, los distintos programas o usuarios se turnan para utilizarlo. Uno de ellos obtiene acceso al recurso, después otro, y así sucesivamente

**2. Multiplexaje en el Espacio**

El otro tipo de multiplexaje es en el espacio. En lugar de que los clientes tomen turnos, cada uno obtiene una parte del recurso de forma simultánea

---

La canalización es una técnica de organización dentro de la CPU diseñada para **mejorar el rendimiento**.

En este modelo, los diseñadores de las CPUs abandonaron el enfoque de obtener, decodificar y ejecutar una instrucción a la vez. En su lugar, la canalización permite que la CPU tenga medios para **ejecutar más de una instrucción al mismo tiempo**

---

Una CPU **supraescalar** (o *superescalar*) es un diseño de arquitectura de procesador más avanzado que la canalización (*pipeline*), cuyo objetivo principal es **mejorar el rendimiento** utilizando múltiples unidades funcionales.

Este diseño organiza el "cerebro" de la computadora (la CPU) de tal manera que puede **ejecutar más de una instrucción al mismo tiempo**.

A continuación, se detallan sus características principales:

**Mecanismo y Componentes**

1. **Múltiples Unidades de Ejecución:** El diseño de una CPU supraescalar incluye **varias unidades de ejecución**. Estas unidades pueden estar especializadas; por ejemplo, una para la aritmética de enteros, otra para la aritmética de punto flotante y otra para las operaciones Booleanas.

2. **Obtención y Búfer de Contención:** A la vez, se **obtienen y decodifican dos o más instrucciones**, las cuales se vacían en un **búfer de contención** (o *issue buffer*) hasta que se puedan ejecutar.

3. **Ejecución Desordenada:** Tan pronto como una unidad de ejecución se encuentra libre, busca en el búfer de contención para ver si hay una instrucción que pueda manejar, la saca del búfer y la ejecuta. Una consecuencia de este diseño es que las **instrucciones del programa con frecuencia se ejecutan en forma desordenada**.

4. **Coherencia de Resultados:** Es responsabilidad del **hardware asegurarse de que el resultado producido sea el mismo** que se hubiera obtenido si las instrucciones se hubieran ejecutado de forma secuencial.

---

La **multiprogramación** es un concepto fundamental en los sistemas operativos y una técnica crucial diseñada para **mejorar la eficiencia y el rendimiento** de la Unidad Central de Procesamiento (CPU). Implica la **ejecución simultánea de varios programas** o procesos.

---

Una **condición de carrera** (race condition) ocurre en sistemas operativos cuando **dos o más procesos están leyendo o escribiendo algunos datos compartidos** y el **resultado final depende de quién se ejecuta y exactamente cuándo lo hace**

---

La **concurrencia** se refiere a la capacidad de un sistema operativo para manejar y ejecutar **varias actividades o programas de manera simultánea o cuasi-simultánea**