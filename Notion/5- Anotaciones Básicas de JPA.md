---
notion-id: 29bac26b-dee7-81d6-9203-eaf1a9976ccd
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - 29bac26b-dee7-80d2-9ccf-cc05773f4eeb
Blocking: []
Categoria: ""
---
![[image1 5.png]]

![[image2 5.png]]

![[image3 5.png]]

Cuando creamos una entidad cada atributo se convierte en una columna de la tabla, por

defecto el nombre de la columna es igual al del atributo.

![[image4 5.png]]

Con esto le damos a JPA un manual de instrucciones de como queremos la columna.

![[image5 6.png]]

A veces en nuestra clase tenemos campos que usamos dentro de la aplicación. Pero no queremos guardarlo en la base de datos. Puede ser un valor calculado, un

dato temporal o simplemente un dato que

no tiene sentido persistir.

Para eso nosotros tenemos una anotación @Transient, que es como decirle a JPA. Este campo a la hora de guardar lo tenés que ignorar.

Como se ve en el ejemplo, tenemos el stock disponible calculado. Aunque exista en la clase, al estar mapeado con esa anotación, JPA no lo va a convertir en una columna.

![[image6 8.png]]

En Java tenemos algo llamado Enum que nos sirve para representar un conjunto limitado de valores posibles.

Cuando nosotros guardamos un Enum en la base de datos,

por defecto, JPA lo usa como un número, el índice de la posición. Esto no es muy legible y puede ser un problema si nosotros cambiamos después el orden de los valores. Por eso, lo más recomendable en el caso de usar enum es guardar el nombre como texto y para eso usamos la anotación @enumerated enum type string.

![[image7 7.png]]

Como se ve en el ejemplo, tenemos la clase con las siguientes características:• @Entity: Marca que la clase será una entidad JPA.

- @Table(name = "nombre_tabla"): Permite especificar el nombre de la tabla en la base de datos, evitando usar el nombre de la clase.
- @Id y @GeneratedValue: Indican la clave primaria y cómo se va a generar ese valor.
- @Column(name = "nombre_columna", nullable = false, length = 100):• Se personaliza el nombre de la columna.
- Se define si puede ser nula o no.
- Se establece un largo máximo.
- @Column(unique = true): En el caso del código de barras, se especifica que el valor debe serúnico. No puede haber registros duplicados.
- @Enumerated(EnumType.STRING): Indica que el valor del Enum se va a guardar como una cadena.
- @Transient: En el caso del stock disponible, se usa para indicar que ese campo no se va a mapear en la tabla.

![[image8 6.png]]

<u>6- Ciclo de vida de una entidad</u>