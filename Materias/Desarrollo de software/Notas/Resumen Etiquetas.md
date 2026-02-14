---
Parent item:
  - "[[Materias/Desarrollo de software/JPA\\|JPA]]"
---
### Anotaciones Fundamentales de Entidades

Son las etiquetas básicas para definir que una clase Java representa una tabla en la base de datos.

- `**@Entity**`: Marca una clase como una entidad JPA. Es el punto de partida.

```Java
@Entity
public class Persona { ... }
```

- `**@Table(name = "nombre_tabla")**`: Especifica el nombre exacto de la tabla en la base de datos. Si no se usa, JPA asume que el nombre de la tabla es el mismo que el de la clase.

```Java
@Table(name = "personas_clientes")
public class Persona { ... }
```

- `**@Id**`: Designa el atributo que funcionará como la **clave primaria** (Primary Key) de la entidad. Toda entidad debe tener una.

```Java
@Id
private Long id;
```

- `**@GeneratedValue(strategy = ...)**`: Configura la estrategia de generación automática para la clave primaria.Java
    
    - `**GenerationType.IDENTITY**`: Delega la generación del ID a la base de datos (comúnmente usado para columnas autoincrementables).
    
    - `**GenerationType.AUTO**`: JPA elige la estrategia más adecuada para la base de datos que se esté utilizando (opción por defecto).
    
    ```Java
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    ```
    

---

### Anotaciones de Mapeo de Atributos

Estas anotaciones controlan cómo los atributos de una clase se mapean a las columnas de la tabla.

- `**@Column(...)**`: Permite personalizar la columna asociada a un atributo.Java
    
    - `name`: Nombre exacto de la columna.
    
    - `nullable`: Si puede ser nulo (`true`/`false`).
    
    - `unique`: Si el valor debe ser único en la tabla (`true`/`false`).
    
    - `length`: Longitud máxima para campos de texto.
    
    ```Java
    @Column(name = "nombre_completo", nullable = false, length = 150)
    private String nombre;
    ```
    

- `**@Transient**`: Indica a JPA que **ignore** este atributo. No se creará una columna para él en la base de datos. Útil para campos calculados o temporales.
    
    ```Java
    @Transient
    private int edadCalculada;
    ```
    

- `**@Enumerated(...)**`: Especifica cómo se debe persistir un tipo `Enum`.Java
    
    - `**EnumType.STRING**`: (Recomendado) Guarda el nombre del valor del enum como texto (ej. "ACTIVO").
    
    - `**EnumType.ORDINAL**`: (Por defecto, riesgoso) Guarda la posición numérica del enum (ej. 0, 1, 2).
    
    ```Java
    @Enumerated(EnumType.STRING)
    private EstadoPedido estado;
    ```
    

---

### Anotaciones y Conceptos de Relaciones 🔗

Aquí se define cómo se conectan las entidades entre sí.

### Tipos de Relaciones

- `**@OneToOne**`: Relación de uno a uno (ej. `Usuario` tiene un `Perfil`).

- `**@ManyToOne**`: Relación de muchos a uno (ej. muchos `Empleados` pertenecen a un `Departamento`). **Este lado siempre es el dueño de la relación en la base de datos**.

- `**@OneToMany**`: Relación de uno a muchos (ej. un `Departamento` tiene muchos `Empleados`).

- `**@ManyToMany**`: Relación de muchos a muchos (ej. un `Estudiante` está en muchos `Cursos` y un `Curso` tiene muchos `Estudiantes`).

### Anotaciones Auxiliares para Relaciones

- `**@JoinColumn(name = "columna_fk")**`: Se usa en el lado **dueño** de la relación (`@OneToOne`, `@ManyToOne`) para especificar el nombre de la columna que contendrá la clave foránea (Foreign Key).
    
    ```Java
    @ManyToOne
    @JoinColumn(name = "id_departamento")
    private Departamento departamento;
    ```
    

- `**@JoinTable(...)**`: Se usa en relaciones `@ManyToMany` para configurar la tabla intermedia que conecta las dos entidades.

```Java
@ManyToMany
@JoinTable(
    name = "estudiante_curso",
    joinColumns = @JoinColumn(name = "id_estudiante"),
    inverseJoinColumns = @JoinColumn(name = "id_curso")
)
private List<Curso> cursos;
```

- `**mappedBy = "nombre_atributo"**`: La clave de las **relaciones bidireccionales**. Se coloca en el lado **inverso** (no dueño) de la relación para indicar que el mapeo ya está definido en el atributo correspondiente del lado dueño. **Evita la creación de claves foráneas o tablas intermedias duplicadas**.

```Java
// Lado inverso (Departamento)
@OneToMany(mappedBy = "departamento")
private List<Empleado> empleados;
```

### Comportamiento de las Relaciones

- `**cascade = CascadeType...**`: Propaga operaciones (guardar, actualizar, borrar) de la entidad padre a las entidades hijas.
    
    - `PERSIST`: Guarda las hijas al guardar el padre.
    
    - `MERGE`: Actualiza las hijas al actualizar el padre.
    
    - `REMOVE`: Borra las hijas al borrar el padre (¡cuidado!).
    
    - `ALL`: Aplica todas las operaciones anteriores.
    
    ```Java
    @OneToOne(cascade = CascadeType.ALL)
    private Domicilio domicilio;
    ```
    

- `**orphanRemoval = true**`: Si una entidad hija es removida de la colección de su padre, se elimina automáticamente de la base de datos. Es útil para relaciones donde la hija no puede existir sin el padre.

```Java
@OneToMany(mappedBy = "persona", orphanRemoval = true)
private List<Domicilio> domicilios;
```

- `**fetch = FetchType...**`: Define la estrategia de carga de datos para una relación.Java
    
    - `**LAZY**` (Perezosa): Los datos de la relación solo se cargan desde la base de datos cuando se accede a ellos por primera vez. **Es el valor por defecto para colecciones (**`**@OneToMany**`**,** `**@ManyToMany**`**) y el recomendado para optimizar el rendimiento.**
    
    - `**EAGER**` (Ansiosa): Los datos de la relación se cargan inmediatamente junto con la entidad principal. **Es el valor por defecto para relaciones** `**x-to-One**` **(**`**@OneToOne**`**,** `**@ManyToOne**`**)**. Puede causar problemas de rendimiento (N+1) si se abusa de él.
    
    ```Java
    @OneToMany(fetch = FetchType.LAZY)
    private List<Curso> cursos;
    ```
    

---

### Consultas con JPQL (Jakarta Persistence Query Language)

JPQL es un lenguaje similar a SQL pero que opera sobre **entidades y atributos**, no sobre tablas y columnas.

### Sintaxis Básica

- Se usan los nombres de las **clases de entidad** y sus **atributos**.

- Es obligatorio usar un **alias** (ej. `p` para `Persona`).

- Los parámetros se definen con dos puntos (`:nombreParametro`).

Fragmento de código

```Java
- Seleccionar todas las personas mayores de una edad específica, ordenadas por nombre
SELECT p FROM Persona p WHERE p.edad > :edadMinima ORDER BY p.nombre ASC
```

### JOIN en Relaciones

Los `JOIN` son muy naturales, ya que se basan en los atributos de relación definidos en las entidades.

Fragmento de código

```Java
- Seleccionar personas que viven en una ciudad específica
SELECT p FROM Persona p JOIN p.domicilio d WHERE d.ciudad = :nombreCiudad
```

### Funciones de Agregación

Soporta funciones como `COUNT`, `AVG`, `SUM`, `MAX`, `MIN` y `SIZE` (para el tamaño de colecciones).

Fragmento de código

```Java
- Contar el número de cursos en los que está inscrita una persona
SELECT SIZE(p.cursos) FROM Persona p WHERE p.id = :idPersona
-- Calcular la edad promedio de todas las personas
SELECT AVG(p.edad) FROM Persona p
```

### Consultas Nombradas (Named Queries)

Permiten definir consultas reutilizables directamente en la entidad.

- **Definición en la entidad:**
    
    ```Java
    @Entity
    @NamedQuery(name = "Persona.buscarPorCiudad", query = "SELECT p FROM Persona p JOIN p.domicilio d WHERE d.ciudad = :ciudad")
    public class Persona { ... }
    ```
    

- **Uso en el código:**
    
    ```Java
    TypedQuery<Persona> query = em.createNamedQuery("Persona.buscarPorCiudad", Persona.class);
    query.setParameter("ciudad", "Springfield");
    List<Persona> personas = query.getResultList();
    ```
    

---

### Configuración Clave en `persistence.xml` ⚙️

Propiedades importantes que se definen en el archivo `persistence.xml`.

- **Conexión a la base de datos**:
    
    - `javax.persistence.jdbc.url`: La URL de conexión (ej. `jdbc:h2:mem:testdb` o `jdbc:h2:file:./data/mydb`).
    
    - `javax.persistence.jdbc.user`: Usuario de la base de datos (ej. `sa`).
    
    - `javax.persistence.jdbc.password`: Contraseña.
    
    - `javax.persistence.jdbc.driver`: El driver JDBC (ej. `org.h2.Driver`).
    

- **Propiedades de Hibernate**:
    
    - `hibernate.dialect`: El "dialecto" SQL específico de la base de datos (ej. `org.hibernate.dialect.H2Dialect`).
    
    - `hibernate.hbm2ddl.auto`: Define cómo se gestiona el esquema de la base de datos. Valores comunes: `create-drop`, `update`, `validate`, `none`.
    
    - `hibernate.show_sql`: Muestra en consola las consultas SQL que genera JPA (`true`/`false`).
    
    - `hibernate.format_sql`: Formatea el SQL mostrado para que sea más legible (`true`/`false`).
    

---

### Ciclo de Vida de la Entidad

Describe los cuatro estados por los que puede pasar un objeto de entidad.

1. **Nuevo (Transient)**: El objeto acaba de ser creado con `new` y JPA no lo conoce.

1. **Gestionado (Persistent)**: El objeto está asociado a un contexto de persistencia. JPA rastrea sus cambios y los sincronizará con la base de datos. Se llega a este estado con `em.persist()` o `em.find()`.

1. **Desasociado (Detached)**: El objeto tiene un ID pero ya no está asociado al contexto de persistencia (ej. después de cerrar el `EntityManager`). Los cambios no se sincronizan.

1. **Eliminado (Removed)**: El objeto está marcado para ser eliminado de la base de datos. La eliminación se efectúa al hacer `commit` de la transacción. Se llega a este estado con `em.remove()`.