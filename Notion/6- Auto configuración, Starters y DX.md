---
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - "[[Notion/Fundamentos de Spring Boot|Fundamentos de Spring Boot]]"
Blocking: []
Categoria: ""
---
### 🎯 El Problema Antes de Spring Boot

- Configurar un proyecto Java manualmente implicaba horas de trabajo.
- Había que gestionar dependencias en archivos XML enormes.
- Era muy común tener conflictos de versiones e incompatibilidades.
- Se perdía más tiempo preparando el proyecto que escribiendo lógica de negocio.

---

### 💡 La Solución de Spring Boot

Spring Boot elimina esta fricción con dos conceptos clave: Starters y Autoconfiguración.

### 1. Starters (Paquetes de Dependencias)

- **¿Qué son?** Son paquetes de dependencias pre-configurados que incluyen todo lo necesario para una funcionalidad específica.
- En lugar de añadir 10 librerías manualmente, solo añades un "starter".
- **Ejemplos Clave:**
    - `spring-boot-starter-web`: Trae Tomcat embebido, Spring MVC, Jackson (para JSON) y validación.
    - `spring-boot-starter-data-jpa`: Trae Hibernate, Spring Data JPA y un *pool* de conexiones.
    - `spring-boot-starter-security`: Configura autenticación básica y filtros de seguridad.

### 2. Autoconfiguración (La "Magia")

- **¿Qué es?** Es el proceso donde Spring Boot detecta qué *Starters* y librerías tienes en tu proyecto (*classpath*) y **automáticamente configura los Beans necesarios** con valores por defecto.
- **¿Cómo funciona?**
    1. Spring Boot arranca y escanea el *classpath*.
    2. Detecta la presencia de ciertas clases (ej. si encuentra Spring MVC del `starter-web`).
    3. Basado en "condiciones" (ej. `@ConditionalOnClass` o `@ConditionalOnMissingBean`), decide qué Beans crear.
    4. **Ejemplo:** Si detecta `starter-web`, automáticamente configura un servidor **Tomcat embebido** y un `DispatcherServlet` para que puedas empezar a crear controladores de inmediato.
- **Lo mejor:** Si no te gustan los valores por defecto, **siempre puedes sobrescribir la configuración** (como cambiar el puerto en `application.properties`).

---

### 🚀 Herramientas de Productividad (Developer Experience)

Spring Boot también mejora la experiencia de desarrollo con herramientas integradas:

### 1. Spring Boot DevTools

- Es un *Starter* especial (`spring-boot-devtools`) que solo se usa en desarrollo.
- **Característica Principal: Hot Reload**
    - Cuando guardas un cambio en tu código, DevTools **reinicia automáticamente** la aplicación en segundo plano.
    - Esto acelera drásticamente el ciclo de desarrollo, ya que ves tus cambios reflejados en segundos sin tener que reiniciar manualmente.
- También deshabilita cachés (para evitar problemas en desarrollo) y permite *LiveReload* en el navegador.
- **Configuración:** No requiere ninguna, solo añadir la dependencia.

### 2. Logging (Registros)

- Spring Boot trae un sistema de *logging* (registros de consola) configurado por defecto.
- **Control Total:** Puedes controlar el nivel de detalle de los *logs* desde tu archivo `application.properties` o `application.yml`.
- **Ejemplo de configuración:**Properties
`# Poner el logging de mi código en modo DEBUG (muy detallado)
logging.level.com.mi.paquete=DEBUG

# Reducir el "ruido" de Spring, mostrando solo advertencias (WARN)
logging.level.org.springframework.web=WARN`
- Esto da visibilidad clara de lo que pasa en la aplicación sin instalar o configurar nada extra.

---

### 💻 Demostración Práctica

- **Starters y Autoconfig:** Al tener `starter-web`, se crea un `@RestController`. Al correr la app, se ve en la consola que **Tomcat arranca en el puerto 8080** automáticamente. El *endpoint* (`/hello`) funciona sin configurar un servidor.
- **DevTools (Hot Reload):** Con la app corriendo, se modifica el texto que devuelve el controlador (ej. "Hola" por "Hola con Hot Reload"). Se guarda el archivo. Al refrescar el navegador, el cambio aparece **sin haber reiniciado manualmente la aplicación**.
- **Logging:** Se configuran los niveles en `.properties`. Se crea un `Logger` en el controlador y se añaden mensajes (TRACE, DEBUG, INFO, WARN, ERROR). Al llamar al *endpoint*, la consola muestra los *logs* `DEBUG`, `INFO`, `WARN` y `ERROR`, pero **oculta **`**TRACE**` (porque el nivel se fijó en `DEBUG`).

---

### ✅ Conclusión y Fin de la Serie

- **Starters + Autoconfiguración** = Velocidad (proyectos listos en minutos, no horas).
- **DevTools** = Productividad (ciclo de feedback inmediato).
- **Logging** = Visibilidad y control.
- **Próximos Pasos:** Con estos fundamentos, la próxima serie aplicará todo para construir una **API REST** profesional (usando Controladores, Servicios, Repositorios, Validación y Documentación).
