
--dossier 00.1:

Fecha: 18/08/2026

Sistema operativo: W11, Fedora linux y kali linux virtualizado en VMware

Herramientas: Todas las disponibles en Kali Linux, tambien se cuenta con una antena para auditar redes de 2.4Ghz

Estructura de carpetas:

Seguridad-Ofensiva-Avanzada/
└── Operacion-00/
    ├── bitacora.md
    ├── capturas/
    ├── evidencias/
    └── informe/

Hardware del equipo: 24gb de ram, Disco ssd de 512gb y procesador intel i5 13420h.

El equipo cuenta con un dual boot entre w11 y fedora linux. Pero se usara kali linux en VMware desde w11.

Virtualización: 8gb de ram, 4 nucleos y 80gb de espacio virtual.

Terminal: Acceso verificado a la consola de Kali Linux.

Herramientas base comprobadas: Nmap (utilizado previamente para escaneo de puertos), Wireshark (listo para análisis de tráfico) y Netcat.

Problemas técnicos detectados: Ninguno por el momento. La antena Atheros AR9271 y el adaptador de red virtual NAT funcionan correctamente y hay conectividad a Internet para la máquina de trabajo.

Grupo: Somos 5 personas y el nombre hasta el momento es Evil Twin. Trabajaremos de manera conjunta y no habra roles fijos, los roles rotaran según las necesidades del equipo.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
--dossier 00.2:

Fecha: 18/08/2026

1. ¿Por qué la superficie de ataque no se limita únicamente a puertos abiertos?
Porque incluye todos los puntos, caminos, servicios, interfaces, identidades, configuraciones o procesos que podrían ser utilizados para comprometer un sistema o afectar un activo, no solo puertos abiertos.

2. Explicar con un ejemplo cómo una vulnerabilidad puede transformarse en riesgo.
Por ejemplo, una vulnerabilidad como un software desactualizado (debilidad) puede ser explotada por un atacante para acceder a datos sensibles, lo que genera un impacto como la filtración de información, convirtiéndose así en un riesgo.

¿Por qué una práctica ofensiva requiere autorización y alcance definido?
3. Porque solo adquiere valor profesional cuando se realiza dentro de un marco autorizado, con un alcance claro, para evitar daños, respetar límites éticos y legales, y asegurar que la actividad contribuya a mejorar la seguridad.

4. ¿Cuál es la diferencia entre seguridad de la información, seguridad informática y ciberseguridad?
Seguridad de la información protege la información en cualquier soporte (digital, físico, verbal).
Seguridad informática protege sistemas, software y redes.
Ciberseguridad protege el ecosistema digital, incluyendo redes, servicios, identidades y datos frente a amenazas remotas.

5. Mencionar tres activos digitales que podrían existir en una institución educativa.
Bases de datos y archivos.
Usuarios, cuentas y credenciales.
Sistemas operativos y aplicaciones.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

--dossier 00.3:

Fecha: 18/08/2026

1. Diferencia entre amenaza, vulnerabilidad, impacto y riesgo:

Amenaza: Es el actor o evento que tiene la capacidad de causar un daño.  

Vulnerabilidad: Es la debilidad (técnica o humana) que la amenaza puede aprovechar.  

Impacto: Es la consecuencia real o posible si ese evento sucede (por ejemplo, pérdida de datos).  

Riesgo: Es la probabilidad resultante de que una amenaza específica aproveche una vulnerabilidad existente y genere un impacto sobre un activo.

2. Tres activos digitales en una institución educativa y su valor:

Bases de datos académicas (como Sysacad): Tienen un valor crítico porque almacenan información personal, notas y el progreso curricular de todo el alumnado.  

Plataforma de campus virtual (Moodle/Zoom): Su valor radica en la disponibilidad; si se cae, se interrumpe el dictado de clases.  

Credenciales de administradores de red: Tienen un valor alto porque otorgan acceso privilegiado a la infraestructura tecnológica subyacente.

3. Ejemplo de evento que no es un incidente:

Un evento es cualquier hecho observable, como un usuario legítimo iniciando sesión en un sistema o un simple error tipográfico al ingresar una contraseña. No se convierte en incidente porque no compromete la confidencialidad, integridad o disponibilidad del sistema.

4. Ejemplos de controles:

Preventivo: Implementar Autenticación Multifactor (MFA) o configurar reglas estrictas de firewall para evitar accesos no deseados.  

Detectivo: Monitoreo activo de logs o implementación de un SIEM para alertar sobre comportamientos anómalos.  

Correctivo: Restaurar una base de datos desde un backup después de una falla o revocar credenciales comprometidas.

5. Por qué un exploit/payload requiere un entorno autorizado:

Un exploit busca aprovechar una vulnerabilidad real y un payload ejecuta una carga de acción. Fuera de un entorno de laboratorio autorizado, su uso puede alterar configuraciones, interrumpir servicios críticos o constituir un delito.

6. Dos Indicadores de Compromiso (IoC) y su información:Inicios de sesión desde ubicaciones inusuales o fuera de horario (IoC de Identidad): Aportan indicios de que unas credenciales pueden haber sido robadas o adivinadas.  Ejecución de un proceso desconocido o servicio nuevo (IoC de Sistema): Sugiere que un atacante pudo haber instalado malware o establecido persistencia en el equipo.

Escenario de análisis:

Activo: Servidor que aloja contenedores Docker con servicios de automatización de ventas.  

Amenaza: Un ataque automatizado de fuerza bruta desde internet.  

Vulnerabilidad: El puerto SSH expuesto públicamente con contraseñas por defecto y sin MFA.  

Impacto: Toma de control del servidor, exposición de flujos de clientes y caída de la automatización.  

Riesgo: Alto, debido a la facilidad de explotación (vulnerabilidad grave) y las graves consecuencias operativas (impacto crítico).

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

--dossier 00.4:

Fecha: 18/08/2026

1. ¿Por qué una técnica ofensiva requiere autorización expresa antes de ejecutarse?

Porque las técnicas pueden causar daños si se aplican fuera de un marco autorizado.  

Una prueba técnicamente exitosa puede ser inválida, riesgosa o ilícita si se realiza sin permiso o si afecta a terceros no involucrados.

2. Explicar con palabras propias qué significa alcance autorizado.

Es la definición exacta de qué sistemas se pueden evaluar, bajo qué condiciones y hasta dónde puede avanzar la actividad.  

En una evaluación profesional, cualquier objetivo o acción que no esté expresamente incluida se considera fuera de alcance.

3. Mencionar tres acciones que estarían fuera de los límites del laboratorio.

Escanear equipos ajenos de la misma red o de Internet.  

Probar sitios web reales o aplicaciones sin el permiso expreso del titular.  

Publicar capturas, credenciales o resultados de las prácticas fuera del aula.  

4. ¿Por qué el trabajo grupal no elimina la responsabilidad individual?

Porque cada operador debe responder por sus propias acciones técnicas y por el uso que hace de la información obtenida.  

Cada integrante del grupo debe comprender perfectamente qué hizo, por qué lo hizo y cómo quedó documentado.  

5. Indicar dos ejemplos de información que debe tratarse con confidencialidad durante una práctica.

Las credenciales de laboratorio entregadas para realizar la actividad.  

Las evidencias generadas, como capturas de pantalla, logs o salidas de comandos.  

6. Explicar la diferencia entre aprendizaje autorizado y prueba no autorizada.

El aprendizaje autorizado se realiza en un entorno de laboratorio, con una consigna clara, límites definidos y entregables.  

La prueba no autorizada ocurre al ejecutar herramientas sobre un sistema ajeno sin permiso o excediendo el alcance, lo cual puede implicar responsabilidad académica, civil o penal. 

7. ¿Qué debería hacer un estudiante si detecta un acceso no previsto o un comportamiento anómalo durante una operación?

El estudiante debe detener inmediatamente la actividad y comunicar la situación a la cátedra antes de continuar.  

"Me comprometo a realizar las prácticas de seguridad ofensiva contando siempre con la debida autorización, respetando estrictamente el alcance definido por la cátedra para cada laboratorio, y manteniendo la absoluta confidencialidad sobre las credenciales, evidencias y hallazgos obtenidos durante las operaciones."

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
dossier 00.5:

Fecha: 18/08/2026

1. ¿Cuál es la diferencia principal entre Red Team y Blue Team?

El Red Team se encarga de simular adversarios y evaluar las defensas mediante técnicas ofensivas controladas.  

Por el contrario, el Blue Team tiene la función de defender, monitorear, detectar y responder ante esas amenazas.

2. ¿Qué aporta el enfoque Purple Team a una organización?

Aporta la integración del aprendizaje entre el Red Team y el Blue Team.  

Busca que el conocimiento ofensivo fortalezca la defensa, transformando los hallazgos en mejoras concretas de controles y detecciones.

3. ¿Cuál es la función principal de un SOC?

Su función principal es monitorear, analizar y gestionar eventos de seguridad.  

Observa la infraestructura digital para detectar anomalías, investigar alertas y escalar incidentes de forma temprana

4. ¿Qué diferencia existe entre un pentest y un ejercicio Red Team?

Un pentest tiene un alcance técnico delimitado y busca identificar, validar y documentar vulnerabilidades.  

Un ejercicio de Red Team suele tener un alcance más amplio y orientado a objetivos estratégicos, buscando evaluar la capacidad real de defensa frente a una simulación de adversarios.

5. ¿Por qué un CSIRT/CERT necesita coordinar con áreas técnicas, legales y de comunicación?

Porque gestionar un incidente no se limita al análisis técnico.  

Requiere articular acciones de contención, recuperación, comunicación institucional y priorización para manejar el incidente de manera integral.

6. Mencionar dos tareas que podría realizar un analista de seguridad.

Revisar alertas de seguridad.  

Analizar logs, eventos y patrones de comportamiento.

7. ¿Qué es threat intelligence y por qué puede ser útil para priorizar defensas?

Es la recolección, análisis y contextualización de información sobre amenazas, actores, técnicas y vulnerabilidades.

Es útil porque provee conocimiento accionable que ayuda a entender qué buscar, por qué buscarlo y cómo anticipar ataques para mejorar las defensas.

8. Explicar cómo un hallazgo ofensivo podría transformarse en una mejora defensiva.

Si un equipo ofensivo identifica una falla de control o documenta una ruta de ataque, el equipo defensivo puede utilizar esa información para ajustar configuraciones, mejorar las reglas de detección y reducir la superficie de ataque.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

dossier 00.6:

Fecha: 18/08/2026

Estructura de carpetas de la operación 00: C:\Users\yeron\OneDrive\Desktop\SeguridadOfensivaAvanzada\Operacion-00

En capturas estara la evidencia de esto.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

dossier 00.7:

Fecha: 19/08/2026
Operación: 00
Desafío: Web 01 - XSS Reflejado
Categoría: Web
Objetivo: Identificar una vulnerabilidad XSS reflejada y obtener la flag.
Alcance: URL `https://xss01.malbec-defense.com`

Acciones realizadas:
1. Se realizó fuzzing manual enviando una cadena simple (`prueba`) en el parámetro `q` para observar el comportamiento de la aplicación
2. Se inyectaron etiquetas HTML (`<h1>ALERTA</h1>`), confirmando visualmente la falta de sanitización de caracteres especiales (`<` y `>`).
3. Se escaló a un ataque Cross-Site Scripting (XSS) inyectando el payload de JavaScript clásico (`<script>alert(1)</script>`), logrando la ejecución de código en el entorno del cliente.

Herramientas utilizadas:** Navegador web y herramientas de desarrollador (pestañas Elements y Console).

Evidencias: Captura de la inyección exitosa y de la visualización de la caja verde con la flag, guardadas en el directorio `capturas/`.

**Resultado: Desafío validado. Flag obtenida: `flag{lab01_xss_reflected_9f3a7c2b}`.

Conclusión: La aplicación no sanitiza ni valida correctamente la entrada del usuario en el parámetro de búsqueda, lo que permite inyectar código JavaScript arbitrario que el navegador interpreta y ejecuta como legítimo.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Fecha: 19/08/2026
Operación: 01
Desafío: Web 02 – SQL Injection
Categoría: Web
Objetivo: Bypassear el login mediante SQL Injection y obtener la flag.
Alcance: URL https://sql01.malbec-defense.com

Acciones realizadas:
1. Se analizó la consulta SQL del backend proporcionada en la pista: SELECT * FROM users WHERE username='...' AND password='...'.
2. Se probaron inyecciones con comillas simples (admin'-- y admin' OR '1'='1'), pero el backend las escapaba o generaba sintaxis inválida.
3. Se probaron inyecciones con comillas dobles (admin" OR 1=1-- y admin" OR 1=1#), pero el backend envolvía los valores con comillas simples, resultando en consultas como WHERE username='admin" OR 1=1#', donde #' no era un comentario válido.
4. Se inyectó el payload ' OR '1'='1 en el campo Usuario, generando la consulta:
   SELECT * FROM users WHERE username='' OR '1'='1' AND password='123'
   La condición '1'='1' (siempre verdadera) permitió bypassear el login sin credenciales válidas.

Herramientas utilizadas: Navegador web y herramientas de desarrollador (pestaña Network para analizar consultas simuladas).

Evidencias: Capturas de los intentos fallidos (con comillas simples, dobles y comentarios) y la inyección exitosa, guardadas en el directorio capturas/.

Resultado: Desafío validado. Flag obtenida: flag{lab02_sql_login_bypass_c8f12d4a}.

Conclusión: La aplicación no sanitiza ni valida correctamente las entradas en los campos de autenticación, permitiendo inyectar código SQL arbitrario que modifica la lógica de la consulta y autentica al usuario sin credenciales legítimas. Esto es un ejemplo clásico de SQL Injection en cláusulas WHERE.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

