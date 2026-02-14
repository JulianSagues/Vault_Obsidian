---
Parent item:
  - "[[Materias/Desarrollo de software/Notas/Resumen Videos\\|Resumen Videos]]"
---
![[Assets/image1 17.png|image1 17.png]]

Este archivo es como el mapa de ruta para que JPA funcione. Indica a que BD conectarse, que clases son nuestras entidades en la BD, que proveedor de JPA vamos a usar y como manejar el esquema de la base de datos. Sin este archivo JPA no puede hacer nada.

![[Assets/image2 17.png|image2 17.png]]

Ejemplo del archivo persistense.xml con las etiquetas de arriba:

![[Assets/image3 23.png|image3 23.png]]

![[Assets/image4 23.png|image4 23.png]]

Ejemplo:

![[Assets/image5 19.png|image5 19.png]]

![[Assets/image6 21.png|image6 21.png]]

Sirve para que JPA sepa que clases debe mapear en la BD.

![[Assets/image7 20.png|image7 20.png]]

Este vive dentro del persistense unit y es donde JPA define a que BD se va conectar y como va

a conectarse. Aca armamos un combo completo para decirle a JPA como hacer su magia.

![[Assets/image8 22.png|image8 22.png]]

Acá le decimos a JPA como conectarse a la BD, esto es como darle las llaves del auto a JPA

para que empiece a trabajar en la BD.

![[Assets/image9 16.png|image9 16.png]]

JPA es solo la especificación nosotros necesitamos un proveedor, en nuestro caso es

Hibernate.

Esto nos mostrara la instrucciones SQL que se hagan.

![[Assets/image10 15.png|image10 15.png]]

Ejemplo completo de persistense.xml:

![[Assets/image11 15.png|image11 15.png]]

![[Assets/image12 15.png|image12 15.png]]

![[Assets/image13 15.png|image13 15.png]]

![[Assets/image14 18.png|image14 18.png]]

4- JPA paso a paso