- [[1-Diagrama de Clases.drawio]]
- [[1-Diagrama de Casos de Uso.drawio]]

---
[[CU - Aceptar convenio.docx]]

**Estado Inicial:**
- El convenio tiene que estar registrado
- El profesional tiene que saber sobre el tipo servicio
- Debe existir el estado de convenio aceptado (si hay disponibilidad horaria), registrado, en progreso, registrado y rechazado(si no hay disponibilidad horaria)
**Estado Final:**
- El convenio queda aceptado o rechazado
**Parámetros de Entrada:**
- numeroConvenio
**Precondición:**
- profesional instanciado con socioResponsable verdadero
**Flujo:**
1. Inicia caso de uso
2. Se verifica que el profesional sea socio responsable y se le pide que ingrese el numeroConvenio
3. Ingresa numeroConvenio
4. Se verifica que el numero sea correcto, se buscan los estados registrado, aceptado, firmado, en progreso y rechazado y se verifica que el convenio este registrado
5. Leemos el inicio del convenio y su final, creamos una variable para guardar el año de inicio(añoMesIteracion) y empezamos con el control de horas:
	1. mientras el año de incio sea menor o igual al año final se hace:
		1. leemos las intancias de ConvenioTipoServicio relacionadas al convenio
		2. Por cada instancia que encontramos hacemos:
			1. leemos las horas minimas y los tipo servicios relacionados junto con su codigo
			2. creamos las variables totalHorasDiponiblesConsultora y totalHorasOcupadasConsultora
			3. buscamos instancias de profesionalTipoServicio con la fechaDesde menor a añoMesIteracion, con la fechaHasta mayor a añoMesIteracion y relacionada a un tipo servicio
			4. por cada instancia que encontramos:
				1. buscamos un profesional que no este dado de baja y que este relacionado a una de las intancias de PTS
				2. Si no se encontro ninguna instancia continuamos
				3. leemos las horas max por mes y el cuit
				4. hacemos que totalHorasDisponiblesConsultora = totalHorasDisponiblesConsultora + horasMaxPorMes
			5. buscamos instancias de convenio que añoMesIteracion este entre su año de inicio y de fin y este en estado firmado, en progreso o aceptado
			6. por cada instancia que encontramos
				1. leemos su ConvenioTipoServicio
				2. seleccionamos las instancias que esten relacionada a un tipo servicio que hayamos leido del convenio anterior
				3. si no encontramos ninguna continuamos
				4. leemos las horas minimas por servicio
				5. totalHorasOcupadas = totalHorasOcupadas + horasMinimasPorServicio
			7. hacemos totalHorasOcupadas = totalHorasOcupadas + horasMinimasPorServicio pero le sumamos las horas minimas del convenio propio
			8. comprobamos que las horas ocupadas sean menores a las disponibles
		3. hacemos añoMesIteracion = adelantarMes(añoMesIteracion)
	2. hacemos que el convenio quede aceptado
6. guardamos cambios
7. fin cu

**CA importantes:**
1. si no se cumple que hay disponibilidad horario el convenio queda rechazado

---
[[CU - Aprobar servicio.docx]]
**Flujo:**
1. Buscamos el estado de servicio terminado
2. buscamos el estado de convenio en progreso
3. buscamos convenio relacionados al cliente (de la precondicion) y en estado en progreso
4. por cada convenio encotrado
	1. leemos el proyecto, su nombre y su el numero del convenio
	2. leemos los convenioTipoServicio asociados
	3. por cada una de esas instacias
		1. leemos los tipo servicio asociados y su nombre
		2. buscamos instancias de servicio asociados a al convenioTipoServicio y en estado terminados
		3. por cada servicio
			1. leemos su descripcion
			2. mostramos el numero del convenio, el nombre del proyecto el nombre del tipo servicio y la descripcion del servicio
5. Pedimos que selecione el servicio a aprobar
6. seleciona el servicio
7. leemos las horas estimadas, horas efectuadas, descripcion, profesional asociado, su nombre
8. mostramos las horas estimadas, horas efectuadas, descripcion y el nombre del profesional
9. leemos las tareas relacionadas
10. por cada tarea
	1. leemos su nombre
	2. lo mostramos
11. pedimos que se apruebe o no el servicio
12. elige accion
13. verificamos que haya aprobado
14. buscamos estado aprobado
15. modificamos el servicio a aprobado
16. leemos las instancias de servicio estado relacionadas al servicio
17. seleccionamos la instancia que no tenga fecha hasta
18. modificamos la fecha hasta con la fecha actual
19. creamos una instancia de servicio estado con fecha desde igual a la fecha actual, fecha hasta igual a vacio, contador servicio igual al generado, observaciones igual a servicio aprobado
20. relacionamos el servicio a lo creado
21. mostrar mensaje que se aprobo el servicio

CA:
1. Si se desaprueba el servicio hacemos lo mismo pero con en progreso y observacion servicio desaprobado

----
[[CU - Cancelar convenio.docx]]
Flujo:
1. comprobamos que sea un socio responsable
2. pedimos que diga quien cancela
3. elige el rol del usuario cliente o consultora
4. pedimos que ingrese el numero del convenio
5. ingresa el numero 
6. comprobamos que exista
7. buscamos los estados de convenio y servicio cancelado
8. buscamos el convenio
9. verificamos que el estado sea aceptado
10. modificamos el vonbernop para que quede en estado cancelado y la fecha de cancelacion actual

CA:
1. Si el econvenio estaba firmado y el rol es cliente, cobrar multa es verdadero, sino falso
2. si el convenio estaba en progreso
	1. leemos las intancias de convenio tipo servicio
	2. buscamos estado en progreso y terminado de servicio
	3. por cada instancia leida
		1. buscamos servicios relacionados a convenio tipo servicio y en estado en progreso o terminados
		2. comprobamos que no se hayan encontrado servicios porque no se pueden cancelar en ese estado
	4. buscamos el estado asignado de servicio
	5. por cada instancia de convenio tipo servicio leida
		1. buscamos servicios en estado asignado y relacionados
		2. por cada servicio encontrado
			1. leemos servicio estado
			2. selecionamos la instancia que tiene fecha hasta vacia
			3. le ponemos fecha hasta con fecha actual
			4. hacemos instancia de servicio estado con fecha desde igual a fecha actual, fecha hasta vacia, contador igual al generado y observaciones igual a servicio cancelado
			5. el servicio queda cancelado con relacion al servicio estado creado
	6. si era cliente cobrar multa verdadero, sino falso

---
[[CU - Configurar tarifas.docx]]
flujo:
1. comprobamos que socio responsable sea verdadero
2. buscamos configuraciones tarifa
3. por cada instacia
	1. leemos numero configuracion, hora desde, hora hasta
	2. mostramos esas cosas
4. solitamos accion
5. seleccionar accion modificar o agregar
6. comprobamos que agrega
7. solicitamos monto multa, fecha hasta y desde
8. ingresar monto y fechas
9. comprobamos que fecha desde sea mayor a la actual y fecha hasta mayor a desde
10. buscmaos tipos de servicios
11. creamos variable cuenta = contar(tipoServicio)
12. selecionamos la primera instancia de tipoServicio
13. leemos su nimbre y lo mostramos
14. pedimos la tarifa fija y la tarifa por hora
15. ingresa las arifas
16. creamos intancia de tarifa servicio con numero igual al generado, tarifa fija igual a la ingresada, tarifa por hora igual a la ingresada y relacion a tipo servicio seleccionado
17. cuenta = cuenta -1
18. si cuenta es 0 ir a paso 21
19. seleccionar siguiente isntancia
20. ir a paso 13
21. crear instancia de configuracion tarida con numero igual al generado, monto multa, fecha desde y hasta igual al ingresado

CA:
1. si se quiere modificar se solicita que desea modifcar
	1. selecciona tarifa periodo o tipo de servicio
	2. comprobar que sea tarifas
	3. leemos las instancias de tarifas relacionadas a configuracion
	4. por cada instancia
		1. leemos tarifa fija y por hora
		2. leemos tioservicio relacionado
		3. leemos el nombre
		4. mostramo tarifa fija, por hora, nombre
	5. mostramos que tipo servicio modificar
	6. selecciona instancia de tarifa
	7. solicitamos nuevos valores
	8. ingresa tarifas
	9. modificamos valores de tarifa servicio
	10. preguntamos si quiere modificar otro
	11. si si, ir para atras
	12. preguntamos si queiere modificar otra cosa
	13. si si, ir para atras
	14. con el perido lo mismo 
	15. si se elige servicio creamos la tarifa de cero
2. 

---
[[CU - Entregar servicio.docx]]
flujo:
1. buscamos el eesado de servicio en progreso
2. comprobamos que este instanciado
3. buscamos servicios en progreso del profesional
4. por cada servicio
	1. leemos numero, descripcion y hroas estimadas y los mostramos
5. pedimos que seleccione servicio
6. selecciona por numero de servicio
7. solicitamos 