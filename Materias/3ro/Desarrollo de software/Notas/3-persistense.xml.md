---
Parent item:
  - "[[Materias/Desarrollo de software/Resumen Videos\\|Resumen Videos]]"
---
![[Assets/image1 8.png|image1 8.png]]

Este archivo es como el mapa de ruta para que JPA funcione. Indica a que BD conectarse, que clases son nuestras entidades en la BD, que proveedor de JPA vamos a usar y como manejar el esquema de la base de datos. Sin este archivo JPA no puede hacer nada.

![[Assets/image2 8.png|image2 8.png]]

Ejemplo del archivo persistense.xml con las etiquetas de arriba:

![[Assets/image3 8.png|image3 8.png]]

![[Assets/image4 8.png|image4 8.png]]

Ejemplo:

![[Assets/image5 8.png|image5 8.png]]

![[Assets/image6 8.png|image6 8.png]]

Sirve para que JPA sepa que clases debe mapear en la BD.

![[Assets/image7 8.png|image7 8.png]]

Este vive dentro del persistense unit y es donde JPA define a que BD se va conectar y como va

a conectarse. Aca armamos un combo completo para decirle a JPA como hacer su magia.

![[Assets/image8 8.png|image8 8.png]]

Acá le decimos a JPA como conectarse a la BD, esto es como darle las llaves del auto a JPA

para que empiece a trabajar en la BD.

![[Assets/image9 7.png|image9 7.png]]

JPA es solo la especificación nosotros necesitamos un proveedor, en nuestro caso es

Hibernate.

Esto nos mostrara la instrucciones SQL que se hagan.

![[Assets/image10 7.png|image10 7.png]]

Ejemplo completo de persistense.xml:

![[Assets/image11 7.png|image11 7.png]]

![[Assets/image12 7.png|image12 7.png]]

![[Assets/image13 7.png|image13 7.png]]

![[Assets/image14 7.png|image14 7.png]]

4- JPA paso a paso