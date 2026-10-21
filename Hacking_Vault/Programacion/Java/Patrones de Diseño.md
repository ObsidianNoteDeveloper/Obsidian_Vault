
# FUNDAMENTOS DE LA POO

## Conceptos básicos de POO

Los Objetos son instancias de clases.
- Una clase es como un plano que define la estructura de los objetos, que son instancias concretas de esa clase.

**Jerarquías de clase**

Superclase/_Clase padre_ (enumera los atributos y comportamiento común) >> Subclase/_Clase hija_ (heredan el estado y el comportamiento de su padre y se limitan a definir atributos o comportamientos que son diferentes).
- Las flechas con punta triangular hueca indican herencia y siempre van desde una subclase a una superclase.
- Las flechas de varias subclases se pueden solapar o dibujarse por separado.

<div style="text-align: center;">  
<img src="Pasted%20image%2020261016140706.png" width="500">  
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 1</b>. Diagrama UML de una jerarquía de clases. Todas las clases de este diagrama son parte de la jerarquía de clases Animal.
</div>

> [!Note]
> En un diagrama UML las clases se pueden simplificar si es más importante mostrar sus relaciones que sus contenidos

Las subclases pueden sobrescribir el comportamiento de los métodos que heredan de clases padre.
- Una subclase puede sustituir completamente el comportamiento por defecto o limitarse a mejorarlo con material adicional.

#### Los pilares de la POO

**Abstracción**
- Es el modelo de un objeto o fenómeno del mundo real, limitado a un contexto específico, que representa todos los datos relevantes a este contexto con gran precisión, omitiendo el resto.

**Encapsulación**
- Capacidad que tiene un objeto de esconder partes de su estado y comportamiento de otros objetos, exponiendo únicamente una interfaz limitada al resto del programa.

> [!Note]
> **Interfaz:** una parte pública de un objeto, abierta a interacciones con otros objetos

- _Encapsular_ significa hacerlo `privado` y, por ello, accesible únicamente desde dentro de los métodos de su propia clase.
- Existe un modelo un poco menos restrictivos llamado `protegido` que hace que un miembro de una clase también esté disponible para las subclases.

> [!Note]
> También existe el tipo `interface`.
> - Las interfaces en UML se parecen mucho a las clases, pero sólo tienen métodos.
> - Las flechas con punta triangular hueca y líneas discontinuas indican que las clases implementan una interfaz.
> - Varias clases pueden implementar una interfaz.

<div style="text-align: center;">  
<img src="Pasted%20image%2020261016141600.png" width="500">  
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 2</b>. Diagrama UML de una jerarquía de clases. Todas las clases de este diagrama son parte de la jerarquía de clases Animal.
</div>

**Herencia**

La herencia es la capacidad de crear nuevas clases sobre otras existentes.

En la mayoría de los lenguajes de programación una subclase puede extender una única superclase. Por otro lado, cualquier clase puede implementar varias interfaces al mismo tiempo.

<div style="text-align: center;">  
<img src="Pasted%20image%2020261016142602.png" width="300">  
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 3</b>. Diagrama UML de extensión de una única clase en comparación con la implementación de múltiples interfaces al mismo tiempo.
</div>

**Polimorfismo**

#### Relaciones entre objetos


# INTRODUCCIÓN A LOS PATRONES DE DISEÑO

## Qué es un patrón de diseño


## Qué aprender sobre patrones


# PRINCIPIOS DE DISEÑO DE SOFTWARE

## Principios del diseño


## Principios SOLID


# EL CATÁLOGO DE PATRONES DE DISEÑO

## Patrones creacionales

### 1. Factory Method / Método fábrica 


### 2. Abstract Factory / Fábrica abstracta


### 3. Builder / Constructor 


### 4. Prototype / Prototipo


### 5. Singleton / Instancia única


## Patrones estructurales

### 6. Adapter / Adaptador


### 7. Bridge / Puente


### 8. Composite / Objeto compuesto


### 9. Decorator / Decorador


### 10. Facade / Fachada


### 11. Flyweight / Peso mosca


### 12. Proxy


## Patrones de comportamiento 

### 13. Chain of Responsibility / Cadena de responsabilidad


### 14. Command / Comando


### 15. Iterator / Iterador


### 16. Mediator / Mediador


### 17. Memento / Recuerdo


### 18. Observer / Observador


### 19. State / Estado


### 20. Strategy / Estrategia


### 21. Template Method / Método plantilla


### 22. Visitor / Visitante