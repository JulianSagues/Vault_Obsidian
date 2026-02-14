---
notion-id: 2a5ac26b-dee7-805b-8b02-daea3a81ed92
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - 2a5ac26b-dee7-80da-9597-ebc120e56de4
Blocking: []
Categoria: ""
---
### 📦 El Corazón de Spring: Application Context

![[image 29.png]]

- El **Application Context** (o Contexto de la Aplicación) es el **contenedor central** de Spring.
- Es el verdadero "corazón" de la aplicación.
- Su trabajo principal es **crear, configurar, gestionar y conectar** todos los objetos (Beans) de la aplicación.
- Administra el **ciclo de vida completo** de estos objetos, desde su creación hasta su destrucción.

![[image 30.png]]

---

### ⚙️ ¿Qué es un "Bean"?

![[image 31.png]]

- Un **Bean** (o "bin", como se menciona en el video) es simplemente un **objeto que es gestionado por Spring**.
- En lugar de que el programador cree instancias manualmente usando `new` (por ejemplo, `new UsuarioService()`), le decimos a Spring que lo haga por nosotros.
- Spring crea esta instancia una sola vez (por defecto) y la reutiliza en cualquier parte de la aplicación que la necesite.
- Cualquier clase puede ser un Bean: un servicio, un repositorio, un controlador, etc.

![[image 32.png]]

---

### 🔍 ¿Cómo sabe Spring qué clases convertir en Beans?

![[image 33.png]]

La magia ocurre gracias al **Component Scan** (Escaneo de Componentes):

1. **¿Dónde está?** Esta función ya viene incluida dentro de la anotación `@SpringBootApplication` (la que está en la clase principal con el `main`).
2. **¿Qué hace?** Cuando la aplicación arranca, Spring escanea automáticamente el paquete donde está la clase principal y **todos sus sub-paquetes**.
3. **¿Qué busca?** Busca clases marcadas con anotaciones especiales (llamadas estereotipos):
    - `@Component`: La anotación genérica para cualquier Bean.
    - `@Service`: Para clases de lógica de negocio.
    - `@Repository`: Para clases de acceso a datos.
    - `@Controller` (o `@RestController`): Para clases que exponen APIs web.
4. **¿El resultado?** Cuando encuentra una clase con una de estas anotaciones, Spring la registra automáticamente como un Bean dentro del `ApplicationContext`.

---

### 🔄 El Ciclo de Vida de un Bean

![[image 34.png]]

Spring gestiona un ciclo de vida ordenado para cada Bean:

5. **Detección:** Encuentra la clase (vía Component Scan).
6. **Instanciación:** Llama al constructor para crear el objeto.
7. **Inyección:** Le "inyecta" cualquier otra dependencia (Bean) que necesite (se verá en el próximo video).
8. **Inicialización:** Ejecuta métodos de inicialización (por ejemplo, uno marcado con `@PostConstruct`).
9. **Listo para Usar:** El Bean está activo y disponible en el `ApplicationContext`.
10. **Destrucción:** Cuando la aplicación se apaga, Spring llama a los métodos de destrucción y libera los recursos.

![[image 35.png]]

---

![[image 36.png]]

### 💻 Demostración Práctica del Video

Para demostrar esto, el video realiza dos pruebas:

**1. Creación y Uso de un Bean:**

![[image 37.png]]

- Se crea una nueva clase `SaludoService`.
- Se le añade la anotación `@Component`.
- En el método `main`, se obtiene el `ApplicationContext` y se le pide el Bean: `context.getBean(SaludoService.class)`.
- Se llama a un método de `SaludoService` y se imprime el resultado.
- **Resultado:** Funciona, demostrando que Spring detectó, creó y gestionó el objeto `SaludoService` automáticamente.

![[image 38.png]]

![[image 39.png]]

**2. Demostración del Ciclo de Vida:**

![[image 40.png]]

- Se añade un `System.out.println` en el **constructor** de `SaludoService`.
- Se crea un método de inicialización con la anotación `@PostConstruct` y otro `System.out.println`.
- **Resultado en consola:** Se ve claramente el orden:

![[image 41.png]]

11. Se imprime el mensaje del **Constructor**.
12. Se imprime el mensaje del método `**@PostConstruct**`.
13. Se imprime el saludo (cuando el Bean ya está listo y se usa).

---

### ✅ Resumen y Próximos Pasos

![[image 42.png]]

- **Application Context:** Es el contenedor que gestiona todo.
- **Beans:** Son los objetos gestionados por el contenedor.
- **Component Scan:** Es cómo Spring encuentra qué objetos debe gestionar.
- **Beneficio:** No tenemos que preocuparnos por crear o conectar objetos; Spring lo hace por nosotros, resultando en código más ordenado, mantenible y fácil de testear.
- **Próximo Video:** Se explicará la **Inyección de Dependencias**, que es el mecanismo que usa Spring para conectar los Beans entre sí.