### **1.1-Introducción a la Ingeniería de Software**
1) Que es la crisis del software?
	1) Problemas que aparecen en el desarrollo del software a desarrollar, mantener y atender la demanda de nuevas aplicaciones.
2) Cuáles son los mitos del desarrollo del software? Mencione un ejemplo de cada uno
	1) Mitos de la gestión:
		1) Tenemos escritos estándares y procedimientos para construir sw, ¿no le da a la gente todo lo que necesita?
			1) Si el equipo no está entrenado para dichos estándares o no hay supervisión para que estos se sigan, es muy probable que los desarrolladores recaigan en costumbres
		2) Mi gente dispone de las herramientas de desarrollo de sw más avanzadas, después de todo les compramos el hw mas moderno
			1) Un equipo necesita capacitaciones continuas para poder sacarle provecho a las nuevas herramientas
		3) Si se falla en la planificación, se puede añadir más programadores y adelantar el tiempo perdido
			1) Se puede añadir gente pero de manera planificada, ya que en la afirmación no se están teniendo en cuenta tareas con precedencia ni el tiempo de adaptación del nuevo personal.
	2) Mitos del cliente:
		1) Si los requisitos del proyecto cambian continuamente, los cambios pueden acomodarse fácilmente, ya que el software es flexible
			1) A medida que avanza el proyecto realizar un cambio se hace más costoso y complejo progresivamente ya que puede conllevar la reescritura de código entre otras tareas repetidas
	3) Mitos de los desarrolladores:
		1) Una vez que escribamos el programa y hacemos que funcione, nuestro trabajo ha terminado
			1) Una vez que se entrega el programa, resta el 70% del trabajo aprox.
		2) Hasta que no tenga el programa, ejecutándose, realmente no tengo forma de probar su calidad.
			1) Es falso ya que desde un comienzo se pueden aplicar revisiones técnicas y la implementación de testeos unitarios
		3) Lo único que se entrega al terminar el proyecto es el programa funcionando.
			1) Aparte del programa se debe entregar la documentación que respalda este y guías para el mantenimiento
3) Nombre las 3 características del software
	1) El Sw se desarrolla, no se fabrica en un sentido clásico
	2) El Sw no se estropea
	3) La mayoría del sw se construye a medida en vez de ensamblar componentes existentes
4) Defina: Ingeniería de software
	1) Es una disciplina que comprende todos los aspectos de la producción de sw, desde las etapas iniciales de la especificación del sistema, hasta el mantenimiento de este después de que se utiliza.
5) Indique cuál es el objetivo de la ingeniería de software mediante un proceso.
	1)  el objetivo de la ingeniería de software es lograr productos de software de calidad (tanto en su forma final como durante su elaboración), mediante un proceso apoyado por métodos y herramientas.
6) Cuáles son las diferencias entre ingeniería de sistemas, la de software y la de componentes?
	1) La Ingeniería en Sistemas se involucran en las especificaciones del sistema, diseño, definición de su arquitectura, desarrollo , implementación y en la integración para crear el sistema de información final. Se enfoca en la gestión de la información.
	2) La Ingeniería de Software se centra en el desarrollo de software, desde la definición de los requerimientos hasta su mantenimiento.
	3) La Ingeniería de Componentes es una metodología dentro de la Ingeniería de Software que se basa en la creación y reutilización de componentes de software independientes.
7) Cuál es el objetivo de la Ing. De Software basado en la Tecnología multicapa? Y cuál es el fundamento de la ingeniería de software?
	1) El fundamento de la ingeniería de sw es la capa de proceso 
	2) Este proceso define un marco de trabajo para un conjunto de áreas clave 
	3) Desde lo anterior, el objetivo de la ingeniería de sw es lograr productos de sw de calidad, tanto es su forma final como en su elaboración, mediante un proceso apoyado por métodos y herramientas
8) Cuales problemas se identifican en los requerimientos?
	1) Los usuarios no saben lo que quieren
	2) Un sistema tiene muchos usuarios y ninguno tiene una visión de conjunto
	3) No saben cómo hacer más eficiente la operación en su conjunto
	4) No saben qué aportes de su trabajo pueden transformarse en sw
	5) No saben detallar lo que saben de forma precisa
9) Cuáles son las leyes & Lemas de los requerimientos y que indican?
	1) Ley de Ziv
		1) Los requisitos nunca se entienden completamente
	2) Ley de Humphrey
		1) Los usuarios no saben realmente el sw que quieren hasta que lo ven funcionando
	3) Lema de Wegner
		1) Un sistema interactivo nunca puede ser ni especificado ni testeado por completo
10) Qué tipos de requerimientos hay según la función de calidad e indique como se ligan con satisfacción del cliente
	1) Requerimientos normales
		1) Ligado con la satisfacción, si estos requerimientos están presentes, el cliente queda satisfecho
	2) Requerimientos esperados
		1) Su ausencia es motivo de insatisfacción, pueden no estar declarados explícitamente
	3) Requerimientos emocionantes o innovadores
		1) Suelen ser muy satisfactores, va más allá de las expectativas del cliente
11) Nombre qué técnicas de validación de requerimientos pueden usarse
	1) Revisiones de requerimientos 
		1) Los requerimientos son analizados sistemáticamente por un equipo de revisores 
	2) Construcción de prototipos 
		1) Se muestra un modelo ejecutable del sistema a los usuarios finales y a los clientes 
	3) Generación de casos de prueba 
		1) Los requerimientos deben poder probarse, si las pruebas son parte del proceso de validación, se pueden revelar problemas en los requerimientos. 
	4) Análisis de consistencia automática 
		1) Si los requerimientos se expresan como un modelo del sistema en una notación estructurada o formal, para poder hallar inconsistencias.
12) Qué son los requerimientos funcionales, no funcionales y los del dominio? Qué son las restricciones del diseño? (ver cuadro)
	1) Requerimientos funcionales 
		1) Definen funciones del sistema que será capaz de realizar 
	2) Requerimientos no funcionales
		1) Son restricciones o limitaciones de los servicios o funciones ofrecidos por el sistema 
	3) Requerimientos del dominio 
		1) Provienen del dominio de aplicación del sistema y reflejan las características de ese dominio. Pueden ser funcionales o no funcionales 
	4) Restricciones del Diseño 
		1) Son condicionantes existentes para el diseño, sin anticiparlo. Son todos aquellos factores externos o del entorno a los que debe adaptarse el sistema, es decir, son requerimientos adicionales (compatibilidades, seguridad, plazos de tiempo y dinero, normas, estándares, etc.).
13) Cuadro de incumplimiento en los requerimientos funcionales y No funcionales: explíquelo
	1) ![[Preguntas parcial 1.png]]
	2) Los requisitos funcionales especifican qué funciones debe tener un sistema, si estos no se completan, se le quitarán funcionalidades a este, por tanto el sistema será degradado. Los requisitos no funcionales plantean restricciones o limitaciones de las funciones,si estos no se cumplen el sistema será inútil
14) En qué se diferencian los “requisitos de usuario” DRU de los “requisitos del software” ERS?
	1) La principal diferencia entre la DRU y la ERS es que en DRU se emplea lenguaje natural mientras que la ERS emplea modelos o notaciones formales. La diferencia radica en el nivel de detalles de ambos documentos
15) Tipos de requerimientos según la función de calidad: definición, satisfacción del cliente, ejemplos
	1) Requerimientos Normales> ligados con la satisfacción
		1) Ej. Tipos de gráficos, funciones específicas del sistema, y niveles de rendimientos definidos.
	2) Requerimientos esperados> el cliente puede no declararlos explícitamente y su ausencia es motivo de insatisfacción
		1) Ej. Fácil interacción, operación general correcta y confiable, facilidad de instalación
	3) Requerimientos Emocionantes o Innovadores>suelen ser muy satisfactorias
		1) Ej. Pantallas sensible al tacto, correo de voz visual.
16) Que debe especificar un proceso de Ingeniería de software?
	1) Secuencia de actividades 
	2) Productos que deben crearse 
	3) Asignación de tareas 
	4) Criterios para controlar el proceso
17) Nombre 5 características de los productos de sw
	1) Mantenible 
	2) Confiabilidad
	3) Eficiencia
	4) Utilización adecuada (el sw debe contar con una interfaz de usuario adecuada y su documentación) 
	5) Entendible 
	6) Visible 
	7) Soportable 
	8) Aceptable 
	9) Seguridad 
	10) Robusto 
	11) Escalable 
	12) Rápido
18) Cuáles son los retos de la Ingeniería de software? Explíquelos brevemente
	1) De lo heredado: 
		1) El reto es mantener y actualizar el sw tal que se eviten los costos excesivos y que los servicios esenciales del negocio sigan funcionando 
	2) De la heterogeneidad: 
		1) Desarrollar técnicas para construir un sw confiable, que sea lo suficientemente flexible 
	3) De la entrega: 
		1) El resto es reducir los tiempos de entrega para sistemas grandes y complejos sin comprometer la calidad del sistema
19) En que consiste en la Interfaz Usuaria: calidad percibida, calidad externa y calidad en el uso?
	1) Calidad percibida: Conjunto de características de un producto que aportan gran satisfacción a unos usuarios específicos. 
	2) Calidad externa: Instante en el cual un producto satisface las necesidades establecidas e implícitas cuando este es un utilizado bajo ciertas condiciones específicas.
	3) Calidad en el uso: La efectividad, eficiencia y satisfacción con el cuál ciertos usuarios pueden alcanzar ciertas metas en entornos concretos
20) Defina la usabilidad e indique a que hace referencia?
	1) Es la forma en la que se alcanzan los objetivos con efectividad, eficiencia y satisfacción. Esta hace referencia a la rapidez y facilidad con que las personas llevan a cabo sus tareas propias a través del uso del producto objeto de interés.
21) A qué hace referencia la usabilidad y en que puntos descansa?
	1) La usabilidad, hace referencia, a la rapidez y facilidad con que las personas llevan cabo sus tareas propias a través del uso del producto objeto de interés, idea que descansa en cuatro puntos:
		1)  Una aproximación al usuario: enfocarse en los usuarios. Se tienen que conocer, entender y trabajar con las personas que representan a los usuarios actuales o potenciales del producto.
		2) Un amplio conocimiento del contexto de uso: Las personas utilizan los productos para incrementar su propia productividad. Un producto se considera fácil de aprender y usar en términos del tiempo que toma el usuario para llevar a cabo su objetivo, el número de pasos que tiene que realizar para ello, y el éxito que tiene en predecir la acción apropiada para llevar a cabo
		3) El producto ha de satisfacer las necesidades del usuario: Los usuarios son gente ocupada intentando llevar a cabo una tarea. Se va a relacionar usabilidad con productividad y calidad.
		4) Son los usuarios, y no los diseñadores y los desarrolladores, los que determinan cuando un producto es fácil de usar
22) Cuándo se considera la usabilidad?
	1) Independientemente del método de desarrollo del sistema, debe considerarse a lo largo de todo el proyecto, para así no hacer cambios drásticos en etapas futuras del sistema
23) Cuales son las ventajas de las GUI? (Somerville págs. 327 a 347)
	1) Son relativamente fáciles de aprender y utilizar: los usuarios que no tienen experiencia previa en computación pueden aprender a usar la interfaz tras una breve sesión de capacitación.  
	2) Permiten trabajar con pantallas múltiples (ventanas): el usuario puede pasar de una tarea a otra sin perder de vista la información generada durante la primera actividad. 
	3) Acceso rápido e interacción inmediata: es posible interactuar con rapidez y acceder de manera directa a cualquier punto de la pantalla.
24) Nombre los principios de diseño de interfaces usuarias (Somerville)
	1) Familiaridad del usuario: La interfaz debe utilizar términos y conceptos tomados de la experiencia de las personas que más utilizan el sistema.  
	2) Consistencia: Siempre que sea posible, la interfaz debe ser consistente; es decir, las operaciones comparables se activan de la misma forma.  
	3) Mínima sorpresa: El comportamiento del sistema no debe provocar sorpresas a los usuarios (acciones comparables deben tener efectos comparables).  
	4) Recuperabilidad (o Recuperación): La interfaz debe incluir mecanismos para permitir a los usuarios recuperarse de los errores (por ejemplo, confirmación de acciones destructivas o función para deshacer).  
	5) Guía al usuario (o Asistencia al usuario): Cuando ocurren errores, la interfaz debe proveer retroalimentación significativa y características de ayuda sensible al contexto.  
	6) Diversidad de usuarios: La interfaz debe proveer características de interacción apropiadas para los diferentes tipos de usuarios del sistema (desde novatos hasta expertos, e incluso contemplando discapacidades).
25) Cuales son los 5 estilos primarios de interaccion con el usuario según Shneiderman? (Somerville)
	1) Manipulación directa: El usuario interactúa con objetos en la pantalla 
	2) Selección de menús: El usuario selecciona un comando preestablecido
	3) Rellenado de formularios: El usuario completa un formulario
	4) Lenguaje de comandos: El usuario utiliza comandos especiales y parámetros 
	5) Lenguaje natural: El usuario se comunica naturalmente
26) Cuales son los 5 lineamientos claves para la utilización efectiva del color en las interfaces de usuario? (Somerville)
	1) Limitar el número de colores y respetar aquellos colores ya definidos
	2) Utilizar colores diferentes para denotar cambios de estado 
	3) Utilizar colores para apoyar la tarea del usuario 
	4) Utilizar colores de forma consistente y uniforme 
	5) Elegir cuidadosamente los pares de colores
27) En que consiste la evaluación de la interfaz? Que comprende? (Somerville)
	1) Proceso en el cual se pone a prueba el rendimiento de la interfaz y cómo se utiliza con el fin de verificar que se cumplen los requerimientos del usuario
### 1.2-Disciplinas de la ingeniería de **software**
1) Identifique los objetivos a tener en cuenta cuando queremos implementar u optar por un servicio
de ingeniería de software
2) Nombre las disciplinas de software usadas por un ingeniero de software
3) Qué es un principio?
4) Nombre los siete principios de la ingeniería de software y analice por qué existe cada principio (el
para qué o por qué)
5) Defina qué es Clean Code? Qué reduce, evita y qué prioriza?
6) Cuáles son las buenas prácticas de Codigo Limpio? Describalas brevemente. Piensa en un
ejemplo.
7) Nombre y explique las reglas vinculadas al “Código limpio” (90/90, Navaja de Oakham, YAGNI,
DRY, ley de Demeter, optimización prematura, etc.)