---
Parent item:
  - "[[Materias/Desarrollo de software/Resumen Videos\\|Resumen Videos]]"
---
![[image1.png]]

H2 es una BD relacional que esta completamente escrita en JAVA, es de código abierto.

![[image2.png]]

![[image3.png]]

![[image4.png]]

Modo En Memoria-> Toda la información se guarda en RAM y caundo se apaga la app toda la info se borra. Se usa para pruebas unitarias o para empezar con una BD limpia.

Modo Basado en Archivos-> La información se guarda en el disco y si reiniciamos la aplicación la información va a seguir estando ahí. Esto es ideal cuándo queremos trabajar localmente.

![[image5.png]]

Modo Embebido-> Es cuando la BD se va ejecutar dentro de la misma aplicación y nos va a evitar tener que levantar un servidor aparte para ejecutar la base de datos.

Modo Cliente-Servidor-> Se usa cuando quiero que muchas aplicaciones o usuarios se conecten a la misma base de datos desde distintas computadoras como si fuera un servidor de verdad.

![[image6.png]]

H2 es totalmente compatible con JPA, pero para logar que trabajen juntos necesitamos configurar el archivo persistense.xml

Este archivo estará dentro de la carpeta META-INF y es donde le decimos a JPA como conectarse a la BD y que proveedor va a usar.

Dentro del archivo persistense.xml vamos a tener que indicar algunos datos clave que son: el driver de jdbc de h2, la url de conexión, modo de memoria. el usuario y la contraseña.

![[image7.png]]

![[image8.png]]

![[image9.png]]

![[image10.png]]

![[image11.png]]

Esto me dice que url poner si lo hice para RAM o archivo.

![[image12.png]]

El persistense.xml es como el corazón de la configuración sin eso JPA no podrá trabajar.

![[image13.png]]

![[image14.png]]

3-persistense.xml