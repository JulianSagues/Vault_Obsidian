---
Parent item:
  - "[[Materias/Desarrollo de software/Resumen Videos\\|Resumen Videos]]"
---
![[Assets/image1 14.png|image1 14.png]]

Las relaciones bidireccionales permiten que dos entidades se referencien mutuamente, es

decir, que podamos navegar desde A hacia B y desde B hacia A.

Esto es útil cuando la lógica de negocio necesita conocer ambos extremos de la relación.

![[Assets/image2 14.png|image2 14.png]]

✅ Ventajas de las relaciones bidireccionales

![[Assets/image3 20.png|image3 20.png]]

**Navegación más rica:**

acceso desde cualquiera de las entidades

![[Assets/image4 20.png|image4 20.png]]

**Modelo de objetos más completo:**

refleja mejor las relaciones reales

![[Assets/image5 16.png|image5 16.png]]

**Mejor reflejo del dominio:**

si en la vida real ambas entidades se conocen, el código

también

![[Assets/image6 18.png|image6 18.png]]

**Serialización más completa:**

útil en APIs REST para respuestas más detalladas

![[Assets/image7 17.png|image7 17.png]]

🧩 Conceptos clave

🔸 Lado propietario

• Mantiene la clave foránea

• Define @JoinColumn

• Afecta directamente la base de datos

🔸 Lado inverso

• No impacta la base de datos

• Sirve para navegación en el código

• Se define con mappedBy

⚠️ Si no se define correctamente, JPA puede interpretar que hay dos relaciones distintas →errores y duplicaciones.

![[Assets/image10 13.png|image10 13.png]]

![[Assets/image11 13.png|image11 13.png]]

![[Assets/image8 19.png|image8 19.png]]

🔗 Tipos de relaciones bidireccionales

1. OneToOne

![[Assets/image3 20.png|image3 20.png]]

Ejemplo: Usuario ↔︎ DetalleUsuario

Usuario tiene el campo detalle → lado propietario

DetalleUsuario tiene el campo usuario con mappedBy = "detalle" → lado inverso

![[Assets/image9 14.png|image9 14.png]]

![[Assets/image13 13.png|image13 13.png]]

![[Assets/image14 16.png|image14 16.png]]

![[Assets/image15 12.png|image15 12.png]]

![[Assets/image16 13.png|image16 13.png]]

2. OneToMany / ManyToOne

![[Assets/image5 16.png|image5 16.png]]

Ejemplo: Departamento ↔︎ Empleado

Empleado tiene referencia a Departamento → lado propietario

Departamento tiene lista de empleados con mappedBy = "departamento" → lado inverso

![[Assets/image12 13.png|image12 13.png]]

3. ManyToMany

![[Assets/image6 18.png|image6 18.png]]

Ejemplo: Estudiante ↔︎ Curso

Estudiante define @ManyToMany con @JoinTable → lado propietario Curso define @ManyToMany(mappedBy = "cursos") → lado inverso

⚠️ Si se omite mappedBy , JPA crea dos tablas intermedias → error común.

![[Assets/image17 8.png|image17 8.png]]

![[Assets/image18 8.png|image18 8.png]]

⚠️ Errores comunes

![[Assets/image19 17.png|image19 17.png]]

Olvidar mappedBy → relaciones duplicadas

![[Assets/image20 15.png|image20 15.png]]

No sincronizar ambos lados → inconsistencias

![[Assets/image21 20.png|image21 20.png]]

Ciclos de referencia en JSON → usar @JsonManagedReference y @JsonBackReference

![[Assets/image4 20.png|image4 20.png]]

Mal uso de cascade → eliminar entidades por error

👉 Los tipos de cascade se explicarán en un video posterior.

![[Assets/image22 9.png|image22 9.png]]

![[Assets/image23 6.png|image23 6.png]]

📌 ¿Cuándo conviene usar relaciones bidireccionales?

![[Assets/image19 17.png|image19 17.png]]

Cuando las entidades se consultan o modifican juntas frecuentemente

![[Assets/image20 15.png|image20 15.png]]

Cuando la interfaz necesita acceder a ambos lados

![[Assets/image21 20.png|image21 20.png]]

Cuando el dominio lo exige (relaciones reales en ambos sentidos)

![[Assets/image20 15.png|image20 15.png]]

Cuando se necesita validación simétrica desde ambos extremos

❌ Evitarlas si:

![[Assets/image25 6.png|image25 6.png]]

![[Assets/image26 7.png|image26 7.png]]

![[Assets/image27 6.png|image27 6.png]]

![[Assets/image28 6.png|image28 6.png]]

![[Assets/image29 6.png|image29 6.png]]

![[Assets/image30 6.png|image30 6.png]]

![[Assets/image31 6.png|image31 6.png]]

![[Assets/image32 5.png|image32 5.png]]

![[Assets/image33 5.png|image33 5.png]]

![[Assets/image34 5.png|image34 5.png]]

![[Assets/image35 5.png|image35 5.png]]

![[Assets/image36 5.png|image36 5.png]]

![[Assets/image37 5.png|image37 5.png]]

![[Assets/image38 5.png|image38 5.png]]

![[Assets/image39 5.png|image39 5.png]]

![[Assets/image40 5.png|image40 5.png]]

![[Assets/image41 6.png|image41 6.png]]

![[Assets/image42 5.png|image42 5.png]]

![[Assets/image43 5.png|image43 5.png]]

![[Assets/image44 5.png|image44 5.png]]

![[Assets/image45 5.png|image45 5.png]]

![[Assets/image46 5.png|image46 5.png]]

![[Assets/image47 3.png|image47 3.png]]

![[Assets/image48 3.png|image48 3.png]]

![[Assets/image49 3.png|image49 3.png]]

![[Assets/image50 3.png|image50 3.png]]

![[Assets/image51 3.png|image51 3.png]]

![[Assets/image52 3.png|image52 3.png]]

![[Assets/image53 3.png|image53 3.png]]

![[Assets/image54 3.png|image54 3.png]]

![[Assets/image55 2.png|image55 2.png]]

![[Assets/image56 2.png|image56 2.png]]

![[Assets/image57 2.png|image57 2.png]]

![[Assets/image58 2.png|image58 2.png]]

![[Assets/image59 2.png|image59 2.png]]

![[Assets/image60 2.png|image60 2.png]]

![[Assets/image61 2.png|image61 2.png]]

![[Assets/image62 2.png|image62 2.png]]

![[Assets/image63 2.png|image63 2.png]]

![[Assets/image24 13.png|image24 13.png]]

Solo una entidad necesita conocer a la otra

![[Assets/image21 20.png|image21 20.png]]

Agregan complejidad sin aportar valor

![[Assets/image20 15.png|image20 15.png]]

No se requiere navegación en ambos sentidos

🧾 Conclusión

Las relaciones bidireccionales en JPA son poderosas y flexibles, pero requieren planificación y sincronización.

Usarlas solo cuando estén justificadas por el modelo de dominio o la lógica de negocio. Los **métodos helper** son clave para mantener la consistencia.

**Ejemplo JPA @OneToOne Unidireccional y Bidireccional**

![[Assets/image64 2.png|image64 2.png]]

Se trabaja con una relación **OneToOne** entre dos entidades: Persona y Domicilio . Primero se implementa como **unidireccional**, luego como **bidireccional** para comparar comportamientos.

🔸 Parte 1: Relación OneToOne Unidireccional

![[Assets/image65 2.png|image65 2.png]]

🧱 Entidad Domicilio

• @Entity : convierte la clase en tabla Domicilio

• @Id : define clave primaria

• @GeneratedValue(strategy = GenerationType.IDENTITY) : autoincrementa el ID• - Atributos: calle , ciudad

• - ❌ No tiene referencia a Persona → modelo unidireccional

![[Assets/image69 2.png|image69 2.png]]

![[Assets/image70 2.png|image70 2.png]]

![[Assets/image71 2.png|image71 2.png]]

![[Assets/image72 2.png|image72 2.png]]

![[Assets/image73 2.png|image73 2.png]]

![[Assets/image74 2.png|image74 2.png]]

![[Assets/image75 2.png|image75 2.png]]

![[Assets/image76 2.png|image76 2.png]]

![[Assets/image77 2.png|image77 2.png]]

![[Assets/image78 2.png|image78 2.png]]

![[Assets/image79 2.png|image79 2.png]]

![[Assets/image80 2.png|image80 2.png]]

![[Assets/image81 2.png|image81 2.png]]

![[Assets/image82 2.png|image82 2.png]]

![[Assets/image83 2.png|image83 2.png]]

![[Assets/image84 2.png|image84 2.png]]

![[Assets/image85 2.png|image85 2.png]]

![[Assets/image86 2.png|image86 2.png]]

![[Assets/image87 2.png|image87 2.png]]

![[Assets/image66 2.png|image66 2.png]]

🧱 Entidad Persona

@Entity , @Id , @GeneratedValue

![[Assets/image67 6.png|image67 6.png]]

Atributo domicilio con @OneToOne

![[Assets/image68 6.png|image68 6.png]]

JPA agrega automáticamente una columna domicilio_id en la tabla persona

![[Assets/image67 6.png|image67 6.png]]

No se usa mappedBy , cascade , etc.

🧪 Ejemplo en main

1. Se crea el EntityManager con unidad de persistencia uno_a_uno_ugni 2. Se inicia una transacción

3. Se crean dos objetos Domicilio con mismos datos pero distintas instancias 4. Se persisten ambos domicilios

5. Se crean dos objetos Persona y se les asigna un Domicilio

6. Se persisten las personas

7. Se consulta Persona con ID 1 → el toString() muestra también el domicilio 8. Se hace commit y se imprime el ID del domicilio

9. Se manejan errores con try-catch y se cierra con finally

🧾 Resultado

![[Assets/image24 13.png|image24 13.png]]

Relación unidireccional: solo Persona conoce a Domicilio

![[Assets/image19 17.png|image19 17.png]]

En la base de datos: clave foránea domicilio_id en tabla persona

🔸 Parte 2: Relación OneToOne Bidireccional

![[Assets/image89 2.png|image89 2.png]]

![[Assets/image90 2.png|image90 2.png]]

![[Assets/image91 2.png|image91 2.png]]

![[Assets/image92 2.png|image92 2.png]]

![[Assets/image93 2.png|image93 2.png]]

🧱 Entidad Domicilio

![[Assets/image88 2.png|image88 2.png]]

![[Assets/image21 20.png|image21 20.png]]

Se agrega atributo persona

![[Assets/image67 6.png|image67 6.png]]

Se anota con @OneToOne(mappedBy = "domicilio")

![[Assets/image24 13.png|image24 13.png]]

Esto indica que Domicilio es el lado inverso

![[Assets/image19 17.png|image19 17.png]]

⚠️ Si se omite mappedBy , JPA crea una segunda columna → rompe el modelo

🧱 Entidad Persona

![[Assets/image97 2.png|image97 2.png]]

![[Assets/image98 2.png|image98 2.png]]

![[Assets/image99 2.png|image99 2.png]]

![[Assets/image100 2.png|image100 2.png]]

![[Assets/image101 2.png|image101 2.png]]

![[Assets/image94 2.png|image94 2.png]]

![[Assets/image95 5.png|image95 5.png]]

Sigue con @OneToOne sin mappedBy → lado propietario

![[Assets/image96 2.png|image96 2.png]]

Se agrega método helper en setDomicilio() para sincronizar ambos lados:

public void setDomicilio(Domicilio d) { this.domicilio = d; d.setPersona(this); }

🧪 Ventajas del modelo bidireccional

![[Assets/image20 15.png|image20 15.png]]

Navegación en ambos sentidos: persona → domicilio y domicilio → persona

![[Assets/image21 20.png|image21 20.png]]

Mejora el modelo de objetos

![[Assets/image67 6.png|image67 6.png]]

En la base de datos: sigue existiendo una sola clave foránea en persona

⚠️ Consideraciones de diseño

![[Assets/image19 17.png|image19 17.png]]

Bidireccionalidad implica responsabilidad de mantener sincronización esto se hace con el

método helper.

![[Assets/image68 6.png|image68 6.png]]

Si no se necesita navegar desde ambos lados, conviene mantenerlo unidireccional.

![[Assets/image95 5.png|image95 5.png]]

Métodos helper son clave para evitar inconsistencias en memoria.

**Ejemplo JPA @ManyToOne y @OneToMany**

🧪 Ejemplo en main

![[Assets/image105 2.png|image105 2.png]]

![[Assets/image106 2.png|image106 2.png]]

![[Assets/image107 2.png|image107 2.png]]

![[Assets/image108 2.png|image108 2.png]]

1. Se crea el EntityManagerFactory y EntityManager 2. Se inicia la transacción

3. Se crean y pers

🧱 Entidad Persona

![[Assets/image102 2.png|image102 2.png]]

@Entity , @Id , @GeneratedValue

![[Assets/image21 20.png|image21 20.png]]

Atributo nombre

![[Assets/image103 5.png|image103 5.png]]

Atributo List con:

@OneToMany(cascade = {PERSIST, MERGE}, fetch = FetchType.LAZY) @JoinColumn(name = "persona_id") → define la clave foránea

📌 Aunque se mapea desde Persona , el **dueño de la relación** es Domicilio . La columna persona_id se agrega en la tabla domicilio .

🧱 Entidad Domicilio es el dueño de la relación

![[Assets/image104 2.png|image104 2.png]]

@Entity , @Id , @GeneratedValue

![[Assets/image24 13.png|image24 13.png]]

Atributos: calle , ciudad

![[Assets/image19 17.png|image19 17.png]]

❌ No tiene referencia a Persona → modelo unidireccional

![[Assets/image109 2.png|image109 2.png]]

![[Assets/image110 2.png|image110 2.png]]

🔄 Relación OneToMany Bidireccional

En el modelo bidireccional, no solo Persona accede a sus Domicilios , sino que **cada** Domicilio **también conoce a su** Persona . Esto permite navegación en ambos sentidos y refleja mejor el dominio real.

🧱 Cambios en la entidad Persona

![[Assets/image111 2.png|image111 2.png]]

![[Assets/image95 5.png|image95 5.png]]

Se elimina la anotación @JoinColumn , ya que Persona

**ya no es el dueño de la relación**

.

![[Assets/image67 6.png|image67 6.png]]

Se usa @OneToMany(mappedBy = "persona") , indicando que la relación está gestionada

desde el atributo persona en la clase Domicilio .

![[Assets/image24 13.png|image24 13.png]]

Se agrega un

**método helper**

para mantener sincronización:

public void addDomicilio(Domicilio d) { domicilios.add(d); d.setPersona(this); }

Este método asegura que al agregar un domicilio, también se establezca la referencia inversa.

🧱 Cambios en la entidad Domicilio

![[Assets/image112 2.png|image112 2.png]]

![[Assets/image113 2.png|image113 2.png]]

Se agrega el atributo persona con la anotación @ManyToOne .

![[Assets/image95 5.png|image95 5.png]]

Se usa @JoinColumn(name = "persona_id") para definir la clave foránea.

![[Assets/image20 15.png|image20 15.png]]

Ahora Domicilio puede acceder directamente a su Persona asociada.

📌 La clave foránea sigue estando en la tabla domicilio , como en el modelo unidireccional.

➡️ El cambio es **solo en el modelo de objetos**, no en la estructura de la base de datos.

🧪 Cambios en el método main

![[Assets/image68 6.png|image68 6.png]]

Se utiliza el método helper addDomicilio() para vincular correctamente ambos lados.

![[Assets/image21 20.png|image21 20.png]]

Al consultar una Persona , se puede recorrer su lista de Domicilios y desde cada uno

acceder a la Persona asociada.

![[Assets/image103 5.png|image103 5.png]]

Esto

**no era posible**

en el modelo unidireccional, donde Domicilio no conocía a su

dueño.

✅ Ventajas del modelo bidireccional

![[Assets/image115 2.png|image115 2.png]]

![[Assets/image68 6.png|image68 6.png]]

Navegación completa entre entidades

![[Assets/image95 5.png|image95 5.png]]

Reflejo más fiel del dominio

![[Assets/image103 5.png|image103 5.png]]

Útil para APIs, DTOs y vistas complejas

![[Assets/image21 20.png|image21 20.png]]

Permite validaciones desde ambos lados

⚠️ Consideraciones

![[Assets/image68 6.png|image68 6.png]]

Requiere mantener sincronización entre ambos lados

![[Assets/image19 17.png|image19 17.png]]

Los métodos helper son clave para evitar inconsistencias

![[Assets/image68 6.png|image68 6.png]]

Si no se necesita navegación inversa, conviene mantenerlo unidireccional para reducir

complejidad

**Ejemplo JPA @ManyToMany Unidireccional y Bidirecional**

![[Assets/image114 2.png|image114 2.png]]

🧠 **Concepto**

![[Assets/image103 5.png|image103 5.png]]

Una persona puede estar inscripta en varios cursos

![[Assets/image21 20.png|image21 20.png]]

Un curso puede tener muchas personas inscriptas

![[Assets/image103 5.png|image103 5.png]]

Pero

**solo se puede navegar desde**

Persona

**hacia**

Curso

Curso no conoce a sus inscriptos → modelo unidireccional

🧱 **Entidad** Curso

![[Assets/image69 2.png|image69 2.png]]

![[Assets/image118 2.png|image118 2.png]]

![[Assets/image119 2.png|image119 2.png]]

![[Assets/image120 2.png|image120 2.png]]

![[Assets/image121 2.png|image121 2.png]]

![[Assets/image122 2.png|image122 2.png]]

![[Assets/image123 2.png|image123 2.png]]

![[Assets/image116 2.png|image116 2.png]]

@Entity , @Id , @GeneratedValue

![[Assets/image117 3.png|image117 3.png]]

Atributo nombre

![[Assets/image24 13.png|image24 13.png]]

❌ No tiene referencia a Persona

🧱 **Entidad** Persona

@ManyToMany

@JoinTable(name = "persona_curso", joinColumns = ..., inverseJoinColumns =

...)

![[Assets/image67 6.png|image67 6.png]]

Se crea una

**tabla intermedia**

persona_curso con dos columnas:

![[Assets/image126 2.png|image126 2.png]]

![[Assets/image127 2.png|image127 2.png]]

![[Assets/image128 2.png|image128 2.png]]

![[Assets/image129 2.png|image129 2.png]]

![[Assets/image130 2.png|image130 2.png]]

![[Assets/image131 2.png|image131 2.png]]

![[Assets/image132 2.png|image132 2.png]]

![[Assets/image133 2.png|image133 2.png]]

![[Assets/image134 2.png|image134 2.png]]

![[Assets/image135 2.png|image135 2.png]]

![[Assets/image136 2.png|image136 2.png]]

![[Assets/image137 2.png|image137 2.png]]

- persona_id → clave primaria de Persona

- curso_id → clave primaria de Curso

📌 La relación se gestiona **solo desde** Persona , lo que la hace unidireccional.

🧪 **Ejemplo en** main

![[Assets/image124 3.png|image124 3.png]]

Se crean dos cursos: Java y Base de Datos

![[Assets/image21 20.png|image21 20.png]]

Se persisten ambos

![[Assets/image125 2.png|image125 2.png]]

Se crea una persona (Lucía) y se le asignan los cursos

![[Assets/image113 2.png|image113 2.png]]

Se persiste la persona y se hace commit

![[Assets/image117 3.png|image117 3.png]]

Se imprime Lucía y sus cursos

![[Assets/image20 15.png|image20 15.png]]

❌ No se puede acceder desde Curso a sus inscriptos

⚠️ **Limitaciones**

![[Assets/image19 17.png|image19 17.png]]

Navegación incompleta

![[Assets/image24 13.png|image24 13.png]]

No se puede consultar desde Curso quiénes están inscriptos

![[Assets/image21 20.png|image21 20.png]]

En la mayoría de los casos reales, esto

**no es suficiente**

![[Assets/image141 2.png|image141 2.png]]

![[Assets/image142 2.png|image142 2.png]]

![[Assets/image143 2.png|image143 2.png]]

![[Assets/image144 2.png|image144 2.png]]

![[Assets/image145 2.png|image145 2.png]]

![[Assets/image146 2.png|image146 2.png]]

![[Assets/image147 2.png|image147 2.png]]

![[Assets/image148 2.png|image148 2.png]]

![[Assets/image149 2.png|image149 2.png]]

🔄 **Parte 2: ManyToMany Bidireccional**

🧠 **Concepto**

![[Assets/image138 2.png|image138 2.png]]

Permite navegar en

**ambos sentidos**

:

Persona → Curso

Curso → Persona

![[Assets/image117 3.png|image117 3.png]]

Modelo más completo y usado en aplicaciones reales

🧱 **Entidad** Curso

![[Assets/image124 3.png|image124 3.png]]

Se agrega atributo List<Persona>

![[Assets/image139 2.png|image139 2.png]]

Se anota con @ManyToMany(mappedBy = "cursos")

mappedBy indica que Curso**no es el dueño de la relación**

![[Assets/image140 2.png|image140 2.png]]

Evita que JPA cree una segunda tabla intermedia

🧱 **Entidad** Persona

![[Assets/image150 2.png|image150 2.png]]

![[Assets/image24 13.png|image24 13.png]]

Mantiene @ManyToMany con @JoinTable

![[Assets/image19 17.png|image19 17.png]]

Se agrega

**método helper**

para mantener sincronización:

public void agregarCurso(Curso c) {

cursos.add(c);

c.getInscriptos().add(this);

}

🧪 **Ejemplo en** main

![[Assets/image21 20.png|image21 20.png]]

Se usa el método helper para vincular Persona y Curso

![[Assets/image19 17.png|image19 17.png]]

Se puede imprimir:

![[Assets/image21 20.png|image21 20.png]]

Todos los cursos de una persona

![[Assets/image20 15.png|image20 15.png]]

Todas las personas inscriptas en un curso

![[Assets/image124 3.png|image124 3.png]]

Esto

**no era posible**

en el modelo unidireccional

✅ **Ventajas del modelo bidireccional**

![[Assets/image125 2.png|image125 2.png]]

Navegación completa

![[Assets/image140 2.png|image140 2.png]]

Más flexibilidad para consultas, reportes y vistas

![[Assets/image156 2.png|image156 2.png]]

![[Assets/image151 2.png|image151 2.png]]

Reflejo más fiel del dominio

![[Assets/image152 2.png|image152 2.png]]

Ideal cuando ambas entidades necesitan conocerse

⚠️ **Consideraciones**

![[Assets/image151 2.png|image151 2.png]]

Requiere más trabajo y sincronización manual

![[Assets/image153 2.png|image153 2.png]]

Si no se necesita navegación inversa, conviene usar el modelo unidireccional

mappedBy es clave para evitar duplicación de tablas

![[Assets/image154 2.png|image154 2.png]]

Los

**métodos helper**

aseguran consistencia en memoria

![[Assets/image155 2.png|image155 2.png]]

Solo el

**lado propietario**

(definido con @JoinTable ) afecta la base de datos

9- CascadeType y orphanRemoval