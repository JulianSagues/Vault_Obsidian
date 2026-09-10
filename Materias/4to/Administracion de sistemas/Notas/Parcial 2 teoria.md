
# Expo1: Arquitecturas Centralizadas, Descentralizadas y Distribuidas

## Idea central
Una arquitectura informática define **dónde se almacenan los datos, quién procesa, cómo se comunican los equipos y cómo se administra la red**.

## 1. Centralizada
Todo (datos, procesamiento, administración) está en **un único servidor**. Los clientes solo piden y reciben resultados.

- **Ventajas:** fácil de administrar, buen control y seguridad, backups simples.
- **Desventajas:** si el servidor cae, cae todo el sistema; cuello de botella; servidor caro.
- **Ejemplos:** bancos tradicionales, universidades con servidor central.

## 2. Descentralizada
Existen **varios centros de procesamiento independientes** (cada sede/departamento tiene su propio servidor y base de datos), que se comunican entre sí pero mantienen autonomía.

- **Ventajas:** autonomía por área, una falla solo afecta a esa sede, menor carga por equipo.
- **Desventajas:** administración más compleja, riesgo de duplicar información, difícil mantener todo sincronizado.
- **Ejemplos:** empresas con sucursales, organismos de gobierno, universidades con sedes propias.

## 3. Distribuida
El procesamiento y los datos están **repartidos entre múltiples equipos (nodos)** que colaboran como si fueran un solo sistema. El usuario no sabe en qué nodo se ejecuta algo.

- **Ventajas:** alta disponibilidad, escalabilidad, tolerancia a fallos, mejor aprovechamiento del hardware, más velocidad con muchos usuarios.
- **Desventajas:** administración compleja, difícil sincronizar datos, necesita redes confiables.
- **Ejemplos:** Google, Netflix, AWS, Big Data, bases de datos distribuidas.

## Comparación rápida

| Característica       | Centralizada | Descentralizada | Distribuida |
|-----------------------|--------------|------------------|-------------|
| Procesamiento         | 1 servidor   | Varios independientes | Muchos equipos juntos |
| Administración        | Simple       | Media            | Compleja    |
| Escalabilidad         | Baja         | Media            | Alta        |
| Tolerancia a fallos   | Baja         | Media            | Alta        |
| Costo inicial         | Alto         | Medio            | Variable    |

## Conclusión
Hoy la mayoría de las organizaciones usa arquitecturas **distribuidas** por la nube e Internet, pero las tres siguen siendo válidas según el contexto: centralizada = control y simpleza; descentralizada = autonomía; distribuida = disponibilidad y escalabilidad.

# Expo2: Medios de Interconexión Cableados

## Idea central
Son elementos físicos que transportan datos entre dispositivos, convirtiendo la información en señales **eléctricas** (cobre) u **ópticas** (fibra). Los principales son: par trenzado, coaxial y fibra óptica.

## 1. Cable de Par Trenzado
Pares de cobre trenzados entre sí para **reducir interferencias electromagnéticas**. Usado en redes LAN, con conectores **RJ-45** (8 posiciones).

- **UTP** (Unshielded Twisted Pair): sin blindaje, bajo costo, fácil instalación. El más usado en Ethernet.
- **STP** (Shielded Twisted Pair): con blindaje extra, mejor contra interferencias, útil en ambientes con mucha electricidad.

**Normas T568A y T568B:** esquemas de conexión de los cables en el conector RJ-45; difieren en la posición de los pares verde y naranja. **Regla clave:** no mezclar normas en la misma instalación (salvo cable cruzado), o falla la conectividad.

- **Ventajas:** bajo costo, fácil instalación y mantenimiento, buena flexibilidad.
- **Desventajas:** más sensible a interferencias, distancia limitada, rendimiento depende de la categoría del cable.

## 2. Cable Coaxial
Conductor de cobre central rodeado de aislante, malla metálica y cubierta exterior. Señal eléctrica. Fue clave en Ethernet antiguo, hoy usado sobre todo en **TV, cámaras y servicios de acceso por cable**.

**Estructura:** conductor central → dieléctrico/aislante → blindaje metálico → cubierta exterior.

- **Ventajas:** buena protección contra interferencias, resistente, cubre distancias considerables, apto para radiofrecuencia/video.
- **Desventajas:** menos flexible que el par trenzado, instalación más difícil, reemplazado en LAN modernas por UTP/fibra.

## 3. Fibra Óptica
Transmite información mediante **pulsos de luz** por un núcleo de vidrio (no usa corriente eléctrica). Permite grandes velocidades y distancias, con **alta resistencia a interferencias electromagnéticas**.

**Estructura:** cubierta del cable → capas aislantes → buffer → unidades de fibra → miembro de fuerza (FRP, resistencia mecánica).

- **Fibra monomodo (SMF):** núcleo pequeño, un solo modo de propagación → ideal para **larga distancia** y telecomunicaciones.
- **Fibra multimodo (MMF):** núcleo más grande, múltiples modos → ideal para **distancias cortas** (edificios, campus, data centers).

- **Ventajas:** muy alta capacidad, grandes distancias, altísima resistencia a interferencias, baja atenuación.
- **Desventajas:** mayor costo inicial, instalación especializada, fibras físicamente delicadas, empalmes complejos.

## Comparación rápida

| Característica | Par trenzado | Coaxial | Fibra óptica |
|---|---|---|---|
| Señal | Eléctrica | Eléctrica | Óptica |
| Flexibilidad | Alta | Media/baja | Variable |
| Resistencia a interferencias | Media | Buena | Muy alta |
| Distancias largas | Limitadas | Buenas según uso | Excelente |
| Instalación | Sencilla | Moderada | Especializada |
| Uso actual | LAN | TV/RF/HFC | Backbone y telecom |

## Aplicaciones actuales
- **Par trenzado:** hogares, oficinas, redes LAN, empresas, centros de datos.
- **Coaxial:** TV por cable, internet por cable, antenas, radiofrecuencias.
- **Fibra óptica:** proveedores de internet, redes troncales, centros de datos, redes metropolitanas, enlaces entre edificios.

## Conclusión
No hay un medio "mejor" en todos los casos: **par trenzado** = bajo costo y fácil instalación (LAN); **coaxial** = perdió protagonismo en LAN pero sigue en TV/RF; **fibra óptica** = máxima capacidad y distancia, clave en redes troncales y data centers. La elección depende de distancia, velocidad, presupuesto y ambiente.
# Expo3: Redes por Radiofrecuencia

## ¿Qué es la radiofrecuencia?
Tecnología inalámbrica que usa **ondas electromagnéticas (ondas de radio)** para transmitir información. El **transmisor** convierte datos en ondas de radio; el **receptor** las reconvierte en información. El espectro útil va de **300 Hz a 300 GHz**.

## Elementos de la comunicación
- **Modulación de frecuencia:** convierte señales en ondas (AM, FM, PM).
- **Antena:** envía/recibe ondas; su diseño y ubicación afecta alcance y calidad.
- **Codificación/decodificación de canales:** mejora estabilidad y anti-interferencia.
- **Gestión de energía:** ajusta potencia para no interferir con otras señales.
- **Gestión de bandas de frecuencia:** administra el espectro para evitar desperdicio e interferencias.

## Clasificación según alcance
| Tipo | Alcance | Ejemplo |
|---|---|---|
| **WPAN** (personal) | ~10 m | Bluetooth |
| **WLAN** (local) | Edificio/oficina | WiFi doméstico |
| **WMAN** (metropolitana) | Tamaño de ciudad | 2G/3G/4G/5G |
| **WWAN** (amplia) | Muchos km | Redes celulares 4G/5G |

## Bluetooth (WPAN)
Conecta dispositivos a **corta distancia** (ej: celular-parlante), reemplazando cables simples. Usa banda de **2,4 GHz** (compartida, buen equilibrio alcance/penetración).

**Topologías Bluetooth:**
1. **Punto a punto:** conexión directa 1 a 1.
2. **Piconet:** varios dispositivos comparten canal, uno actúa como central.
3. **Scatternet:** dos o más piconets conectadas entre sí.
4. **Broadcast:** un dispositivo transmite a muchos (1 a muchos).
5. **Bluetooth mesh:** comunicación de muchos a muchos, **descentralizada** (red en malla).

## WiFi (WLAN)
Transmite ondas de radio en frecuencias de **2.4 GHz, 5 GHz y 6 GHz**. A mayor frecuencia → más velocidad pero menos alcance (2,4 GHz llega más lejos, 6 GHz es más rápido pero de menor rango). Usa protocolos **IEEE 802.11**.

**Modos de conexión:**
- **Infraestructura:** conecta equipos inalámbricos a una red cableada mediante un **Punto de Acceso** (o router).
- **Ad-hoc:** dispositivos conectados entre sí sin punto de acceso, de igual a igual (**Peer to Peer**), útil para compartir info puntualmente a baja velocidad.

## Redes celulares 4G y 5G (WWAN)
Administradas por operadores de telecomunicaciones. Dividen la cobertura en **celdas**, cada una atendida por una **estación base** conectada a una red central. Al moverse el usuario entre celdas, la conexión se **transfiere automáticamente**. No usan una única frecuencia (a diferencia de WiFi/Bluetooth).

- **4G (LTE):** mejora la transmisión de datos móviles. Celdas de **5 a 100 km**, latencia **menor a 50 ms**.
- **5G:** evolución del 4G. Mayor velocidad, **menor latencia** (hasta ~1 ms) y mayor capacidad de dispositivos conectados → habilita **IoT**. Aprovecha infraestructura ya existente de 4G.

## Conclusión
Las redes inalámbricas ofrecen **movilidad y flexibilidad** que el cable no iguala, organizadas según alcance (WPAN, WLAN, WWAN). Todas se basan en la **radiofrecuencia**, un recurso limitado que debe gestionarse bien para evitar interferencias. El salto de **4G a 5G** es clave sobre todo por la **reducción drástica de latencia**, habilitando aplicaciones críticas (telemedicina, vehículos conectados). A futuro se espera la convivencia de 4G/5G y la llegada del **6G**.
# Expo3: Medios de Conexión Satelital

## Idea central
Cuando la fibra o las redes móviles no son viables (geografía extrema, catástrofes), el **internet satelital** conecta usuarios con la red mundial mediante satélites en órbita. En la última década pasó de ser lento y caro a una alternativa competitiva.

## Arquitectura de una red satelital
1. **Segmento Espacial (satélite):** actúa como repetidor: recibe la señal, la amplifica, cambia su frecuencia y la retransmite.
2. **Segmento Terrestre (Gateway/Telepuerto):** instalaciones conectadas al backbone de Internet mundial por fibra de alta capacidad.
3. **Segmento de Usuario (VSAT):** antena parabólica (necesita línea de vista al cielo) + módem satelital que decodifica la señal para los equipos del cliente.

## Funcionamiento
1. El usuario envía la solicitud → antena → **uplink** (enlace ascendente) al satélite.
2. El satélite amplifica y retransmite hacia el **gateway**, conectado a Internet.
3. La respuesta vuelve por el camino inverso: Internet → gateway → satélite → **downlink** (enlace descendente) → usuario.
4. Todo ocurre en milisegundos, permitiendo conectividad donde no llegan redes terrestres.

## Clasificación de satélites según órbita
| Tipo | Distancia | Latencia | Características |
|---|---|---|---|
| **GEO** | ~35.786 km | 500-700 ms | Fijos respecto a la Tierra; 3-4 satélites cubren casi todo el planeta; ideal para TV/broadcast; alta latencia afecta tiempo real |
| **MEO** | 2.000-35.786 km | Media | Usado en GPS/Galileo; ej. O3b (cruceros, islas); antenas deben rastrear el satélite |
| **LEO** | 160-2.000 km | 20-40 ms | La revolución actual (Starlink, OneWeb, Kuiper); baja latencia similar a banda ancha; requiere miles de satélites (constelación) y antenas **Phased Array** |

## Bandas de frecuencia
- **Banda C (4-8 GHz):** antenas grandes (2-3m); resiste bien la lluvia; usada en zonas tropicales.
- **Banda Ku (12-18 GHz):** estándar en TV satelital y VSAT corporativo; antenas chicas (60-90cm); sufre **atenuación por lluvia (Rain Fade)**.
- **Banda Ka (26-40 GHz):** mucho ancho de banda, cientos de Mbps (HTS, LEO); muy sensible al clima, requiere ajuste dinámico de potencia.

## Ventajas y desafíos
- **Ventajas:** cobertura en zonas extremas (océanos, desiertos, montañas); despliegue rápido (horas, sin obras civiles); independencia terrestre (útil ante desastres).
- **Desafíos:** costo por GB más alto que terrestre (aunque LEO lo está bajando); sensibilidad climática; necesidad de línea de vista sin obstrucciones.

## Casos de uso
- Aviación y marítimo (WiFi a bordo).
- Comunidades rurales (escuelas, hospitales sin ISP rentable).
- Respaldo corporativo/failover ante corte de fibra.

## Situación en Argentina
Según **ENACOM**, las conexiones satelitales crecieron **7.180%**: de 2.992 (fines 2023) a 217.812 (mediados 2025), por desregulación de cielos y nuevos proveedores. Hay un convenio público-privado (+U$S21 millones) con **Starlink** para llevar internet satelital a escuelas estatales.

**Proveedores en el mercado argentino:**
- **Starlink (SpaceX):** líder en LEO.
- **Amazon Leo (Project Kuiper):** próximo a llegar, acuerdo con DirecTV.
- **Orbith:** usuarios finales y mayorista para ISPs rurales.
- **Hughes / Eutelsat OneWeb:** combinan GEO (Júpiter 3) con distribución LEO; enlaces corporativos.
- **ARSAT:** estatal, gestiona satélites geoestacionarios ARSAT-1 y ARSAT-2 desde Benavídez.

## Conclusión
Gracias a la banda Ka y las constelaciones LEO, la brecha de rendimiento entre satélite y redes terrestres se achicó drásticamente. A futuro se espera integración entre redes satelitales y 5G terrestre para un ecosistema global sin interrupciones.
# Expo5:Gestión de Centros de Procesamiento de Datos (CPD)

## Idea central
Un CPD es la infraestructura física y lógica que aloja los sistemas críticos (servidores, almacenamiento, redes, energía, climatización, seguridad). Gestionarlo bien implica 4 bloques: **operación diaria, recursos/capacidad, seguridad/continuidad y gobernanza**. Una mala gestión = interrupciones, sobrecostos y riesgo legal.

## 1. Operaciones diarias y mantenimiento

**ITSM (IT Service Management):** enfoque integral que acompaña todo el proceso: planificar, desplegar y dar soporte. Integra dos plataformas:
- **BMS (Building Management System):** gestiona el edificio completo (temperatura, humedad, seguridad), interfaz general.
- **DCIM (Data Center Infrastructure Management):** exclusivo del data center, más técnico: gestión de activos TI, monitoreo de red y rendimiento.

**Mantenimiento:**
- **Preventivo:** revisiones periódicas programadas para detectar fallas antes de que ocurran.
- **Correctivo:** actúa cuando ya hay falla. Se divide en:
  - *No programado:* falla inesperada, solución inmediata.
  - *Programado:* la reparación puede esperar recursos disponibles.

**Gestión de Activos y Cambios:** proceso estructurado para manejar cambios en TI (reactivos o proactivos), buscando minimizar incidentes y alinearse con objetivos/normas. Sigue 4 pasos:
1. **Planificación y evaluación** (riesgos, criterios de éxito).
2. **Aprobación del cambio** (por la CCB - Junta de Control del Cambio).
3. **Implementación** (coordinada, comunicación transparente).
4. **Supervisión y revisión** (pruebas post-implementación, feedback documentado).

## 2. Recursos y capacidad
Un datacenter necesita **5 subsistemas** para ser considerado tal (si falta uno, es "una sala con servidores"):
1. Espacio físico y racks (white space).
2. Alimentación eléctrica (UPS, generadores, PDU).
3. Refrigeración (CRAC/CRAH, contención de pasillos).
4. Cableado estructurado (cobre y fibra organizados).
5. Seguridad física y monitoreo (control de acceso, CCTV, sensores).

## 3. Seguridad, ciberseguridad y continuidad
Deben protegerse contra intrusiones, incendios, catástrofes naturales, cortes de luz, errores humanos y ataques.

- **Seguridad física:** control de acceso autenticado (mínimo privilegio necesario), personal de seguridad 24hs (disuasión), CCTV en accesos, protección de equipos de energía/refrigeración/redes, resistencia a inundaciones/incendios, ubicación geográfica óptima.
- **Seguridad lógica:** normas estrictas de supervisión y auditoría; pruebas y revisión de código antes de desplegar apps, ya que un malware puede comprometer no solo el CPD sino a todos los clientes alojados.

## 4. Gobernanza, métricas y tendencias

**PUE (Power Usage Effectiveness):** ratio entre energía total consumida y la energía usada realmente por los servidores. Estándar creado por The Green Grid (2007) para medir eficiencia energética.
- Cuanto más bajo, mejor: en 2024, los mejores CPD llegaron a **1,09**; la media global es **~1,6**; los de última generación logran **<1,4**.
- **Niveles de medición:**
  - **PUE1:** suministro principal (UPS), mediciones mensuales manuales.
  - **PUE2:** unidades de distribución (PDU), lecturas diarias automatizadas.
  - **PUE3:** equipos informáticos, mediciones cada ≤15 min (mayor precisión).

**Normativas:** regulan aspectos físicos (accesos, incendios, redundancia eléctrica) y lógicos (ciberseguridad, gestión de usuarios, encriptación). Buscan asegurar disponibilidad, seguridad y continuidad del negocio, no solo cumplir un requisito legal.

**Clasificación Tier (ANSI/TIA-942):** desarrollada por el **Uptime Institute**, determina la capacidad del CPD para tolerar fallos y mantener disponibilidad (niveles/tiers).

## Conclusión
Un CPD resiliente combina los 4 bloques (operación, capacidad, seguridad, gobernanza). Tendencias futuras: **IA aplicada al DCIM** (mantenimiento predictivo), **edge computing** (reducir latencia acercando el procesamiento al usuario) y mayor exigencia de **sustentabilidad** (PUE como KPI regulatorio).
# Expo6: Implementación de Data Center

## 1. Qué es un Data Center
Instalación física diseñada para alojar sistemas informáticos, servidores, redes y almacenamiento. Garantiza operaciones digitales continuas y seguras mediante: **almacenamiento**, **procesamiento** y **conectividad**.

## 2. Planificación y análisis de requisitos
- **Capacidad:** definida según volumen actual y crecimiento proyectado.
- **Tráfico de red:** ancho de banda, QoS, conectividad con ISPs.
- **Seguridad y normativa:** control de acceso, cámaras, firewalls, IDS, cumplimiento legal/ambiental.
- **Ubicación:** bajo riesgo de desastres naturales, energía confiable, múltiples proveedores de internet.
- **Diseño arquitectónico:** espacios, disposición de equipos y soporte (refrigeración, energía, red).
- **Infraestructura eléctrica:** sistemas redundantes (UPS y generadores).
- **Refrigeración:** aire acondicionado, refrigeración líquida o por inmersión.
- **Disposición de servidores:** racks y cableado con separación de pasillos fríos/calientes.
- **Infraestructura de red:** switches/routers/firewalls redundantes, capacidad de redirigir tráfico ante fallas.

## 3. Construcción del Data Center
Etapas principales:
1. **Obra civil:** pisos técnicos elevados (cableado y flujo de aire), recubrimientos ignífugos y sellado contra humedad.
2. **Instalación eléctrica y refrigeración:** UPS, generadores, aire de precisión; separación física de pasillos fríos/calientes.
3. **Cableado estructurado y montaje:** armado de racks, tendido ordenado de fibra/cobre en bandejas.
4. **Medidas de seguridad:** firewalls, IDS, protección antimalware, cifrado, control de accesos.
5. **Pruebas y validación:** pruebas de estrés, cargas térmicas/eléctricas, simulacros de corte de energía.
6. **Implementación tecnológica:** sistemas operativos, apps de gestión, **DCIM**, sistemas de backup y recuperación.

## 4. Clasificación de Data Centers
Una empresa puede usar varios tipos combinados:
- **On-premise:** infraestructura propia, gestión total por la empresa.
- **Edge:** instalaciones pequeñas cerca del usuario, baja latencia (IoT, streaming, gaming, IA/ML).
- **Colocation:** el cliente es dueño del hardware pero alquila espacio (edificio, energía, refrigeración, seguridad) a un tercero.
- **Managed:** el cliente alquila espacio **y** servidores/hardware al proveedor.
- **Modular:** instalaciones portátiles en contenedores, ideales para recuperación de desastres o despliegues temporales.
- **Hyperscale:** instalaciones masivas (AWS, Azure, Google Cloud), miles/millones de servidores, base de la nube pública.

## 5. Niveles (Tiers) — Uptime Institute
| Nivel | Características |
|---|---|
| **I** | Capacidad básica: 1 fuente de energía, refrigeración constante, 1 generador. |
| **II** | Componentes redundantes (energía y refrigeración), permite mantenimiento sin cortar del todo. |
| **III** | Mantenible simultáneamente: rutas y componentes redundantes, sin parar operaciones durante mantenimiento. |
| **IV** | Sistemas independientes y físicamente aislados, **tolerante a fallos**: las operaciones siguen aunque falle un componente. |

## 6. Gestión y mantenimiento
Requiere estrategia integral de seguridad (controles administrativos + informáticos, firewalls, protocolos de ciberseguridad).

- **Administrador de Data Center:** mantiene, instala/actualiza software y hardware, organiza el espacio físico.
- **DCA (Data Center Administrator):** especialista técnico en infraestructura física/virtual, hardware y software.
- **DCM (Data Center Manager):** responsable ejecutivo de operaciones globales, personal, seguridad y mantenimiento.

**Tendencia actual:** prácticas eco-sustentables (impulsadas por el crecimiento de IA): virtualización, energías renovables, hardware de bajo consumo.

## Conclusión
Los Data Centers son el núcleo de la era digital (nube, IA, big data). Un diseño bien planificado, ingeniería precisa y gestión profesional garantizan escalabilidad, disponibilidad y resiliencia a largo plazo — invertir en esta infraestructura es una decisión estratégica, no solo técnica.

# Expo7: Benchmarks de Hardware

## Idea central
Los benchmarks son **pruebas estandarizadas** que miden el rendimiento de componentes o de un equipo completo, bajo condiciones específicas. Un solo benchmark **no representa el rendimiento total**: hay que combinar varias pruebas y relacionarlas con el uso real.

## ¿Para qué sirven?
- Comparar rendimiento entre equipos.
- Elegir el hardware adecuado para una tarea (programación, video, gaming).
- Detectar problemas de rendimiento o fallas de hardware.
- Verificar si una actualización (drivers, RAM, SSD) mejoró el equipo.
- Identificar **cuellos de botella**.
- Evaluar servidores antes de ponerlos en producción.

## Componentes evaluados y herramientas
| Componente | Qué mide | Herramientas |
|---|---|---|
| **CPU** | Cálculos e instrucciones (single-core y multi-core) | Cinebench, Geekbench, PassMark |
| **GPU** | Procesamiento gráfico paralelo (juegos, render 3D) | 3DMark, FurMark |
| **RAM** | Velocidad lectura/escritura, ancho de banda, latencia | AIDA64, MemTest86 |
| **Almacenamiento** | Velocidad lectura/escritura secuencial y aleatoria | CrystalDiskMark, AS SSD Benchmark |
| **Sistema completo** | Rendimiento general | PCMark |

## Tipos de benchmarks
- **Sintéticos:** operaciones repetitivas diseñadas específicamente para medir hardware (Cinebench, 3DMark, CrystalDiskMark). Fáciles de comparar, pero no siempre reflejan el uso real.
- **De uso real:** tareas habituales (editar video, renderizar, compilar). Ej: PCMark. Reflejan mejor la experiencia real, pero son más difíciles de reproducir exactamente.

## Factores que influyen en el resultado
- Temperatura y refrigeración del equipo.
- Programas en segundo plano.
- Drivers actualizados o no.
- Configuración del sistema operativo.

Por esto, equipos con specs similares pueden dar resultados distintos → se recomienda repetir pruebas en condiciones parecidas.

## Aplicación en un CPD
Los benchmarks verifican que los servidores funcionen bien **antes de entrar en producción**. Se usan estándares reconocidos:
- **SPEC:** incluye *SPEC CPU* (procesador) y *SPECpower* (relación rendimiento/consumo energético, clave en un data center).
- **TPC:** incluye *TPC-C* (simula transacciones de base de datos) y *TPC-H* (consultas sobre grandes volúmenes de datos).

También ayudan a evaluar almacenamiento, detectar equipos de bajo rendimiento y planificar ampliaciones (rendimiento, energía, refrigeración).

## Ventajas y desventajas
| Ventajas | Desventajas |
|---|---|
| Comparación objetiva de hardware | Un sintético no siempre refleja el uso diario |
| Detectan fallas | Los resultados varían según configuración |
| Facilitan decisiones de compra | El calor durante la prueba puede bajar el rendimiento |
| Comprueban mejoras tras actualizaciones | Comparar versiones distintas del mismo benchmark da conclusiones erróneas |
| Útiles para planificar infraestructura | Interpretarlos bien requiere conocimiento técnico |

## Buenas prácticas para mediciones confiables
- Cerrar programas de fondo y pausar descargas.
- Usar siempre la **misma versión** del benchmark.
- Repetir la prueba varias veces y descartar valores atípicos.
- Dejar que el equipo vuelva a temperatura base entre pruebas.
- Combinar benchmarks **sintéticos + de uso real**.
- Documentar la configuración (drivers, SO, perfil de energía) junto a los resultados.

## Conclusión
Los benchmarks son clave para medir, comparar y decidir sobre hardware/servidores, pero **ningún benchmark aislado** representa el rendimiento real: conviene combinar pruebas y considerar el uso real del sistema.
# Expo8: Análisis Integral de Riesgos en el CPD: Vulnerabilidades Topológicas y Lógicas

## Idea central
La disponibilidad de red en un CPD depende del **diseño físico (topología)** y de la **correcta configuración lógica** de los dispositivos. Una falla en cualquiera de los dos puede comprometer la continuidad del servicio.

## Riesgos Físicos (según topología)

- **Bus (ducto):** todos conectados a un mismo cable principal. **Diseño más frágil**: un corte en el ducto o falla de terminadores provoca rebote de señal, colisiones y caída total de la red.
- **Estrella:** todos conectan a un equipo central (switch). **Riesgo:** punto único de falla — si el switch pierde energía, se daña o se corta su enlace troncal, toda esa sección del CPD queda aislada.
- **Anillo:** dispositivos en círculo cerrado, acceso controlado por paso de **token**. Un corte en cualquier tramo rompe el anillo completo y detiene el token, dejando toda la red inoperante.
- **Malla:** interconexión múltiple entre dispositivos. Muy tolerante a cortes individuales, pero el riesgo pasa a ser la **complejidad**: exceso de cableado que obstruye el flujo de aire frío (sobrecalentamiento) y mayor probabilidad de error humano al desconectar cables durante mantenimiento.

## Riesgos Lógicos

- **Tormentas de difusión (Broadcast Storms):** en topologías con caminos redundantes o switches mal configurados, un paquete de broadcast circula sin fin si no hay mecanismo anti-bucles → satura el ancho de banda y puede colapsar la red sin ningún daño físico.
- **Fallas del protocolo Spanning Tree (STP):** STP bloquea caminos lógicamente para evitar bucles. Si está mal configurado, deshabilitado o se conecta un dispositivo incompatible, se generan bucles de capa 2 → derivan en tormentas de difusión.
- **Saturación de la tabla CAM del switch:** un atacante (o falla) inunda el switch con MACs falsas, agotando su tabla de direccionamiento. El switch termina comportándose como un **hub**, retransmitiendo todo el tráfico a todos los puertos → compromete rendimiento y confidencialidad.
- **ARP Spoofing (envenenamiento de ARP):** como ARP no autentica, un dispositivo malicioso puede asociar su MAC a la IP de otro equipo (ej. el gateway) para interceptar, modificar o descartar tráfico, sin fallas físicas visibles.
- **Segmentación lógica insuficiente (VLANs):** si no hay buena segmentación por VLAN, o hay errores de "VLAN hopping" en puertos troncales, un dispositivo comprometido en un segmento puede acceder a recursos de otro segmento que debería estar aislado.
- **Punto único de falla en configuración lógica:** si rutas estáticas, tablas de enrutamiento o reglas de firewall están en un solo dispositivo sin respaldo, un error de configuración o actualización fallida puede tirar toda la red aunque el hardware esté intacto.

## Análisis de riesgos
- Los **riesgos físicos** son la mayor amenaza cuando afectan componentes críticos: bus, estrella y anillo tienen puntos cuya falla interrumpe **toda** la comunicación. La elección de topología define directamente la tolerancia a fallos.
- Los **riesgos lógicos** (mala configuración, falta de protecciones, ataques internos) pueden causar degradación del servicio, pérdida de confidencialidad o inoperatividad total, **sin necesidad de falla física**.
- Conclusión: la seguridad del CPD depende tanto de la infraestructura como de la calidad de sus configuraciones.

## Conclusión general
Reducir el riesgo no es solo agregar equipamiento o corregir fallas puntuales: requiere una **estrategia integral** que combine redundancia física, configuraciones seguras, monitoreo permanente, mantenimiento preventivo y buenos procedimientos de administración.
# Expo9: Planes de Contingencia: BCP y DRP

## Idea central
La preparación ante contingencias es lo que diferencia a una empresa que sobrevive un incidente crítico de una que cesa operaciones. Dos planes clave: **BCP** (continuidad del negocio) y **DRP** (recuperación ante desastres).

## Plan de Continuidad del Negocio (BCP)
**Definición:** estrategia global, logística y organizativa que garantiza que los procesos críticos sigan funcionando antes, durante e inmediatamente después de una interrupción. Incluye procesos manuales si la tecnología no está disponible.

**Características:**
- **Enfoque corporativo integral:** abarca todo el negocio (logística, cadena de suministro, RRHH, operaciones diarias).
- **Naturaleza proactiva:** tácticas preventivas para evitar la paralización.
- **Estructura de "paraguas":** contiene varios planes dentro, como el plan de reanudación del negocio (BRP), emergencia de ocupantes (OEP), planes de comunicación, gestión de crisis y **el propio DRP**.
- **BIA (Análisis de Impacto en el Negocio):** exige entender amenazas, estimar probabilidad de cada evento y definir el personal mínimo indispensable.

## Plan de Recuperación ante Desastres (DRP)
**Definición:** documento técnico con el paso a paso para recuperar sistemas, datos e infraestructura afectados tras un incidente.

**Características:**
- **Enfoque específico:** solo sistemas de TI.
- **Naturaleza reactiva:** se activa después del desastre.
- **Depende de inventarios y backups:** hardware/software clasificado por prioridad (crítico/importante/sin importancia); backups deben guardarse fuera de la empresa.
- **Roles técnicos:** ej. "Gestor de activos", "Supervisor de DRP".
- **Criterios estrictos de activación:** no cualquier caída activa el DRP (ej. reiniciar un servidor en 20 min es un incidente, no un desastre).
- **Escalabilidad por niveles (Tiers):**
  - **Tier 1 (misión crítica):** RTO casi inmediato (ej. base de datos de clientes, pasarela de pagos).
  - **Tier 2 (importantes):** pueden esperar 12-24 hs (ej. correo interno).
  - **Tier 3 (secundarios):** pueden estar caídos días sin afectar operación crítica.

## BCP vs. DRP: diferencias clave
| | BCP | DRP |
|---|---|---|
| Enfoque | Proactivo, estratégico | Reactivo, técnico |
| Alcance | Todo el negocio | Infraestructura TI |
| Objetivo | Que el negocio siga operando | Levantar los sistemas caídos |
| Jerarquía | Plan "paraguas" | Módulo dentro del BCP |

**Caso práctico (ciberataque):** el DRP guía a los técnicos en la recuperación de infraestructura y backups; en simultáneo, el BCP define cómo comunicar la crisis a clientes y qué procesos alternativos usan los empleados (ej. registros en papel) mientras TI soluciona el problema.

## Indicadores críticos: RPO y RTO
Se definen mediante un **BIA**, equilibrando costo de recuperación vs. impacto financiero de la inactividad.

- **RPO (Recovery Point Objective):** cantidad máxima de datos que la empresa tolera perder (ej. RPO de 4hs = tolera perder hasta 4hs de info desde el último backup). Se calcula según tasa de cambio de datos, criticidad y requisitos regulatorios.
- **RTO (Recovery Time Objective):** tiempo máximo tolerable sin que funcionen los sistemas. Se fija por debajo del **MTPD** (Período Máximo Tolerable de Interrupción), considerando costo por hora de caída (ingresos perdidos, penalidades, reputación).

**Normas relacionadas:**
- **ISO 22301:** requisitos para un Sistema de Gestión de Continuidad del Negocio (SGCN), exige definir/documentar/probar RTO y RPO.
- **NIST SP 800-34 Rev. 1:** guía federal de planificación de contingencias.
- **Regulaciones sectoriales** (NIS2, DORA, HIPAA): exigen objetivos específicos según el rubro (financiero, salud), sin valores numéricos universales pero sí realistas y probados.

## Conclusión
La **resiliencia empresarial** es la capacidad de absorber un evento disruptivo, adaptarse y recuperarse sin colapsar. BCP y DRP deben funcionar coordinados:
- **BCP:** escudo proactivo que protege al negocio completo con métodos alternativos.
- **DRP:** motor técnico que restaura la infraestructura tecnológica.

Juntos permiten que la empresa sepa cuánto daño puede tolerar (datos, tiempo, costos) y tenga planes de acción para minimizar impacto económico y reputacional.

-----
