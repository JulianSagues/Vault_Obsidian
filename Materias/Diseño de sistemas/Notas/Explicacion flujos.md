- [[1-Diagrama de Clases.drawio]]
- [[1-Diagrama de Casos de Uso.drawio]]

---
[[CU - Aceptar convenio.docx]]

**Estado Inicial:**
- El convenio tiene que estar registrado
- El profesional tiene que saber sobre el tipo servicio
- Debe existir el estado aceptado (si hay disponibilidad horaria), registrado, en progreso, registrado y rechazado(si no hay disponibilidad horaria)
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
%% rompe-lista %%
CA importantes:
8. 