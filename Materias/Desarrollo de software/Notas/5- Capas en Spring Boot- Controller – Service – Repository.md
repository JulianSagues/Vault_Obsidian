---
Parent item:
  - "[[Materias/Desarrollo de software/Notas/API REST SPRING BOOT\\|API REST SPRING BOOT]]"
---
### 🎯 El Problema: "Todo en el Controlador"

![[Assets/image 459.png|image 459.png]]

Si seguimos poniendo toda la lógica en el controlador, el proyecto se vuelve un "lío" (un "controller gordo"):

- Se mezcla la lógica de negocio (validaciones) con el acceso a datos.

- Es imposible de testear de forma aislada.

- No se puede reutilizar el código.

- Se vuelve inmantenible a medida que crece y viola principios de diseño (como SOLID).

---

### 💡 La Solución: Separar Responsabilidades

La arquitectura en 3 capas resuelve esto asignando un rol claro a cada componente.

### 1. La Capa Controller (`@RestController`)

![[Assets/image 1 51.png|image 1 51.png]]

- Es la **"puerta de entrada"**. Es la capa más externa.

- **Qué SÍ hace:**
    
    - Recibe la petición HTTP y lee los datos (`@RequestBody`, `@PathVariable`, etc.).
    
    - Coordina la operación, llamando al **Service** correspondiente.
    
    - Devuelve la respuesta HTTP (convierte el resultado a JSON).
    

- **Qué NO hace:**
    
    - **No debe contener lógica de negocio** (cálculos, validaciones de reglas).
    
    - **No debe hablar NUNCA directamente con la base de datos** (nunca debe inyectar un Repository).
    

- Debe ser "liviana" (thin).

### 2. La Capa Service (`@Service`)

![[Assets/image 2 48.png|image 2 48.png]]

- Es el **"cerebro"** de la aplicación.

- **Qué SÍ hace:**
    
    - Contiene toda la **lógica de negocio** (reglas, validaciones, cálculos).
    
    - Orquesta las operaciones (ej. "para crear un usuario, primero valida el email, luego guarda en BD, y finalmente envía un correo").
    
    - Llama al **Repository** para pedirle o enviarle datos.
    

- Es reutilizable (varios controladores podrían usar el mismo servicio).

### 3. La Capa Repository (`@Repository`)

![[Assets/image 3 41.png|image 3 41.png]]

- Es el **"guardián de los datos"**. Es la capa más interna.

- **Qué SÍ hace:**
    
    - Tiene una **única responsabilidad**: acceder a los datos (guardar, leer, actualizar, borrar).
    
    - Abstrae la fuente de datos.
    

- **Qué NO hace:**
    
    - **No debe contener lógica de negocio**. Solo se limita a ejecutar las consultas.
    

---

### 🔁 El Flujo Completo

El flujo de una petición ahora sigue un orden estricto:

![[Assets/image 4 34.png|image 4 34.png]]

**Cliente (Postman)** → `HTTP Request` → **(Capa 1) Controller** → `Llama al` → **(Capa 2) Service** → `Llama al` → **(Capa 3) Repository** → **Base de Datos**

La respuesta viaja en el sentido opuesto:

**Base de Datos** → **Repository** → **Service** → **Controller** → `HTTP Response (JSON)` → **Cliente (Postman)**

---

### 💻 Demostración Práctica (App "Usuarios en memoria")

El video reestructura el proyecto con paquetes (carpetas) para cada capa: `controller`, `service`, `repository` y `model`.

- `**model/Usuario.java**`: Es un POJO simple (con Lombok) que define la entidad: `id`, `nombre`, `email`.

- `**repository/UsuarioRepository.java**`:
    
    - Se anota con `@Repository`.
    
    - **Simula la base de datos** usando una `List<Usuario>` en memoria.
    
    - Tiene métodos como `guardar()`, `listarTodos()`, `buscarPorId()`.
    

- `**service/UsuarioService.java**`:
    
    - Se anota con `@Service`.
    
    - Recibe el `UsuarioRepository` por inyección de dependencias.
    
    - Contiene la lógica, ej. el método `crearUsuario()` llama a `repository.guardar()`.
    

- `**controller/UsuarioController.java**`:
    
    - Se anota con `@RestController` y `@RequestMapping("/usuarios")`.
    
    - Recibe el `UsuarioService` por inyección de dependencias.
    
    - Sus métodos (`POST`, `GET`) son muy simples: solo reciben la petición y llaman al servicio (ej. `return usuarioService.crearUsuario(usuario)`).
    

---

### 🚀 Pruebas en Postman

Al probar la nueva arquitectura en Postman, el resultado es el mismo, pero el flujo interno es mucho más limpio:

1. `**POST /usuarios**` (con un JSON): El `Controller` recibe, llama al `Service`, el `Service` llama al `Repository`, el `Repository` añade el usuario a la `List` y le asigna un ID. La respuesta es el usuario creado.

1. `**GET /usuarios**`: Devuelve la lista de usuarios (que incluye el creado en el paso 1).

1. `**GET /usuarios/1**`: Devuelve el usuario específico de la lista.

---

### ✅ Conclusión y Próximos Pasos

- Separar en capas (Controller, Service, Repository) es la práctica estándar para crear APIs **ordenadas, mantenibles y testeables**.

- **Controller** es la puerta (HTTP).

- **Service** es el cerebro (Lógica).

- **Repository** es el guardián (Datos).

- **Próximos Pasos:** El siguiente paso lógico es reemplazar el `UsuarioRepository` de memoria por uno que se conecte a una **base de datos real usando Spring Data JPA**. También se introducirán **DTOs** y **Validaciones**.