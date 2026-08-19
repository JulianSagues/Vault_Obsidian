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
16) Que debe especificar un proceso de Ingeniería de software?
17) Nombre 5 características de los productos de sw
18) Cuáles son los retos de la Ingeniería de software? Explíquelos brevemente
19) En que consiste en la Interfaz Usuaria: calidad percibida, calidad externa y calidad en el uso?
20) Defina la usabilidad e indique a que hace referencia?
21) A qué hace referencia la usabilidad y en que puntos descansa?
22) Cuándo se considera la usabilidad?
23) Cuales son las ventajas de las GUI? (Somerville págs. 327 a 347)
24) Nombre los principios de diseño de interfaces usuarias (Somerville)
25) Cuales son los 5 estilos primarios de interaccion con el usuario según Shneiderman? (Somerville)
26) Cuales son los 5 lineamientos claves para la utilización efectiva del color en las interfaces de usuario? (Somerville)
27) En que consiste la evaluación de la interfaz? Que comprende? (Somerville)