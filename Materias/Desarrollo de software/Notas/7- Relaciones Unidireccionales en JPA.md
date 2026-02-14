---
Parent item:
  - "[[Materias/Desarrollo de software/Notas/Resumen Videos\\|Resumen Videos]]"
---
![[Assets/image1 15.png|image1 15.png]]

Antes de entrar en lo específico de las relaciones unidireccionales, vamos a entender qué son las relaciones en JPA en general.

En toda aplicación que modela datos reales, las entidades no viven aisladas.

Un cliente tiene un pedido, un pedido tiene un producto y un producto pertenece a una categoría.

JPA nos da una forma declarativa y elegante de expresar esas relaciones usando anotaciones.

![[Assets/image2 15.png|image2 15.png]]

Una relación unidireccional significa que solo una entidad conoce a la otra. Ejemplo: A → B (A tiene referencia a B, pero B no sabe nada de A).

**Ventajas:**

![[Assets/image3 21.png|image3 21.png]]

Menos código

![[Assets/image4 21.png|image4 21.png]]

Menos acoplamiento

![[Assets/image3 21.png|image3 21.png]]

Más fácil de mantener

![[Assets/image5 17.png|image5 17.png]]

![[Assets/image3 21.png|image3 21.png]]

![[Assets/image6 19.png|image6 19.png]]

1. OneToOne

![[Assets/image7 18.png|image7 18.png]]

Ejemplo: Usuario → DetalleUsuario

![[Assets/image4 21.png|image4 21.png]]

Solo Usuario tiene referencia a DetalleUsuario

![[Assets/image8 20.png|image8 20.png]]

Se usa @JoinColumn con unique = true

![[Assets/image4 21.png|image4 21.png]]

La clave foránea se guarda en la tabla de Usuario

![[Assets/image10 14.png|image10 14.png]]

![[Assets/image11 14.png|image11 14.png]]

![[Assets/image12 14.png|image12 14.png]]

![[Assets/image13 14.png|image13 14.png]]

![[Assets/image14 17.png|image14 17.png]]

![[Assets/image15 13.png|image15 13.png]]

![[Assets/image16 14.png|image16 14.png]]

![[Assets/image17 9.png|image17 9.png]]

![[Assets/image18 9.png|image18 9.png]]

![[Assets/image19 18.png|image19 18.png]]

![[Assets/image20 16.png|image20 16.png]]

![[Assets/image21 21.png|image21 21.png]]

2. ManyToOne

![[Assets/image4 21.png|image4 21.png]]

Ejemplo: Empleado → Departamento

![[Assets/image8 20.png|image8 20.png]]

Muchos empleados referencian a un mismo departamento

![[Assets/image4 21.png|image4 21.png]]

Solo Empleado tiene la referencia

Departamento no conoce a sus empleados

![[Assets/image7 18.png|image7 18.png]]

Se genera departamento_id en la tabla de empleados

![[Assets/image9 15.png|image9 15.png]]

![[Assets/image25 7.png|image25 7.png]]

3. OneToMany

![[Assets/image3 21.png|image3 21.png]]

Ejemplo: Factura → ItemFactura

Factura tiene una lista de ítems

![[Assets/image4 21.png|image4 21.png]]

Los ítems no conocen a la factura

![[Assets/image8 20.png|image8 20.png]]

Se usa @JoinColumn para evitar tabla intermedia

![[Assets/image22 10.png|image22 10.png]]

La clave foránea factura_id se guarda en la tabla de ítems

![[Assets/image23 7.png|image23 7.png]]

4. ManyToMany (no habitual)

![[Assets/image8 20.png|image8 20.png]]

Se puede hacer unidireccional, pero lo común es bidireccional

![[Assets/image22 10.png|image22 10.png]]

Se verá en un video aparte

![[Assets/image24 14.png|image24 14.png]]

✅ Buenas prácticas

![[Assets/image3 21.png|image3 21.png]]

Usar fetch = FetchType.LAZY para evitar carga innecesaria.

![[Assets/image8 20.png|image8 20.png]]

Siempre usar @JoinColumn para controlar claves foráneas.

![[Assets/image26 8.png|image26 8.png]]

No usar mappedBy en relaciones unidireccionales (solo en bidireccionales).

![[Assets/image27 7.png|image27 7.png]]

⚠️ Problema N + 1

• Al consultar muchas entidades, se pueden generar múltiples consultas adicionales• Solución: usar o para cargar relaciones en una sola consulta.

![[Assets/image28 7.png|image28 7.png]]

🧾 Resumen

![[Assets/image22 10.png|image22 10.png]]

**OneToOne**

: una entidad referencia a otra

![[Assets/image29 7.png|image29 7.png]]

**ManyToOne**

: muchas entidades referencian a una

![[Assets/image30 7.png|image30 7.png]]

**OneToMany**

: una entidad tiene una lista de otras

![[Assets/image26 8.png|image26 8.png]]

Buenas prácticas: FetchType.LAZY , @JoinColumn , evitar mappedBy

![[Assets/image31 7.png|image31 7.png]]

Evitar N+1 con JOIN FETCH o EntityGraph

8- Relaciones Bidireccionales en JPA