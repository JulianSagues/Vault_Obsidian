
---
![[1-Diagrama de Casos de Uso.drawio]]

[[Explicación Consultoría]]

---
### Actores:
- Socio Responsable: Profesional/persona de la consultoría con tareas referidas gestión de convenios
- Demonio de facturación: programa que se encarga de hacer facturación de convenios
- Profesional: persona que realiza los servicios del convenio
- Cliente: persona que solicita un convenio
- Administrador del sistema: "creador" del sistema que se encarga de tareas referidas al sistema
---
[[CU - Aceptar convenio (Maxi).docx|Aceptar Convenio]]
Para realizar este caso de uso el convenio debe estar registrado. El socio responsable deberá ingresar el numero de convenio. Una vez ingresado se verifica que el profesional tenga una disponibilidad horaria compatible con las pedidas por el tipo de servicio solicitado por el cliente, de ser así, se acepta el convenio y queda en estado aceptado. En caso contrario el convenio quedara rechazado. De ser aceptado se comienza con la primera iteración del servicio.

---
[[CU - Aprobar servicio.docx|Aprobar servicio]]
