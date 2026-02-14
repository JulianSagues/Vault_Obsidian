---
base: "[[Notion/Materias/Desarrollo de software/Desarrollo de software.base]]"
Archivos Adjuntos: ""
Sub-item:
  - "[[Notion/Materias/Desarrollo de software/Resumen Videos|Resumen Videos]]"
  - "[[Notion/Materias/Desarrollo de software/Resumen Etiquetas|Resumen Etiquetas]]"
  - "[[Notion/Materias/Desarrollo de software/Relaciones de persistencia con JPA y las Técnicas de Herencia|Relaciones de persistencia con JPA y las Técnicas de Herencia]]"
Blocked by: []
Parent item: []
Blocking: []
Categoria: ""
---
# Relaciones de persistencia en JPA

## 🔸 Introducción

**JPA (Java Persistence API)** es la especificación de Java para el *mapeo objeto–relacional* (ORM).

Permite que las clases Java se guarden automáticamente en tablas de bases de datos relacionales.

### Componentes principales

- `**@Entity**` → indica que la clase es una entidad persistente.
- `**@Table(name = "nombre_tabla")**` → mapea la clase a una tabla específica.
- `**@Id**` → define el identificador primario.
- `**@GeneratedValue(strategy = ...)**` → controla cómo se genera el ID.
    - `IDENTITY`: lo genera la BD (auto_increment).
    - `SEQUENCE`: usa una secuencia.
    - `TABLE`: usa una tabla auxiliar.
    - `AUTO`: deja que el proveedor (Hibernate) decida.

---

## 🔸 Ciclo de vida de las entidades

| Estado | Descripción | Método de transición |
| --- | --- | --- |
| **Transient** | Objeto Java sin conexión a BD. | `new` |
| **Managed (Persisted)** | Controlado por el `EntityManager`. | `persist()` o `find()` |
| **Detached** | Ya no controlado por el `EntityManager`. | `clear()`, `close()` |
| **Removed** | Marcado para eliminación. | `remove()` |

---

## 🔸 Relaciones entre entidades

| Tipo | Anotación | Ejemplo | Descripción |
| --- | --- | --- | --- |
| **Uno a Uno** | `@OneToOne` | Persona–Pasaporte | Cada persona tiene un pasaporte. |
| **Uno a Muchos** | `@OneToMany` | Cliente–Pedidos | Un cliente puede tener varios pedidos. |
| **Muchos a Uno** | `@ManyToOne` | Pedido–Cliente | Muchos pedidos pertenecen a un cliente. |
| **Muchos a Muchos** | `@ManyToMany` | Alumno–Curso | Ambas partes tienen múltiples asociaciones. |

### Atributos de relación

- `**mappedBy**`: indica el lado inverso (no propietario).
- `**cascade**`: define qué operaciones se propagan (ALL, PERSIST, MERGE, REMOVE…).
- `**fetch**`: define cómo se cargan los datos relacionados:
    - `EAGER`: se cargan inmediatamente.
    - `LAZY`: se cargan bajo demanda.

### Ejemplo completo

```java
@Entity
public class Cliente {
    @Id @GeneratedValue
    private Long id;
    private String nombre;

    @OneToMany(mappedBy="cliente", cascade=CascadeType.ALL, fetch=FetchType.LAZY)
    private List<Pedido> pedidos;
}

@Entity
public class Pedido {
    @Id @GeneratedValue
    private Long id;

    @ManyToOne
    @JoinColumn(name="cliente_id")
    private Cliente cliente;
}
```

---

## 🔸 Configuración de cascadas

| Tipo de cascada | Propagación |
| --- | --- |
| `PERSIST` | Guardar entidad hija al persistir la principal |
| `MERGE` | Actualizar entidad hija al actualizar la principal |
| `REMOVE` | Eliminar entidad hija al eliminar la principal |
| `REFRESH` | Actualizar datos desde la BD |
| `DETACH` | Desasociar del contexto de persistencia |
| `ALL` | Aplica todas las anteriores |

---

# Herencia en JPA

La herencia permite modelar jerarquías de clases donde una superclase define atributos comunes y las subclases agregan sus propios campos.

### Estrategias

| Estrategia | Anotación | Ventajas | Desventajas |
| --- | --- | --- | --- |
| **Single Table** | `@Inheritance(strategy = InheritanceType.SINGLE_TABLE)` | Rápida, una sola tabla. | Muchos nulls, difícil de mantener. |
| **Joined** | `@Inheritance(strategy = InheritanceType.JOINED)` | Normalizada, evita nulls. | Más joins, menor rendimiento. |
| **Table per Class** | `@Inheritance(strategy = InheritanceType.TABLE_PER_CLASS)` | Tablas independientes. | Sin herencia en SQL real, consultas complejas. |

### Ejemplo

```java
@Entity
@Inheritance(strategy = InheritanceType.JOINED)
@DiscriminatorColumn(name="tipo")
public abstract class Empleado {
    @Id @GeneratedValue
    protected Long id;
    protected String nombre;
}

@Entity
@DiscriminatorValue("TC")
public class EmpleadoTiempoCompleto extends Empleado {
    private double salarioMensual;
}

@Entity
@DiscriminatorValue("TP")
public class EmpleadoPorHora extends Empleado {
    private double valorHora;
}
```
