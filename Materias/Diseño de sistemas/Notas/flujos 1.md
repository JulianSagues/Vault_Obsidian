
---
iniciar proceso de facturacion

- buscamos los estados que se pueden facturar del comvenio, el estado arpobado y el estado facturado y el pendiente de cliente
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
			- leemos tipo servicio y tarifa servicio
			- leemos tarifa fija y por hora
			- buscamos servicios en los estados buscados y que su año mes servicio sea el mes anterior
			- total horas efectuadas = 0
			- por cada servbicio
				- leemos las horas efectuadas
				- total horas efectuadas = total horas efectuadas + horas efectuadas
				- valor servicio = total horas efectuadas * tarifa por hora
				- creamos intancia de proceso ffaturacion servicio con monto servicio igual a valor servicio
			- leemos las horas minimas por servicio
			- si las horas minimas son mayores a las efectuadas valor tipo servicio igual a tarifa fija
			- leemos el tipo servicio relacionado y creamos instancia de proceso facturacion de convneio tipo servicio con monto tipo servicio igual a valor tipo servicio
			- valor convenio = valor conveniio + valor tipo servicio
			- 