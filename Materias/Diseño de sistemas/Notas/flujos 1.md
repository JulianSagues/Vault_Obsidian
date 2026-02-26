
---
iniciar proceso de facturacion

- buscamos los estados que se pueden facturar del comvenio, el estado arpobado y el estado facturado de servicio y el pendiente de cliente
- buscamos la configuracion actual para leer el monto de la multa
- buscamos los clientes dados de baja
- por cada cliente
	- declaramos una variable llamada valorcliente = 0
	- buscamos los convenios que no esten cancelados y que su fecha fin sea mayor a la actual
	- buscamos los convenios cancelados 
	- si no encontramos seguimos con el sigueinte
	- por cada convenio
		- declaramos valor convenio = 0 y cant mese = 0
		- leemos su año mes fin y convenio tipo servicio
		- por cada convenio tipo servicio
			- valor tipo servicio = 0
			- leemos tipo servicio y tarifa servicio
			- leemos tarifa fija y por hora
			- buscamos servicios en los estados buscados y que su año mes servicio sea el mes anterior
			- total horas efectuadas = 0
			- por cada servbicio
				- leemos las horas efectuadas
				- total horas efectuadas = total horas efectuadas + horas efectuadas
				- valor servicio = total horas efectuadas * tarifa por hora
				- creamos intancia de proceso ffaturacion servicio con monto servicio igual a valor servicio
				- valor tipo servicio = valor tipo servicio + valor servicio
			- leemos las horas minimas por servicio
			- si las horas minimas son mayores a las efectuadas valor tipo servicio igual a tarifa fija
			- leemos el tipo servicio relacionado y creamos instancia de proceso facturacion de convneio tipo servicio con monto tipo servicio igual a valor tipo servicio
			- valor convenio = valor conveniio + valor tipo servicio
		- leemos estado de convenio, cobrar multa y su nombre
		- si es cancelado y  es verdadero
			- leemos fecha cancelacion
			- cantmeses = calcularcantidadmeses(fecha hora cancelacion, aañomes fin)
			- valor multa = cant meses * monto multa por mes
			- valor convenio = valor convenio + valor multa
		- sino valor multa = 0
		- creamos instancia de proceso facturacion convenio con monto convenio igual valor convenio y monto multa igual a valor multa
		- valor cliente = valor cliente + valor convenio
	- creamos instancia de pf cliente con numero factura cliente igual al generado, fecha hora facturacion igual a la actual monto sin iva a valor cliente, todo lo demas vacio y queda pendiente
- buscamos estado simulado
- creamos proceso facturacion con fechaHoraProceso facturacion igual a la actual, numero igual al generado, año mes facturacion igual anterior, lo demas vacio

---
entregar servicio
- buscamos estado en progreso servicio
- profesional instanciado
- buscamos servicios en progreso y del profesional
- por cada servicio leemos su descripcion su numero y las horas estimadas y las mostramos
- solicitamos seleccion
- solicitamos oservaciones
- leemos tareas del servicio
- can horas efectuadas = 0
- por cada tarea leemos sus horas duracion y sumamos a las horas efectuadas
- buscamos el estado terminado
- buscamos la instancia de estado servicio que no tenga fecha hasta
- le ponemos fecha hasta actual
- creamos instancia de servicio estado con la fecha desde actual contador generado y observaciones servicio terminado
- modificamos instancia de servicio con las horas efectuadas calculadas 
- confirmamos entrega

---
cancelar convenio
- comprobamos que sea socio responsable
- solicitamos rol del cancelador
- ingresamos numero convenio
- buscamos estado convenio cancelado y servicio cancelado
- comprobamos que el convenio sea aceptado leyendolo
- modificamos convenio con fecha cancalacion actual y cobrar multa falso
- si estado es firmado
	- si rol cliente modificamos para cobrar verdadero
	- si consultora cobrar multa falso
- si en progreso
	- leemos instasncias convenio tipo servicio
	- buscamos estado servicio en progreso y terminados
	- por cada convenio tipo servicio buscamos servicios que esten en estos estados, de ser asi no se puede cancelar
	- buscamos estados asignado de servicio
	- por cada convenio tipo servicio buscamos servicios asignados
		- por cada servicio
			- leemos instancias de servicio estado y seleccionamos la que tenga fecha hora hasta vacia y se la completamos con la actual
			- creamos instancia de serivico estado con fecha desde actual, contador generado y observacion servicio cancelado
			- modificamos instancia de servicio con relación a esta y estado cancelado
	- si rol usuario cobramos multa
	- sino no

---
registrar tarea

- buscamos los estados en progreso y asignado
- comprobamos profesional instanciado
- buscamos sevicios del profesional y en alguno de los estados
- leemos lo importante y lo mostramos
- solicitamos que seleccione servicio
- cantidad tareas = 0
- leemos la instancia de tarea relacionadas
- por cada tarea
	- canttidad de taareas ++
	- leemos sus datos y lo mostramos
- solicitamos datos tareas
- comprobamos datos
- creamos la instancia de tare con los datos ingresados y numero igual cantidad de tareas + 1
- modificar servicio para agregar relacion
- leemos estado servicio y su nombre
- si el nombre es asignado cambiamos el estado a en progreso y creamos servicio estado
- preguntar si quiere agregar otra tarea

---
aceptar convenio
- comprobamos que sea socio responsable
- pedimos el numero de convenio
- buscamos estados de convenio registrados, aceptados, firmados y en progreso
- buscamos el convenio ingresado en estado registrado
- leemos año mes fin y año mes inicio
- añomesiteracion = año mes inicio
- mientras el año mes iteracion sea menor a año mes fin}
	- leemos instancias de convenio tipo servicio
	- por cada instancia
		- leemos horas min por servicio
		- leemos tipo servicio
		- buscamos intancias de profesional tipo servicio que año mes iteracion este entre sus fechas y relacionada al tipo de servicio
		- por cada instancia
			- buscamos instancia de profesional relacionada
			- si no se encontro seguimos con la siguiente
			- leemos sus horas max
			- horas disponibles consultoria = horas disponibles consultorias + horas max
		- buscamos instancia de convenio con año mes iteracion entre sus fechas y en estado acpetado, firmado o en progreso
		- por cada convenio
			- leemos instancia convenio tipo servicio relacionada al tipo servicio leido antes
			- leemos sus horas minimas por servicio
			- horas ocupadas consultora = horas ocupadas consultora + horas minimas por servicio
		- horas ocupadas consultora = horas ocupadas consultora + horas minimas por servicio de nuestros servicio
		- comprobamos que horas ocupadas sean menores a las disponibles
	- año mes iteracion  = adelantar mes(año mes iteracion)
- modificamos instancia de convenio a aceptado

---
solicitar servicio
- buscamos estados convenio en progreso y firmado
- comprobamos que el cliente este instanciado
- buscamos convenio del cliente firmado
- por cada convenio leemos sus datos y los mostramos
- solicitamos seleccion
- leemos convenio tipo servicio
- por cada instancia leemos instancia de tipo servicio, sus datos y los mostramos
- solicitamos seleccion de servicio
- solicitamos horas estimadas
- buscamos estados servicio asignado, en progreso, terminado y aprobado
- buscamos profesionales
- por cada profesional
	- leemos instancia de cts
	- por cada instancia 
		- leemos hora desde, hasta y tipo servicio
		- si hora desde es menor a actual, hora hasta es mayor a actual y tipo servicio leido es igual al seleccionado
			- agregar profesional a lista de profesional
- definier pseeudoentidad disponibilidad profesional(horas min, horas max, horas disonibles, cuitprofesional)
- por cada profesional de la lista
	- leemos cuit, horas max, horas min
	- creamos instancia disponibiliadd con los datos ledios y hora disponibles igual a horas max
	- horas ocupadas =  0
	- buscamos servicios en proceso y asignados del consultor del año actual
	- por cada servicio
		- leemos las horas estimadas
		- horas ocupadas = horas ocupadas + horas estimadas
	- buscamos servicios terminados y aceptados del año actual
	- por cada servicio
		- leemos las horas estimadas
		- horas ocupadas = horas ocupadas + horas estimadas
	- modificar la pseuentidad con horas disponebles igual a horas disponibles - horas ocupas
- ordenar por(horas disponibles, mayor)
- por cada pseuentidad creada
	- leer jhoras disponibles
	- si horas disponibles >horas estimadas
		- leer profesional cuit
- buscar profesional cuit con cuit de pseuentidad
- solicitar descripcion
- buscamos estado asignado
- creamos instancia servicio estado
- creamos instancia de servicio con descripcion ingresado, horas estimadas ingresadas, año mes servicio actual y numero generado

---
1. Los "Monstruos" de los Bucles y Variables

Estos son los que te van a pedir iterar mucho. Anotate bien qué calcula cada uno:

• **Aceptar Convenio (El del bucle MIENTRAS por fechas)****:**

    ◦ **El truco:** Evalúa si toda la consultora tiene horas suficientes mes a mes.

    ◦ **Estructura clave:** Usa un bucle `MIENTRAS [añoMesIteracion sea menor o igual que añoMesFin]`.

    ◦ **Variables:** Adentro de ese bucle, siempre pone a cero `totalHorasDisponiblesConsultora = 0` y `totalHorasOcupadasConsultora = 0`. Luego suma las horas de los profesionales activos y resta las de los convenios activos.

• **Solicitar Servicio (El de la Pseudoentidad)****:**

    ◦ **El truco:** Tiene que buscar a los profesionales que les sobre tiempo y ordenarlos.

    ◦ **Estructura clave:** Vas a declarar una pseudoentidad: `Definir pseudoentidad DisponibilidadProfesional (horasDisponibles, horasMin, horasMax, profesionalCUIT)`.

    ◦ **Variables:** Por cada profesional, calculás sus `horasOcupadas` sumando las horas de los servicios que ya tiene "En progreso" o "Asignados". Luego restás eso a sus horas máximas y guardás el objeto en la pseudoentidad para ordenarlo de mayor a menor (`OrdenarPor(horasDisponibles; mayor a menor)`).

• **Iniciar Proceso de Facturación (El Demonio con 4 niveles)****:**

    ◦ **El truco:** Es automático (Actor: Demonio) y va de mayor a menor jerarquía: **Cliente -> Convenio -> ConvenioTipoServicio -> Servicio**.

    ◦ **Variables:** En cada nivel pone un acumulador a cero: `valorCliente = 0`, `valorConvenio = 0`, `valorTipoServicio = 0`.

    ◦ **La trampa del negocio:** Cuando llega al nivel de los Servicios, suma las `horasEfectuadas`. Ojo con esta validación: **SI** las `totalHorasEfectuadas` son menores a las `horasMinimasPorServicio`, se le cobra la `tarifaFija` de ese servicio; sino, se multiplica por la `tarifaPorHora`.

2. Los de Comunicación con el Exterior (APIs)

Acá la clave no es la lógica matemática, sino cómo se invoca a los sistemas externos.

• **Gestionar Proceso de Facturación (Enviar / Reenviar / Anular)****:**

    ◦ **El truco de Enviar/Reenviar:** Interactúa con AFIP/ARCA y un servidor de Mail. Tenés que usar un bucle `MIENTRAS` para controlar los reintentos si falla la conexión: `MIENTRAS [contadorFallos != 0 && contadorIntentos < 3]`.

    ◦ **Sintaxis de invocación:** `Invocar servicio “Generar factura electrónica” del Sistema ARCA...` y `Invocar servicio "Enviar mail" Servidor Mail`.

    ◦ **El truco de Anular:** Llama a la API de ARCA para “Generar nota de crédito” y cambia en cascada los estados de todos los convenios y servicios afectados.

3. Los del Día a Día (Acumuladores y Contadores simples)

Estos son fáciles pero rigurosos con los cambios de estado:

• **Registrar Tarea****:**

    ◦ **El truco:** Necesita asignarle un número a la tarea.

    ◦ **Variables:** Pone `cantidadTareas = 0`. Hace un `Por cada` tarea que ya tiene el servicio y suma `cantidadTareas++`. Al crear la nueva tarea, le pone como número: `[cantidadTareas + 1]`.

    ◦ **La trampa de Estado:** Si el servicio estaba en estado "Asignado" (es decir, esta es la primera tarea), el sistema lo debe cambiar obligatoriamente a "En progreso", creando una nueva instancia de `ServicioEstado`.

• **Entregar Servicio****:**

    ◦ **El truco:** Totalizar el tiempo trabajado.

    ◦ **Variables:** Pone `horasEfectuadas = 0`. Recorre todas las tareas y suma `horasEfectuadas = horasEfectuadas + horasDuracion`. Al finalizar, cambia el estado del servicio a "Terminado".

• **Configurar Tarifas****:**

    ◦ **El truco:** Iterar usando un contador "manual". En lugar de usar un "Por cada..." tradicional, este CU hace `cuenta = Contar(TipoServicio)`. Muestra un servicio, pide tarifas, resta `cuenta = cuenta - 1` y hace un `SI cuenta es igual a 0...` para saber si terminó o si usa la primitiva `Ir a paso...` para volver a repetir el bucle.