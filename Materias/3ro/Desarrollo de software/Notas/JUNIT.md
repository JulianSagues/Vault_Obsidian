---
Sub-item:
  - "[[Materias/Desarrollo de software/Resumen de Junit videos\\|Resumen de Junit videos]]"
---
# Testing Unitario (JUnit y Mockito)

## 🔸 Concepto

Verificar que **cada componente funcione correctamente en forma aislada**.

No se prueba toda la aplicación, sino cada método de manera independiente.

---

## 🔸 JUnit 5 — estructura

### Ciclo de ejecución

1. `@BeforeAll` → se ejecuta una vez antes de todos los tests.

1. `@BeforeEach` → antes de cada test.

1. `@Test` → test individual.

1. `@AfterEach` → después de cada test.

1. `@AfterAll` → después de todos los tests.

### Ejemplo

```Java
class CalculadoraTest {
    private Calculadora calc;

    @BeforeEach
    void init() {
        calc = new Calculadora();
    }

    @Test
    void sumaCorrecta() {
        assertEquals(5, calc.sumar(2, 3));
    }

    @Test
    void divisionPorCeroLanzaExcepcion() {
        assertThrows(ArithmeticException.class, () -> calc.dividir(4, 0));
    }
}
```

---

## 🔸 Tipos de aserciones

|Método|Uso principal|Ejemplo|Descripción|
|---|---|---|---|
|`assertEquals(expected, actual)`|Comparar valores|`assertEquals(5, suma(2, 3));`|Verifica que el resultado sea igual al esperado.|
|`assertNotEquals(unexpected, actual)`|Asegurar que **no** sean iguales|`assertNotEquals(0, division(10, 2));`|Comprueba que dos valores sean distintos.|
|`assertTrue(condition)`|Verificar condición verdadera|`assertTrue(lista.isEmpty());`|La condición debe ser `true`.|
|`assertFalse(condition)`|Verificar condición falsa|`assertFalse(usuario.isAdmin());`|La condición debe ser `false`.|
|`assertNull(object)`|Verificar `null`|`assertNull(buscarUsuario("noExiste"));`|El objeto debe ser `null`.|
|`assertNotNull(object)`|Verificar que no sea `null`|`assertNotNull(buscarUsuario("juan"));`|El objeto no debe ser `null`.|
|`assertSame(expected, actual)`|Verificar misma referencia|`assertSame(obj1, obj2);`|Apuntan al **mismo objeto** en memoria.|
|`assertNotSame(expected, actual)`|Verificar distinta referencia|`assertNotSame(obj1, obj2);`|Son **objetos diferentes** aunque iguales en contenido.|
|`assertArrayEquals(expected, actual)`|Comparar arreglos|`assertArrayEquals(new int[]{1,2}, resultado);`|Los elementos del array deben coincidir.|
|`assertThrows(Exception.class, executable)`|Verificar que una excepción sea lanzada|`assertThrows(IllegalArgumentException.class, () -> dividir(5,0));`|Comprueba que una excepción esperada ocurra.|
|`assertDoesNotThrow(executable)`|Verificar que **no** se lance excepción|`assertDoesNotThrow(() -> procesarArchivo("data.txt"));`|Asegura que el código se ejecute sin errores.|
|`fail(message)`|Forzar fallo manual|`fail("No debería llegar acá");`|Se usa para marcar un test como fallido explícitamente.|

---

## 🔸 Mockito

Framework para **simular dependencias** y probar sin base de datos real.

### Anotaciones

|Anotación|Descripción|
|---|---|
|`@Mock`|Crea un mock de una clase o interfaz.|
|`@InjectMocks`|Inyecta mocks en la clase bajo prueba.|
|`@ExtendWith(MockitoExtension.class)`|Inicializa automáticamente los mocks.|

---

### Ejemplo

```Java
@ExtendWith(MockitoExtension.class)
class ClienteServiceTest {

    @Mock ClienteRepository repo;
    @InjectMocks ClienteService service;

    @Test
    void testGuardarCliente() {
        Cliente c = new Cliente("Lucas");
        when(repo.save(c)).thenReturn(c);

        Cliente resultado = service.guardar(c);

        assertEquals("Lucas", resultado.getNombre());
        verify(repo).save(c);
    }
}
```

### Métodos de verificación

|Método|Función|
|---|---|
|`when(...).thenReturn(...)`|Define el comportamiento del mock.|
|`verify(mock).método()`|Verifica que se haya llamado.|
|`times(n)`|Verifica cantidad de invocaciones.|