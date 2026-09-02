
## Índice

[Introducción a las redes de datos](#Introducción%20a%20las%20redes%20de%20datos)
[Conceptos básicos](#Conceptos%20básicos)
[Tipos de Topología](#Tipos%20de%20Topología)




# Introducción a las redes de datos

Las redes permiten el intercambio de información recursos y servicios entre dispositivos conectados.


# Conceptos básicos 

## 1.1 Redes de comunicaciones de datos. Panorama general

- **Infraestructura de Red:**
	- Las redes se componen de una infraestructura física y lógica.
	
- **Conectividad Ubicua:**
	- Las redes permiten estar conectados en cualquier momento y lugar, facilitando la colaboración y el acceso a recursos.
	
- **Procesamiento y Almacenamiento:**
	- Las redes facilitan el procesamiento y almacenamiento a gran escala en centros de datos.

## 1.2 Beneficios de las redes locales. Usos y aplicaciones

- Colaboración
- Eficiencia 
- Seguridad
- Escalabilidad

## 1.3 Topologías. Importante consideración de diseño

- **Topología Física:**
	- Es la disposición real de los cables y dispositivos.
	
- **Topología Lógica:**
	- Es la forma en que viajan los datos, aunque físicamente sea diferente.

>[!Note]
> Aunque físicamente sea estrella, puede comportarse como bus.

La topología afecta el **rendimiento** (la velocidad, confiabilidad y escalabilidad de la red). Algunas topologías requieren más hardware y cableado lo que impacta en el **costo**. La topología determina la capacidad de la red para adaptarse a cambios y crecimineto (**flexibilidad**).

# Tipos de Topología 

## Topología en estrella

**Centralizado:**
- Todos los dispositivos se conectan a un punto central (conmutador o concentrador).
	
	- Un conmutador de red (conocido en inglés como _switch_) es un dispositivo físico o lógico que conecta múltiples equipos entre sí dentro de una misma red local (LAN) para que puedan comunicarse y compartir recursos.

**Fácil de expandir:**
- Agregar nuevos dispositivos es sencillo, conectándolos al punto central.

**Vulnerabilidad:**
- Si falla el punto central, todo la red se ve afectada.

## Topología en árbol

**Estructurada:**
- Los dispositivos se organizan en una jerarquía de ramas y subramas.

**Escalabilidad:** 
- Permite expandir la red fácilmente.

**Redundancia:**
- Si falla una rama, solo se ve afectada esa sección de la red.

## Topología en anillo

**Conexión circular:**
- Los dispositivos se conectan en un "círculo", formando un bucle cerrado.

**Resiliente:**
- Si falla una conexión, los datos pueden circular en la dirección opuesta.

**Limitada:**
- El rendimiento se ve afectado a medida que se agregan más dispositivos.

### Anillo doble

- Utiliza dos anillos concéntricos independientes donde cada dispositivos se conecta a ambos para ofrecer redundancia y evitar que la red caiga si un anillo falla.

## Topología en bus

**Sencilla:**
- Todos los dispositivos se conectan a un solo cable de comunicación (`bus`).

**Económica:**
- 



![](../img/Topologias.png)