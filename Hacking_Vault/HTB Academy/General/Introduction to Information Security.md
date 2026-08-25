Fundamental | Tier 0

# Estructura de InfoSec

La Seguridad de la Información, a menudo llamada `InfoSec`, trata de proteger la información y los sistemas de personas que no deben tener acceso a ellos.

La `InfoSec` garantiza la confidencialidad, la integridad y la disponibilidad de los datos.

#### Conceptos de seguridad

Riesgo
Amenaza
Vulnerabilidad

---

# Principios de la Seguridad de la Información 

- Confidencialidad (Confidentiality)
- Integridad (Integrity)
- Disponibilidad (Availability)
- No repudio (Non-repudiation)
- Autenticación (Authentication)
- Privacidad (Privacy)

---

# Procesos en la Seguridad de la Información

Estos procesos forman la columna vertebral de una estrategia de seguridad robusta, asegurando que se mantengan la confidencialidad, integridad y disponibilidad (la Tríada CIA) de los datos.

1. Evaluación de riesgos (Risk Assessment)
2. Planificación de la seguridad (Security Planning)
3. Implementación de controles de seguridad (Implementation of Security Controls)
4. Monitoreo y detección (Monitoring and Detection)
5. Respuesta a incidentes (Incident Response)
6. Recuperación ante desastres (Disaster Recovery)
7. Mejora continua (Continuous Improvement)

## Herramientas en la Seguridad de la Información 

- Cortafuegos (Firewalls)
- Sistemas de Detección / Prevención Intrusiones (IDS/IPS)
- Sistemas de Gestión de Información y Eventos de Seguridad (SIEM)
- Escáner de vulnerabilidades
- Herramientas de pruebas de penetración
- Herramienta de cifrado 
- Sistemas de control de acceso
- Plataformas de formación en concienciación sobre seguridad

---
Section 3 / 24
# Seguridad de la Red

|**Elemento**|**Descripción**|
|---|---|
|`Firewalls`|Actúan como barreras entre las redes internas de confianza y las redes externas no confiables, filtrando el tráfico según reglas de seguridad predeterminadas.|
|`Intrusion Detection and Prevention Systems` (`IDS`/`IPS`)|Monitorizan el tráfico de la red en busca de actividades sospechosas y toman acciones automatizadas para detectar o bloquear posibles amenazas.|
|`Virtual Private Networks` (`VPNs`)|Proporcionan conexiones seguras y cifradas a través de redes públicas, garantizando la privacidad e integridad de los datos durante la transmisión. Por ejemplo, las usan los empleados para conectarse a los recursos de la red interna.|
|`Access control mechanisms`|Incluyen protocolos de autenticación y autorización para garantizar que solo los usuarios legítimos puedan acceder a los recursos de la red.|
|`Encryption technologies`|Protegen los datos sensibles tanto en tránsito como en reposo, haciéndolos ilegibles para partes no autorizadas.|

---
Section 4 / 24
# Seguridad de Aplicaciones

Inyección SQL (SQL injection), el cross-site scripting (XSS) y los desbordamientos de búfer (buffer overflows).

El **fuzzing** (también llamado **fuzz testing** o **pruebas de entrada aleatoria**) es una técnica de ciberseguridad y pruebas de software que consiste en enviar una gran cantidad de datos inesperados, malformados o aleatorios a una aplicación para descubrir errores, vulnerabilidades o comportamientos inesperados.

---
Section 5 / 24
# Seguridad Operacional

Operational Security, a menudo abreviado como `OpSec`

En esencia, la OpSec consiste en `identificar información crítica`, analizar amenazas, evaluar vulnerabilidades e implementar medidas de protección adecuadas.

---
Section 6 / 24
# Recuperación ante desastres y continuidad del negocio

La recuperación ante desastres (Disaster Recovery, `DR`) y la continuidad del negocio (Business Continuity, `BC`) son componentes críticos de la estrategia de resiliencia de una organización.

---
Section 7 / 24

# Seguridad en la nube

shared responsibility model

---
Section 8 / 24

# Seguridad física

El objetivo es evitar que personas no autorizadas accedan físicamente a estos recursos, lo que podría provocar filtraciones de datos (data breaches), robos o daños.

- `Facilities Management Team`: Mantienen el edificio y se aseguran de que las medidas de seguridad física estén implementadas y en funcionamiento.
- `IT Security Team`: Se centran en asegurar el hardware y los equipos de red, trabajando a menudo en estrecha colaboración con los equipos de seguridad física.
- `All Employees`: Todos tienen un papel en el seguimiento de los protocolos de seguridad, como no dejar abiertas las puertas de seguridad ni compartir las tarjetas de acceso.

---
Section 9 / 24

# Seguridad móvil

Las `Redes Privadas Virtuales (Virtual Private Networks, VPN)` actúan como túneles seguros y privados que protegen tus datos mientras viajan, evitando que otros escuchen a escondidas.

#### Capas en la protección del dispositivo

| Seguridad del dispositivo | Seguridad de los datos | Seguridad de la red | Seguridad de las aplicaciones |
| ------------------------- | ---------------------- | ------------------- | ----------------------------- |

---
Section 10 / 24

# Seguridad del Internet de las Cosas

|**Actor**|**Responsabilidad**|
|---|---|
|`Device Manufacturers`|Son como los arquitectos y constructores del castillo. Su trabajo es diseñar los dispositivos con la seguridad en mente desde el principio. Esto incluye seguir principios de diseño seguro, como minimizar las características innecesarias que podrían introducir vulnerabilidades, y proporcionar actualizaciones de seguridad oportunas para hacer frente a nuevas amenazas.|
|`Network Administrators`|Estas personas son como los guardias que patrullan las murallas del castillo y vigilan quién entra y sale. Protegen las redes a las que se conectan los dispositivos de IoT, implementando medidas como la segmentación de red (network segmentation) —que es como crear diferentes secciones dentro del castillo para contener cualquier brecha— y sistemas de detección de intrusiones que les alertan de actividades sospechosas.|
|`Application Developers`|Son los escribas y eruditos, que se aseguran de que el software que interactúa con los dispositivos de IoT sea seguro. Implementan métodos de autenticación adecuados, para que solo los usuarios de confianza puedan acceder a las aplicaciones, y protegen los datos mediante cifrado y otras medidas de seguridad.|

---
Section  11 / 24

# Ataque de denegación de servicio distribuido 

Un ataque de `Distributed Denial of Service` (`DDoS`) es un intento malicioso de interrumpir el funcionamiento normal de un sitio web, servidor o servicio en línea sobrecargándolo con una avalancha de tráfico de internet.

Un ataque DDoS involucra tres componentes principales:

1. `The Attacker`: La persona o grupo que coordina el ataque, con el objetivo de perturbar un objetivo específico.
2. `The Botnet (Amplification Network)`: Una red de dispositivos comprometidos distribuidos en varias ubicaciones. Estos pueden incluir ordenadores personales, servidores e incluso dispositivos del internet de las cosas (`IoT`) como termostatos inteligentes o cámaras de seguridad que han sido secuestrados sin el conocimiento de sus propietarios.
3. `The Victim`: El servidor, servicio o red objetivo que el atacante quiere incapacitar.

---
Section 12 / 24

# Ransomware

El ransomware es un tipo de software malicioso (o malware) que se infiltra en servidores, ordenadores y redes, cifrando archivos valiosos para que resulten inaccesibles.

En mayo de 2017, un ataque masivo de ransomware conocido como [[WannaCry]] se extendió rápidamente por todo el mundo, afectando a más de 200 000 ordenadores en más de 150 países

---
Section 13 / 24

# Ingeniería Social

Existen cinco técnicas fundamentales que se utilizan, entre otras:

1. Phishing
2. Pretexting
3. Baiting
4. Tailgating
5. Quid Pro Quo

El phishing es una de las técnicas de ingeniería social más comunes. Los atacantes envían correos electrónicos o mensajes engañosos que parecen proceder de fuentes legítimas para engañar a las personas y hacer que revelen información sensible como nombres de usuario, contraseñas o números de tarjetas de crédito.

El pretexting consiste en crear un escenario inventado (un pretexto) para atraer al objetivo y extraer información o persuadirlo para que realice una acción.

El baiting (o cebo) utiliza la promesa de algo tentador para atraer a las víctimas a una trampa.

El tailgating consiste en que un atacante sigue a una persona autorizada a una zona restringida sin las credenciales adecuadas.

Los ataques de quid pro quo ofrecen un beneficio a cambio de información o acceso.

---
Section 14 / 24

# Amenaza interna

Una `amenaza interna` (insider threat) se refiere al peligro que proviene de individuos que tienen acceso autorizado a los recursos de una organización. Estos insiders abusan de sus privilegios de acceso para dañar a la organización, ya sea de forma intencionada o no.

---
Section 15 / 24

# Amenazas Persistentes Avanzadas

Una `Amenaza Persistente Avanzada` (`APT`, por sus siglas en inglés) es un ciberataque sofisticado y continuo en el que un intruso obtiene acceso no autorizado a la red de una empresa y permanece sin ser detectado durante un período prolongado.

---
Section 16 / 24

# Actores de Amenazas

Un actor de amenazas (equipo) se compone de varios miembros clave, cada uno con habilidades especializadas cruciales para ejecutar ciberataques.

---
Section 17 /  24

# Equipo Rojo 

Un equipo rojo (Red Team) es un grupo especializado de profesionales de la ciberseguridad que simula ataques del mundo real contra los sistemas, las redes e incluso las personas de una organización. Su objetivo es probar las defensas de la organización de forma exhaustiva.

---
Section 18 / 24

# Equipo Azul

El Equipo Azul (Blue Team) sirve como la primera línea de defensa en la ciberseguridad, y está compuesto por un grupo diverso de especialistas que colaboran para proteger la infraestructura digital de una organización.

Esos equipos suelen estar formados por:

| Analistas de Seguridad | Encargados de la Respuesta a Incidentes | Cazadores de Amenazas | Ingenieros de Seguridad |
| ---------------------- | --------------------------------------- | --------------------- | ----------------------- |

Los objetivos del Equipo Azul abarcan un enfoque integral de la ciberseguridad, centrándose en cuatro áreas clave:

|Monitorización continua|Implementación de controles de seguridad|Respuesta a incidentes|Colaboración y formación|
|---|---|---|---|

---
Section 19 / 24

# Equipo Púrpura

El enfoque de Equipo Púrpura (Purple Team) reúne las fortalezas de los equipos Rojo y Azul. Al alinear sus actividades y animarlos a trabajar en conjunto, las organizaciones pueden crear una postura de seguridad (security posture) más eficaz y adaptable.

---
Section 20 / 24

# Director de Seguridad de la información 

Un `CISO` es un ejecutivo de alto nivel dedicado a salvaguardar los activos de información y las tecnologías de una organización. Esta persona da forma a la visión, la estrategia y los programas para proteger a la empresa de las amenazas cibernéticas y garantizar que los datos sensibles permanezcan confidenciales, íntegros y disponibles para quienes los necesiten.

---
Section 21 /  24

# Probadores de penetración 

Un `probador de penetración` (también conocido como `hacker ético`) es un profesional de la ciberseguridad que actúa como un hacker malicioso para encontrar vulnerabilidades en los sistemas informáticos, redes o aplicaciones web de una organización, `pero` sin la intención maliciosa. Su objetivo es identificar las debilidades de seguridad antes de que los atacantes reales puedan explotarlas. Los probadores de penetración ayudan a las organizaciones a fortalecer sus defensas, garantizando que la información valiosa permanezca segura y protegida.

#### Funciones clave de un probador de penetración

- `Hacking ético`: simular ataques a sistemas, redes o aplicaciones para encontrar vulnerabilidades.
- `Identificación de fallas de seguridad`: utilizar herramientas y técnicas especializadas para descubrir debilidades que los hackers reales podrían explotar.
- `Elaboración de informes de hallazgos`: comunicar las vulnerabilidades descubiertas a la dirección y a los equipos de TI de la organización y recomendar soluciones.
- `Aprendizaje continuo`: mantenerse actualizado sobre las últimas técnicas de hacking, herramientas y mejores prácticas de seguridad para ir un paso por delante de los ciberdelincuentes.

Los probadores de penetración suelen tener formaciones diversas, pero comparten un conjunto de habilidades comunes:

- `Conocimientos técnicos`: conocimiento profundo de sistemas operativos, lenguajes de programación, protocolos de red y vulnerabilidades de software comunes.
- `Pensamiento analítico`: la capacidad de probar sistemas metódicamente e interpretar los resultados.
- `Pensar de forma innovadora`: abordar los problemas de maneras novedosas o no convencionales.
- `Habilidades de comunicación`: redactar informes detallados y explicar hallazgos complejos en términos más sencillos a las partes interesadas no técnicas.

Los probadores de penetración pueden formar parte del equipo interno de ciberseguridad de una organización o trabajar para una empresa especializada en ciberseguridad, prestando sus servicios a múltiples clientes.

---
Section 22 / 24

# Centro de Operaciones de Seguridad 

Un `Security Operations Center` (`SOC`) es una unidad centralizada que actúa como el núcleo de las operaciones de ciberseguridad de una organización. Es un lugar donde profesionales cualificados trabajan continuamente para monitorizar, detectar, analizar y responder a amenazas cibernéticas (cyber threats) e incidentes de seguridad (security incidents).

Estos analistas suelen organizarse en tres niveles según su experiencia y especialización.

|**Nivel**|**Descripción**|
|---|---|
|`Tier 1 Analysts`|Manejan la clasificación inicial de alertas y el análisis básico de amenazas.|
|`Tier 2 Analysts`|Gestionan incidentes más complejos, realizan investigaciones más profundas y asesoran a sus colegas junior.|
|`Tier 3 Analysts`|A menudo actúan como Incident Responders, abordan los problemas de seguridad más críticos y realizan análisis avanzados de amenazas.|

---
Section 23 / 24

# Cazadores de recompensas por errores

Los cazadores de recompensas por errores (bug bounty hunters) son profesionales de la ciberseguridad cualificados que operan de forma independiente para descubrir vulnerabilidades en diversos activos digitales pertenecientes a organizaciones. Estos activos pueden incluir aplicaciones de software, sitios web o sistemas de red complejos.

---
Section 24 / 24

# Recomendaciones 

















































