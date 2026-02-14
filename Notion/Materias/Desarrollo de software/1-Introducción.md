---
notion-id: 299ac26b-dee7-80e6-8dff-d814ed8382b7
base: "[[Desarrollo de software.base]]"
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - 299ac26b-dee7-80ad-901b-c3e220f30695
Blocking: []
Categoria: ""
---
## Introducción

¿Qué es JUnit?

JUnit no es más que un framework, es el framework más elegido para hacer testing.

Podríamos hacer testing sobre una capa web, para testing sobre el código puro y duro, es decir, el código que nosotros escribimos en nuestros controladores, en nuestros repositorios, en los servicios que vayamos a implementar, bueno, para ese tipo de código podemos utilizar Junit.


¿Por qué deberíamos de hacer pruebas?

Las pruebas son esenciales en cualquier tipo de código que escribamos, ya que son ellas las que nos van a proteger de que, frente a futuros cambios sobre las implementaciones  ya existentes, el test es el que nos va a proteger de que sigamos otorgando los resultados esperados, es decir, si nosotros, antes de comenzar algo, se espera que frente a un determinado input tengamos un output de resultado.

Al tener escrito un test que valide ese output, nosotros sabemos que si hemos modificado el código, para esas pruebas, son las que nos van a salvar o resguardar de estar alterando erróneamente nuestro código.


¿Qué cosas más podemos chequear en el código?

Nosotros cada vez que escribimos métodos, puede ser que estos métodos tengan o lancen o tengan en su firma la declaración de una excepción, entonces nosotros podríamos testear eso y controlar, porque un método que tiene marcado la posibilidad de lanzar una excepción de determinado tipo, que al final nunca la manda, es una excepción que está mal declarada, porque el método no lo hace nunca, entonces mediante este tipo de test, nosotros podríamos encontrar o podríamos chequear de que esa excepción o las excepciones que estén declaradas en algún punto de su código se ejecuten. Básicamente que las excepciones se lancen y no estén al pedo para sirven los test de un código.

También podríamos controlar tiempos de ejecución, eso es clave en el sentido de que si nosotros garantizamos que determinada operación se va a realizar en X cantidad de tiempo, lo tenemos que poder medir y lo tenemos que poder controlar mediante el unit.


Ejemplo de proyecto:

![[image 353.png]]

Nosotros en los proyectos vamos a tener dentro la carpeta source, una carpeta main y otra test, bueno todos nuestros códigos van a terminar en una carpeta test, pero la invocación de métodos o de clases, digamos las clases en las que nosotros estemos invocando para testear justamente, van a estar en la clase main.

![[image 354.png]]

Entonces nosotros tenemos en la clase principal acá es donde está nuestro código fuente, el código que nosotros queremos cuidar.

![[image 355.png]]

Y en la carpeta source test java van a estar las clases que van a hacer prueba y que van a garantizar o proteger al menos en la calidad del código que está arriba JUnit2021Application.java

Entonces lo primero que hacemos es generar una nueva clase que la vamos a llamar calculadora y sobre esta clase vamos a agregar distintos métodos.

![[image 356.png]]

La vieja manera de hacerlo y lo que está totalmente desaprobado es generar acá un método que sea público, static void main string args y acá poder hacer la invocación clásica de si voy a generar una variable que sea calculadora calc igual new calculadora y sobre calc ejecutar tal vez el método sumar calculadora.

![[image 357.png]]

Esto es lo que está totalmente prohibido, ese método.

![[image 358.png]]

Entonces lo anterior lo borramos y vamos a agregar una nueva clase que se va a llamar CalculadoraTest y en este vamos a agregar un método que se va a llamar public void testSumar 

![[image 359.png]]

Lo único que nosotros necesitamos sí o sí para asegurar que se ejecute es agregar @tTest habiendo agregado esta anotación nosotros estamos en buenas condiciones.

Como buenas prácticas siempre hay que revisar el pom

![[image 360.png]]

En este caso en el pom fíjense que dice versión 8 y nosotros queremos trabajar con la versión 11

![[image 361.png]]


Otra cosa que deberíamos de tener siempre presente es de agregar un plugin que nos garantice que tanto nuestro código fuente y el código que se va a ejecutar posteriormente mantengan la misma versión.

![[image 362.png]]

Entonces para retomar el test simplemente vamos a hacer una invocación vamos a generar una instancia de calculadora.

![[image 363.png]]

¿Cómo ejecutamos esto?

 Es sencillo botón derecho:

![[image 364.png]]

Una vez que ejecutamos nos sale esto:

![[image 365.png]]

Lo que nos está pasando es lo siguiente nosotros hemos actualizado el archivo pom, de manera que pueda hacerlo con el plugin.

Otra manera de ejecutar es apretando las teclas shift alt d y posteriormente la tecla t

![[image 366.png]]

Entonces lo ejecutamos y nos devuelve este:

![[image 367.png]]

Se ejecutó el test y el resultado es 5.

Ahora veremos las anotaciones por ejemplo:

@BeforeAll y este es este método se garantiza que se va a ejecutar antes de todos los test entonces

Tanto @BeforeAll  como @AfterAll son métodos que deben ser declarados como estáticos.

Dentro de CalculadoraTest

![[image 368.png]]

![[image 369.png]]

![[image 370.png]]

![[image 371.png]]

Entonces ejecutamos y nos queda esto:

![[image 372.png]]

@BeforeAll: Se ejecuta una vez antes de todas las pruebas.
@AfterAll: Se ejecuta una vez después de todas las pruebas.
@BeforeEach: Se ejecuta antes de cada prueba.
@AfterEach: Se ejecuta después de cada prueba.
