Lo que buscamos modelar fue la temporada 2026 de la F1 obteniendo los resultados para los equipos y pilotos
El principal problema que queriamos analizar era la incertidumbre en la toma decisiones y la prediccion de puntos bajo las condiciones estocaicas de un campeonato de f1
Nuesto modelo utilizo datos historicos de la F1, para ser implementado en anylogic junto a python para la generacion de numeros aleatorios. 
Con el modelo implementado se diseño experimentos para verificar que su validez, para finalmente analizar estos resultados

El campeonato de f1 esta formado por 24 grandes premios, los cuales a su vez se dividen en 2 carreras, la qualy y la race
La qualy es una carrera individual donde se compararn los tiempos de cada piloto y de esta comparacion se obtiene el orden de salida de la Race
La race es una carrera donde todos los corredores corren juntos y en base a su puesto se les otorga una cantidad de puntos, mientras mas altos en puestos quedan mas puntos. los pilotos posteriores al puesto 10 no ganan puntos

Existen 11 equipos compuestos de 2 pilotos cada uno

Existen dos premios, el premio de constructores otorgado al equico cuya suma de puntos entre sus pilotos sea mayor y el premio de pilotos, otorgado al piloto con mayor cantidad de puntos