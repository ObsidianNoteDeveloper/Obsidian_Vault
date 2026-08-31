# Construcción de cables UTP para conexión directa y cruzada


- [[#Capa 1 del Modelo OSI]]
	- [[#Capa 1 del Modelo OSI]]
		- [[#Cable UTP]]
- [[#Reporte]]




## Capa 1 del Modelo OSI

La **Capa 1** del Modelo OSI es la **Capa Física**. Es la base de toda la comunicación en red y se encarga de transmitir los bits de datos binarios (0s y 1s) a través de un medio físico.

Convierte los datos digitales (bits) en señales eléctricas, ópticas o de radio. Determina los cables, conectores y frecuencias que se van a utilizar. Regula la tasa de transferencia de datos (bits por segundo).




### Cable UTP

Un **cable UTP** (UnShielded Twisted Pair o par trenzado sin blindaje) es el estándar universal para las conexiones de red locales.  Es un tipo de cable de red formado por pares de hilos de cobre entrelazados sin una malla protectora externa. El trenzado de los hilos ayuda a reducir el ruido eléctrico y las interferencias de señales externas.


#### Características principales

- **Sin blindaje:** No incluye láminas metálicas ni mallas de protección contra interferencias fuertes.
	
- **Diseño interno:** Contiene cuatro pares de hilos de cobre de colores.
	
- **Conectores:** Terminan comúnmente en fichas de tipo [[#Conectores RJ45]].
	
- **Ventajas:** Es barato, muy flexible, compatibilidad universal y fácil de instalar en espacios reducidos.
	
- **Desventajas:** Vulnerable a interferencias, distancia limitada, menor resistencia física y aunque es veloz para redes locales, su capacidad de transmisión de datos es inferior a la de la **fibra óptica**.



##### Conectores RJ45

Las fichas de tipo **RJ45** (tambien llamadas conectores **RJ45**) son los enchufes que se conectan a las computadoras, módems, routers y consolas a Internet. Las siglas **RJ** significan _Registered Jack_ (Clavija Regitrada) y el 45 es el número de la norma de su diseño técnico.

**Estandares de colores (Cómo se acomodan los cables)

Existen dos normas universales:
	
- **T568A:** Utilizada comúnmente en instalaciones telefónicas y de redes institucionales.

- **T568B:** Es la más popular en todo el mundo para redes domésticas y de oficina.

> [!Note]
> Si ambos extremos del cable usan la misma norma (por ejemplo, **B en un lado y B en el otro**), se crea un **cable directo**, que sirve para conectar un dispositivo (PC) a un switch o router. Si se combina una norma en cada extremo (A de un lado y B del otro), se crea un **cable cruzado**, usado para conectar dos dispositivos iguales directamente entre sí (PC a PC). 


#### Usos Comunes

- Conexión a Internet en casas y oficinas 
	
- Redes de área local o **LAN**
	
- Sistemas de telefonía fija y cámaras de seguridad.

#### Categorías Frecuentes

- **Cat 5e:** Soporta hasta 1,000 Mbps (1 Gbps) de velocidad.

- **Cat 6:** Mejora el ancho de banda y reduce la interferencia interna entre pares.

- **Cat 6a / Cat 7:** Diseñados para velocidades mayores de hasta 10 Gbps a frecuencias más altas.

---

# Reporte

**¿Cuál es la diferencia que existe al emplear (no al construir) el código de colores T568\-A y T568-B dentro del cableado estructurado?**

La principal diferencia entre ambos es el intercambio de los pares verde y naranja


**Investigue la configuración para un cable cruzado en redes de tipo Gigabit Ethernet**

Para un cable cruzado, empleamos el estándar T568-A en un extremo y T568-B en el otro extremo, donde se produce el cruce de los pares verde y naranja

**Conclusión**

La construcción de cables UTP permite comprender de manera práctica el funcionamiento de la **Capa Física del modelo OSI**, ya que el orden de los conductores determina cómo se establecen las conexiones eléctricas entre los dispositivos de una red.

Es importante entender que los estándares **T568A y T568B** no representan diferentes categorías de cable, sino diferentes formas de organizar los conductores dentro de un conector RJ45. Utilizar el mismo estándar en ambos extremos produce un cable directo, mientras que utilizar T568A en un extremo y T568B en el otro produce un cable cruzado.


**Bibliografia en formato APA**

Cisco Systems. (2026). _Configuración y verificación de la negociación automática de semidúplex/dúplex completo de Ethernet 10/100/1000 Mb

Cisco Systems. (2006). _Especificaciones de los cables Ethernet 100BaseTX y 10BaseT

Cisco Systems. (2019). _Cisco Catalyst 1000 Series Switch Hardware Installation Guide











