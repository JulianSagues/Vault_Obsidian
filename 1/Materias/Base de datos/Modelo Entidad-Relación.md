---
Material de Estudio:
  - "[[Gua_estudio_practica_2_Modelos-ER.pdf]]"
---
![[Assets/image 425.png|image 425.png]]

Pasos para el diseño

1. Encontrar entidades (conjuntos de entidades)

1. Identificar atributos de las entidades

1. Buscar identificadores

1. Especificar las relaciones y cardinalidades

1. Identificar relaciones especiales y resolver atributos derivados, volátiles,  
    multivaluados y compuestos, relaciones muchos a mucho y relaciones trasferibles  
    y no trasferibles

1. Especializar y generalizar entidades donde sea posible

### ENTIDADES

Una ENTIDAD es una cosa u objeto concreto o abstracto que existe en el mundo, real y que puede diferenciarse de otros; no es una propiedad concreta sino un objeto que puede poseer múltiples propiedades (atributos).

CONJUNTO DE ENTIDADES es la clase o tipo al que pertenecen entidades con características comunes. Es decir, las entidades que poseen las mismas propiedades forman conjuntos de entidades.

![[Assets/image 1 20.png|image 1 20.png]]

### Dependencia de existencia

Decimos que existe una dependencia de existencia entre una entidad, subordinada, y otra, dominante, cuando la eliminación de la entidad dominante, conlleva también la eliminación de la entidad o entidades subordinadas.

Notación Barker: Las entidades se representan esquemáticamente mediante cajas de bordes redondeados, dentro de las cuales se coloca el nombre de la entidad. Este nombre va siempre en singular y en mayúsculas.

![[Assets/image 2 18.png|image 2 18.png]]

### ATRIBUTOS

Describen propiedades de las entidades y las relaciones.

Cada una de las características que posee una entidad, y que agrupadas permiten distinguirla de otras entidades del mismo conjunto.

Un atributo es cualquier detalle que sirve para:

- Identificar.

- Describir.

- Cualificar.

- Clasificar.

- Expresar el estado de una entidad.

Un atributo puede tener valor solo durante una parte del tiempo o ser desconocido. Esta clase de atributos se denomina opcional y se representa mediante un pequeño círculo (sin rellenar) antepuesto al nombre del atributo

Notación Barker: El valor de un atributo que debe ser siempre conocido, se representa mediante un asterisco (*) o un punto (.) antepuesto al nombre del atributo. Nótese que esto se aplica a los atributos cuyo valor debe ser siempre conocido, invalidando instancias de la entidad en las que no haya valor para estos.

![[Assets/image 3 15.png|image 3 15.png]]

Se manejan varios tipos distintos de atributos: simples o compuestos; monovaluados o multivaluados y almacenados o derivados.

![[Assets/image 4 13.png|image 4 13.png]]

Los atributos compuestos son útiles para modelar situaciones en las que un usuario en unas ocasiones hace referencia al atributo compuesto como una unidad, pero otras veces se refiere específicamente a sus componentes. Si solo se hace referencia al atributo compuesto como un todo, no hay necesidad de subdividirlo en sus atributos componentes.

![[Assets/image 5 8.png|image 5 8.png]]

![[Assets/image 6 7.png|image 6 7.png]]

Notación Barker: Para representar un atributo, se escribe su nombre en minúscula y singular,  
opcionalmente acompañado de un ejemplo de su valor.

Los atributos deben describir únicamente a las entidades con las que están asociadas.

Una entidad suele tener entre dos y ocho atributos. Si se encuentran más de ocho, probablemente hay entidades o relaciones ocultas en el modelo.

Una entidad solo puede tener un valor para cada atributo en un momento dado. Si resulta esencial tener múltiples valores, es necesario crear una entidad para almacenarlos y una relación de muchos a uno con la entidad original

El nombre de un atributo se debe escribir en singular y minúscula. Un nombre plural coincide, usualmente, con el problema de repetición mencionado anteriormente. Así mismo, la repetición de atributos puede revelar la existencia de entidades faltantes en el modelo.

Un atributo se transforma en una entidad cuando tiene significado completo en sí mismo, con relaciones y atributos propios.

### IDENTIFICADOR ÚNICO

Toda entidad debe poder ser identificada con unicidad mediante uno de sus atributos o una combinación de los mismos, denominado identificador único. Por lo tanto, siempre resulta necesario determinar qué atributo o atributos sirven para identificar una entidad

Identificador Único: es un conjunto de atributos que identifican de forma unívoca una entidad: es el conjunto mínimo compuesto por uno o más atributos que permite identificar de manera unívoca a una ocurrencia de entidad dentro de un tipo de entidad.

Para que un atributo sea considerado un buen identificador tiene que cumplir:

- Deben distinguir a cada ejemplar teniendo en cuenta las entidades que utiliza el modelo. No tiene que ser un identificador absoluto.

- Todos los ejemplares de una entidad deben tener el mismo identificador.

- Cuando un atributo es importante aun cuando no tenga una entidad concreta asociada, entonces se trata de una entidad y no de un atributo

El Identificador Único puede ser un atributo, combinación de atributos o combinación de atributos y relaciones.

A los atributos que se pueden emplear alternativamente como identificadores de una entidad se les denomina identificadores alternativos.

El método esencial para representar el identificador único en un diagrama entidad relación consiste en anteceder con el signo # a cada atributo que contribuya al identificador único y en colocar una barra cruzada en la línea de la(s) relación(es) que participa(n) del identificador.

- UID candidato: uno de los diferentes UID que se pueden utilizar para identificar algo

- UID primario: UID candidato que es el identificador primario de algo

- UID secundario: UID candidato que también identifica algo, pero no es el UID primario

Los UID secundarios pueden resultar útiles como una forma alternativa de búsqueda de datos.

### RELACIONES entre entidades

Una relación es una asociación nombrable, significativa entre dos entidades.

Interrelación: es la asociación o conexión entre conjuntos de entidades.

![[Assets/image 7 6.png|image 7 6.png]]

Toda relación tiene dos extremos, para cada uno de los cuales existen:

- Una leyenda.

- Un grado o cardinalidad (uno o muchos)

- Una opcionalidad (opcional u obligatoria).

Grado: número de conjuntos de entidades que intervienen en una interrelación

![[Assets/image 8 5.png|image 8 5.png]]

Existen además tres tipos distintos de interelaciones binarias, dependiendo del número de entidades del primer conjunto de entidades y del segundo. Así hablaremos de interrelaciones 1:1 (uno a uno), 1:N (uno a muchos) y N:M (muchos a muchos).

Los ROLES representan el papel que juega una entidad en una determinada relación. Ejemplo:  

![[Assets/image 9 4.png|image 9 4.png]]

NOTACIÓN BARKER: Una relación se representa mediante una línea que conecta las cajas correspondientes a las dos entidades o que conecte recursivamente a una caja consigo misma El nombre de cada relación se coloca en minúscula junto al extremo apropiado, como se muestra.

![[Assets/image 10 4.png|image 10 4.png]]

Cuando el extremo de la relación es obligatoria se emplea el verbo debe antes del nombre de la relación. Para relaciones opcionales, se emplea el verbo puede.

Así, el diagrama anterior se lee de izquierda a derecha como:

- Una ENTIDAD-A debe ser nombre-1 un ENTIDAD-B.

Y leído de derecha a izquierda:

- Una ENTIDAD-B puede ser nombre-2 muchos ENTIDAD-A

La relación más común es la de grado 1:N, obligatoria en el extremo N y opcional en el extremo 1.

Una relación recursiva suele representar jerarquías definidas sobre una misma entidad, como se muestra en el siguiente diagrama.

![[Assets/image 11 4.png|image 11 4.png]]

Este diagrama podría corresponder, por ejemplo, a una jerarquía de cargos en una empresa (jefes y subordinados).

El plural del nombre de la entidad se emplea cuando el grado es muchos.

Al elaborar diagramas entidad-relación se logra mayor legibilidad al colocar el extremo abierto (muchos) en el lado izquierdo o superior. Adicionalmente, el uso de los verbos ser y estar provee nombres de la relación más significativos y útiles.

![[Assets/image 12 4.png|image 12 4.png]]

### Cardinalidad

La correspondencia de cardinalidades, o razón de cardinalidad, expresa el número de entidades a las que otra entidad puede estar asociada por medio de una interrelación. Dicho de otro modo, expresa el número de entidades con las que puede asociarse una entidad.

Se anota en términos de:

- cardinalidad mínima. Indica el número mínimo de asociaciones en las que aparecerá cada ejemplar de la entidad (el valor que se anota es de cero o uno)

- cardinalidad máxima. Indica el número máximo de relaciones en las que puede aparecer cada ejemplar de la entidad (puede ser uno o muchos)

![[Assets/image 13 4.png|image 13 4.png]]

![[Assets/image 14 4.png|image 14 4.png]]

![[Assets/image 15 3.png|image 15 3.png]]

![[Assets/image 16 3.png|image 16 3.png]]

![[Assets/image 17 3.png|image 17 3.png]]

![[Assets/image 18 3.png|image 18 3.png]]

![[Assets/image 19 3.png|image 19 3.png]]

### ATRIBUTOS DE LOS TIPOS DE RELACIÓN

![[Assets/image 20 3.png|image 20 3.png]]

![[Assets/image 21 3.png|image 21 3.png]]

Resumiendo, los atributos de los tipos de relación 1:N y 1:1 se pueden trasladar a al menos uno de los tipos de entidad participantes. En el caso de 1:1 a cualquiera de los dos tipos de entidad participantes, mientras que en el caso 1:N se puede trasladar al tipo de entidad que tiene una participación con cardinalidad 1.

En el caso de los tipos de relación N:M, algunos atributos pueden estar determinados por la combinación de la entidades participantes en una instancia del tipo de relación, y no por alguna de ellas sola.

Entidad de intersección: producto de la resolución de una relación de varios a varios.

Relación excluida: relación que participa en el identificador único de una entidad.