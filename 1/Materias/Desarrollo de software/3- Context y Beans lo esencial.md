---
Parent item:
  - "[[Materias/Desarrollo de software/Fundamentos de Spring Boot\\|Fundamentos de Spring Boot]]"
---
### 📦 El Corazón de Spring: Application Context

![[Assets/image 455.png|image 455.png]]

- El **Application Context** (o Contexto de la Aplicación) es el **contenedor central** de Spring.

- Es el verdadero "corazón" de la aplicación.

- Su trabajo principal es **crear, configurar, gestionar y conectar** todos los objetos (Beans) de la aplicación.

- Administra el **ciclo de vida completo** de estos objetos, desde su creación hasta su destrucción.

![[Assets/image 1 47.png|image 1 47.png]]

---

### ⚙️ ¿Qué es un "Bean"?

![[Assets/image 2 44.png|image 2 44.png]]

- Un **Bean** (o "bin", como se menciona en el video) es simplemente un **objeto que es gestionado por Spring**.

- En lugar de que el programador cree instancias manualmente usando `new` (por ejemplo, `new UsuarioService()`), le decimos a Spring que lo haga por nosotros.

- Spring crea esta instancia una sola vez (por defecto) y la reutiliza en cualquier parte de la aplicación que la necesite.

- Cualquier clase puede ser un Bean: un servicio, un repositorio, un controlador, etc.

![[Assets/image 3 38.png|image 3 38.png]]

---

### 🔍 ¿Cómo sabe Spring qué clases convertir en Beans?

![[Assets/image 4 32.png|image 4 32.png]]

La magia ocurre gracias al **Component Scan** (Escaneo de Componentes):

1. **¿Dónde está?** Esta función ya viene incluida dentro de la anotación `@SpringBootApplication` (la que está en la clase principal con el `main`).

1. **¿Qué hace?** Cuando la aplicación arranca, Spring escanea automáticamente el paquete donde está la clase principal y **todos sus sub-paquetes**.

1. **¿Qué busca?** Busca clases marcadas con anotaciones especiales (llamadas estereotipos):
    
    - `@Component`: La anotación genérica para cualquier Bean.
    
    - `@Service`: Para clases de lógica de negocio.
    
    - `@Repository`: Para clases de acceso a datos.
    
    - `@Controller` (o `@RestController`): Para clases que exponen APIs web.
    

1. **¿El resultado?** Cuando encuentra una clase con una de estas anotaciones, Spring la registra automáticamente como un Bean dentro del `ApplicationContext`.

---

### 🔄 El Ciclo de Vida de un Bean

![[Assets/image 5 22.png|image 5 22.png]]

Spring gestiona un ciclo de vida ordenado para cada Bean:

1. **Detección:** Encuentra la clase (vía Component Scan).

1. **Instanciación:** Llama al constructor para crear el objeto.

1. **Inyección:** Le "inyecta" cualquier otra dependencia (Bean) que necesite (se verá en el próximo video).

1. **Inicialización:** Ejecuta métodos de inicialización (por ejemplo, uno marcado con `@PostConstruct`).

1. **Listo para Usar:** El Bean está activo y disponible en el `ApplicationContext`.

1. **Destrucción:** Cuando la aplicación se apaga, Spring llama a los métodos de destrucción y libera los recursos.

![[Assets/image 6 20.png|image 6 20.png]]

---

![[Assets/image 7 19.png|image 7 19.png]]

### 💻 Demostración Práctica del Video

Para demostrar esto, el video realiza dos pruebas:

**1. Creación y Uso de un Bean:**

![[Assets/image 8 16.png|image 8 16.png]]

- Se crea una nueva clase `SaludoService`.

- Se le añade la anotación `@Component`.

- En el método `main`, se obtiene el `ApplicationContext` y se le pide el Bean: `context.getBean(SaludoService.class)`.

- Se llama a un método de `SaludoService` y se imprime el resultado.

- **Resultado:** Funciona, demostrando que Spring detectó, creó y gestionó el objeto `SaludoService` automáticamente.

![[Assets/image 9 13.png|image 9 13.png]]

![[Assets/image 10 10.png|image 10 10.png]]

**2. Demostración del Ciclo de Vida:**

![[Assets/image 11 10.png|image 11 10.png]]

- Se añade un `System.out.println` en el **constructor** de `SaludoService`.

- Se crea un método de inicialización con la anotación `@PostConstruct` y otro `System.out.println`.

- **Resultado en consola:** Se ve claramente el orden:

![[Assets/image 12 8.png|image 12 8.png]]

1. Se imprime el mensaje del **Constructor**.

1. Se imprime el mensaje del método `**@PostConstruct**`.

1. Se imprime el saludo (cuando el Bean ya está listo y se usa).

---

  

### ✅ Resumen y Próximos Pasos

![[Assets/image 13 8.png|image 13 8.png]]

- **Application Context:** Es el contenedor que gestiona todo.

- **Beans:** Son los objetos gestionados por el contenedor.

- **Component Scan:** Es cómo Spring encuentra qué objetos debe gestionar.

- **Beneficio:** No tenemos que preocuparnos por crear o conectar objetos; Spring lo hace por nosotros, resultando en código más ordenado, mantenible y fácil de testear.

- **Próximo Video:** Se explicará la **Inyección de Dependencias**, que es el mecanismo que usa Spring para conectar los Beans entre sí.