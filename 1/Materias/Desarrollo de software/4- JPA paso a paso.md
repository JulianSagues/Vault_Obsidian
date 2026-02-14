---
Parent item:
  - "[[Materias/Desarrollo de software/Resumen Videos\\|Resumen Videos]]"
---
![[Assets/image1 18.png|image1 18.png]]

Lo primero que debemos hacer es poner las dependencias en el build.gradle:

![[Assets/image2 18.png|image2 18.png]]

Luego debemos crear el archivo persistense.xml para utilizar JPA:

![[Assets/image3 24.png|image3 24.png]]

De esta manera ya tenemos preparado el entorno.

![[Assets/image4 24.png|image4 24.png]]

En JPA una entidad es una clase común de JAVA pero con algunas anotaciones que le van a indicar a JPA que tiene que tiene que mapearse en la tabla de la BD.

Cada instancia de la clase va a representar una fila de la tabla. Trabajaremos con la clase Persona.

![[Assets/image5 20.png|image5 20.png]]

Acá creamos una clase marcada con @Entity que es para decirle a JPA que debe mapearla en la BD, además luego de marcarla con @Entity estamos obligados a poner un @Id para la clave primaria, también podemos poner como se generara ese id (clave primaria de la tabla).

Con @Table le ponemos nombre a la tabla y con @Column le ponemos nombre a una columna de la tabla en la BD.

Una vez que declaramos la entidad debemos declararla en el persistense.xml, porque si no JPA la va a ignorar.

![[Assets/image6 22.png|image6 22.png]]

Así se declara la entidad en el persistense.xml

![[Assets/image7 21.png|image7 21.png]]

EntityManagerFactory-> Crea a EntityManager.

EntityManager-> Es mi puente con la BD.

Ejemplo de uso:

![[Assets/image8 23.png|image8 23.png]]

Los deben crearse y cerrarse al final.

![[Assets/image9 17.png|image9 17.png]]

Las transacciones son paso obligatorio. Cada vez que queramos modificar nuestra BD, guardar, actualizar, etc. Debe hacerse dentro de una transacción, porque las transacciones garantizan consistencia, ósea, o se hacen todos los cambios juntos o no se hace nada. Esto protege la integridad de la BD especialmente si algo falla a mitad de proceso.

![[Assets/image10 16.png|image10 16.png]]

Vamos a guardar una persona con el método persist() del EntityManager

Ejemplo de como guardar a una Persona en la BD usando persist():

![[Assets/image11 16.png|image11 16.png]]

Una vez que ejecutemos esto mostrara el Id de la persona guardada:

![[Assets/image12 16.png|image12 16.png]]

![[Assets/image13 16.png|image13 16.png]]

Ahora vamos a buscar a la persona guardada con el metodo find() del EntityManager:

contexto de persistencia: Si ya tenemos cargado al objeto persona, no va a consultarlo a la BD

otra vez si no que ya lo tiene. En caso de que no lo tengo va a hacer un select a la BD.

![[Assets/image14 19.png|image14 19.png]]

Nos muestra:

![[Assets/image15 14.png|image15 14.png]]

Si queremos verificar que los datos realmente están en la BD es ir a la consola web que tiene

H2.

![[Assets/image16 15.png|image16 15.png]]

5- Anotaciones Básicas de JPA