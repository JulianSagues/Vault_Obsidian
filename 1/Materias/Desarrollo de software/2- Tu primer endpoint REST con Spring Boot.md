---
Parent item:
  - "[[Materias/Desarrollo de software/API REST SPRING BOOT\\|API REST SPRING BOOT]]"
---
### 🎯 Conceptos Teóricos Clave

### 1. ¿Qué es un Endpoint REST?

![[Assets/image 458.png|image 458.png]]

- Es básicamente una **URL** (como `/saludo` o `/usuario`) que "escucha" peticiones HTTP.

- Responde a métodos específicos (verbos HTTP) como `GET`, `POST`, etc.

- El servidor procesa la petición y devuelve una respuesta, que casi siempre está en formato **JSON**.

### 2. El Controlador: @RestController

![[Assets/image 1 50.png|image 1 50.png]]

- En Spring Boot, los _endpoints_ viven dentro de clases anotadas con `**@RestController**`.

- Esta anotación es fundamental y le dice a Spring que esta clase expondrá _endpoints_ HTTP.

- Es un atajo que combina dos anotaciones:
    
    1. `**@Controller**`: Marca la clase como un componente de Spring (un Bean) capaz de manejar peticiones web.
    
    1. `**@ResponseBody**`: Esta es la "magia". Le dice a Spring que **convierta automáticamente** lo que sea que el método devuelva (un objeto Java, un `Map`, un `String`) en una respuesta **JSON** y la ponga en el cuerpo (body) de la respuesta HTTP.
    

### 3. Mapeando Peticiones: @GetMapping

![[Assets/image 2 47.png|image 2 47.png]]

- Esta anotación se pone encima de un método dentro de un `@RestController`.

- "Conecta" una URL específica a ese método, pero **solo para peticiones de tipo** `**GET**`.

- Ejemplo: `@GetMapping("/saludo")` hará que cualquier petición `GET` a `http://localhost:8080/saludo` ejecute ese método.

---

### 💻 Demostración Práctica: Paso a Paso

El video muestra cómo crear dos _endpoints_ básicos en un proyecto de Spring Boot (que ya debe tener la dependencia `**spring-boot-starter-web**`).

### 1. Crear el Controlador

Se crea una nueva clase Java llamada `SaludoController`.

Java

![[Assets/image 3 40.png|image 3 40.png]]

`// Importaciones necesarias... import org.springframework.web.bind.annotation.GetMapping; import org.springframework.web.bind.annotation.RestController; import java.util.Map; import java.util.HashMap; @RestController public class SaludoController { // ... métodos aquí ... }`

### 2. Crear Endpoint 1 (Devuelve Texto Plano)

- Se añade un método que devuelve un `String`.

- Se anota con `@GetMapping("/saludo")`.

Java

`@GetMapping("/saludo") public String obtenerSaludo() { return "saludo"; }`

### 3. Crear Endpoint 2 (Devuelve JSON)

- Se añade un método que devuelve un `Map<String, String>`.

- Se anota con `@GetMapping("/usuario")`.

- Spring convertirá este `Map` de Java a un objeto `JSON` automáticamente.

Java

`@GetMapping("/usuario") public Map<String, String> obtenerUsuario() { Map<String, String> usuario = new HashMap<>(); usuario.put("nombre", "José"); usuario.put("apellido", "Douglas"); return usuario; // Spring lo convierte a JSON }`

---

### 🚀 Ejecución y Pruebas con Postman

### 1. Ejecutar la Aplicación

- Se ejecuta el método `main` de la aplicación Spring Boot.

- **Confirmación clave en la consola:** Se debe buscar el log que dice `**Tomcat started on port(s): 8080**`. Esto confirma que el servidor web está corriendo.

### 2. Probar en Postman

1. **Petición al Endpoint 1 (Texto):**
    
    - **Método:** `GET`
    
    - **URL:** `http://localhost:8080/saludo`
    
    - **Resultado (Body):** `saludo`
    
    - **Resultado (Status):** `200 OK`
    

1. **Petición al Endpoint 2 (JSON):**
    
    - **Método:** `GET`
    
    - **URL:** `http://localhost:8080/usuario`
    
    - **Resultado (Body):**JSON
        
        `{ "nombre": "José", "apellido": "Douglas" }`
        
    
    - **Resultado (Status):** `200 OK`
    

---

### ⚠️ Errores Comunes y Soluciones

- **Error: Puerto 8080 ocupado.**
    
    - **Solución:** Abrir `application.properties` y añadir `server.port=8081` (o cualquier otro puerto libre).
    

- **Error: No funciona (Tomcat no arranca).**
    
    - **Solución:** Asegurarse de tener la dependencia `spring-boot-starter-web` en el archivo `build.gradle` o `pom.xml`.
    

- **Error: 404 Not Found en Postman.**
    
    - **Solución:** Verificar que la URL esté bien escrita (ej. `/saludo` y no `/saludar`) y que la aplicación Spring Boot esté corriendo.
    

---

### ✅ Conclusión y Próximos Pasos

- Se aprendió que `@RestController` crea _endpoints_ que devuelven JSON.

- Se usó `@GetMapping` para definir URLs para peticiones `GET`.

- Se probó exitosamente que la aplicación responde en Postman.

- **Próximo Video:** Se explorarán los otros métodos HTTP clave: `POST`, `PUT` y `DELETE`.