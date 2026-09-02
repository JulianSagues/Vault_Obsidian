9### **1.1-Introducción a la Ingeniería de Software**
1) **Que es la crisis del software?**
	1) Problemas que aparecen en el desarrollo del software a desarrollar, mantener y atender la demanda de nuevas aplicaciones.

2) **Cuáles son los mitos del desarrollo del software? Mencione un ejemplo de cada uno**
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

3) **Nombre las 3 características del software**
	1) El Sw se desarrolla, no se fabrica en un sentido clásico
	2) El Sw no se estropea
	3) La mayoría del sw se construye a medida en vez de ensamblar componentes existentes

4) **Defina: Ingeniería de software**
	1) Es una disciplina que comprende todos los aspectos de la producción de sw, desde las etapas iniciales de la especificación del sistema, hasta el mantenimiento de este después de que se utiliza.

5) **Indique cuál es el objetivo de la ingeniería de software mediante un proceso.**
	1)  el objetivo de la ingeniería de software es lograr productos de software de calidad (tanto en su forma final como durante su elaboración), mediante un proceso apoyado por métodos y herramientas.

6) **Cuáles son las diferencias entre ingeniería de sistemas, la de software y la de componentes?**
	1) La Ingeniería en Sistemas se involucran en las especificaciones del sistema, diseño, definición de su arquitectura, desarrollo , implementación y en la integración para crear el sistema de información final. Se enfoca en la gestión de la información.
	2) La Ingeniería de Software se centra en el desarrollo de software, desde la definición de los requerimientos hasta su mantenimiento.
	3) La Ingeniería de Componentes es una metodología dentro de la Ingeniería de Software que se basa en la creación y reutilización de componentes de software independientes.

7) **Cuál es el objetivo de la Ing. De Software basado en la Tecnología multicapa? Y cuál es el fundamento de la ingeniería de software?**
	1) El fundamento de la ingeniería de sw es la capa de proceso 
	2) Este proceso define un marco de trabajo para un conjunto de áreas clave 
	3) Desde lo anterior, el objetivo de la ingeniería de sw es lograr productos de sw de calidad, tanto es su forma final como en su elaboración, mediante un proceso apoyado por métodos y herramientas

8) **Cuales problemas se identifican en los requerimientos?**
	1) Los usuarios no saben lo que quieren
	2) Un sistema tiene muchos usuarios y ninguno tiene una visión de conjunto
	3) No saben cómo hacer más eficiente la operación en su conjunto
	4) No saben qué aportes de su trabajo pueden transformarse en sw
	5) No saben detallar lo que saben de forma precisa

9) **Cuáles son las leyes & Lemas de los requerimientos y que indican?**
	1) Ley de Ziv
		1) Los requisitos nunca se entienden completamente
	2) Ley de Humphrey
		1) Los usuarios no saben realmente el sw que quieren hasta que lo ven funcionando
	3) Lema de Wegner
		1) Un sistema interactivo nunca puede ser ni especificado ni testeado por completo

10) **Qué tipos de requerimientos hay según la función de calidad e indique como se ligan con satisfacción del cliente**
	1) Requerimientos normales
		1) Ligado con la satisfacción, si estos requerimientos están presentes, el cliente queda satisfecho
	2) Requerimientos esperados
		1) Su ausencia es motivo de insatisfacción, pueden no estar declarados explícitamente
	3) Requerimientos emocionantes o innovadores
		1) Suelen ser muy satisfactores, va más allá de las expectativas del cliente

11) **Nombre qué técnicas de validación de requerimientos pueden usarse**
	1) Revisiones de requerimientos 
		1) Los requerimientos son analizados sistemáticamente por un equipo de revisores 
	2) Construcción de prototipos 
		1) Se muestra un modelo ejecutable del sistema a los usuarios finales y a los clientes 
	3) Generación de casos de prueba 
		1) Los requerimientos deben poder probarse, si las pruebas son parte del proceso de validación, se pueden revelar problemas en los requerimientos. 
	4) Análisis de consistencia automática 
		1) Si los requerimientos se expresan como un modelo del sistema en una notación estructurada o formal, para poder hallar inconsistencias.

12) **Qué son los requerimientos funcionales, no funcionales y los del dominio? Qué son las restricciones del diseño? (ver cuadro)**
	1) Requerimientos funcionales 
		1) Definen funciones del sistema que será capaz de realizar 
	2) Requerimientos no funcionales
		1) Son restricciones o limitaciones de los servicios o funciones ofrecidos por el sistema 
	3) Requerimientos del dominio 
		1) Provienen del dominio de aplicación del sistema y reflejan las características de ese dominio. Pueden ser funcionales o no funcionales 
	4) Restricciones del Diseño 
		1) Son condicionantes existentes para el diseño, sin anticiparlo. Son todos aquellos factores externos o del entorno a los que debe adaptarse el sistema, es decir, son requerimientos adicionales (compatibilidades, seguridad, plazos de tiempo y dinero, normas, estándares, etc.).

13) **Cuadro de incumplimiento en los requerimientos funcionales y No funcionales: explíquelo**
	1) ![[Preguntas parcial 1.png]]
	2) Los requisitos funcionales especifican qué funciones debe tener un sistema, si estos no se completan, se le quitarán funcionalidades a este, por tanto el sistema será degradado. Los requisitos no funcionales plantean restricciones o limitaciones de las funciones,si estos no se cumplen el sistema será inútil

14) **En qué se diferencian los “requisitos de usuario” DRU de los “requisitos del software” ERS?**
	1) La principal diferencia entre la DRU y la ERS es que en DRU se emplea lenguaje natural mientras que la ERS emplea modelos o notaciones formales. La diferencia radica en el nivel de detalles de ambos documentos

15) **Tipos de requerimientos según la función de calidad: definición, satisfacción del cliente, ejemplos**
	1) Requerimientos Normales> ligados con la satisfacción
		1) Ej. Tipos de gráficos, funciones específicas del sistema, y niveles de rendimientos definidos.
	2) Requerimientos esperados> el cliente puede no declararlos explícitamente y su ausencia es motivo de insatisfacción
		1) Ej. Fácil interacción, operación general correcta y confiable, facilidad de instalación
	3) Requerimientos Emocionantes o Innovadores>suelen ser muy satisfactorias
		1) Ej. Pantallas sensible al tacto, correo de voz visual.

16) **Que debe especificar un proceso de Ingeniería de software?**
	1) Secuencia de actividades 
	2) Productos que deben crearse 
	3) Asignación de tareas 
	4) Criterios para controlar el proceso

17) **Nombre 5 características de los productos de sw**
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

18) **Cuáles son los retos de la Ingeniería de software? Explíquelos brevemente**
	1) De lo heredado: 
		1) El reto es mantener y actualizar el sw tal que se eviten los costos excesivos y que los servicios esenciales del negocio sigan funcionando 
	2) De la heterogeneidad: 
		1) Desarrollar técnicas para construir un sw confiable, que sea lo suficientemente flexible 
	3) De la entrega: 
		1) El resto es reducir los tiempos de entrega para sistemas grandes y complejos sin comprometer la calidad del sistema

19) **En que consiste en la Interfaz Usuaria: calidad percibida, calidad externa y calidad en el uso?**
	1) Calidad percibida: Conjunto de características de un producto que aportan gran satisfacción a unos usuarios específicos. 
	2) Calidad externa: Instante en el cual un producto satisface las necesidades establecidas e implícitas cuando este es un utilizado bajo ciertas condiciones específicas.
	3) Calidad en el uso: La efectividad, eficiencia y satisfacción con el cuál ciertos usuarios pueden alcanzar ciertas metas en entornos concretos

20) **Defina la usabilidad e indique a que hace referencia?**
	1) Es la forma en la que se alcanzan los objetivos con efectividad, eficiencia y satisfacción. Esta hace referencia a la rapidez y facilidad con que las personas llevan a cabo sus tareas propias a través del uso del producto objeto de interés.

21) **A qué hace referencia la usabilidad y en que puntos descansa?**
	1) La usabilidad, hace referencia, a la rapidez y facilidad con que las personas llevan cabo sus tareas propias a través del uso del producto objeto de interés, idea que descansa en cuatro puntos:
		1)  Una aproximación al usuario: enfocarse en los usuarios. Se tienen que conocer, entender y trabajar con las personas que representan a los usuarios actuales o potenciales del producto.
		2) Un amplio conocimiento del contexto de uso: Las personas utilizan los productos para incrementar su propia productividad. Un producto se considera fácil de aprender y usar en términos del tiempo que toma el usuario para llevar a cabo su objetivo, el número de pasos que tiene que realizar para ello, y el éxito que tiene en predecir la acción apropiada para llevar a cabo
		3) El producto ha de satisfacer las necesidades del usuario: Los usuarios son gente ocupada intentando llevar a cabo una tarea. Se va a relacionar usabilidad con productividad y calidad.
		4) Son los usuarios, y no los diseñadores y los desarrolladores, los que determinan cuando un producto es fácil de usar

22) **Cuándo se considera la usabilidad?**
	1) Independientemente del método de desarrollo del sistema, debe considerarse a lo largo de todo el proyecto, para así no hacer cambios drásticos en etapas futuras del sistema

23) **Cuales son las ventajas de las GUI? (Somerville págs. 327 a 347)**
	1) Son relativamente fáciles de aprender y utilizar: los usuarios que no tienen experiencia previa en computación pueden aprender a usar la interfaz tras una breve sesión de capacitación.  
	2) Permiten trabajar con pantallas múltiples (ventanas): el usuario puede pasar de una tarea a otra sin perder de vista la información generada durante la primera actividad. 
	3) Acceso rápido e interacción inmediata: es posible interactuar con rapidez y acceder de manera directa a cualquier punto de la pantalla.

24) **Nombre los principios de diseño de interfaces usuarias (Somerville)**
	1) Familiaridad del usuario: La interfaz debe utilizar términos y conceptos tomados de la experiencia de las personas que más utilizan el sistema.  
	2) Consistencia: Siempre que sea posible, la interfaz debe ser consistente; es decir, las operaciones comparables se activan de la misma forma.  
	3) Mínima sorpresa: El comportamiento del sistema no debe provocar sorpresas a los usuarios (acciones comparables deben tener efectos comparables).  
	4) Recuperabilidad (o Recuperación): La interfaz debe incluir mecanismos para permitir a los usuarios recuperarse de los errores (por ejemplo, confirmación de acciones destructivas o función para deshacer).  
	5) Guía al usuario (o Asistencia al usuario): Cuando ocurren errores, la interfaz debe proveer retroalimentación significativa y características de ayuda sensible al contexto.  
	6) Diversidad de usuarios: La interfaz debe proveer características de interacción apropiadas para los diferentes tipos de usuarios del sistema (desde novatos hasta expertos, e incluso contemplando discapacidades).

25) **Cuales son los 5 estilos primarios de interaccion con el usuario según Shneiderman? (Somerville)**
	1) Manipulación directa: El usuario interactúa con objetos en la pantalla 
	2) Selección de menús: El usuario selecciona un comando preestablecido
	3) Rellenado de formularios: El usuario completa un formulario
	4) Lenguaje de comandos: El usuario utiliza comandos especiales y parámetros 
	5) Lenguaje natural: El usuario se comunica naturalmente

26) **Cuales son los 5 lineamientos claves para la utilización efectiva del color en las interfaces de usuario? (Somerville)**
	1) Limitar el número de colores y respetar aquellos colores ya definidos
	2) Utilizar colores diferentes para denotar cambios de estado 
	3) Utilizar colores para apoyar la tarea del usuario 
	4) Utilizar colores de forma consistente y uniforme 
	5) Elegir cuidadosamente los pares de colores

27) **En que consiste la evaluación de la interfaz? Que comprende? (Somerville)**
	1) Proceso en el cual se pone a prueba el rendimiento de la interfaz y cómo se utiliza con el fin de verificar que se cumplen los requerimientos del usuario

### 1.2-Disciplinas de la ingeniería de **software**
1) **Identifique los objetivos a tener en cuenta cuando queremos implementar u optar por un servicio**
	1) Diseñar programas adaptados a las necesidades y exigencias de los clientes 
	2) Desarrollar, desplegar, implementar y mantener los sistemas 
	3) Solucionar problemas de programación 
	4) Estar presente en todas las fases del ciclo de vida de un producto 
	5) Estimar y contabilizar los costes de un proyecto y evaluar los tiempos de desarrollo 
	6) Realizar el seguimiento del presupuesto y cumplir los plazos de entrega. 
	7) Liderar equipos de trabajo de desarrollo de software de ingeniería de software

2) **Nombre las disciplinas de software usadas por un ingeniero de software**
	1) Modelado de negocios 
	2) Requerimientos 
	3) Análisis y diseño 
	4) Pruebas 
	5) Administración y configuración del cambio
	6) Administración de proyectos 
	7) Ambientes 
	8) Implementación

3) **Qué es un principio?**
	1) Un principio es una ley importante y es requerida en un sistema de pensamiento.

4) **Nombre los siete principios de la ingeniería de software y analice por qué existe cada principio (el para qué o por qué)**
	1) La razón que exista todo 
		1) ¿Esto agrega valor real al sistema?
	2) Mantenerlo sencillo
		1) Algo sencillo pero bien codificado hace el sw más fácil de usar y mantener 
	3) Mantener la visión 
		1) Es importante tener claro a donde se tiene que llegar para dar las pautas necesarias 
	4) Otros consumirán lo que usted produce 
		1) El código que creamos va a ser leído y mantenido por otras personas, hay que construir el sistema pensando en la audiencia 
	5) Abrace el futuro 
		1) Tener en cuenta el rápido avance de la tecnología para un sw mantenible en el tiempo 
	6) Planee por adelantado la reutilización 
		1) Reutilizar código es beneficioso, pero es un gran reto tener un alto nivel de este, por lo que es muy importante la planificación inicial 
	7) Pensar
		1) No hay que largarse a trabajar de una sin antes haber pensado cómo se va a trabajar

5) **Defina qué es Clean Code? Qué reduce, evita y qué prioriza?**
	1) El código limpio o sostenible es aquel que es fácil de entender por un humano y, por lo tanto, fácil de modificar, extender y probar en el tiempo
	2) Un código limpio evita complejidades innecesarias y se organiza de manera que su propósito sea evidente al leerlo. Esto implica nombrar variables y funciones de forma descriptiva, mantener funciones cortas y enfocadas en una sola tarea, y estructurar el código de manera lógica y coherente.
	3) Su valor radica en que reduce la probabilidad de errores y facilita la colaboración en proyectos de software. Un código claro y bien organizado es más fácil de modificar, actualizar y depurar, lo que ahorra tiempo y recursos a largo plazo. Además, fomenta la creación de software más robusto y adaptable a cambios futuros.

6) **Cuáles son las buenas prácticas de Codigo Limpio? Describalas brevemente. Piensa en un ejemplo.**
	1) La legibilidad es clave 
		1) Un código claro y comprensible facilita el mantenimiento y el trabajo en equipo. 
		2) Usar nombres descriptivos en variables y funciones para que su propósito sea evidente sin comentarios adicionales. 
	2) Funciones pequeñas y específicas 
		1) Las funciones deben realizar una sola tarea bien definida para mejorar su reutilización y prueba. 
		2) Dividir una función compleja en varias funciones más pequeñas con responsabilidades específicas. 
	3) Nombres significativos 
		1) Los nombres de variables, funciones y clases deben reflejar su propósito.
		2) En lugar de XW19, usar cantidadProductosVendidos para mejorar la claridad. 
	4) Eliminar código muerto 
		1) Eliminar código innecesario o no utilizado para reducir la complejidad y evitar confusiones. 
		2) Eliminar funciones obsoletas que ya no se llaman en el sistema.
	5) Principio de la menor sorpresa 
		1) El código debe comportarse de manera predecible y seguir convenciones establecidas. 
		2) Respetar los estándares de nombres y estructuras comunes en el lenguaje de programación utilizado. 
	6) Modularidad y encapsulamiento 
		1) Organizar el código en componentes independientes y proteger detalles internos. 
		2) Crear módulos separados para lógica de negocio y acceso a datos, evitando la dependencia directa. 
	7) Escribir pruebas 
		1) Las pruebas unitarias garantizan que el código funciona correctamente y previenen errores. 
		2) Implementar pruebas automáticas para verificar la funcionalidad de cada componente antes de su despliegue. 
	8) Refactorización continua 
		1) Mejorar el código sin alterar su comportamiento externo para mantener la calidad a largo plazo. 
		2) Simplificar una función compleja eliminando redundancias y mejorando su estructura

7) **Nombre y explique las reglas vinculadas al “Código limpio” (90/90, Navaja de Oakham, YAGNI, DRY, ley de Demeter, optimización prematura, etc.)**
	1) Reglas vinculadas al código limpio: 
		1) Regla del noventa-noventa 90/90: 
			1) El primer 90% del código ocupa el 90% del tiempo de desarrollo, el 10% restante ocupa otro 90% de tiempo de desarrollo 
			2) Esto quiere decir que no hay que subestimar el ultimo 10% ya que puede ser extremadamente laborioso y consumir tanto tiempo como el primer 90% 
		2) La navaja de Oakham 
			1) Las entidades no deben multiplicarse sin necesidad 
			2) Siempre es importante pensar primero en los beneficios de añadir otro método/clase/herramienta/proceso 
		3) No lo vas a necesitas YAGNI
			1) Implementar solo lo que necesitamos, y más tarde, si es necesario, extendemos una funcionalidad o creamos una nueva 
		4) Diseño grande por adelantado
			1) No empezar a desarrollar una funcionalidad sin primero pensar en la arquitectura de la aplicación y diseñar todo el sistema hasta detalles 
		5) No te repitas DRY
			1) No repetir lo mismo en diferentes lugares 
			2) Reutilización de código 
		6) Evitar la optimización prematura 
			1) No llevar a cabo la optimización en las primeras etapas del desarrollo, puede hacer más daño que bien 
	2) Principio del menor asombro 
		1) El código debe ser intuitivo y obvio, no intentar sorprender a otro desarrollador cuando revise el código
		2) Evitar los efectos secundarios, y si no se puede, documentarlos.
	3) Ley de Demeter
		1) Dividir las áreas de responsabilidad entre las clases y encapsular la lógica dentro de una clase, método o estructura. 
		2) Aplicando esto, la aplicación se vuelve más flexible, comprensible y fácil de mantener

8) **Explique en que consiste SOLID, cuáles son y para qué sirven estos principios. Arme un cuadro de Clean Code y SOLID, indicando: definción, que aseguran, que cuida (marco), objetivo central, alcance y beneficios.**
	1) La aplicación de los principios SOLID está muy relacionada con la comprensión y el uso de patrones de diseño, que nos permitirán mantener una alta cohesión y un bajo acoplamiento de sw. Se debe: 
		1) Crear un sw eficaz 
		2) Escribir código limpio y flexible a cambios 
		3) Permitir escalabilidad
	2) ![[Preguntas parcial 1-1.png]]
	
9) **En qué ayudan las buenas prácticas?**
	1) Cuando se aplican juntos, estos principios ayudan a un desarrollador a crear un código que es fácil de mantener y extender en el tiempo. 
	2) Las buenas prácticas que pueden ayudar a escribir un mejor código: más limpio, mantenible y escalable

10) **Defina el Espaguetti Code. Dé ejemplo de porqué está escrito mal el código**
	1) El código espagueti se refiere a una estructura de código desorganizada y difícil de seguir, donde la lógica se retuerce de forma impredecible, lo que dificulta su comprensión y mantenimiento.
	2) No está asociado a un lenguaje o entorno en particular, el problema es “COMO ESTÁ ESCRITO EL CODIGO”, surgido de una o más situaciones como por ejemplo:
		1) Desarrollo rápido o bajo presión, improvisando y sacrifican la calidad del código por la velocidad, llevando a soluciones rápidas y hacks (soluciones rápidas y sucias). 
		2) Falta de experiencia, diseñando código no escalable ni adaptable. 
		3) Añadir nuevas funciones sin refactorizar, puede generar dependencias complejas y una lógica difícil de gestionar. 
		4) Falta de planificación, codificar sin haber pensado en la arquitectura ni diseño. 
		5) Mala comunicación en los equipos, la falta de comunicación o de prácticas de codificación estandarizadas, puede resultar en bases de código inconsistentes y desordenadas. 
		6) Legacy Code o Código Heredado: el código se escribió para abordar algún caso excepcional que no se conocía durante el diseño/desarrollo original.

11) **Nombre las características comunes del Código espagueti**
	1) Funciones largas y monolíticas
	2) Falta de control
	3) Lógica duplicada
	4) Exceso de variables globales

12) **Nombre/identifique soluciones o estrategias comprobadas para prevenir y corregir el código espagueti:**
	1) Estrategias comprobadas para prevenir y corregir el código espagueti:
		1) Seguir las mejores prácticas
			1) Adoptar estándares y directrices de codificación (Ej. PHP: PSR, Java: Java Code Conventions) 
			2) Utilizar convenciones de: Nomenclatura (Ej. En Java: clases en PascalCase, métodos y variables en camelCase), Indentación (4 espacios), Comentarios (Ej: Java: usar Javadoc /…*/, en .Net: /// para XML ), Componentes (Ej. En ReactJS: uso de funciones en lugar de clases), 
		3) Aprovechar patrones establecidos 
			1) Usar MVC, Singleton o Factory para estructurar el código de forma lógica. 
		4) Refactorizar periódicamente 
			1) Para limpiar, clarificar, estructurar, simplificar y eliminar la lógica redundante, sin cambiar su funcionalidad.
		5) Utilizar el control de versiones 
			1) Para garantizan el seguimiento de los cambios, lo que facilita la reversión a un estado limpio. 
		6) Priorizar las revisiones de código 
			1) Las revisiones por pares ayudan a identificar y solucionar posibles problemas de forma temprana, mejorando la calidad general del código. 
		7) Aprovechar la programación modular 
			1) Dividir el código en módulos pequeños, reutilizables e independientes para mejorar la legibilidad y el mantenimiento. 
		8) Invertir en capacitación 
			1) Capacitar a tu equipo sobre las mejores prácticas, los principios de diseño y la importancia de una codificación limpia.

13) **Por qué es complejo el software? Mencione los motivos**
	1) ¨La complejidad del SW es una propiedad esencial y no accidental¨ 
		1) Complejidad accidental: Se debe a la manera en que intentamos solucionar el problema 
		2) Complejidad esencial: Es inherente al problema en sí mismo

14) **Qué se puede proponer para mejorar el desarrollo de software?**
	1) Aplicar métodos, técnicas y herramientas de desarrollo 
	2) Adoptar estándares de desarrollo
	3) Utilizar la experiencia acumulada 
	4) Documentación 
	5) Aplicar estándares, lecciones aprendidas y buenas prácticas

15) **En que consiste el Desarrollo Distribuido o Global de Sw (DGS)? Qué escenarios puede tener? (ver cuadro)**
	1) El desarrollo distribuido de Sw se da cuando los stakeholders del proyecto se encuentran distribuidos entre varios sitios remotos. Este se da con sub equipos y equipos en lugares geográficos distintos, haciendo uso de las tecnologías de comunicación 
	2) El modelo del global delivery hace referencia a realizar el delivery en procesos de negocio. Se basa en una estrategia horaria, contando con oficinas a lo largo del planeta para dar soporte o estar funcionando las 24 horas. Esto se consigue gracias al bajo costo de las comunicaciones y teniendo los modelos bajo el mismo gerenciamiento y usando los mismos procesos. 
	3) Escenarios: 
		1) Mismo lugar 
		2) Mismo país 
		3) Otro país

16) **Nombra por lo menos 3 desafíos del Desarrollo Global de Sw**
	1) Diferencias culturales y prácticas de negocio del cliente 
	2) Participación apropiada de usuarios y personal de campo 
	3) Conciencia de trabajo local y comunicación informal 
	4) Relación de confianza laboral 
	5) Gestión de conflictos y discusiones abiertas de interés 
	6) Entendimiento común de los requisitos 
	7) Reuniones efectivas 
	8) Demoras

17) **Cuáles son las características más importantes donde hay trabajo remoto…**
	1) Dispersión geográfica, cultural y escala de valores 
	2) Diferentes culturas de empresas, husos horarios, idiomas, procesos de trabajo, entendimiento de roles, formas de trabajo, experiencias, visiones del producto/servicio, etc.

18) **Qué es el outsourcing y porqué se recurre a él? Cuál es el punto clave?**
	1) Es un sistema de contratación en el que una empresa recurre a otra para realizar tareas especializadas. La organización confía la ejecución de ciertas actividades a proveedores estrenos que son expertos en su campo

19) **Cuáles son los dos tipos diferentes de outsourcing?**
	1) Total: 
		1) Se transfieren las infraestructuras y el personal al proveedor y se hace cargo de todas las fases de implementación y asume el riesgo de la propiedad de los recursos
	2) Selectivo: 
		1) Con este tipo se permite al cliente cubrir ciertas necesidades minimizando riesgos respecto al outsourcing total.

20) **Indique de qué se tratan los modelos de delivery global (Ver cuadro comparativo, su término, tener en cuenta la descripción y ubicación geográfica)**
	1) ONSITE 
		1) Se trabaja físicamente en las instalaciones del cliente
	2) ONSHORE 
		1) El trabajo se subcontrata a empresas dentro del mismo país
	3) OFFSHORE 
		1) El trabajo se envía a empresas en otros países, generalmente con costos laborales menores 
	4) NEARSHORE 
		1) Se subcontrata a países vecinos o con zonas horarias similares 
	5) OFFSITE 
		1) El personal trabaja fuera de las instalaciones del cliente, puede ser dentro o fuera del país 
	6) HÍBRIDO 
		1) Combina onshore y offshore

21) **Cuáles son actualmente los Modelos de Outosurcing de proyectos IT?**
	1) ![[Preguntas parcial 1-2.png]]

### **Unidad 2.1: Introducción a la gestión ágil de proyectos de desarrollo de software**
1) **Defina qué es agilidad? Qué colaboración requiere la agilidad?**
	1) Es la habilidad de responder de forma versátil al cambio para maximizar los benficios. Se requiere de la colaboración interna del equipo y externa del cliente.

2) **Por qué razones surge agil?**
	1) Las metodologías ágiles surgen como una extensión a las metodologías tradicionales para mejorar el desarrollo de sistemas, según el tipo de proyecto y empresa, añadiendo y mejorando (optimizando) las practicas de desarrollo de empresa.

3) **Manifiesto por el desarrollo ágil de SW: nombre sus valores ágiles (valores ágiles sobre tradicionales)**
	1) Individuos e interacciones sobre Procesos y Herramientas
	2) Software funcionando sobre Documentación exhaustiva 
	3) Colaboración con el Cliente sobre Negociación de cambios
	4) Respuesta ante el cambio sobre seguimiento de un plan

4) **Dentro de los principios del Manifiesto Agil, explique el concepto de feedback en ágil (Principios nros.1 y 6)**
	1) Principio 1: Nuestra mayor prioridad es satisfacer al cliente mediante la entrega temprana y continuada de software con valor 
	2) Principio 6: El método más eficiente y efectivo de comunicar información al equipo de desarrollo y entre sus miembros es la conversación cara a cara

5) **Dentro del principio nro 9, cuál es la formula para mejorar la agilidad?**
	1) Atención continua + Excelencia Técnica + Buen Diseño = Mejora de la agilidad

6) **Cuáles son sus elementos claves?**
	1) Poca Documentación 
	2) Simplicidad 
	3) Análisis como una actividad constante 
	4) Diseño evolutivo 
	5) Testeos diarios

7) Cuadro comparativo entre Gestión Tradicional vs Agil
	1) ![[Preguntas parcial 1-3.png]]

8) **Agil vs. Tradicional: cuándo es bueno elegir cada uno?**
	1) Ágil: 
		1) Acuerdo iterativo adaptable a los cambios, son buenos cuando consiguen entregar de forma repetible un valor innovador 
	2) Tradicional: 
		1) Búsqueda de un acuerdo previamente negociado, son buenos cuando consiguen desarrollar de forma repetible los productos especificados en el tiempo y con los costes previstos

9) **Cuáles son las premisas de Gestión Agil y Tradicional. Indique cual es predictiva y cual adaptativa.**
	1) La gestión tradicional es predictiva y se ha desarrollado sobre las premisas: 
		1) El plan crea estimaciones de costos/cronogramas 
		2) Todos los proyectos mantienen características y comportamientos regulares 
		3) El objetivo de la ejecución de un proyecto es lograr el producto provisto en el tiempo planificado 
	2) La gestión ágil es adaptativa sus premisas son las siguientes:
		1) La visión crea estimaciones de las funcionalidades 
		2) No hay una forma única y válida para gestionar cualquier tipo de proyecto 
		3) Hay proyectos que tienen como objetivo valor para el producto, y no funcionalidad, fecha y costes

10) **Explique la conversión del triángulo de restricciones de Tradicional a Ágil (armar gráfica)**
	1) ![[Preguntas parcial 1-4.png]]

11) **Qué implicaciones tiene pasar de organizaciones tradicionales a ágiles**
	1) ![[Preguntas parcial 1-5.png]]

12) **Cómo elegimos un framework?**
	1) Hay que tener en cuenta muchos factores para elegir uno ya que todos tienen sus fortalezas y debilidades. los factores a tener en cuenta son el tamaño de la empres, estructura del equipo, recursos disponibles, necesidades de las partes interesadas, estructura de su cartera de productos y la prioridad para el cliente en el desarrollo del proyecto

13) **Qué tipo de modelo es Scrum?**
	1) Scrum es un modelo ágil o modelo de referencia no centrado en las prácticas de programación, sino en las prácticas de gestión

14) **Defina: empowerment y feedback constante**
	1) Empowerment: 
		1) Otorgar autonomía para tomar decisiones al equipo de desarrollo y genera un clima de sinergia grupal 
	2) Feedback constante 
		1) Permite el desarrollo incremental y el crecimiento adaptativo de la programación

### **Unidad 2.2: Scrum: ceremonias, roles y artefactos**
1) **Nombre cuáles son los valores o principios que son base de toda la actividad en Scrum (ver gráfica)**
	1) ![[Preguntas parcial 1-6.png]]

2) **Explique el framework Scrum identificando: roles, compromisos/ceremonias/eventos, artefactos y como es su flujo/proceso. Identifique cada uno de ellos ( usar el resumen)**
	1) ![[Preguntas parcial 1-7.png]]
	2) ![[Preguntas parcial 1-8.png]]

3) **Qué es un MVP?**
	1) MVP se refiere al producto mínimo viable (en inglés, “minimum viable product”), o sea, un producto con las características esenciales para satisfacer a los clientes.

4) **Según la gráfica: qué comprende un “Sprint cero”?**
	1) ![[Preguntas parcial 1-9.png]]

5) **Los roles scrum que buscan? (gráfica con tres círculos donde buscan el balance)**
	1) Product owner, busca que se haga lo correcto, prioriza por valor el backlog 
	2) Scrum Master, vela por el proceso, que se haga rápido, elimina impedimentos S
	3) crum Team, Planifican y convierten el sprint backlog en el incremento de valor. Hace bien lo pedido, con calidad y buenas prácticas. Que no haya deuda técnica

6) **Qué es la deuda técnica? De 3 ejemplos de las formas.**
	1) Es la suma de todas las cosas que no hemos hecho anteriormente y que había que haber hecho para tener un software decente y de calidad. Es el costo del trabajo adicional causado por la elección de la solución más rápida en lugar de la más efectiva. Ejemplos: Definición inicial del proyecto insuficiente, lógica de negocios que no debe estar, algoritmos y funciones difíciles de leer y entender, falta de unit tests bugs no resueltos env arios sprints

7) **Qué tipos de deuda técnica hay (S.McConnell)?**
	1) Intencional: Surge de una decisión consciente de optimizar el presente en lugar del futuro 
	2) No Intencional: Ocurre cuando se comete un error inevitable
	3) Se puede gestionar de dos maneras: 
		1) Mantener una lista de deudas dentro de un sistema de seguimiento 
		2) Mantener la lista de deudas como parte de un trabajo pendiente del producto de Scrum

8) **De qué forma un líder puede gestionar la deuda técnica?**
	1) Mantener una lista de deudas dentro de un sistema de seguimiento: Cada vez que contraigas una deuda, ingresa las tareas necesarias para saldar esa deuda en tu sistema de seguimiento junto con un esfuerzo y cronograma estimados. Usa el backlog de la deuda para hacer un seguimiento del progreso de tu deuda técnica. Cualquier deuda no resuelta de más de 90 días debe considerarse crítica. 
	2) 4Mantener la lista de deudas como parte de un trabajo pendiente del producto de Scrum: Trata cada deuda como una US de Scrum y estima el esfuerzo y el cronograma para saldar cada deuda al igual que las otras US

9) **Cuáles son las metas de un equipo auto-organizado?**
	1) ![[Preguntas parcial 1-10.png]]

10) **Cuáles objetivos se agregan en Scrum 2020?**
	1) Scrum se basa en la inteligencia colectiva de las personas que lo utilizan, en lugar de proporcionar a las personas instrucciones detalladas, las reglas de Scrum guían sus relaciones e interacciones. 
		1) Menos prescriptivo, lenguaje más simple y eliminación de terminología específica del software. 
		2) No más preguntas en la Daily Scrum, se propone la estructura según el Objetivo del Producto 
			1) El Objetivo del producto sirve como objetivo y describe un estado futuro del producto. 
			2) el Product Goal & Sprint Goal: se entrega valor derivado del objetivo del producto y ayuda ha enmarcar el Sprint Goal, sus Sprint Reviews y le da sentido a lo que se hace.
		4) Las "funciones o roles" se reemplaza por "responsabilidades". 
		5) Los “componentes” se reemplaza por “artefactos”.

11) **Ver el objetivo y responsabilidades de los roles (cuadro)**
	1) Developer: 
		1) Objetivo: Son las personas que se encargan de generar el incremento usable, haciendo las cosas útiles. 
		2) Responsabilidades: Crear el Sprint Backlog / Velar por la calidad / Adaptarse cada día para alcanzar el Sprint goal / Ser responsables y profesionales 
	2) Product Owner 
		1) Objetivo: Maximizar el valor del Scrum Team / Entrega un backlog priorizado de lo que desea en el sprint backlog / Debe mantener el Product Backlog 
		2) Responsabilidad: Mantener el product backlog 
	3) Scrum Master 
		1) Objetivo: Hacer que el Scrum Team y la organización entiendan Scrum / Es un líder servicial 
		2) Responsabilidades:
			1) El Scrum Master sirve al Scrum Team de varias maneras: 
				1) Les enseña a ser autogestionados y multifuncionales (se mantiene) 
				2) Acompaña para crear productos de alto valor (se mantiene) 
				3) Elimina impedimentos (se mantiene) 
				4) Se aclara que, los eventos deben ser productos y útiles, ajustándose al time-box. En la versión de 2017 la explicación era más ambigua. 
			2) El Scrum Master sirve al Product Owner de varias maneras: 
				1) Enseñando al PO a definir el Product Goal y a mantener el Product Backlog (se mantiene con matices). 
				2) Haciendo ver la importancia de que los PBIs sean claros (se mantiene).
				3) Hacer entender que planificamos en un entorno complejo y con empirismo (se mantiene). 
				4) Facilitando la colaboración entre las partes interesadas (se aclara con respecto a 2017). 
			3) El Scrum Master sirve a la organización de varias maneras: 
				1) Liderando y organizando la implantación de Scrum en la organización (se mantiene). Planificando y asesorando la implantación de Scrum (se mantiene con matices).
				2) Ayudando a entender a las partes interesadas como trabaja el empirismo para resolver problemas complejos. (se aclara) 
				3) Eliminar barreras entre los interesados y el Scrum Team

12) **En Scrum nombre los resultado si mantenemos los valores en cada persona que trabaja en el equipo que desarrolla el proyecto? (reviews, backlog saneado, equipo de alto rendimiento, etc.)**
	1) Reviews 
	2) un Backlog saneado 
	3) Equipo de alto rendimiento
	4) Sprints cortos 
	5) Time-box, en los que las cosas tienen un tiempo limitado para hacerse, como el review o los sprints

13) **Explique las características de un equipo agil (auto-organizado, autónomo, multidisciplinario, cross funcional, autogestionado o empowerment, autogestionado.)**
	1) Autoorganización: El equipo decide cómo convertir los ítems del Product Backlog en soluciones que funcionan 
	2) Cross-funcional: Tienen todas las habilidades necesarias para crear el incremento del producto 
	3) No hay títulos: Todo el mundo es un desarrollador, nadie tiene un título especial 
	4) No existen sub-equipos: En el equipo de desarrollo
	5) Están comprometidos: Con lograr el objetivo del Sprint y entregar un incremento de alta calidad

14) **Scrum: cuadro de Eventos, nombre y explique cada evento o ceremonia y sus objetivos (reutilizar para la preguntas que siguen)**
	1) ![[Preguntas parcial 1-11.png]]
	2) ![[Pasted image 20260820095548.png]]

15) **Defina qué es un Sprint y cuánto puede durar**
	1) Es el periodo de tiempo durante el que se desarrolla un incremento de funcionalidad. Un sprint dura menos de 30 dias

16) **Indique la definición de backlog**
	1) Listado con los requisitos del sistema, donde se indica: contenido, priorización y disponibilidad.

17) **Indique cómo se puede trabajar en la ejecución de un Sprint (push y pull)**
	1) Se puede trabajar de varias formas: 
		1) se autoasigna a las tareas (notar que en una tarea puede haber más de una persona para aumentar su calidad, para aprender entre pares, etc.) o se asignan en el desarrollo según capacidades/skills o roles en algunos casos, o disponibilidades.
	2) Cuando se planifica, se hace PUSH porque se empujan todo el trabajo que es capaz de desarrollar.
	3) Cuando el desarrollador se sienta con el tester o QA, y lo acompaña a resolver los problemas, esperando la validación se hace PULL, ya que vamos marcando el ritmo según la capacidad del tester de validar los desarrollos

18) **Qué preguntas se responden dentro de la Sprint Planning? (gráfica de qué y cómo)**
	1) ![[Pasted image 20260820095822.png]]

19) **Cómo hacemos un Sprint Planning? Ver las gráficas: de 3 pasos(objetivos, Sprint backlog y Plan) y la de los roles (PO, equipo y SM)**
	1) ![[Pasted image 20260820095859.png]]

20) **Que debe hacer el Scrum Master para que no haya bloqueos**
	1) El Scrun Master debe trabajar con el Equipo y asegurarse que: 
		1) Si hay un trabajo pendiente que esté bien preparado con sus prioridades y dependencias en orden. Esto puede ser un gran desafío que podría descarrilar el proceso si no se administra adecuadamente. 
		2) Haya una buena comprensión de la velocidad y capacidad del equipo, tal que refleje licencias, vacaciones, I&D y las reuniones de Equipo. 
		3) Se capture lo definido en la Planning y se guarde en una herramienta de gestión de proyectos y colaborativa. De esa manera, tanto la decisión como la razón son fáciles de ver para todos.

21) **Cuál es el único compromiso que asume el equipo?**
	1) El Equipo se compromete a desarrollar PBIs del sprint para transformarlas en un incremento de producto potencialmente entregable.

22) **Qué preguntas se responden en una Daily, en qué se centra su dirección y cuál es su propósito?**
	1) QUÉ: Primera parte de la reunión. Se realiza en un timebox de alrededor de 2 horas (si la iteración es de 2 semanas): 
	2) CÓMO: Segunda parte de la reunión. Se realiza en un timebox de alrededor de 2 horas (si la iteración es de 2 semanas). El equipo planifica la iteración, elabora la táctica que le permitirá conseguir el mejor resultado posible con el mínimo esfuerzo.

23) **Para qué sirve una Sprint Review o demo?**
	1) Comprensión del producto: Todo el Equipo llega a escuchar la intención, el razonamiento y la implementación de la funcionalidad
	2) Formación de equipos: Los lazos creados mediante esta práctica nos unen más y nos hacen un grupo más integrado a pesar de la distancia. 
	3) Afianza a cliente: el cliente comprende el avance y entrega del producto, dando DONE a aquello que satisfaga los requerimientos y la definición de DONE. El cliente mejora su confianza.

24) **Qué es una agenda o guión de una Review?**
	1) La guía o guión de la demo (guide, demo guide notes or demo’s script) es una buena práctica que muchos toman y es algo muy simple, es como una agenda ordenada donde se hace una lista de los issues a presentar (con estado DONE) y los que no se llegaron a presentar con su estado basado en el Sprint Backlog.

25) **Qué es una retrospectiva? Cuál es su propósito?**
	1) La Retrospectiva es una reunión con una duración fija que se realiza al final de cada Sprint para que el Equipo reflexione sobre su progreso, se den retroalimentación y para inspeccionar y mejorar.

26) **==Defina una User Story y qué representa. Cómo es su estructura? Cuál es la jerarquía que tiene en un backlog? Indique qué es una Epica y un Storyboard (PRACTICA)==**
27) **==Explique en que consiste INVEST (PRACTICA)==**
28) **==Explique las técnicas usadas para priorizar las US (MoSCoW, pares, Kano y 100 puntos) PRACTICA==**
29) **==Explique las dependencias entre US - PRACTICA==**
30) **==Explique que son los criterios de aceptación y sus formatos/Gherkin (PRACTICA)==**
31) **==Explique cual es el método para medir la calidad de un criterio de aceptación (SMART)(PRACTICA)==**
32) **==Indique cuales son las reglas de escritura para los criterios de aceptación(PRACTICA)==**
33) **==Explique en que consiste el user story mapping. De qué se compone le mapa? (PRACTICA)==**

34) **Que representan los Story Points? Sobre que tratan?**
	1) los story points representan todo lo que pueda afectar el esfuerzo necesario para completar un ítem
	2) Los Story Points tratan sobre incertidumbre, complejidad o riesgo. Estos son factores que influyen en el esfuerzo, pero cada uno de ellos por sí solo no es suficiente para determinar el esfuerzo.

35) **Cómo sabes como vamos al estimar?**
	1) Aun cuando un elemento no está del todo claro, se puede estimar. La forma como se haga dependerá de muchos factores, pero es mejor hacerlo conforme sea la situación.

36) **Qué no hay que hacer en Scrum?**
	1) Dejar de respetar el framework acordado con el PO: no hacer demos, saltarse las Daily o Stand-ups, no hacer Retrospectivas, no cumplir DoD, por ejemplo.
	2) Ser poco específico
	3) No comunicarse/no disponer de un Product Owner o BA que conozca el negocio
	4) Dejar de actualizar los tableros/herramientas que gestionan información
	5) No estar disponible para que se comuniquen conmigo 
	6) Contar con un Scrum Master que esté asignado a varios clientes/proyectos. 
	7) Particionar/asignar por % o a varios proyectos a los team member del Scrum Team (salvo excepciones: arquitecto, DBA, DevOps, especialista, etc.) 
	8) No aplicar buenas prácticas 
	9) Sacrificar la calidad del software

37) **Defina Scrum. Qué permite y porqué se dice que es un framework (ppts más adelante)**
	1) Se trata de un marco de trabajo o framework que sirve para gestionar proyectos basado en las entregas de en corto plazo de producto definitivo. Este nos permite organizar un equipo que logre un ritmo sostenible y cíclico de trabajo a través de múltiples iteraciones, entregando productos parciales o incrementos de valor al cliente.

38) **Cuál es la función de los artefactos en Scrum? Y cuál es el compromiso que contienen?**
	1) Su función es aumentar la transparencia, clave para inspeccionar y adaptar en los eventos.
	2) Cada artefacto tiene un compromiso que asegura que genera transparencia.
		1) ![[Pasted image 20260820101415.png]]

39) **Defina cada uno de los artefactos.**
	1) Product Backlog 
		1) Es una lista ordenada que es la fuente de trabajo para todo el Scrum Team. Los items pueden considerarse “Ready” para el siguiente Sprint gracias al refinamiento. El refinamiento consiste en trabajar los PBIs en elementos más pequeños y manejables. Los atributos de los PBIs quedan abiertos al contexto del equipo.
	2) Sprint Backlog 
		1) El Sprint Backlog contiene el Sprint Goal, los PBIs seleccionados y el plan para lograrlo. Debe tener el detalle suficiente para que los Developers puedan inspeccionar su trabajo y saber si están alcanzando el Sprint Goal marcado
	3) Incremento 
		1) Cada incremento debe ser un paso hacia el Product Goal que nos hayamos fijado. Debemos asegurar que un nuevo incremento funciona con el resto. Durante el Sprint, se pueden generar muchos incrementos, y que estos se presentarán juntos en la Sprint Review al finalizar el Sprint.

40) **Time-box: definición, propósitos, aplicaciones/ejemplos y riesgos**
	1) ![[Pasted image 20260820101638.png]]

41) **Compara la definicion y flexibilidad del time-box en Agil, los deadlines tradicionales y un cronograma de Gantt**
	1) ![[Pasted image 20260820101655.png]]

42) **Defina el refinamiento**
	1) El refinamiento es una reorganización del Product Backlog, es decir, una actualización del mismo

43) **Que formas hay de estimar? (cuadro)**
	1) ![[Pasted image 20260820101741.png]]

44) **Que es el refinamiento?**
	1) El refinamiento es una reorganización del Product Backlog, es decir, una actualización del mismo

45) **Qué es y que diferencia hay entre un PBI y una UCuales son los items del PBI?**
	1) Una historia de usuario es una explicación general e informal de una función de software escrita desde la perspectiva del usuario final o cliente
	2) Las PBIs son elementos de alto nivel que describe una funcionalidad general que pueden incluir historias de usuario, pero también pueden abarcar otros tipos de elementos, como tareas técnicas o mejoras de infraestructura.
		1) Pueden incluir especificaciones, solicitudes de nuevas funciones, correcciones de errores o requisitos de cambio.
	3) La PBI es un elemento de alto nivel que describe una funcionalidad general (en este caso, “crear un sistema de registro de usuarios”). 
	4) Las historias de usuario son más específicas y detalladas. Cada historia de usuario se enfoca en una tarea o característica particular que contribuye a la PBI general.

46) **Qué es el Slicing? Cómo se hace?**
	1) Slicing permite descomponer el trabajo en ítems más pequeños
	2) ![[Pasted image 20260820102133.png]]

47) **Defina los criterios de aceptación vs DoD vs DoR**
	1) ![[Pasted image 20260820102208.png]]

### **2.3-Desarrollo y Métricas Agiles**
1) **Cómo se eligen las métricas en un proyecto ágil?**
	1) Las métricas se eligen: según el Proyecto y qué se necesita medir/reportar al management del Proyecto y cliente, que nos permita medir la calidad, el cumplimiento de objetivos, hallar errores, y oportunidades de mejora. y que se puedan realimentar y actualizar.

2) **En Kanban, que significa WIP y que se mide?**
	1) WIP (Work In Progress) mide el lead time (tiempo medio para completar un elemento, a veces llamado "tiempo de ciclo"), optimiza el proceso para que el lead time sea tan pequeño y predecible como sea posible.

3) **Qué es XP?**
	1) Es la integración de las prácticas de métodos tradicionales resumiendo o utilizando lo más práctico y eficaz,. sin olvidar la añadidura de características importantes mencionadas en el manifiesto ágil.

4) **Qué responsabilidades tiene un arquitecto?**
	1) Tiene la responsabilidad de investigar, evaluar y seleccionar las mejores alternativas tecnológicas para atender las necesidades específicas del negocio a un costo razonable.

5) **Completar: Los arquitectos deben identificar e involucrar activamente a los interesados de modo de….**
	1) Comprender las restricciones reales del sistema 
	2) Administrar las expectativas de los interesados 
	3) Negociar las prioridades del sistema 
	4) Tomar decisiones de compromiso

6) **Cuáles son las tres etapas del proceso de arquitectura de software?**
	1) Definir los requerimientos 
	2) Diseño de la arquitectura 
	3) Validación

7) **Qué cuestionamientos se deben hacer para precisar el funcionamiento final del sw?**
	1) Costo - Duración de desarrollo - Cantidad de usuarios - Grado de aislamiento

8) **Nombre ejemplos de con qué trabaja un arquitecto (ver gráfica de colores)**
	1) ![[Preguntas parcial 1-12.png]]

9) **Nombre las responsabilidades que posee un Arquitecto de software**
	1) Articular la visión arquitectónica 
	2) Conceptuar y experimentar con diferentes alternativas tecnológicas 
	3) Crear modelos, componentes y documentos de especificación de interfaces 
	4) Validar la arquitectura contra los requerimientos y presunciones del impacto de la alternativa seleccionada sobre la estrategia tecnológica de la organización.

10) **Nombre las funciones de un Arquitecto de software. Cuál es la fundamental del rol?**
	1) Debe ser una persona con amplios conocimientos técnicos. gran experiencia en programación, liderazgo y que ejerza lo siguiente: Gestión de los requisitos no funcionales y definición de la Arquitectura Software / Selección de la Tecnología y por lo tanto, es responsable del riesgo técnico. / Mejora continua de la Arquitectura.

11) **Según el tamaño de un sistema, que tipos de arquitectos especializados pueden intervenir? ¿Cuál es su especialización?**
	1) ![[Preguntas parcial 1-13.png]]

12) **Qué plantean y para qué sirven las métricas?**
	1) Plantean el para qué medimos y qué valor agregan. Sirven para apalancar la mejora continua, ayudando a la organizaciones a enfocar a las personas en lo más importante y en generar valor.

13) **Cómo se calcula el avance de un “proyecto” ágil?**
	1) Se calcula mediante metricas

14) **Cuáles son las métricas agiles principales y su definición**
	1) ==Valor (outcome o resultado)== 
		1) ==cualitativas/cuantitativas== 
	2) ==Eficiencia (output o salida) y Desperdicio== 
	3) ==Estimación==
		1) ==Velocidad==
	4) ==Equipo y Cultura== 
	5) ==Cambio==
	6) ==Deuda Técnica==
		1) ==calidad del producto==

15) **Cómo usar métricas ágiles para optimizar la entrega y cuáles son los antipatrones ante los que hay que estar alerta?**
	1) El Sprint Burndown chart hace visible el trabajo del equipo Scrum: es una representación gráfica de la velocidad a la que se completa el trabajo y cuánto trabajo queda por hacer.
		1) Antipatrones ante los que estar alerta 
			1) El equipo termina antes de tiempo todos los sprints porque no están asumiendo trabajo suficiente. 
			2) El equipo no cumple las previsiones sprint tras sprint porque están asumiendo demasiado trabajo. 
			3) La línea de evolución marca caídas pronunciadas en lugar de una evolución más gradual debido a que el trabajo no se ha dividido granularmente. 
			4) El propietario del producto añade o cambia el alcance en mitad del sprint.
	2) Los diagramas de evolución de épicas y versiones sirven para realizar el seguimiento del progreso del desarrollo a lo largo de una muestra más amplia de trabajo que en la evolución de sprints, y guía el desarrollo de los equipos de scrum y kanban.
		1) Antipatrones ante los que estar alerta
			1) Las previsiones de epicas o versiones no se actualizan a medida que el equipo avanza por el trabajo. 
			2) No se observa progreso después de varias iteraciones.
			3) Cuando el PO no entiende completamente el problema a solucionar. 
			4) El alcance aumenta con mayor rapidez que la capacidad de atenderlo el equipo. 
			5) El equipo no está lanzando versiones incrementales a lo largo del desarrollo de las epicas
	3) La velocidad es la cantidad media de trabajo que un equipo de scrum lleva a cabo durante un sprint, medida en puntos de historia u horas, y es muy útil para los pronósticos
		1) Antipatrones ante los que estar alerta 
			1) Si la velocidad experimenta muchas variaciones en un largo periodo de tiempo, revisa las prácticas de estimación del equipo.
	4) Los gráficos de control se centran en el tiempo de ciclo de los problemas individuales: el tiempo total desde "en progreso" hasta "terminado".
		1) Antipatrones ante los que estar alerta 
			1) Los gráficos de control pueden parecer demasiado variables al principio. No te preocupes demasiado con cada dato que se salga de la norma. Busca tendencias. Estas son dos áreas a las que estar atentos: 
			2) Aumento de la duración del ciclo: El aumento de la duración del ciclo mina la agilidad lograda con tanto esfuerzo por parte del equipo. En la retrospectiva del equipo, dedica tiempo a entender el motivo de este aumento. Una excepción: Si la definición que hace el equipo de "finalizado" ha aumentado, la duración del ciclo probablemente aumente también. 
			3) Duración del ciclo heterogénea: El objetivo es tener una duración del ciclo homogénea de los elementos de trabajo que tengan valores de punto de historia similares. Filtra el gráfico de control para cada valor de punto de historia en busca de homogeneidad. Si la duración del ciclo es heterogénea en valores de punto de historia grandes y pequeños, dedica tiempo en la retrospectiva a examinar los aspectos que se han pasado por alto y a mejorar las estimaciones futuras.
	5) El diagrama de flujo acumulado es un recurso clave para los equipos de kanban. Ayuda a garantizar la coherencia del ritmo de trabajo en todo el equipo. Con el número de tickets en el eje de ordenadas, el tiempo en el eje de abscisas y colores para indicar los distintos estados del workflow, indica visualmente las limitaciones y los cuellos de botella conjuntamente con los límites del trabajo en curso
		1) Antipatrones ante los que estar alerta 
			1) Las incidencias que causan bloqueos crean enormes copias de seguridad en algunas partes del proceso y muy escasas en otros. 
			2) Crecimiento incontrolado del backlog a lo largo del tiempo. Esto da como resultado que los propietarios del producto no cierren incidencias obsoletas o que las incidencias con prioridad más baja no se traten nunca

16) **Describa las tres magnitudes que miden la gestión de proyectos agiles**
	1) Tiempo: El desarrollo ágil emplea la técnica “timeboxing” para gestión de tiempo. En el caso de Scrum, la unidad de tiempo para cada incremento de producto es el Sprint.
	2) Velocidad (Continuando con lo anterior): Velocidad es la magnitud que viene determinada por la cantidad de trabajo realizada en un periodo de tiempo (Timebox). Los equipos que miden el trabajo con tiempo ideal, hablan de “Velocidad”
	3) Trabajo: Medir el trabajo puede ser necesario por dos razones: para registrar el ya hecho, o para estimar anticipadamente, el que hay que realizar. En ambos casos se necesita una unidad, y un criterio objetivo de cómo se cuantifica.

17) **Explique en qué consiste y qué mide: velocidad, velocidad absoluta y relativa, trabajo, tiempo, tiempo real e ideal, tiempo teórico o de tarea, trabajo ya realizado, trabajo pendiente de realizar, unidades de trabajo y puntos de función.**
	1) Velocidad es la magnitud que viene determinada por la cantidad de trabajo realizada en un periodo de tiempo (Timebox) Los equipos que miden el trabajo con tiempo ideal, hablan de “Velocidad”.
	2) Velocidad absoluta: cantidad de producto construido en un sprint. Se expresa en la misma unidad en la que se realizan las estimaciones (puntos de función, horas o días reales o teóricos).
	3) Velocidad relativa: Cantidad de producto construido en una unidad de tiempo de trabajo
	4) Trabajo: Medir el trabajo puede ser necesario por dos razones: para registrar el ya hecho, o para estimar anticipadamente, el que hay que realizar. En ambos casos se necesita una unidad, y un criterio objetivo de cómo se cuantifica.
	5) Tiempo: El desarrollo ágil emplea la técnica “timeboxing” para gestión de tiempo. En el caso de Scrum, la unidad de tiempo para cada incremento de producto es el Sprint.
	6) Tiempo real o tiempo de trabajo: Tiempo efectivo para realizar un trabajo. Se suele medir en horas o días
	7) Tiempo ideal: se refiere al tiempo de trabajo necesario, en “condiciones ideales”, esto es, sin ninguna interrupción, pausa, distracción o atención a tareas ajenas a la tarea del sprint que se tiene asignada.
	8) Tiempo teórico o tiempo de tarea: Tiempo que sería necesario para realizar un trabajo en “condiciones ideales”: si no se produjera ninguna interrupción, llamadas telefónicas, descansos, reuniones, etc
	9) Trabajo ya realizado: Para medirlo basta contabilizar lo ya realizado, empleando las unidades con las que se opere: líneas de código, horas trabajadas (reales o teóricas)
	10) Trabajo pendiente de realizar: Scrum mide el trabajo pendiente para: 
		1) Estimar el esfuerzo y la duración prevista para cada tarea. 
		2) Determinar el avance del proyecto, y en especial de cada sprint
	11) Unidades de trabajo: Las unidades para medir el trabajo pueden estar relacionadas directamente con el producto, como los tradicionales puntos de función de COCOMO; o indirectamente, a través del tiempo necesario para realizarlo.
	12) Puntos de función o puntos de funcionalidad: Unidad de medida relativa para determinar la cantidad de trabajo necesaria para construir una funcionalidad o historia de usuario del product backlog

18) **En qué consisten las métricas: Lead Time y Cycle time**
	1) lead time (tiempo medio para completar un elemento, a veces llamado "tiempo de ciclo")
	2) Cycle time: el tiempo total desde "en progreso" hasta "terminado