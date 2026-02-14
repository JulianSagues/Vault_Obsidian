---
Parent item:
  - "[[Materias/Desarrollo de software/Notas/JPA\\|JPA]]"
Sub-item:
  - "[[Materias/Desarrollo de software/Notas/1-JPA\\|1-JPA]]"
  - "[[Materias/Desarrollo de software/Notas/2- H2 Database\\|2- H2 Database]]"
  - "[[Materias/Desarrollo de software/Notas/3-persistense.xml\\|3-persistense.xml]]"
  - "[[Materias/Desarrollo de software/Notas/4- JPA paso a paso\\|4- JPA paso a paso]]"
  - "[[Materias/Desarrollo de software/Notas/5- Anotaciones Básicas de JPA\\|5- Anotaciones Básicas de JPA]]"
  - "[[Materias/Comunicacion de datos/6- Ciclo de vida de una entidad\\|6- Ciclo de vida de una entidad]]"
  - "[[Materias/Desarrollo de software/Notas/7- Relaciones Unidireccionales en JPA\\|7- Relaciones Unidireccionales en JPA]]"
  - "[[Materias/Desarrollo de software/Notas/8- Relaciones Bidireccionales en JPA\\|8- Relaciones Bidireccionales en JPA]]"
  - "[[Materias/Desarrollo de software/Notas/9- CascadeType y orphanRemoval\\|9- CascadeType y orphanRemoval]]"
  - "[[Materias/Desarrollo de software/Notas/10- FetchType LAZY vs EAGER\\|10- FetchType LAZY vs EAGER]]"
---
### 1 - ¿Qué es JPA?

Este video introductorio define **JPA (Jakarta Persistence API)** como una especificación estándar de Java para el mapeo objeto-relacional (ORM), lo que simplifica enormemente el trabajo con bases de datos en aplicaciones Java. El ponente explica que JPA actúa como un **"puente inteligente"** entre el mundo de los objetos Java y el mundo de las tablas relacionales.

Se destacan **tres beneficios principales** de usar JPA:

- **Mapeo Objeto-Relacional**: Permite a los desarrolladores trabajar directamente con objetos Java (POJOs) sin escribir SQL para cada operación (INSERT, SELECT, UPDATE, DELETE).

- **Gestión del Ciclo de Vida**: JPA se encarga automáticamente de crear, leer, actualizar y eliminar objetos en la base de datos.

- **Abstracción de la Base de Datos**: Ofrece la flexibilidad de cambiar de un sistema de base de datos a otro (por ejemplo, de H2 a MySQL) con mínimos cambios en el código de la aplicación, solo modificando la configuración.

Es importante entender que JPA es una **especificación** (un conjunto de reglas), no una herramienta en sí. Para utilizarla, se necesita un **proveedor** que implemente estas reglas, siendo **Hibernate** y **EclipseLink** los ejemplos más comunes. El video también menciona la flexibilidad de configuración, que se logra a través de **anotaciones** en las clases Java o archivos XML, o una combinación de ambos.

Finalmente, se presentan los **componentes clave** de JPA:

- **Entidades**: Clases Java que representan tablas en la base de datos.

- **Entity Manager**: Un objeto que actúa como "control remoto" para interactuar con la base de datos (guardar, buscar, actualizar, eliminar).

- **Entity Manager Factory**: Una "fábrica" encargada de crear instancias del Entity Manager.

- **Unidad de Persistencia**: Un concepto que agrupa un conjunto de entidades y define la configuración para trabajar con ellas, generalmente a través del archivo `persistence.xml`.

- **JPQL (Jakarta Persistence Query Language)**: Un lenguaje de consulta orientado a objetos que permite realizar búsquedas utilizando entidades y atributos de Java, en lugar de tablas y columnas SQL.

Este video sienta las bases para comprender la importancia y el funcionamiento general de JPA en el desarrollo moderno de Java, destacando sus ventajas en productividad, mantenibilidad, portabilidad y rendimiento.

---

### 2- H2 Database

Este segundo video se enfoca en **H2 Database**, una base de datos relacional ligera y de código abierto, completamente escrita en Java, que es ideal para entornos de desarrollo y pruebas con JPA. Su naturaleza 100% Java permite una integración sencilla en cualquier sistema con una Java Virtual Machine.

Entre sus **características principales** se destacan:

- Una **consola web** que permite gestionar la base de datos desde el navegador, facilitando la visualización y manipulación de datos.

- Compatibilidad con el estándar **SQL**, lo que la hace familiar para quienes ya conocen MySQL o PostgreSQL.

El video explica los **cuatro modos de funcionamiento** de H2:

- **Modo Memoria**: La información se guarda en la RAM y se borra al apagar la aplicación, perfecto para pruebas unitarias o inicios con una base de datos limpia.

- **Modo Basado en Archivos**: Los datos se almacenan en disco, persistiendo incluso después de reiniciar la aplicación, ideal para desarrollo local.

- **Modo Embebido**: La base de datos se ejecuta dentro de la misma aplicación Java, eliminando la necesidad de un servidor externo.

- **Modo Cliente-Servidor**: Permite que múltiples aplicaciones o usuarios se conecten a la misma base de datos desde diferentes máquinas, simulando un entorno de servidor real.

Se demuestra cómo **descargar e instalar H2** y, lo más importante, cómo **configurarlo para trabajar con JPA** a través del archivo `persistence.xml`. En este archivo, se deben indicar propiedades clave como el driver JDBC de H2, la URL de conexión (que varía según el modo en memoria o archivo), el usuario (comúnmente "SA") y la contraseña. Se muestran ejemplos de `persistence.xml` para los modos en memoria y archivo.

Finalmente, el video detalla cómo **acceder y usar la consola web de H2** para inspeccionar tablas, ejecutar consultas SQL y verificar los datos. Se brindan consejos importantes para la configuración, como la necesidad del `persistence.xml`, la URL y el driver JDBC, y la propiedad `schema generation` de Hibernate (por ejemplo, `drop-and-create` o `update`) para definir cómo JPA gestionará el esquema de la base de datos al iniciar la aplicación.

---

### 3 - Persistence.xml

Este video se sumerge en el `**persistence.xml**`, descrito como el "corazón de la configuración de JPA". Su función es ser el "mapa de ruta" para JPA, indicando a qué base de datos conectarse, qué clases son entidades, qué proveedor de JPA utilizar y cómo gestionar el esquema de la base de datos.

Las **partes principales** de un archivo `persistence.xml` son:

- El **elemento raíz** `**<persistence>**`.

- Una o más **unidades de persistencia (**`**<persistent-unit>**`**)**, que son el centro de la configuración. Cada unidad debe tener un nombre único (ej. `ejemplo_PU`) que JPA usará para crear el `EntityManagerFactory`. También se especifica el tipo de transacción, como `RESOURCE_LOCAL` para aplicaciones sencillas o `JTA` para entornos con servidores de aplicaciones.

- Las **clases de entidad (**`**<class>**`**)**: Aquí se declaran todas las clases Java que JPA debe mapear a tablas de la base de datos (por ejemplo, `Persona`, `Domicilio`). Si una entidad no se lista aquí, JPA la ignorará.

- El **bloque de propiedades (**`**<properties>**`**)**: Este es crucial y se encuentra dentro de `<persistent-unit>`. Aquí se configuran dos tipos de propiedades:
    
    - **Propiedades de conexión JDBC**: Incluyen el `driver` de la base de datos (ej. `org.h2.Driver`), la `URL` de conexión (para modos en memoria o archivo de H2), el `usuario` y la `contraseña`.
    
    - **Propiedades del proveedor de JPA (Hibernate en este caso)**: Como el `dialecto` SQL para H2 (`org.hibernate.dialect.H2Dialect`), `show_sql` (para ver las consultas SQL en consola) y `format_sql` (para un formato legible del SQL).
    

Una de las propiedades más importantes es la **estrategia de generación del esquema (**`**hibernate.hbm2ddl.auto**`**)**, que indica a JPA qué hacer con las tablas al inicio de la aplicación:

- `drop-and-create`: Borra todas las tablas y las crea de nuevo.

- `create`: Crea las tablas solo si no existen.

- `update`: Intenta actualizar el esquema sin borrar datos.

- `validate`: Solo revisa que el esquema coincida con las entidades, sin hacer cambios.

El video muestra un **ejemplo completo de** `**persistence.xml**` con todas estas configuraciones. Finalmente, explica cómo se utiliza este archivo desde el código Java para obtener el `EntityManagerFactory` y el `EntityManager`, y ofrece **recomendaciones** como evitar almacenar contraseñas en texto plano, usar diferentes `persistence.xml` para desarrollo y producción, y desactivar `show_sql` en producción para mejorar el rendimiento.

---

### 4 - JPA paso a paso

Este video marca el paso de la teoría a la práctica, mostrando **JPA en acción por primera vez**. El objetivo es unir los conceptos previos (JPA, H2 y `persistence.xml`) para construir un ejemplo completo, creando una entidad, configurándola, conectándose a la base de datos y guardando información real.

Los **pasos para preparar el entorno** son:

1. **Crear un proyecto Java**: Se recomienda usar un IDE como IntelliJ IDEA, seleccionando Maven o Gradle como gestor de dependencias y un JDK (por ejemplo, JDK 17).

1. **Añadir dependencias**: Incluir las librerías de H2, JPA y el proveedor de JPA (Hibernate) en el archivo de configuración de dependencias (`build.gradle` para Gradle o `pom.xml` para Maven). Se sugiere usar Maven Repository para buscar las dependencias.

1. **Crear el** `**persistence.xml**`: Este archivo se coloca en la carpeta `src/main/resources/META-INF`, conteniendo la configuración de la unidad de persistencia, las clases de entidad, las propiedades de conexión a H2 y las propiedades específicas de Hibernate.

El video luego se enfoca en la **creación de la primera entidad JPA**:

- Una entidad es una **clase Java común** con anotaciones específicas que le indican a JPA cómo mapearla a una tabla de la base de datos.

- Se crea la clase `Persona`, anotada con `**@Entity**` para indicar que es una entidad.

- Se define un campo para la **clave primaria (**`**id**`**)** y se anota con `**@Id**`.

- Para que el ID se genere automáticamente, se utiliza `**@GeneratedValue**` con una estrategia como `GenerationType.IDENTITY` (autoincrementable).

- Otras propiedades de los atributos (como `nombre`) se pueden definir con `**@Column**`, permitiendo especificar el nombre de la columna, si es `nullable` o `unique`, y su longitud. La tabla también puede tener un nombre personalizado con `@Table`.

- Es crucial **declarar la entidad en el** `**persistence.xml**` para que JPA la reconozca.

Para la **interacción con JPA** en el código Java:

- Se crean el `**EntityManagerFactory**` (una sola vez por aplicación) y el `**EntityManager**` (el "puente" para las operaciones de base de datos).

- Se enfatiza la necesidad de **transacciones** (`beginTransaction()`, `commit()`, `rollback()`) para cualquier modificación en la base de datos, garantizando la consistencia.

- Se demuestra cómo **guardar un objeto** `**Persona**` utilizando `entityManager.persist(persona)` y cómo **buscarlo** por su ID utilizando `entityManager.find(Persona.class, id)`. Se explica que JPA usa un "contexto de persistencia" o caché de primer nivel para evitar consultas repetidas si el objeto ya está cargado.

- Finalmente, se muestra cómo **verificar los datos** en la base de datos utilizando la consola web de H2, confirmando que la información se ha guardado correctamente.

Este video es fundamental para comprender el flujo de trabajo básico con JPA, desde la configuración del proyecto hasta la persistencia y recuperación de datos en un entorno real con un código mínimo y sin SQL directo.

---

### 5- Anotaciones básicas JPA

Este video profundiza en las **anotaciones básicas de JPA**, que son las instrucciones que se le dan a JPA para que entienda cómo las clases Java se mapean a tablas de la base de datos y cómo cada atributo se guarda en ellas. Sin estas anotaciones, JPA no podría adivinar la estructura de la base de datos.

Las **anotaciones clave** explicadas son:

- `**@Entity**`: Es la anotación fundamental que marca una clase como una entidad de JPA, indicando que representa una tabla en la base de datos.

- `**@Table**`: Permite especificar el nombre exacto de la tabla en la base de datos (`name`) si es diferente del nombre de la clase Java, y otras configuraciones. Ejemplo: `@Table(name = "productos_inventario")`.

- `**@Id**`: Se usa para designar el campo que será la **clave primaria** de la tabla, identificando de manera única cada registro.

- `**@GeneratedValue**`: Esta anotación se combina con `@Id` para configurar la **generación automática de valores para la clave primaria**. Se exploran dos estrategias comunes:
    
    - `GenerationType.IDENTITY`: La base de datos genera el ID automáticamente (autoincremental).
    
    - `GenerationType.AUTO`: JPA elige la estrategia más conveniente para la base de datos subyacente.
    

- `**@Column**`: Permite un control granular sobre cómo se mapea un atributo de la entidad a una columna de la tabla. Sus atributos incluyen:
    
    - `name`: Para especificar el nombre exacto de la columna.
    
    - `nullable`: Indica si la columna puede aceptar valores nulos (`true`) o no (`false`).
    
    - `length`: Define la longitud máxima para campos de texto.
    
    - `unique`: Asegura que los valores en esa columna sean únicos en toda la tabla.
    
    - Ejemplo: `@Column(name = "nombre_producto", nullable = false, length = 100, unique = true)`.
    

- `**@Transient**`: Se utiliza para marcar campos de la clase que **no deben ser persistidos** en la base de datos. Estos campos pueden ser valores calculados o datos temporales que solo existen en la aplicación.

- `**@Enumerated(EnumType.STRING)**`: Cuando se trabaja con tipos `Enum` en Java, esta anotación permite que JPA guarde el **nombre del valor Enum como una cadena de texto** en la base de datos, en lugar de su posición ordinal (índice numérico). Esto mejora la legibilidad y la robustez ante cambios en el orden del Enum.

El video concluye mostrando un **ejemplo combinado** de una clase `Producto` que utiliza todas estas anotaciones, ilustrando cómo definir una entidad completa en JPA con personalizaciones para las tablas, claves primarias, columnas, campos transitorios y enumeraciones. Con estas anotaciones, los desarrolladores tienen las herramientas para definir cualquier entidad básica en JPA.

---

### 6- Ciclo de vida de una entidad en JPA

Este video explica el **ciclo de vida de una entidad en JPA**, un concepto fundamental para entender cómo JPA gestiona los objetos en memoria y cómo interactúan con la base de datos. Saber en qué estado se encuentra una entidad ayuda a evitar errores y optimizar el rendimiento. El **Entity Manager** es el actor principal en este proceso, ya que es quien gestiona los estados de la entidad.

Una entidad puede estar en **cuatro estados diferentes**:

1. **Nuevo (Transient)**: Una entidad está en este estado cuando se acaba de instanciar (`new Objeto()`). No tiene un ID asignado por la base de datos y JPA no la conoce. Los cambios realizados en este estado no se guardarán hasta que se incorpore a JPA.

1. **Gestionado (Persistent)**: La entidad está bajo el control del `Entity Manager`. Esto significa que JPA detectará automáticamente cualquier cambio en sus atributos (conocido como **"dirty checking"**) y los sincronizará con la base de datos al realizar un `commit`. Se puede llegar a este estado de varias maneras:
    
    - Usando `entityManager.persist()` en una entidad nueva.
    
    - Usando `entityManager.find()` para buscar una entidad existente.
    
    - Ejecutando consultas JPQL o Criteria que devuelvan entidades.  
        En este estado, JPA también utiliza una caché de primer nivel para evitar consultas innecesarias.
    

1. **Desasociado (Detached)**: Una entidad pasa a este estado cuando ya no está bajo el control activo del `Entity Manager`, aunque aún conserva su ID válido de la base de datos. Esto puede ocurrir si se cierra el `Entity Manager`, se llama al método `detach()` sobre la entidad, o si se serializa. Los cambios realizados en una entidad desasociada **no serán persistidos** en la base de datos automáticamente.

1. **Eliminado (Removed)**: La entidad está marcada para ser eliminada de la base de datos. Se alcanza este estado al llamar a `entityManager.remove()` sobre una entidad gestionada. La eliminación física en la base de datos no ocurre de inmediato, sino cuando se confirma la transacción con `commit`.

El video ilustra las **transiciones entre estados** con un diagrama, mostrando que el paso de un estado a otro se logra mediante operaciones específicas de JPA (ej. `persist` de Nuevo a Gestionado, `close` o `detach` de Gestionado a Desasociado, `merge` de Desasociado a Gestionado, `remove` de Gestionado a Eliminado).

Se ofrecen **buenas prácticas** como:

- Cerrar el `Entity Manager` cuando no se esté usando para evitar consumo excesivo de recursos.

- Mantener las transacciones cortas.

- Verificar siempre el estado de la entidad antes de operar.

- Usar `merge()` solo cuando sea necesario.

Finalmente, se abordan **errores comunes**:

- Modificar un objeto desasociado y esperar que se guarde.

- **Lazy Initialization Exception**: Ocurre al intentar acceder a datos de una relación `LAZY` después de que el `Entity Manager` ha sido cerrado.

- Olvidar hacer el `commit` de la transacción.

Dominar el ciclo de vida de las entidades es crucial para un manejo efectivo de la persistencia en JPA.

---

### Ejemplo en código: Ciclo de vida de las entidades

Este video es un **ejemplo práctico y detallado** en código Java que ilustra los diferentes estados en el ciclo de vida de una entidad JPA utilizando una clase `Producto`.

1. **Estado Nuevo (Transient)**:
    
    - Se crea un objeto `Producto` usando `new Producto()`, y en este punto, el producto existe solo en memoria, no tiene un ID asignado por la base de datos y JPA no lo está gestionando. Si el programa terminara, este objeto desaparecería sin dejar rastro en la base de datos.
    

1. **Estado Gestionado (Persistent)**:
    
    - Para pasar al estado gestionado, se inicia una transacción y se llama a `entityManager.persist(producto)`. Después del `commit`, el producto ya tiene un ID asignado y está bajo el control de JPA.
    
    - Se demuestra el **"dirty checking"**: mientras el producto está gestionado, se modifica su precio (`producto.setPrecio(1100)`). Al hacer `commit`, JPA detecta automáticamente este cambio y genera una sentencia UPDATE en la base de datos sin que el programador tenga que escribirla manualmente. Esto resalta una de las grandes ventajas de JPA.
    

1. **Estado Desasociado (Detached)**:
    
    - El producto se desasocia al **cerrar el** `**EntityManager**` (`entityManager.close()`). Aunque el objeto `Producto` sigue existiendo en memoria y conserva su ID, ya no está bajo la gestión de JPA.
    
    - Se muestra que si se modifica el precio de un producto desasociado (`producto.setPrecio(999)`), estos cambios **no se persisten** en la base de datos, solo se reflejan en el objeto en memoria.
    
    - Para volver a gestionar un objeto desasociado, se debe crear un nuevo `EntityManager` y usar `entityManager.merge(producto)`. `merge` se encargará de reasociar el objeto y persistir los cambios pendientes en la base de datos.
    

1. **Estado Eliminado (Removed)**:
    
    - Finalmente, se demuestra el estado eliminado. Se inicia una transacción, se llama a `entityManager.remove(producto)` sobre el producto gestionado, y al hacer `commit`, el registro se **elimina físicamente** de la base de datos.
    

El video concluye que, aunque la teoría pueda parecer abstracta, la práctica con este ejemplo claro hace que los cuatro estados principales (Nuevo, Gestionado, Desasociado, Eliminado) y sus transiciones sean fáciles de comprender, destacando cómo JPA automatiza gran parte del trabajo de persistencia.

---

### 7- Relaciones Unidireccionales en JPA

Este video se centra en las **relaciones unidireccionales entre entidades en JPA**. En estas relaciones, solo una entidad "conoce" o tiene una referencia a la otra, actuando como una "flecha que va de A hacia B, pero B no sabe nada de A". Este tipo de mapeo es más simple, con menos código y acoplamiento, siendo ideal cuando no se necesita que ambas entidades se conozcan mutuamente.

Se exploran **tres tipos principales de relaciones unidireccionales**:

1. `**@OneToOne**` **(Uno a Uno)**:
    
    - Una entidad se relaciona con una única instancia de otra entidad.
    
    - **Ejemplo**: `Usuario` tiene un `DetalleUsuario`. `Usuario` contiene una referencia a `DetalleUsuario`, pero `DetalleUsuario` no tiene una referencia de vuelta a `Usuario`.
    
    - Se usa `**@JoinColumn**` para indicar que la clave foránea se guardará en la tabla de la entidad propietaria (en este caso, `usuario`). Se añade `unique = true` para asegurar la unicidad de la relación.
    

1. `**@ManyToOne**` **(Muchos a Uno)**:
    
    - Muchas instancias de una entidad se relacionan con una única instancia de otra entidad.
    
    - **Ejemplo**: Muchos `Empleados` trabajan en un `Departamento`. Cada `Empleado` tiene una referencia a su `Departamento`, pero `Departamento` no tiene una lista de `Empleados`.
    
    - La clave foránea (ej. `departamento_id`) se guarda en la tabla de la entidad "muchos" (en este caso, `empleado`).
    

1. `**@OneToMany**` **(Uno a Muchos)**:
    
    - Una entidad se relaciona con varias instancias de otra entidad.
    
    - **Ejemplo**: Una `Factura` tiene muchos `ItemFactura`. `Factura` contiene una lista de `ItemFactura`, pero `ItemFactura` no tiene una referencia de vuelta a `Factura`.
    
    - Es **crucial usar** `**@JoinColumn**` con `@OneToMany` unidireccional. Si no se especifica, Hibernate podría crear una tabla intermedia innecesaria (como si fuera un Many-to-Many). Al usar `@JoinColumn` (ej. `factura_id`), se le indica a JPA que la clave foránea debe ir directamente en la tabla de los ítems, simplificando la estructura de la base de datos.
    
    - Se menciona que `Many-to-Many` también puede ser unidireccional, aunque es menos común y se suele implementar de forma bidireccional.
    

El video ofrece **buenas prácticas** para trabajar con relaciones unidireccionales:

- Utilizar `**FetchType.LAZY**` por defecto en colecciones para evitar cargar datos innecesarios, lo que es crucial para el rendimiento.

- Siempre usar `**@JoinColumn**` para controlar la ubicación de las claves foráneas.

- No usar `mappedBy` en relaciones unidireccionales, ya que es exclusivo de las bidireccionales.

- Se aborda el problema **N+1** (múltiples consultas adicionales para cargar relaciones) y se sugiere usar `join fetch` o `EntityGraph` para optimizar las consultas.

En resumen, las relaciones unidireccionales son una forma sencilla y eficiente de conectar entidades cuando la navegación en una sola dirección es suficiente, y el uso correcto de `@JoinColumn` y `FetchType.LAZY` es clave para un buen rendimiento.

---

### 8- Relaciones Bidireccionales en JPA

Este video se adentra en las **relaciones bidireccionales entre entidades en JPA**, donde dos entidades se referencian mutuamente, permitiendo la navegación en ambos sentidos ("una flecha doble, de A hacia B y de B hacia A").

Las **razones para usar relaciones bidireccionales** incluyen:

- **Navegación más rica**: Permite acceder a los datos desde cualquiera de las entidades, simplificando consultas y operaciones.

- **Modelo de objeto más completo**: Representa mejor las relaciones reales entre los objetos del dominio (ej. un estudiante tiene cursos y un curso tiene estudiantes).

- **Mejor reflejo del dominio**: Si en la vida real las entidades están relacionadas en ambos sentidos, el código debería reflejarlo.

- **Serialización completa**: Útil en APIs REST para armar respuestas que muestran toda la información relacionada.

Un concepto **clave** en las relaciones bidireccionales es el **lado propietario** y el **lado inverso**:

- **Lado Propietario**: Es la entidad que mantiene la clave foránea en la base de datos, define el `@JoinColumn` y es la que realmente afecta la persistencia.

- **Lado Inverso**: No tiene impacto directo en la base de datos; solo sirve para la navegación en el código y se define con el atributo `mappedBy`. Solo uno de los lados debe ser el propietario para evitar que JPA interprete dos relaciones distintas y genere errores.

El video explica cómo implementar las relaciones bidireccionales:

1. `**@OneToOne**` **Bidireccional**:
    
    - **Ejemplo**: `Usuario` y `UsuarioDetalle`. `Usuario` es el lado propietario con `@OneToOne` y `@JoinColumn`. `UsuarioDetalle` es el lado inverso, con `@OneToOne(mappedBy = "detalles")`, donde "detalles" es el nombre del atributo en la clase `Usuario` que hace referencia a `UsuarioDetalle`.
    

1. `**@OneToMany**` **/** `**@ManyToOne**` **Bidireccional**:
    
    - **Ejemplo**: `Empleado` y `Departamento`. `Empleado` es el lado propietario con `@ManyToOne` (y `@JoinColumn` implícito o explícito). `Departamento` es el lado inverso con `@OneToMany(mappedBy = "departamento")`, donde "departamento" es el atributo en `Empleado` que referencia a `Departamento`. El lado `ManyToOne` siempre es el propietario de la clave foránea en la base de datos.
    

1. `**@ManyToMany**` **Bidireccional**:
    
    - **Ejemplo**: `Estudiante` y `Curso`. `Estudiante` es el lado propietario, definiendo `@ManyToMany` junto con `@JoinTable` para configurar la tabla intermedia (ej. `estudiantes_cursos`). `Curso` es el lado inverso, con `@ManyToMany(mappedBy = "cursos")`, donde "cursos" es el nombre del atributo en `Estudiante` que referencia a `Curso`. Es crucial definir `mappedBy` para evitar que JPA cree dos tablas intermedias.
    

Un aspecto vital es **mantener sincronizados ambos lados de la relación**. Si se agrega una entidad de un lado, se debe actualizar el otro lado también. Para esto, se recomienda implementar **métodos** _**helper**_ (ej. `addEmpleado()` en `Departamento`) que se encarguen de establecer la relación en ambas direcciones, haciendo el código más claro, seguro y menos propenso a errores.

Se analizan **errores comunes**:

- Olvidar `mappedBy`, lo que crea dos relaciones separadas y duplica columnas o tablas.

- No sincronizar ambos lados, llevando a modelos inconsistentes.

- **Ciclos de referencia en JSON**: Al serializar entidades bidireccionales, pueden ocurrir ciclos infinitos. Se sugieren anotaciones como `@JsonManagedReference` y `@JsonBackReference`.

- Mal uso de operaciones en cascada (`CascadeType`), que se verán en otro video.

Finalmente, se discute cuándo **conviene o no** usar relaciones bidireccionales. Son útiles cuando las entidades se consultan o modifican juntas con frecuencia, o cuando una interfaz necesita acceder a ambos lados. Sin embargo, si solo una entidad necesita conocer a la otra, es mejor mantenerla unidireccional para evitar complejidad extra. La bidireccionalidad añade flexibilidad, pero también mayor complejidad y mantenimiento.

---

### Ejemplo JPA @OneToOne Unidireccional y Bidireccional

Este video ofrece un **ejemplo práctico en código** de las relaciones One-to-One, comparando la implementación unidireccional y bidireccional en JPA.

**1. Relación** `**@OneToOne**` **Unidireccional:**

- **Modelo**: Se utilizan dos entidades, `Persona` y `Domicilio`. La `Persona` tiene una referencia a un `Domicilio` (`@OneToOne` en `Persona`), pero `Domicilio` no tiene ninguna referencia de vuelta a `Persona`.

- **Implementación**:
    
    - La entidad `Domicilio` es simple, con `@Entity`, `@Id` y `@GeneratedValue`.
    
    - La entidad `Persona` también tiene sus anotaciones básicas y un atributo `domicilio` anotado con `@OneToOne`. JPA, por defecto, agregará una columna `domicilio_id` como clave foránea en la tabla `persona`, apuntando al ID del domicilio asociado.
    

- **Funcionamiento**: Se demuestra cómo crear y persistir objetos `Domicilio` y `Persona`, asignando un domicilio a una persona. Se busca una `Persona` por ID, y gracias al mapeo unidireccional, se pueden acceder a los datos del domicilio desde el objeto `Persona`. Se confirma que a nivel de base de datos, la clave foránea reside en la tabla `persona`. La limitación es que desde un objeto `Domicilio` no se puede saber a qué `Persona` pertenece.

**2. Relación** `**@OneToOne**` **Bidireccional:**

- **Modelo**: Se modifica el modelo para que la relación entre `Persona` y `Domicilio` sea bidireccional, permitiendo la navegación en ambos sentidos.

- **Implementación**:
    
    - En la entidad `Domicilio`, se agrega un nuevo campo `persona` y se anota con `@OneToOne(mappedBy = "domicilio")`. `mappedBy = "domicilio"` indica que la relación ya está gestionada por el atributo `domicilio` en la clase `Persona`, y `Domicilio` es el lado inverso. **Es crucial no tener dos claves foráneas para la misma relación; el** `**mappedBy**` **lo evita.**
    
    - La entidad `Persona` sigue siendo el lado propietario, por lo que su anotación `@OneToOne` no lleva `mappedBy`. Sin embargo, se agrega un **método** _**helper**_ (`setDomicilio`) en `Persona`. Este método no solo asigna el domicilio a la persona, sino que también se asegura de establecer la referencia de la persona en el objeto `Domicilio` (`domicilio.setPersona(this)`), manteniendo la **sincronización** de ambos lados de la relación en memoria.
    

- **Funcionamiento**: Ahora, al buscar un `Domicilio`, se puede acceder directamente a la `Persona` asociada a través de `domicilio.getPersona()`, algo imposible en el modelo unidireccional. El video subraya que a nivel de base de datos, la estructura sigue siendo la misma (una sola clave foránea en la tabla `persona`); el cambio es puramente en el modelo de objetos y la capacidad de navegación.

El video concluye que la bidireccionalidad ofrece el doble de navegación, pero conlleva la responsabilidad de mantener sincronizados ambos lados con métodos _helper_ para evitar inconsistencias. La elección entre unidireccional y bidireccional depende de las necesidades de navegación del diseño de la aplicación.

---

### Ejemplo JPA @ManyToOne y @OneToMany

Este video proporciona un **ejemplo en código** de las relaciones Many-to-One y One-to-Many en JPA, tanto en su forma unidireccional como bidireccional.

**1. Relación** `**@OneToMany**` **Unidireccional:**

- **Modelo**: Una `Persona` puede tener una lista de muchos `Domicilios`. La `Persona` conoce a sus `Domicilios`, pero el `Domicilio` no conoce a la `Persona`.

- **Implementación**:
    
    - En la entidad `Persona`, se usa `@OneToMany` para mapear una lista de `Domicilios`.
    
    - Se añaden atributos como `cascade = CascadeType.ALL` (o `PERSIST`, `MERGE`) para propagar operaciones a los domicilios relacionados.
    
    - `fetch = FetchType.LAZY` se usa para cargar los domicilios solo cuando sean necesarios, mejorando la eficiencia.
    
    - `**@JoinColumn(name = "persona_id")**` es crucial aquí. En una relación `@OneToMany`, el lado "many" (el `Domicilio`) es siempre el dueño de la relación en la base de datos. Por lo tanto, esta anotación indica a JPA que cree la clave foránea `persona_id` en la tabla `domicilio`, apuntando a la `Persona` dueña.
    
    - La entidad `Domicilio` es simple, sin ninguna referencia a `Persona`.
    

- **Funcionamiento**: Se demuestra cómo crear domicilios, una persona, vincular los domicilios a la persona y persistirla. Se muestra cómo buscar la persona y acceder a su lista de domicilios. También se ejemplifica cómo editar y eliminar un domicilio de la lista de la persona, y cómo estas operaciones, gracias al `cascade`, se reflejan en la base de datos.

**2. Relación** `**@ManyToOne**` **/** `**@OneToMany**` **Bidireccional:**

- **Modelo**: Se transforma la relación anterior para que sea bidireccional, permitiendo que `Domicilio` también conozca a la `Persona` a la que pertenece.

- **Implementación**:
    
    - En la entidad `Persona`, la anotación `@OneToMany` ahora incluye `mappedBy = "persona"`. Esto indica que la relación en la base de datos es gestionada por el atributo `persona` en la entidad `Domicilio`, haciendo de `Persona` el lado inverso para la colección de domicilios. La anotación `@JoinColumn` se retira de `Persona` porque ya no es el lado propietario en términos de la clave foránea.
    
    - En la entidad `Domicilio`, se agrega un atributo `persona` anotado con `**@ManyToOne**` y `**@JoinColumn(name = "persona_id")**`. Esto convierte a `Domicilio` en el lado propietario de la clave foránea `persona_id`, que se crea en su tabla.
    
    - Se introduce un **método** _**helper**_ (`addDomicilio`) en la clase `Persona`. Este método no solo añade el domicilio a la lista de la persona, sino que también se asegura de establecer la `Persona` en el objeto `Domicilio` (`domicilio.setPersona(this)`), manteniendo la **sincronización** bidireccional en memoria.
    

- **Funcionamiento**: Se demuestra cómo, con esta configuración bidireccional, ahora se puede navegar de una `Persona` a sus `Domicilios` y, a la inversa, desde un `Domicilio` se puede acceder a la `Persona` asociada. A nivel de base de datos, la clave foránea sigue estando en la tabla `domicilio`, como en el caso unidireccional; el cambio principal es en la capacidad de navegación en el modelo de objetos.

El video enfatiza que la bidireccionalidad ofrece mayor flexibilidad en la navegación, pero requiere la gestión manual de la sincronización en memoria mediante métodos _helper_ para evitar inconsistencias. La elección entre ambos tipos depende de las necesidades de la aplicación.

---

### Ejemplo JPA @ManyToMany Unidireccional y Bidirecional

Este video proporciona un **ejemplo en código** de las relaciones Many-to-Many en JPA, cubriendo tanto la implementación unidireccional como la bidireccional.

**1. Relación** `**@ManyToMany**` **Unidireccional:**

- **Modelo**: Se modela una relación entre `Persona` y `Curso`, donde una persona puede estar inscrita en varios cursos y un curso puede tener muchas personas inscritas. En esta versión unidireccional, solo se puede navegar de `Persona` a `Curso`; `Curso` no tiene conocimiento de las `Personas` inscritas.

- **Implementación**:
    
    - La entidad `Curso` es simple, con `@Entity`, `@Id`, `@GeneratedValue` y un atributo `nombre`. **No tiene ninguna referencia a** `**Persona**`.
    
    - En la entidad `Persona`, se utiliza `@ManyToMany` para mapear una lista de `Cursos`.
    
    - La anotación `**@JoinTable**` es fundamental para las relaciones Many-to-Many. Define una **tabla intermedia** (ej. `persona_curso`) con dos columnas: `joinColumns` (clave foránea de la entidad propietaria, `persona_id`) y `inverseJoinColumns` (clave foránea de la entidad inversa, `curso_id`). Esta tabla intermedia es la que gestiona la relación en la base de datos.
    

- **Funcionamiento**: Se crea y persiste una `Persona` con varios `Cursos` asociados. Se demuestra que al buscar la `Persona`, se puede acceder a la lista de sus `Cursos`. Sin embargo, se confirma la limitación de la unidireccionalidad: desde un objeto `Curso`, no hay forma de saber qué `Personas` están inscritas.

**2. Relación** `**@ManyToMany**` **Bidireccional:**

- **Modelo**: Se extiende el modelo para que la relación sea bidireccional, permitiendo navegar desde `Persona` a `Curso` y desde `Curso` a `Persona`.

- **Implementación**:
    
    - En la entidad `Curso`, se agrega un atributo `personasInscriptas` (una lista de `Persona`) y se anota con `**@ManyToMany(mappedBy = "cursos")**`. `mappedBy = "cursos"` indica que la relación es gestionada por el atributo `cursos` en la clase `Persona`, haciendo de `Curso` el lado inverso. **Es vital usar** `**mappedBy**` **para evitar la creación de una segunda tabla intermedia por JPA**.
    
    - La entidad `Persona` sigue siendo el lado propietario y mantiene la configuración de `@ManyToMany` y `@JoinTable`.
    
    - Se introduce un **método** _**helper**_ (`agregarCurso`) en la clase `Persona`. Este método añade el curso a la lista de la persona y, crucialmente, también añade la persona a la lista de inscritos del curso (`curso.addInscripto(this)`), garantizando la **sincronización** bidireccional en memoria.
    

- **Funcionamiento**: Se demuestra la ventaja de la bidireccionalidad: no solo se puede obtener los cursos de una persona, sino que también se puede obtener un `Curso` y ver la lista de `Personas` inscritas en él. A nivel de base de datos, la tabla intermedia sigue siendo la misma, sin duplicaciones.

El video concluye que la relación Many-to-Many bidireccional, aunque requiere más trabajo de sincronización con métodos _helper_, ofrece una flexibilidad mucho mayor y es el modelo más recomendado cuando ambas entidades necesitan conocerse mutuamente. `mappedBy` es clave para evitar la duplicación de tablas intermedias.

---

### CascadeType y orphanRemoval

Este video explora dos conceptos avanzados en JPA: `**CascadeType**` y `**orphanRemoval**`, que simplifican la persistencia y gestión de entidades relacionadas.

**1.** `**CascadeType**` **(Operaciones en Cascada):**

- **Concepto**: `CascadeType` es un mecanismo que permite que las operaciones realizadas sobre una entidad principal se **propaguen automáticamente** a sus entidades relacionadas. Esto elimina la necesidad de persistir, actualizar o eliminar manualmente cada entidad asociada, reduciendo el código repetitivo y propenso a errores.

- **Tipos de** `**CascadeType**`:
    
    - `PERSIST`: Propaga la operación de persistencia. Si se persiste la entidad principal, las relacionadas también se persistirán.
    
    - `MERGE`: Propaga las actualizaciones. Si se actualiza la entidad principal, los cambios en las relacionadas también se aplicarán.
    
    - `REMOVE`: Propaga la eliminación. Si se elimina la entidad principal, las relacionadas también se borrarán.
    
    - `REFRESH`: Refresca el estado de la entidad desde la base de datos, propagándose a las relacionadas.
    
    - `DETACH`: Desasocia la entidad del contexto de persistencia, propagándose a las relacionadas.
    
    - `ALL`: Combina todos los tipos anteriores. Se recomienda usar `ALL` con precaución y, en su lugar, elegir los tipos específicos necesarios para cada relación para evitar comportamientos inesperados.
    

- **Uso Práctico**: Se demuestra cómo, al aplicar `CascadeType.PERSIST` en una relación `@OneToOne` (ej. `Persona` y `Domicilio`), solo se necesita persistir la `Persona` para que su `Domicilio` asociado también se guarde automáticamente. Lo mismo se aplica a relaciones `@ManyToMany` (ej. `Persona` y `Curso`), donde al persistir la `Persona`, los `Cursos` asociados también se persistirán.

- **Recomendación**: Es crucial aplicar el `CascadeType` en el **lado dueño de la relación** (el que tiene la clave foránea o la tabla intermedia) y no en el lado inverso (`mappedBy`).

**2.** `**orphanRemoval**` **(Eliminación de Huérfanos):**

- **Concepto**: `orphanRemoval = true` es una propiedad que, cuando se aplica a una relación (`@OneToOne` o `@OneToMany`), elimina automáticamente de la base de datos a una entidad dependiente si pierde su relación con la entidad principal.

- **Ejemplo**: Si una `Persona` tiene un `Domicilio` y se le quita ese domicilio (`persona.setDomicilio(null)`), y `orphanRemoval` está activado, el `Domicilio` se borrará automáticamente de la base de datos cuando se persista la `Persona` modificada.

- **Cuándo usarlo**: Solo es adecuado cuando la entidad dependiente **no tiene sentido existir por sí sola** sin su entidad principal (es decir, es un "huérfano"). Se debe usar con mucho cuidado debido a su naturaleza destructiva.

**Consejos importantes**:

- Tener precaución con `CascadeType.REMOVE`, ya que puede borrar más de lo deseado en cascada.

- Usar `orphanRemoval` solo cuando la entidad dependiente no pueda existir sola.

- Ser específico con los tipos de `CascadeType` en lugar de usar `ALL`.

El video cierra con **ejemplos en código** que demuestran la funcionalidad de `CascadeType.PERSIST` en relaciones `@OneToOne` y `@ManyToMany`, y el comportamiento de `orphanRemoval` al eliminar un domicilio asociado a una persona. Estos conceptos son mejoras significativas para escribir código JPA más profesional, limpio y mantenible.

---

### FetchType LAZY vs EAGER

Este video explica el concepto de `**FetchType**` en JPA, que define cómo y cuándo se cargan las relaciones de una entidad desde la base de datos. Es crucial para el rendimiento, ya que impacta directamente en la cantidad de consultas SQL y el momento en que se realizan. Existen dos estrategias principales:

1. `**FetchType.EAGER**` **(Carga Ansiosa o Inmediata):**
    
    - **Concepto**: La relación se carga **inmediatamente** junto con la entidad principal en una única consulta SQL (generalmente mediante un `JOIN`).
    
    - **Ventajas**: Es simple de usar, ya que todos los datos relacionados están disponibles de inmediato, evitando sorpresas al intentar acceder a ellos.
    
    - **Riesgos**: Puede ser **ineficiente** al traer datos que no se necesitan, haciendo las consultas más pesadas y afectando el rendimiento, especialmente en relaciones con muchas entidades.
    
    - **Comportamiento por defecto**: Es el `FetchType` por defecto para las relaciones `@OneToOne` y `@ManyToOne`.
    
    - **Ejemplo en código**: Se muestra cómo al configurar `@OneToOne(fetch = FetchType.EAGER)` entre `Persona` y `Domicilio`, al buscar una `Persona`, se ejecuta una sola consulta `SELECT` que incluye los datos del domicilio.
    

1. `**FetchType.LAZY**` **(Carga Perezosa o Bajo Demanda):**
    
    - **Concepto**: La relación se carga **solo cuando se accede a ella** por primera vez. Inicialmente, la entidad principal se carga sin sus relaciones `LAZY`. Cuando se invoca un método `get` para acceder a la relación (ej. `persona.getCursos()`), JPA dispara una nueva consulta a la base de datos para cargar esos datos.
    
    - **Ventajas**: Es mucho más **eficiente** al evitar traer datos innecesarios, lo que reduce el tráfico de red y el consumo de recursos de la base de datos.
    
    - **Riesgos**: Requiere más cuidado. Si se intenta acceder a una relación `LAZY` después de que el `Entity Manager` ha sido cerrado, se producirá una `**LazyInitializationException**`.
    
    - **Comportamiento por defecto**: Es el `FetchType` por defecto para las relaciones `@OneToMany` y `@ManyToMany`.
    
    - **Ejemplo en código**: Al configurar `@OneToOne(fetch = FetchType.LAZY)`, al buscar una `Persona`, la primera consulta solo trae los datos de la persona. Solo cuando se intenta acceder al domicilio (ej. en el `toString()` de `Persona`), se dispara una segunda consulta `SELECT` para obtener los datos del domicilio.
    

El video enfatiza la **diferencia en relaciones de colección (**`**@OneToMany**`**,** `**@ManyToMany**`**)**:

- En estas relaciones, `LAZY` es el `FetchType` por defecto y el recomendado.

- Forzar `EAGER` en colecciones grandes puede llevar al **problema N+1**: una consulta para la entidad principal y luego N consultas adicionales (una por cada elemento de la colección) para cargar sus relaciones, lo que es un desastre para el rendimiento. Se muestra en código cómo un `SELECT` de todas las personas con `FetchType.EAGER` en su relación `@ManyToMany` con `Cursos` genera múltiples consultas adicionales por cada persona.

**Consejos clave**:

- Usar `LAZY` por defecto en colecciones.

- Usar `EAGER` solo en relaciones pequeñas (`@OneToOne`, `@ManyToOne`) si se tiene la certeza de que siempre se necesitarán esos datos.

- Si se necesita una colección `LAZY` cargada en un caso puntual, usar `**join fetch**` o `EntityGraph` en una consulta JPQL específica, en lugar de cambiar la configuración global del `FetchType`.

- **Siempre revisar el SQL generado por JPA** para entender cuántas consultas se están realizando.

En resumen, `FetchType` es una herramienta poderosa para optimizar las consultas a la base de datos. `EAGER` es conveniente pero costoso, mientras que `LAZY` es más eficiente pero requiere un manejo cuidadoso del contexto de persistencia. La elección correcta depende de las necesidades específicas de la aplicación y el impacto en el rendimiento.

---

### JPA - Consultas avanzadas con JPQL

Este video se dedica a **JPQL (Jakarta Persistence Query Language)**, el lenguaje de consultas de JPA que permite realizar búsquedas avanzadas trabajando **directamente con objetos y atributos** de las entidades, a diferencia de SQL que opera sobre tablas y columnas. JPQL es más natural porque se integra con el modelo de objetos Java.

Las **características clave de JPQL** incluyen:

- **Sintaxis similar a SQL**: Para quienes ya conocen SQL, la curva de aprendizaje es corta.

- **Uso de alias**: Se usa un alias para la entidad (ej. `P` para `Persona`) y los parámetros se escriben con dos puntos (ej. `:nombre`), lo que previene la concatenación de strings y protege contra SQL injection.

- **Operaciones básicas**: Permite filtrar con `WHERE`, ordenar con `ORDER BY` y buscar con `LIKE`, de manera similar a SQL, pero aplicando estas operaciones a atributos de entidades. Ejemplo: `SELECT P FROM Persona P WHERE P.edad > 25 ORDER BY P.nombre ASC`.

- `**JOIN**` **natural en relaciones**: Una de las mayores ventajas de JPQL es la forma simplificada de realizar `JOIN`s. Como las relaciones ya están definidas con anotaciones (ej. `@OneToMany`, `@ManyToOne`), JPQL aprovecha estas relaciones en lugar de requerir especificaciones manuales de claves foráneas o tablas intermedias. Ejemplo: `SELECT P FROM Persona P JOIN P.cursos C WHERE C.nombre = :nombreCurso`.

- **Funciones de agregación**: Soporta funciones clásicas como `COUNT`, `AVG`, `SUM`, `MAX` y `MIN`, útiles para estadísticas y reportes. Ejemplo: `SELECT COUNT(P) FROM Persona P` o `SELECT AVG(P.edad) FROM Persona P`.

- **Subconsultas**: Permite realizar subconsultas para casos más complejos, brindando la misma potencia que SQL pero sobre entidades.

`**Named Queries**` **(Consultas Nombradas):**

- Para consultas que se usan repetidamente, se pueden definir como `Named Queries` directamente en la entidad usando la anotación `@NamedQuery`.

- Esto centraliza y reutiliza las consultas, y además se validan en tiempo de compilación.

- **Uso**: Se llama a `entityManager.createNamedQuery("nombreDeLaQuery")` y se establecen los parámetros.

El video presenta un **ejemplo práctico en código** utilizando las entidades `Persona`, `Curso` y `Domicilio` para demostrar:

1. **Consulta con** `**ORDER BY**`: Traer todas las personas ordenadas por nombre.

1. **Consulta con** `**JOIN**` **y** `**WHERE**`: Filtrar personas por ciudad utilizando un `JOIN` con la relación `Domicilio`.

1. **Consulta con función de agregación** `**SIZE()**`: Obtener cursos con más de un número `N` de inscritos (ej. `SELECT C FROM Curso C WHERE SIZE(C.personasInscriptas) > :minimo`).

1. **Uso de** `**Named Query**`: Ejecutar una consulta predefinida para buscar personas por ciudad.

**Recomendaciones**:

- Siempre usar **parámetros** en lugar de concatenar strings en las consultas.

- Usar `join fetch` para cargar relaciones `LAZY` y evitar `LazyInitializationException`.

- Definir `Named Queries` para consultas recurrentes.

JPQL es el paso final para conectar el modelo de objetos con la base de datos, proporcionando una flexibilidad enorme para trabajar con datos en aplicaciones reales y construir sistemas robustos y mantenibles.

---

## Resumen General de la Lista de Reproducción "Curso de JPA con Spring Boot"

Esta lista de reproducción ofrece un **curso completo y práctico de JPA (Jakarta Persistence API)**, guiando al desarrollador desde los conceptos más básicos hasta las implementaciones avanzadas de relaciones y consultas. El enfoque principal es entender cómo JPA simplifica la interacción con bases de datos relacionales en aplicaciones Java, eliminando la necesidad de escribir SQL directamente.

Los videos progresan lógicamente, cubriendo los siguientes **pilares fundamentales**:

1. **Introducción a JPA**: Se define qué es JPA, sus beneficios clave (mapeo ORM, gestión del ciclo de vida, abstracción de DB) y sus componentes principales (Entidades, Entity Manager, JPQL).

1. **Configuración del Entorno**: Se enseña a usar H2 Database como una base de datos ligera para desarrollo y se detalla cómo configurar el crucial archivo `persistence.xml` para conectar JPA con la base de datos y definir las propiedades de persistencia.

1. **Manejo de Entidades**: Se explica paso a paso cómo crear entidades Java, usar anotaciones básicas (`@Entity`, `@Id`, `@GeneratedValue`, `@Column`, `@Table`, `@Transient`, `@Enumerated`) para mapearlas a tablas y columnas, y se profundiza en el **ciclo de vida de una entidad** (estados Transient, Persistent, Detached, Removed) y las operaciones (`persist`, `find`, `merge`, `remove`) que provocan las transiciones.

1. **Gestión de Relaciones**: Se abordan exhaustivamente las **relaciones entre entidades** en JPA:
    
    - **Unidireccionales** (`@OneToOne`, `@ManyToOne`, `@OneToMany`): Cuándo usarlas, cómo implementarlas con `@JoinColumn` y sus implicaciones en la base de datos.
    
    - **Bidireccionales** (`@OneToOne`, `@ManyToOne`/`@OneToMany`, `@ManyToMany`): Cómo establecerlas con `mappedBy`, la importancia del lado propietario e inverso, y la necesidad de **métodos** _**helper**_ para mantener la sincronización en memoria y evitar inconsistencias. Se incluyen ejemplos detallados de cada tipo de relación en código.
    

1. **Optimización y Control Avanzado**: Se exploran conceptos avanzados como `**CascadeType**` (para propagar operaciones entre entidades relacionadas, simplificando el código) y `**orphanRemoval**` (para eliminar entidades "huérfanas" automáticamente). También se analiza `**FetchType**` **(**`**LAZY**` **vs.** `**EAGER**`**)**, explicando cómo controlar cuándo se cargan las relaciones de la base de datos y cómo evitar el costoso problema N+1.

1. **Consultas Avanzadas con JPQL**: Finalmente, se introduce **JPQL (Jakarta Persistence Query Language)**, un potente lenguaje de consultas orientado a objetos que permite realizar filtros, ordenamientos, `JOIN`s, funciones de agregación y subconsultas directamente sobre las entidades Java, aprovechando las relaciones ya definidas, sin escribir SQL nativo. Se cubren también las `Named Queries` para reutilizar consultas.