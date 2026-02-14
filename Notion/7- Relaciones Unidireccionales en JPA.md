---
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - "[[Notion/Materias/Desarrollo de software/Resumen Videos|Resumen Videos]]"
Blocking: []
Categoria: ""
---
![[image1 7.png]]

Antes de entrar en lo específico de las relaciones unidireccionales, vamos a entender qué son las relaciones en JPA en general.

En toda aplicación que modela datos reales, las entidades no viven aisladas.

Un cliente tiene un pedido, un pedido tiene un producto y un producto pertenece a una categoría.

JPA nos da una forma declarativa y elegante de expresar esas relaciones usando anotaciones.

![[image2 7.png]]

Una relación unidireccional significa que solo una entidad conoce a la otra. Ejemplo: A → B (A tiene referencia a B, pero B no sabe nada de A).

**Ventajas:**

![[image3 7.png]]

Menos código

![[image4 7.png]]

Menos acoplamiento

![[image3 8.png]]

Más fácil de mantener

![[image5 8.png]]

![[image3 9.png]]

![[image6 10.png]]

1. OneToOne

![[image7 9.png]]

Ejemplo: Usuario → DetalleUsuario

![[image4 8.png]]

Solo Usuario tiene referencia a DetalleUsuario

![[image8 8.png]]

Se usa @JoinColumn con unique = true

![[image4 9.png]]

La clave foránea se guarda en la tabla de Usuario

![[image10 6.png]]

![[image11 6.png]]

![[image12 6.png]]

![[image13 6.png]]

![[image14 6.png]]

![[image15 3.png]]

![[image16 3.png]]

![[image17 2.png]]

![[image18 2.png]]

![[image19 2.png]]

![[image20 2.png]]

![[image21 2.png]]

2. ManyToOne

![[image4 10.png]]

Ejemplo: Empleado → Departamento

![[image8 9.png]]

Muchos empleados referencian a un mismo departamento

![[image4 11.png]]

Solo Empleado tiene la referencia

Departamento no conoce a sus empleados

![[image7 10.png]]

Se genera departamento_id en la tabla de empleados

![[image9 7.png]]

![[image25 1.png]]

3. OneToMany

![[image3 10.png]]

Ejemplo: Factura → ItemFactura

Factura tiene una lista de ítems

![[image4 12.png]]

Los ítems no conocen a la factura

![[image8 10.png]]

Se usa @JoinColumn para evitar tabla intermedia

![[image22 1.png]]

La clave foránea factura_id se guarda en la tabla de ítems

![[image23 1.png]]

4. ManyToMany (no habitual)

![[image8 11.png]]

Se puede hacer unidireccional, pero lo común es bidireccional

![[image22 2.png]]

Se verá en un video aparte

![[image24 1.png]]

✅ Buenas prácticas

![[image3 11.png]]

Usar fetch = FetchType.LAZY para evitar carga innecesaria.

![[image8 12.png]]

Siempre usar @JoinColumn para controlar claves foráneas.

![[image26 1.png]]

No usar mappedBy en relaciones unidireccionales (solo en bidireccionales).

![[image27 1.png]]

⚠️ Problema N + 1

• Al consultar muchas entidades, se pueden generar múltiples consultas adicionales• Solución: usar o para cargar relaciones en una sola consulta.

![[image28 1.png]]

🧾 Resumen

![[image22 3.png]]

**OneToOne**

: una entidad referencia a otra

![[image29 1.png]]

**ManyToOne**

: muchas entidades referencian a una

![[image30 1.png]]

**OneToMany**

: una entidad tiene una lista de otras

![[image26 2.png]]

Buenas prácticas: FetchType.LAZY , @JoinColumn , evitar mappedBy

![[image31 1.png]]

Evitar N+1 con JOIN FETCH o EntityGraph

<u>8- Relaciones Bidireccionales en JPA</u>