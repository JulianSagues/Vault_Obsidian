---
Parent item:
  - "[[Materias/Desarrollo de software/Notas/Resumen Videos\\|Resumen Videos]]"
---
![[Assets/image1 10.png|image1 10.png]]

H2 es una BD relacional que esta completamente escrita en JAVA, es de código abierto.

![[Assets/image2 10.png|image2 10.png]]

![[Assets/image3 16.png|image3 16.png]]

![[Assets/image4 16.png|image4 16.png]]

Modo En Memoria-> Toda la información se guarda en RAM y caundo se apaga la app toda la info se borra. Se usa para pruebas unitarias o para empezar con una BD limpia.

Modo Basado en Archivos-> La información se guarda en el disco y si reiniciamos la aplicación la información va a seguir estando ahí. Esto es ideal cuándo queremos trabajar localmente.

![[Assets/image5 12.png|image5 12.png]]

Modo Embebido-> Es cuando la BD se va ejecutar dentro de la misma aplicación y nos va a evitar tener que levantar un servidor aparte para ejecutar la base de datos.

Modo Cliente-Servidor-> Se usa cuando quiero que muchas aplicaciones o usuarios se conecten a la misma base de datos desde distintas computadoras como si fuera un servidor de verdad.

![[Assets/image6 14.png|image6 14.png]]

H2 es totalmente compatible con JPA, pero para logar que trabajen juntos necesitamos configurar el archivo persistense.xml

Este archivo estará dentro de la carpeta META-INF y es donde le decimos a JPA como conectarse a la BD y que proveedor va a usar.

Dentro del archivo persistense.xml vamos a tener que indicar algunos datos clave que son: el driver de jdbc de h2, la url de conexión, modo de memoria. el usuario y la contraseña.

![[Assets/image7 13.png|image7 13.png]]

![[Assets/image8 15.png|image8 15.png]]

![[Assets/image9 10.png|image9 10.png]]

![[Assets/image10 9.png|image10 9.png]]

![[Assets/image11 9.png|image11 9.png]]

Esto me dice que url poner si lo hice para RAM o archivo.

![[Assets/image12 9.png|image12 9.png]]

El persistense.xml es como el corazón de la configuración sin eso JPA no podrá trabajar.

![[Assets/image13 9.png|image13 9.png]]

![[Assets/image14 12.png|image14 12.png]]

3-persistense.xml