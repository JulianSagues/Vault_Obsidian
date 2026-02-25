
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
		- 