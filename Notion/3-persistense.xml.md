---
notion-id: 29bac26b-dee7-81db-acf1-dee17239c849
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - 29bac26b-dee7-80d2-9ccf-cc05773f4eeb
Blocking: []
Categoria: ""
---
![[image1 3.png]]

Este archivo es como el mapa de ruta para que JPA funcione. Indica a que BD conectarse, que clases son nuestras entidades en la BD, que proveedor de JPA vamos a usar y como manejar el esquema de la base de datos. Sin este archivo JPA no puede hacer nada.

![[image2 3.png]]

Ejemplo del archivo persistense.xml con las etiquetas de arriba:

![[image3 3.png]]

![[image4 3.png]]

Ejemplo:

![[image5 4.png]]

![[image6 6.png]]

Sirve para que JPA sepa que clases debe mapear en la BD.

![[image7 5.png]]

Este vive dentro del persistense unit y es donde JPA define a que BD se va conectar y como va

a conectarse. Aca armamos un combo completo para decirle a JPA como hacer su magia.

![[image8 4.png]]

Acá le decimos a JPA como conectarse a la BD, esto es como darle las llaves del auto a JPA

para que empiece a trabajar en la BD.

![[image9 4.png]]

JPA es solo la especificación nosotros necesitamos un proveedor, en nuestro caso es

Hibernate.

Esto nos mostrara la instrucciones SQL que se hagan.

![[image10 3.png]]

Ejemplo completo de persistense.xml:

![[image11 3.png]]

![[image12 3.png]]

![[image13 3.png]]

![[image14 3.png]]

<u>4- JPA paso a paso</u>