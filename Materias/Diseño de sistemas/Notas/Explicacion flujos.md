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
7. busca,os esta