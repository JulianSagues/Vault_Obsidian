---
notion-id: 299ac26b-dee7-8085-b520-eedaf0a98ef0
base: "[[Desarrollo de software.base]]"
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - 299ac26b-dee7-80ad-901b-c3e220f30695
Blocking: []
Categoria: ""
---
## Aserciones

Hay situaciones en las que los métodos que nosotros escribimos van a devolver un nulo, van a lanzar una excepción o simplemente deberían demorarse determinado tiempo.


El objetivo principal es ir más allá de simplemente imprimir resultados en la consola (`System.out.println`) y usar métodos de aserción formales para validar la calidad y el comportamiento esperado del código.



Entonces vamos a volver a la calculadora, tenemos un método sumar que devuelve un entero.


1. Preparación del Código a Probar (Clase `Calculadora`)



**Refactorización de **`**sumar**`**:**

![[image 343.png]]

- Cambia los tipos de datos de los parámetros y el valor de retorno de `int` (primitivo) a `Integer` (clase wrapper).
- Añade lógica para **manejar valores nulos**: Si alguno de los parámetros (`a` o `b`) llega como `null`, se le asigna el valor `0` para evitar un `NullPointerException`.

**Creación del método **`**dividir**`**:**

![[image 344.png]]

- Implementa un nuevo método `dividir` que inicialmente usa `Integer`.
- Añade una **validación crítica**: Comprueba si el `denominador` es `null` o es igual a `0`.
- Si la validación falla, **lanza una excepción** (`throw new Exception("denominador inválido")`).
- Debido a esto, debe añadir la declaración `throws Exception` a la firma del método.

**Segunda refactorización de **`**dividir**`**:**

![[image 345.png]]

- Para obtener resultados decimales precisos (en lugar de la división entera, que hacía que `2 / 3` diera `0`), cambia todos los tipos de datos del método `dividir` de `Integer` a `Double`.

### 2. Estructura y Orden de los Tests

El instructor pasa a la clase `CalculadoraTest` y la modifica para mejorar su estructura:

- **Manejo de Excepciones en el Test:** Al llamar al nuevo método `calc.dividir()`, el IDE obliga a manejar la `Exception` declarada. El instructor lo envuelve en un bloque `try-catch`.

![[image 346.png]]

- **Orden de Ejecución de Pruebas:**
    - El instructor nota que el orden en que se ejecutan los tests es impredecible, lo cual es "feo" y "desordenado".
    - Para solucionarlo, introduce la anotación `**@TestMethodOrder**` a nivel de clase.
![[image 347.png]]
    - Luego, usa la anotación `**@Order**` en cada método de prueba (p.ej., `@Order(1)` para `testSumar` y `@Order(2)` para `testDividir`) para forzar una secuencia de ejecución específica.
![[image 348.png]]
![[image 349.png]]

- **Refactorización de Tests:** Para evitar duplicar código (específicamente `Calculadora calc = new Calculadora();` en cada test), mueve la declaración de `calc` como una variable de instancia de la clase. Menciona que esta variable se puede inicializar *antes de cada prueba* (sugiriendo el uso de `@BeforeEach`, aunque no lo implementa explícitamente en este video).

![[image 350.png]]

![[image 351.png]]

Se crea una sola vez y después la inicio cuando la necesite. Entonces haciendo esto tengo menos código para mantener y teniendo a la variable calc con un solo valor.

### 3. El Uso de Aserciones (El Núcleo del Video)

Esta es la parte central del tutorial, donde se reemplaza la verificación manual (mirando la consola) por aserciones de JUnit.

- `**Assertions.assertEquals**`**:**

![[image 352.png]]

- Es la aserción principal que se introduce. Se utiliza para comparar un valor esperado con el valor real devuelto por el método.
- La sintaxis es: `Assertions.assertEquals(valor_esperado, valor_obtenido);`.
- El test **pasa** si los valores son iguales y **falla** si son diferentes.
- Demuestra cómo un test falla cuando cambia el valor esperado, mostrando cómo el IDE de JUnit reporta el error indicando que "no es igual el resultado esperado frente al resultado que obtuvimos".
- `**Assertions.assertTrue**`** y **`**Assertions.assertFalse**`**:**
    - Introduce brevemente estas dos aserciones.
    - `assertTrue(condicion)`: Comprueba que una condición booleana sea verdadera. (Muestra un ejemplo: `assertTrue(esperado == resultado)`, aunque aclara que no es el "ejemplo más feliz" y que `assertEquals` es mejor para ese caso).
    - `assertFalse(esperado == resultado)`: Comprueba que una condición booleana sea falsa.
- **Prueba de Denominador Cero:**
    - Crea un nuevo test (duplicando `testDividir`) para validar el caso de la división por cero, llamándolo `testDividirDenominadorCero`.
    - Configura las variables para que el denominador sea `0.0`.

### 4. Conclusión y Próximos Pasos

El video concluye explicando que, aunque se introdujeron varias aserciones, hay más temas por cubrir. El instructor anticipa que en la próxima sesión enseñará:

1. Cómo **controlar y validar las excepciones** correctamente (algo que preparó en este video con el `try-catch` pero que no finalizó de implementar con una aserción específica).
2. Cómo **deshabilitar tests** (sin borrarlos o comentarlos).
3. El manejo de **parámetros** en los métodos de prueba.