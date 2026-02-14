---
notion-id: 29bac26b-dee7-81a8-85fe-f82fca7f68af
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - 29bac26b-dee7-80d2-9ccf-cc05773f4eeb
Blocking: []
Categoria: ""
---
![[image1 8.png]]

Las relaciones bidireccionales permiten que dos entidades se referencien mutuamente, es

decir, que podamos navegar desde A hacia B y desde B hacia A.

Esto es útil cuando la lógica de negocio necesita conocer ambos extremos de la relación.

![[image2 8.png]]

✅ Ventajas de las relaciones bidireccionales

![[image3 12.png]]

**Navegación más rica:**

acceso desde cualquiera de las entidades

![[image4 13.png]]

**Modelo de objetos más completo:**

refleja mejor las relaciones reales

![[image5 9.png]]

**Mejor reflejo del dominio:**

si en la vida real ambas entidades se conocen, el código

también

![[image6 11.png]]

**Serialización más completa:**

útil en APIs REST para respuestas más detalladas

![[image7 11.png]]

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

![[image10 7.png]]

![[image11 7.png]]

![[image8 13.png]]

🔗 Tipos de relaciones bidireccionales

1. OneToOne

![[image3 13.png]]

Ejemplo: Usuario ↔︎ DetalleUsuario

Usuario tiene el campo detalle → lado propietario

DetalleUsuario tiene el campo usuario con mappedBy = "detalle" → lado inverso

![[image9 8.png]]

![[image13 7.png]]

![[image14 7.png]]

![[image15 4.png]]

![[image16 4.png]]

2. OneToMany / ManyToOne

![[image5 10.png]]

Ejemplo: Departamento ↔︎ Empleado

Empleado tiene referencia a Departamento → lado propietario

Departamento tiene lista de empleados con mappedBy = "departamento" → lado inverso

![[image12 7.png]]

3. ManyToMany

![[image6 12.png]]

Ejemplo: Estudiante ↔︎ Curso

Estudiante define @ManyToMany con @JoinTable → lado propietario Curso define @ManyToMany(mappedBy = "cursos") → lado inverso

⚠️ Si se omite mappedBy , JPA crea dos tablas intermedias → error común.

![[image17 3.png]]

![[image18 3.png]]

⚠️ Errores comunes

![[image19 3.png]]

Olvidar mappedBy → relaciones duplicadas

![[image20 3.png]]

No sincronizar ambos lados → inconsistencias

![[image21 3.png]]

Ciclos de referencia en JSON → usar @JsonManagedReference y @JsonBackReference

![[image4 14.png]]

Mal uso de cascade → eliminar entidades por error

👉 Los tipos de cascade se explicarán en un video posterior.

![[image22 4.png]]

![[image23 2.png]]

📌 ¿Cuándo conviene usar relaciones bidireccionales?

![[image19 4.png]]

Cuando las entidades se consultan o modifican juntas frecuentemente

![[image20 4.png]]

Cuando la interfaz necesita acceder a ambos lados

![[image21 4.png]]

Cuando el dominio lo exige (relaciones reales en ambos sentidos)

![[image20 5.png]]

Cuando se necesita validación simétrica desde ambos extremos

❌ Evitarlas si:

![[image25 2.png]]

![[image26 3.png]]

![[image27 2.png]]

![[image28 2.png]]

![[image29 2.png]]

![[image30 2.png]]

![[image31 2.png]]

![[image32 1.png]]

![[image33 1.png]]

![[image34 1.png]]

![[image35 1.png]]

![[image36 1.png]]

![[image37 1.png]]

![[image38 1.png]]

![[image39 1.png]]

![[image40 1.png]]

![[image41 1.png]]

![[image42 1.png]]

![[image43 1.png]]

![[image44 1.png]]

![[image45 1.png]]

![[image46 1.png]]

![[image47 1.png]]

![[image48 1.png]]

![[image49 1.png]]

![[image50 1.png]]

![[image51 1.png]]

![[image52 1.png]]

![[image53 1.png]]

![[image54 1.png]]

![[image55.png]]

![[image56.png]]

![[image57.png]]

![[image58.png]]

![[image59.png]]

![[image60.png]]

![[image61.png]]

![[image62.png]]

![[image63.png]]

![[image24 2.png]]

Solo una entidad necesita conocer a la otra

![[image21 5.png]]

Agregan complejidad sin aportar valor

![[image20 6.png]]

No se requiere navegación en ambos sentidos

🧾 Conclusión

Las relaciones bidireccionales en JPA son poderosas y flexibles, pero requieren planificación y sincronización.

Usarlas solo cuando estén justificadas por el modelo de dominio o la lógica de negocio. Los **métodos helper** son clave para mantener la consistencia.

**Ejemplo JPA @OneToOne Unidireccional y Bidireccional**

![[image64.png]]

Se trabaja con una relación **OneToOne** entre dos entidades: Persona y Domicilio . Primero se implementa como **unidireccional**, luego como **bidireccional** para comparar comportamientos.

🔸 Parte 1: Relación OneToOne Unidireccional

![[image65.png]]

🧱 Entidad Domicilio

• @Entity : convierte la clase en tabla Domicilio

• @Id : define clave primaria

• @GeneratedValue(strategy = GenerationType.IDENTITY) : autoincrementa el ID• - Atributos: calle , ciudad

• - ❌ No tiene referencia a Persona → modelo unidireccional

![[image69.png]]

![[image70.png]]

![[image71.png]]

![[image72.png]]

![[image73.png]]

![[image74.png]]

![[image75.png]]

![[image76.png]]

![[image77.png]]

![[image78.png]]

![[image79.png]]

![[image80.png]]

![[image81.png]]

![[image82.png]]

![[image83.png]]

![[image84.png]]

![[image85.png]]

![[image86.png]]

![[image87.png]]

![[image66.png]]

🧱 Entidad Persona

@Entity , @Id , @GeneratedValue

![[image67.png]]

Atributo domicilio con @OneToOne

![[image68.png]]

JPA agrega automáticamente una columna domicilio_id en la tabla persona

![[image67 1.png]]

No se usa mappedBy , cascade , etc.

🧪 Ejemplo en main

1. Se crea el EntityManager con unidad de persistencia uno_a_uno_ugni 2. Se inicia una transacción

3. Se crean dos objetos Domicilio con mismos datos pero distintas instancias 4. Se persisten ambos domicilios

5. Se crean dos objetos Persona y se les asigna un Domicilio

6. Se persisten las personas

7. Se consulta Persona con ID 1 → el toString() muestra también el domicilio 8. Se hace commit y se imprime el ID del domicilio

9. Se manejan errores con try-catch y se cierra con finally

🧾 Resultado

![[image24 3.png]]

Relación unidireccional: solo Persona conoce a Domicilio

![[image19 5.png]]

En la base de datos: clave foránea domicilio_id en tabla persona

🔸 Parte 2: Relación OneToOne Bidireccional

![[image89.png]]

![[image90.png]]

![[image91.png]]

![[image92.png]]

![[image93.png]]

🧱 Entidad Domicilio

![[image88.png]]

![[image21 6.png]]

Se agrega atributo persona

![[image67 2.png]]

Se anota con @OneToOne(mappedBy = "domicilio")

![[image24 4.png]]

Esto indica que Domicilio es el lado inverso

![[image19 6.png]]

⚠️ Si se omite mappedBy , JPA crea una segunda columna → rompe el modelo

🧱 Entidad Persona

![[image97.png]]

![[image98.png]]

![[image99.png]]

![[image100.png]]

![[image101.png]]

![[image94.png]]

![[image95.png]]

Sigue con @OneToOne sin mappedBy → lado propietario

![[image96.png]]

Se agrega método helper en setDomicilio() para sincronizar ambos lados:

public void setDomicilio(Domicilio d) { this.domicilio = d; d.setPersona(this); }

🧪 Ventajas del modelo bidireccional

![[image20 7.png]]

Navegación en ambos sentidos: persona → domicilio y domicilio → persona

![[image21 7.png]]

Mejora el modelo de objetos

![[image67 3.png]]

En la base de datos: sigue existiendo una sola clave foránea en persona

⚠️ Consideraciones de diseño

![[image19 7.png]]

Bidireccionalidad implica responsabilidad de mantener sincronización esto se hace con el

método helper.

![[image68 1.png]]

Si no se necesita navegar desde ambos lados, conviene mantenerlo unidireccional.

![[image95 1.png]]

Métodos helper son clave para evitar inconsistencias en memoria.

**Ejemplo JPA @ManyToOne y @OneToMany**

🧪 Ejemplo en main

![[image105.png]]

![[image106.png]]

![[image107.png]]

![[image108.png]]

1. Se crea el EntityManagerFactory y EntityManager 2. Se inicia la transacción

3. Se crean y pers

🧱 Entidad Persona

![[image102.png]]

@Entity , @Id , @GeneratedValue

![[image21 8.png]]

Atributo nombre

![[image103.png]]

Atributo List con:

@OneToMany(cascade = {PERSIST, MERGE}, fetch = FetchType.LAZY) @JoinColumn(name = "persona_id") → define la clave foránea

📌 Aunque se mapea desde Persona , el **dueño de la relación** es Domicilio . La columna persona_id se agrega en la tabla domicilio .

🧱 Entidad Domicilio es el dueño de la relación

![[image104.png]]

@Entity , @Id , @GeneratedValue

![[image24 5.png]]

Atributos: calle , ciudad

![[image19 8.png]]

❌ No tiene referencia a Persona → modelo unidireccional

![[image109.png]]

![[image110.png]]

🔄 Relación OneToMany Bidireccional

En el modelo bidireccional, no solo Persona accede a sus Domicilios , sino que **cada** Domicilio **también conoce a su** Persona . Esto permite navegación en ambos sentidos y refleja mejor el dominio real.

🧱 Cambios en la entidad Persona

![[image111.png]]

![[image95 2.png]]

Se elimina la anotación @JoinColumn , ya que Persona

**ya no es el dueño de la relación**

.

![[image67 4.png]]

Se usa @OneToMany(mappedBy = "persona") , indicando que la relación está gestionada

desde el atributo persona en la clase Domicilio .

![[image24 6.png]]

Se agrega un

**método helper**

para mantener sincronización:

public void addDomicilio(Domicilio d) { domicilios.add(d); d.setPersona(this); }

Este método asegura que al agregar un domicilio, también se establezca la referencia inversa.

🧱 Cambios en la entidad Domicilio

![[image112.png]]

![[image113.png]]

Se agrega el atributo persona con la anotación @ManyToOne .

![[image95 3.png]]

Se usa @JoinColumn(name = "persona_id") para definir la clave foránea.

![[image20 8.png]]

Ahora Domicilio puede acceder directamente a su Persona asociada.

📌 La clave foránea sigue estando en la tabla domicilio , como en el modelo unidireccional.

➡️ El cambio es **solo en el modelo de objetos**, no en la estructura de la base de datos.

🧪 Cambios en el método main

![[image68 2.png]]

Se utiliza el método helper addDomicilio() para vincular correctamente ambos lados.

![[image21 9.png]]

Al consultar una Persona , se puede recorrer su lista de Domicilios y desde cada uno

acceder a la Persona asociada.

![[image103 1.png]]

Esto

**no era posible**

en el modelo unidireccional, donde Domicilio no conocía a su

dueño.

✅ Ventajas del modelo bidireccional

![[image115.png]]

![[image68 3.png]]

Navegación completa entre entidades

![[image95 4.png]]

Reflejo más fiel del dominio

![[image103 2.png]]

Útil para APIs, DTOs y vistas complejas

![[image21 10.png]]

Permite validaciones desde ambos lados

⚠️ Consideraciones

![[image68 4.png]]

Requiere mantener sincronización entre ambos lados

![[image19 9.png]]

Los métodos helper son clave para evitar inconsistencias

![[image68 5.png]]

Si no se necesita navegación inversa, conviene mantenerlo unidireccional para reducir

complejidad

**Ejemplo JPA @ManyToMany Unidireccional y Bidirecional**

![[image114.png]]

🧠 **Concepto**

![[image103 3.png]]

Una persona puede estar inscripta en varios cursos

![[image21 11.png]]

Un curso puede tener muchas personas inscriptas

![[image103 4.png]]

Pero

**solo se puede navegar desde**

Persona

**hacia**

Curso

Curso no conoce a sus inscriptos → modelo unidireccional

🧱 **Entidad** Curso

![[image69 1.png]]

![[image118.png]]

![[image119.png]]

![[image120.png]]

![[image121.png]]

![[image122.png]]

![[image123.png]]

![[image116.png]]

@Entity , @Id , @GeneratedValue

![[image117.png]]

Atributo nombre

![[image24 7.png]]

❌ No tiene referencia a Persona

🧱 **Entidad** Persona

@ManyToMany

@JoinTable(name = "persona_curso", joinColumns = ..., inverseJoinColumns =

...)

![[image67 5.png]]

Se crea una

**tabla intermedia**

persona_curso con dos columnas:

- 

![[image126.png]]

![[image127.png]]

![[image128.png]]

![[image129.png]]

![[image130.png]]

![[image131.png]]

![[image132.png]]

![[image133.png]]

![[image134.png]]

![[image135.png]]

![[image136.png]]

![[image137.png]]

- persona_id → clave primaria de Persona
- curso_id → clave primaria de Curso

📌 La relación se gestiona **solo desde** Persona , lo que la hace unidireccional.

🧪 **Ejemplo en** main

![[image124.png]]

Se crean dos cursos: Java y Base de Datos

![[image21 12.png]]

Se persisten ambos

![[image125.png]]

Se crea una persona (Lucía) y se le asignan los cursos

![[image113 1.png]]

Se persiste la persona y se hace commit

![[image117 1.png]]

Se imprime Lucía y sus cursos

![[image20 9.png]]

❌ No se puede acceder desde Curso a sus inscriptos

⚠️ **Limitaciones**

![[image19 10.png]]

Navegación incompleta

![[image24 8.png]]

No se puede consultar desde Curso quiénes están inscriptos

![[image21 13.png]]

En la mayoría de los casos reales, esto

**no es suficiente**

![[image141.png]]

![[image142.png]]

![[image143.png]]

![[image144.png]]

![[image145.png]]

![[image146.png]]

![[image147.png]]

![[image148.png]]

![[image149.png]]

🔄 **Parte 2: ManyToMany Bidireccional**

🧠 **Concepto**

![[image138.png]]

Permite navegar en

**ambos sentidos**

:

Persona → Curso

Curso → Persona

![[image117 2.png]]

Modelo más completo y usado en aplicaciones reales

🧱 **Entidad** Curso

![[image124 1.png]]

Se agrega atributo List<Persona>

![[image139.png]]

Se anota con @ManyToMany(mappedBy = "cursos")

mappedBy indica que Curso**no es el dueño de la relación**

![[image140.png]]

Evita que JPA cree una segunda tabla intermedia

🧱 **Entidad** Persona

![[image150.png]]

![[image24 9.png]]

Mantiene @ManyToMany con @JoinTable

![[image19 11.png]]

Se agrega

**método helper**

para mantener sincronización:

public void agregarCurso(Curso c) {

cursos.add(c);

c.getInscriptos().add(this);

}

🧪 **Ejemplo en** main

![[image21 14.png]]

Se usa el método helper para vincular Persona y Curso

![[image19 12.png]]

Se puede imprimir:

![[image21 15.png]]

Todos los cursos de una persona

![[image20 10.png]]

Todas las personas inscriptas en un curso

![[image124 2.png]]

Esto

**no era posible**

en el modelo unidireccional

✅ **Ventajas del modelo bidireccional**

![[image125 1.png]]

Navegación completa

![[image140 1.png]]

Más flexibilidad para consultas, reportes y vistas

![[image156.png]]

![[image151.png]]

Reflejo más fiel del dominio

![[image152.png]]

Ideal cuando ambas entidades necesitan conocerse

⚠️ **Consideraciones**

![[image151 1.png]]

Requiere más trabajo y sincronización manual

![[image153.png]]

Si no se necesita navegación inversa, conviene usar el modelo unidireccional

mappedBy es clave para evitar duplicación de tablas

![[image154.png]]

Los

**métodos helper**

aseguran consistencia en memoria

![[image155.png]]

Solo el

**lado propietario**

(definido con @JoinTable ) afecta la base de datos

<u>9- CascadeType y orphanRemoval</u>