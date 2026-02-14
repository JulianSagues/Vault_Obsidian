---
base: "[[Comunicación de datos.base]]"
Parent item: []
Blocking: []
Sub-item: []
Blocked by: []
Categoria:
  - Unidad 6
---
### Definición de enlace Satelital

Los enlaces satelitales son redes que utilizan como medios de transmisión satélites, que se encuentran localizados en órbita alrededor de la tierra. En este tipo de enlaces las estaciones terrestres poseen una antena por medio de la cual pueden enviar/recibir señales generadas desde la tierra. En resumen, los satélites actúan como grandes espejos de las ondas recibidas y enviadas desde las estaciones terrestres. Una característica fundamental de este tipo de sistemas es que utilizan una frecuencia para enviar la señal, denominada UP Link, y otra frecuencia para recibir señales, denominada DOWN Link.

- Ventajas: La principal ventaja de este tipo de sistema es lograr establecer enlaces de comunicaciones, donde ninguno de los otros métodos alternativos es posible de utilizar, ya sea MW, FO, etc.
- Desventaja: Son sistemas muy costosos. El retardo de una señal puede llegar a ser de 1,5 segundos, lo cual es muy importante.

### Tipos de Satélites

De acuerdo a la distancia a la tierra en la que orbiten los satélites, podemos distinguir los siguientes tipos de satélites:

- Satélites LEO (Low Earth Orbit): Estos satélites orbitan generalmente por debajo de los 5000 km. La mayoría de ellos se encuentran entre los 600 y 1600 km.
- Satélites MEO (Medium Earth Orbit): Se encuentran en una órbita entre los 10.000 y 20.000 km. Su posición respecto a la tierra no es fija, por eso necesita un número mayor de satélites para obtener una cobertura mundial. La ventaja principal de este tipo de satélites es que se reduce mucho la latencia o retardo de la señal (información). En la actualidad no hay muchos satélites
- MEO. Lo que hay se usan para posicionamiento. 
- Satélites GEO (Geoestacionaric Earth Orbit): Estos satélites orbitan a 35.848 km de la tierra, sobre el Ecuador terrestre. El período de rotación de estos satélites es exactamente 24 horas, por ello casi siempre se encuentran sobre el mismo lugar de la superficie del planeta. La mayoría de los satélites actualmente utilizados son GEO.
- Satélites HEO (Highly Elliptic Orbit): Estos satélites no siguen una órbita circular, en este caso la órbita es elíptica. Esto implica que alcanzan distancias mayores en el punto más alejado de su órbita. Se utilizan para cartografiar la superficie de la Tierra, ya que pueden detectar un gran ángulo de la superficie terrestre.

### Ecuación de enlace Satelital:

Un enlace satelital cuenta de 3 etapas. Dos están ubicadas en las estaciones terrestres, las cuales se denominan modelo de enlace de subida o bajada. La tercera etapa está ubicada en el espacio, donde la señal de subida cruza por el transpondedor de satélite y será regresado a la tierra en una frecuencia menor, que la frecuencia a la que fue transmitida.

At (dB] = GTx + GRx + Gsat. – At. Up Link – At. Down Link

GTx: Ganancia transmisor, GRx: Ganancia Receptor, Gsat: Ganancia Satélite

At. Up Link : Atenuación Subida, At. Down Link: Atenuación Bajada

### Frecuencias y Bandas Satelitales

![[image 337.png]]

### Tipo de antenas satelitales

- Antena parabólica de foco primario: La superficie de la antena es un raboloide de revolución (parábola circular). Todas las ondas inciden paralelamente al eje principal, se reflejan y van a parar al Foco. El Foco está centrado en el paraboloide. Tiene un rendimiento máximo del 60% aproximadamente, es decir, de toda la energía que llega a la superficie de la antena, el 60% llega al foco y se aprovecha, el resto no llega al foco y se pierde. Se suelen ver de tamaño grande, aproximadamente de 1,5 m de diámetro.

![[image 338.png]]

- Antena parabólica OFFSET: Este tipo de antena se obtiene recortando grandes antenas parabólicas de forma esférica. Tienen el Foco desplazado hacia abajo, de tal forma que queda fuera de la superficie de la antena. Debido a esto, el rendimiento es algo mayor que en la de Foco primario, y llega a ser de un 70% o algo más. El diámetro de las antenas es de 0,6 a 1,8 metros y se utilizan mucho en Banda Ku, ejemplo DTV.

![[image 339.png]]

- Antena parabólica CASSGRAIN: Es similar a la de Foco Primario, sólo que tiene dos reflectores; el mayor apunta al lugar de recepción, y las ondas al chocar, se reflejan y van al Foco donde está el reflector menor; al chocar las ondas, van al Foco último, donde estará colocado el detector. Se suelen utilizar en antenas muy grandes, donde es difícil llegar al Foco para el mantenimiento de la antena. Estas parábolas tienen un diámetro de 10 metros, y se utiliza mucho en Banda C.

![[image 340.png]]

### Ventajas y desventajas de las Bandas más utilizadas

![[image 341.png]]