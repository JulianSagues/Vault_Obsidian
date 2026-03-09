---
Parent item:
  - "[[Materias/Desarrollo de software/Resumen Videos\\|Resumen Videos]]"
---
![[Assets/image1 6.png|image1 6.png]]

Antes de entrar en lo específico de las relaciones unidireccionales, vamos a entender qué son las relaciones en JPA en general.

En toda aplicación que modela datos reales, las entidades no viven aisladas.

Un cliente tiene un pedido, un pedido tiene un producto y un producto pertenece a una categoría.

JPA nos da una forma declarativa y elegante de expresar esas relaciones usando anotaciones.

![[Assets/image2 6.png|image2 6.png]]

Una relación unidireccional significa que solo una entidad conoce a la otra. Ejemplo: A → B (A tiene referencia a B, pero B no sabe nada de A).

**Ventajas:**

![[Assets/image3 6.png|image3 6.png]]

Menos código

![[Assets/image4 6.png|image4 6.png]]

Menos acoplamiento

![[Assets/image3 6.png|image3 6.png]]

Más fácil de mantener

![[Assets/image5 6.png|image5 6.png]]

![[Assets/image3 6.png|image3 6.png]]

![[Assets/image6 6.png|image6 6.png]]

1. OneToOne

![[Assets/image7 6.png|image7 6.png]]

Ejemplo: Usuario → DetalleUsuario

![[Assets/image4 6.png|image4 6.png]]

Solo Usuario tiene referencia a DetalleUsuario

![[Assets/image8 6.png|image8 6.png]]

Se usa @JoinColumn con unique = true

![[Assets/image4 6.png|image4 6.png]]

La clave foránea se guarda en la tabla de Usuario

![[Assets/image10 6.png|image10 6.png]]

![[Assets/image11 6.png|image11 6.png]]

![[Assets/image12 6.png|image12 6.png]]

![[Assets/image13 6.png|image13 6.png]]

![[Assets/image14 6.png|image14 6.png]]

![[Assets/image15 5.png|image15 5.png]]

![[Assets/image16 5.png|image16 5.png]]

![[Assets/image17 5.png|image17 5.png]]

![[Assets/image18 5.png|image18 5.png]]

![[Assets/image19 5.png|image19 5.png]]

![[Assets/image20 5.png|image20 5.png]]

![[Assets/image21 5.png|image21 5.png]]

2. ManyToOne

![[Assets/image4 6.png|image4 6.png]]

Ejemplo: Empleado → Departamento

![[Assets/image8 6.png|image8 6.png]]

Muchos empleados referencian a un mismo departamento

![[Assets/image4 6.png|image4 6.png]]

Solo Empleado tiene la referencia

Departamento no conoce a sus empleados

![[Assets/image7 6.png|image7 6.png]]

Se genera departamento_id en la tabla de empleados

![[Assets/image9 6.png|image9 6.png]]

![[Assets/image25 4.png|image25 4.png]]

3. OneToMany

![[Assets/image3 6.png|image3 6.png]]

Ejemplo: Factura → ItemFactura

Factura tiene una lista de ítems

![[Assets/image4 6.png|image4 6.png]]

Los ítems no conocen a la factura

![[Assets/image8 6.png|image8 6.png]]

Se usa @JoinColumn para evitar tabla intermedia

![[Assets/image22 4.png|image22 4.png]]

La clave foránea factura_id se guarda en la tabla de ítems

![[Assets/image23 4.png|image23 4.png]]

4. ManyToMany (no habitual)

![[Assets/image8 6.png|image8 6.png]]

Se puede hacer unidireccional, pero lo común es bidireccional

![[Assets/image22 4.png|image22 4.png]]

Se verá en un video aparte

![[Assets/image24 4.png|image24 4.png]]

✅ Buenas prácticas

![[Assets/image3 6.png|image3 6.png]]

Usar fetch = FetchType.LAZY para evitar carga innecesaria.

![[Assets/image8 6.png|image8 6.png]]

Siempre usar @JoinColumn para controlar claves foráneas.

![[Assets/image26 4.png|image26 4.png]]

No usar mappedBy en relaciones unidireccionales (solo en bidireccionales).

![[Assets/image27 4.png|image27 4.png]]

⚠️ Problema N + 1

• Al consultar muchas entidades, se pueden generar múltiples consultas adicionales• Solución: usar o para cargar relaciones en una sola consulta.

![[Assets/image28 4.png|image28 4.png]]

🧾 Resumen

![[Assets/image22 4.png|image22 4.png]]

**OneToOne**

: una entidad referencia a otra

![[Assets/image29 4.png|image29 4.png]]

**ManyToOne**

: muchas entidades referencian a una

![[Assets/image30 4.png|image30 4.png]]

**OneToMany**

: una entidad tiene una lista de otras

![[Assets/image26 4.png|image26 4.png]]

Buenas prácticas: FetchType.LAZY , @JoinColumn , evitar mappedBy

![[Assets/image31 4.png|image31 4.png]]

Evitar N+1 con JOIN FETCH o EntityGraph

8- Relaciones Bidireccionales en JPA