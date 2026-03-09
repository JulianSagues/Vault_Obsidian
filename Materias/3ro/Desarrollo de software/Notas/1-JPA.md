---
Parent item:
  - "[[Materias/Desarrollo de software/Resumen Videos\\|Resumen Videos]]"
---
![[Assets/image1 10.png|image1 10.png]]

JPA actúa como el puente entre el modelo de objetos (JAVA) y el modelo relacional (SQL). Es como un traductor que entiende ambos idiomas.

![[Assets/image2 10.png|image2 10.png]]

![[Assets/image3 10.png|image3 10.png]]

JPA define el "QUE" y el proveedor de JPA define el "COMO" se hace.

![[Assets/image4 10.png|image4 10.png]]

En la vida real se usa una combinación de las dos.

![[Assets/image5 10.png|image5 10.png]]

Entidades->Son las clases de JPA que van a representar las tablas de la base de datos.

EntityManager->Es como el control remoto que vamos a usar para hablar con la base de datos.

EntityManagerFactory-> Es como una fabrica que va a crear nuestro EntityManager, es como una fabrica de controles remotos.

Unidad de persistencia -> Agrupa un conjunto de entidades y define la configuración para trabajar con esas entidades.

JPQL -> Es un lenguaje de consulta orientado a objetos., que nos permitira hacer busquedas con nuestras entidades de JAVA.

![[Assets/image6 10.png|image6 10.png]]

Básicamente son las clases normales de JAVA que tenemos, pero con un par de detalles extras. Por ejemplo para esto se marca con @Entity una clase para que JPA lo represente como una tabla en la base de datos, donde cada campo de la clase se va a mapear automáticamente en una tabla en la BD.

También tendrá clave primaria que se marcara con @Id

Ejemplo con clase Persona:

![[Assets/image7 10.png|image7 10.png]]

@Entity -> mapea la clase en el modelo relacional.

@Id pone como clave primaria al atributo id.

@OneToMany es para mapear en el modelo relacional la relación de 1 a N con la clase Inscripción.

![[Assets/image8 10.png|image8 10.png]]

Con estos 5 métodos podremos gestionar el 90% de los datos de la BD.

![[Assets/image9 9.png|image9 9.png]]

Debe instanciarse una única vez cuando se arranque la aplicación y que se use durante todo el

ciclo de vida de la aplicación.

![[Assets/image10 9.png|image10 9.png]]

Es como la zona de trabajo de JPA donde agrupa todas las entidades y define la configuración de conexión con el famoso archivo persistence.xml que va a crear una carpeta META-INF, done ahí le vamos a decir a JPA que entidades usar, como conectarse a la BD y que proveedor de JPA estamos usando.

![[Assets/image11 9.png|image11 9.png]]

JPQL es como SQL pero orientado a objetos, en vez de hablar de tablas y columnas vamos a hablar de entidades y atributos.

![[Assets/image12 9.png|image12 9.png]]

Para usar JPA necesitamos algún proveedor que implemente esas reglas. Hibernate es el más

común.

![[Assets/image13 9.png|image13 9.png]]

![[Assets/image14 9.png|image14 9.png]]

Entonces JPA es como un asistente técnico mientras nosotros nos concentramos en resolver problemas reales de los usuarios, ósea evita que tengamos que ir gestionando la BD manualmente.

2- H2 Database