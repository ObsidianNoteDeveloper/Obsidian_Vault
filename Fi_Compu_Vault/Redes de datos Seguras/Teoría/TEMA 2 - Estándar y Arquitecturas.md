


## Norma o Estandar

**Norma:**
- De carácter obligatorio por organismos gubernamentales.
- Regla que se debe seguir

**Estándar:**
- Enfoque en calidad, mejora y optimización de procesos.

# Organismos de Estandarización

- Desarrollar y promover estándares abiertos y globales para redes de datos

## TIA - Telecommunications Industry Association

- Desarrolla estándares y documentos técnicos.
	
- cableado de telecomunicaciones, centros de datos, radiocomunicaciones, comunicaciones móviles y punto a punto, estructuras y torres para telecomunicaciones, sistemas satelitales y accesibilidad de productos de comunicaciones.

## ISO - International Organization for Standardization

- desarrolla Normas Internacionales mediante el consenso de expertos de sus países miembros, proporcionando soluciones y criterios comunes aplicables internacionalmente.
	
- Dicho organismo fue el desarrollador del modelo de siete capas para las redes de computadoras conocido como el modelo de referencia de interconexión de sistemas abiertos (modelo OSI).

## IEEE - Institute of Electrical and Electronics Engineers

- se dedica al avance de la tecnología mediante publicaciones científicas y técnicas, conferencias, desarrollo de estándares y actividades educativas y profesionales, con el propósito fundamental de fomentar la innovación tecnológica y la excelencia en beneficio de la humanidad.

## NOM - Norma Oficial Mexicana

- Es una regulación técnica de observancia obligatoria
	
- Su finalidad esencial es fomentar la calidad para el desarrollo económico y proteger objetivos legítimos de interés público, como la salud, seguridad, medio ambiente y derecho a la información.

# Modelo OSI de acuerdo al estándar 7498-1

**Open Systems Interconnection**

- El **modelo OSI** es el marco propuesto por la ISO para estandarizar la interconexión de sistemas abiertos: no dicta protocolos concretos, sino que describe qué debe hacer cada capa en una arquitectura por capas.

> [!Note] Protocolo
> Es un conjunto de reglas específicas relacionados al formato y tiempo de los datos transmitidos entre dos dispositivos.

El modelo OSI no prescribe protocolos concretos, sino las relaciones entre piezas en las que una capa ofrece un servicio a la capa superior a través de una interfaz bien definida.

Para prestar ese servicio, dos entidades homólogas de esa misma capa en extremos distintos se comunican mediante un protocolo.

- El punto donde una capa superior accede al servicio de la inferior se denomina **SAP (Service Access Point)**.
	
- Los datos que la capa superior entrega a la inferior son **SDU (Service Data Unit)**.
	
- La capa inferior los encapsula en su propia **PDU (Protocol Data Unit)** añadiendo cabeceras y controles necesarios


