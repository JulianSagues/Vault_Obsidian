---
Parent item:
  - "[[Materias/Desarrollo de software/Resumen de Junit videos\\|Resumen de Junit videos]]"
---
### 1. Pruebas de Excepciones (`Assertions.assertThrows`)

- **Objetivo:** Verificar que un método lanza una excepción específica bajo ciertas condiciones (en este caso, `dividir` cuando el denominador es cero).

- **Problema con** `**try-catch**`**:** El enfoque anterior de usar `try-catch` dentro del test no valida _activamente_ que la excepción _debe_ ocurrir.

- **Solución JUnit:** Se introduce `Assertions.assertThrows`.
    
    - **Sintaxis:** `Exception exception = Assertions.assertThrows(TipoDeExcepcionEsperada.class, () -> { /* Código que debe lanzar la excepción */ });`
    
    ![[Assets/image 62.png|image 62.png]]
    
    - **Funcionamiento:**
        
        1. Se especifica la clase de la excepción que se espera (`Exception.class` en el ejemplo).
        
        1. Se proporciona una expresión lambda (`() -> { ... }`) que contiene la llamada al método que debería fallar (ej: `calc.dividir(a, b)`).
        
        1. JUnit ejecuta el código dentro de la lambda. Si se lanza la excepción esperada (o una subclase de ella), `assertThrows` la captura y la devuelve. El test continúa.
        
        1. Si se lanza una excepción diferente o _ninguna_ excepción, el test **falla**.
        
    
    - **Verificación del Mensaje:** Una vez capturada la excepción (guardada en la variable `exception`), se puede añadir otra aserción para verificar el mensaje específico de la excepción: `Assertions.assertEquals("denominador inválido", exception.getMessage());`. Esto hace la prueba más robusta.
    

- **Implementación:** Se crea un nuevo método de prueba (`testDividirCheckeException`) que configura el denominador a `0.0` y utiliza `assertThrows` junto con `assertEquals` para validar tanto la ocurrencia de la `Exception` como su mensaje.

### 2. Deshabilitar Pruebas (`@Disabled`)

- **Objetivo:** Omitir temporalmente la ejecución de un método de prueba sin borrarlo ni comentarlo.

- **Solución JUnit:** Se utiliza la anotación `@Disabled` encima de la anotación `@Test` (o `@RepeatedTest`, `@Order`, etc.).

- **Resultado:** El test runner reportará la prueba como "skipped" (omitida) en lugar de ejecutarla.

- **Ejemplo:** Se aplica `@Disabled` a un test anterior (`testDividirAssertTrue`) para demostrar su efecto.

### 3. Obtener Información de la Prueba (`TestInfo`)

- **Objetivo:** Mejorar la legibilidad de la salida en consola, identificando qué test se está ejecutando.

- **Solución JUnit:** Se puede inyectar un parámetro de tipo `TestInfo` en los métodos de prueba o en los métodos del ciclo de vida (`@BeforeEach`, `@AfterEach`, etc.).

- **Uso:**
    
    - Se modifican las firmas de `@BeforeEach` y `@AfterEach` para aceptar `TestInfo testInfo`.
    
    - Dentro de estos métodos, se usa `testInfo.getDisplayName()` para obtener el nombre del test actual.
    
    - Se actualizan los `System.out.println` para incluir mensajes como `"inicio " + testInfo.getDisplayName()` y `"finaliza " + testInfo.getDisplayName()`, haciendo la consola más informativa. (Se corrige un error inicial donde los mensajes "inicio" y "finaliza" estaban invertidos).
    

### 4. Repetir Pruebas (`@RepeatedTest`)

- **Objetivo:** Ejecutar el mismo método de prueba varias veces consecutivas.

- **Solución JUnit:** Se reemplaza la anotación `@Test` por `@RepeatedTest(numeroDeVeces)`.

- **Ejemplo:** Se modifica el test de excepción (`testDividirCheckeException`) cambiando `@Test @Order(4)` por `@RepeatedTest(5)`.

- **Resultado:** El test se ejecuta 5 veces. La consola muestra información sobre qué repetición se está ejecutando (ej: "repetition 1 of 5", "repetition 2 of 5", etc.).