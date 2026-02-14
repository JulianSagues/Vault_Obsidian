---
base: "[[Desarrollo de software.base]]"
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - "[[Notion/Fundamentos de Spring Boot|Fundamentos de Spring Boot]]"
Blocking: []
Categoria: ""
---
### 🎯 El Problema: Acoplamiento Manual

- Cuando instanciamos objetos manualmente usando `new` (ej. `new UsuarioService()`), creamos un **acoplamiento fuerte**.
- **Problemas:**
![[image 373.png]]
    - **Difícil de testear:** No podemos reemplazar fácilmente un objeto por una simulación (mock).
    - **Frágil:** Un cambio en un constructor se propaga en cascada por toda la aplicación.
    - **Repetitivo:** Terminamos creando las mismas instancias en múltiples lugares.

---

### 💡 La Solución: Inyección de Dependencias (DI)

![[image 374.png]]

- **¿Qué es?** Es la solución de Spring a este problema y es parte del concepto de **Inversión de Control (IoC)**.
- **¿Cómo funciona?** En lugar de que *nosotros* creemos los objetos (Beans) que una clase necesita, le **delegamos esa responsabilidad a Spring**.
- Simplemente "declaramos" qué dependencias necesitamos, y Spring se encarga de crearlas, conectarlas e "inyectarlas" por nosotros.
- **Beneficios:**

![[image 375.png]]

- **Desacoplamiento:** Las clases no saben cómo se crean sus dependencias, solo que las necesitan (idealmente, dependen de interfaces).
- **Reutilización:** Spring inyecta el mismo Bean (que es singleton por defecto) en todos los lugares donde se necesita.
- **Testeabilidad:** Es muy fácil inyectar "mocks" o simulaciones en lugar de los Beans reales durante las pruebas.

---

### 🏆 Tipos de Inyección (y la Mejor Práctica)

Existen tres formas de inyectar dependencias, pero una es la clara ganadora:

![[image 376.png]]

1. **Por Campo (Field):** (Ej. `@Autowired private UserService service;`) - **Desaconsejada**.
2. **Por Setter:** (Ej. `public void setService(UserService s){...}`) - Se usa en casos específicos.
3. **✅ Por Constructor:** (Ej. `public MiClase(UserService s){...}`) - **¡LA MEJOR PRÁCTICA!**

**¿Por qué usar la inyección por constructor?**

![[image 377.png]]

- **Inmutabilidad:** Las dependencias se pueden declarar como `final`, asegurando que no cambien después de la creación.
- **Dependencias Explícitas:** Queda 100% claro qué necesita la clase para funcionar con solo ver el constructor.
- **Facilita el Testing:** Es muy sencillo crear una instancia de la clase en un test pasándole mocks en el constructor.

---

### 🏷️ Estereotipos de Spring: Organizando el Código

![[image 378.png]]

Los **estereotipos** son anotaciones que le dan un "rol" semántico a una clase. Le dicen a Spring qué tipo de Bean es:

![[image 379.png]]

- `**@Component**`**:** La anotación genérica para cualquier Bean.
- `**@Service**`**:** Para la **lógica de negocio** (ej. `UsuarioService`).
- `**@Repository**`**:** Para la capa de **acceso a datos** (comunicación con la base de datos, ej. `UsuarioRepository`).
- `**@Controller**`** / **`**@RestController**`**:** Para la capa web, maneja peticiones y respuestas **HTTP** (ej. `UsuarioController`).

---

### 🏢 Arquitectura Típica: Controller-Service-Repository

Estos estereotipos definen un flujo de arquitectura muy común y recomendado en Spring Boot:

![[image 380.png]]

4. El `**@RestController**` recibe la solicitud HTTP (ej. desde un navegador).
5. El `Controller` **no** hace lógica pesada. Llama a un `**@Service**`.
6. El `Service` orquesta la lógica de negocio (validaciones, cálculos, etc.).
7. Si necesita datos, el `Service` llama a un `**@Repository**`.
8. El `Repository` se encarga de hablar con la base de datos (consultar, guardar, etc.).

---

### 💻 Demostración Práctica

El video crea un ejemplo de esta arquitectura usando **inyección por constructor**:

9. `**UserRepository**`** (**`**@Repository**`**):**
    - Simula el acceso a la BD.
    - Tiene un método `buscarUsuario()` que devuelve un string fijo: "Juan Cruz Robledo".
10. `**UserService**`** (**`**@Service**`**):**
    - Depende de `UserRepository`.
    - **Lo recibe en el constructor:** `public UserService(UserRepository repository) {...}`.
    - Tiene un método `getUser()` que llama al repositorio y concatena "Hola, ".
11. `**UserController**`** (**`**@RestController**`**):**
    - Depende de `UserService`.
    - **Lo recibe en el constructor:** `public UserController(UserService service) {...}`.
    - Expone un *endpoint* con `@GetMapping("/hello")`.
    - Este método llama a `userService.getUser()`.

**Resultado:**
Al acceder a `localhost:8080/hello`, se dispara la cadena:
`Controller` → `Service` → `Repository`
Y el navegador muestra: "Hola, Juan Cruz Robledo".

**La clave:** En ningún momento se usó la palabra `new`. Spring conectó (inyectó) automáticamente el Repositorio en el Servicio y el Servicio en el Controlador.

---

### ✅ Conclusión y Próximos Pasos

- La **Inyección de Dependencias** (especialmente por constructor) es clave para un código desacoplado, mantenible y testeable.
- Los **Estereotipos** (`@Controller`, `@Service`, `@Repository`) nos ayudan a organizar la arquitectura de forma limpia y profesional.
- **Próximo Video:** Se explorará cómo configurar la aplicación (hacerla flexible) usando los archivos `application.properties`, `application.yml` y perfiles.