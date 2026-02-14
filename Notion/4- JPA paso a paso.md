---
notion-id: 29bac26b-dee7-81e9-98c7-dc0d204264db
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - 29bac26b-dee7-80d2-9ccf-cc05773f4eeb
Blocking: []
Categoria: ""
---
![[image1 4.png]]

Lo primero que debemos hacer es poner las dependencias en el build.gradle:

![[image2 4.png]]

Luego debemos crear el archivo persistense.xml para utilizar JPA:

![[image3 4.png]]

De esta manera ya tenemos preparado el entorno.

![[image4 4.png]]

En JPA una entidad es una clase común de JAVA pero con algunas anotaciones que le van a indicar a JPA que tiene que tiene que mapearse en la tabla de la BD.

Cada instancia de la clase va a representar una fila de la tabla. Trabajaremos con la clase Persona.

![[image5 5.png]]

Acá creamos una clase marcada con @Entity que es para decirle a JPA que debe mapearla en la BD, además luego de marcarla con @Entity estamos obligados a poner un @Id para la clave primaria, también podemos poner como se generara ese id (clave primaria de la tabla).

Con @Table le ponemos nombre a la tabla y con @Column le ponemos nombre a una columna de la tabla en la BD.

Una vez que declaramos la entidad debemos declararla en el persistense.xml, porque si no JPA la va a ignorar.

![[image6 7.png]]

Así se declara la entidad en el persistense.xml

![[image7 6.png]]

EntityManagerFactory-> Crea a EntityManager.

EntityManager-> Es mi puente con la BD.

Ejemplo de uso:

![[image8 5.png]]

Los deben crearse y cerrarse al final.

![[image9 5.png]]

Las transacciones son paso obligatorio. Cada vez que queramos modificar nuestra BD, guardar, actualizar, etc. Debe hacerse dentro de una transacción, porque las transacciones garantizan consistencia, ósea, o se hacen todos los cambios juntos o no se hace nada. Esto protege la integridad de la BD especialmente si algo falla a mitad de proceso.

![[image10 4.png]]

Vamos a guardar una persona con el método persist() del EntityManager

Ejemplo de como guardar a una Persona en la BD usando persist():

![[image11 4.png]]

Una vez que ejecutemos esto mostrara el Id de la persona guardada:

![[image12 4.png]]

![[image13 4.png]]

Ahora vamos a buscar a la persona guardada con el metodo find() del EntityManager:

contexto de persistencia: Si ya tenemos cargado al objeto persona, no va a consultarlo a la BD

otra vez si no que ya lo tiene. En caso de que no lo tengo va a hacer un select a la BD.

![[image14 4.png]]

Nos muestra:

![[image15 1.png]]

Si queremos verificar que los datos realmente están en la BD es ir a la consola web que tiene

H2.

![[image16 1.png]]

<u>5- Anotaciones Básicas de JPA</u>