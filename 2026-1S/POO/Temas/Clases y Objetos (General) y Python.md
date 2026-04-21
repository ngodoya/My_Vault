Una #clase es una plantilla para crear objetos, donde se define un tipo de objeto especificando sus atributos y sus comportamientos (métodos).
>[!Example] Cómo se ve una clase?
>- Clase Fruta, puede tener atributos, como color, tamaño, sabor y acciones como madurar()
>	- Objeto?? podemos hablar de una manzana


```mermaid
classDiagram
    direction RL
    class Fruta{
        +Size str
        +Color list([1 0 0])
    }

```
## Objeto
Un objeto es una ==instancia== de una clase, posee atributos definidos por su clase y puede utilizar los métodos dados por ella (Padre e hijo). Puede remitirse al ejemplo de la clase fruta y su #instancia **manzana**, existen ejemplos más complejos como lo pueden ser la clase **vehiculo** y instancia **automovil** , con atributos más complejos como lo son:
- Color: Rojo
- Locomoción por motor de combustión
Métodos:
* Encender
* Frenar
* Apagar
---
## OOP (Diseño Orientado a Objetos)
Nos enfocamos en abstraer atributos y comportamientos, basándonos en objetos del mundo real, la #abstracción resulta en algo relevante para modelar clases y objetos ya que buscamos traer la idea del mundo real a nuestra virtualidad, ignorando los conceptos especificos y trayendo los aspectos más generales, el ejemplo del automovil es perfecto para la situación, ya que abstraemos la idea general de avanzar, frenar y apagar sin necesidad de ir a su funcionamiento interno, puede verse el ejemplo de las black box.
![[Pasted image 20260421152306.png]]
## Datos, Atributos y Comportamiento
**Dato:** valor en concreto que toma un atributo en un objeto x.
Ejemplo:
```mermaid
classDiagram
    direction RL
    class Fruta{
        +Color: **Rojo***
    }

```
En esta caso el Dato es lo especifico del objeto
**Atributo:** Valor general que comparten los objetos de la clase.
Ejemplo:
```mermaid
classDiagram
    direction RL
    class Fruta{
        + ***Color***: Rojo
    }

```
**Comportamientos (Métodos):** Las acciones que el objeto puede realizar.
Ejemplo:
```mermaid
classDiagram
    direction RL
    class Fruta{
        + Color: Rojo
        + ***pelar().***
    }

```
---
## Herencia y Composición
La #herencia permite que una clase *(Hija)* herede atributos y métodos de una clase *(Padre)*, evitando caer en el #DRY , la composición permite y facilita crear clases complejas teniendo en cuenta la inclusión de objetos de otras clases, teniendo una relación de que A contiene con B, pero B no existe sin A.
### Diferencias:
- La herencia se puede definir como ***es un/a*** (Ej: Charizard es un Pokemon, los Tipo Fuego son un Pokemon). Tiene la ventaja de que podemos crear métodos propios de la nueva clase, por ejemplo A tiene n métodos, pero B puede tener n+1 métodos, como las Aves pueden ser la clase principal, pato puede heredar todo lo que tenga Aves, pero puede tener un método propio como *nadar()*
- Se puede ver como una relación de ***tiene un/a*** (Ej: Entreador tiene un Item, esto sería composición si los items dejaran de exitir al tiempo que deja de existir el entrenador). La clase Coche puede contener un objeto como atributo, el cual puede ser Motor, lo que permite =="absorber"== los métodos del motor, como ==arrancar_motor()==
---
### UML
Revise las relaciones que se pueden realizar en los diagrama UML [Relaciones](https://mermaid.js.org/syntax/classDiagram.html#defining-relationship).
# Clases y Objetos Python
>[!tip] Curiosidad y Repaso
>Incluso los Datos primitivos en Python son un objeto, como lo son ```str```,  ```bool```, ```int```, ```float``` etc.
>Un objeto es una instancia de una clase, que a su es una plantilla para crear objetos.

Es relevante señalar que un objeto sigue las especificaciones de su clase respectiva, no se puede salir de la cuadricula por decirlo así, también hay que añadir que cada instancia tiene sus propios atributos (o incluso metodos si se pasan distintos argumentos).
## Definiciones:
**Instanciar:** En python instanciar un objeto es crear un objeto único a partir de una clase. Los objetos tienen tanto datos **(atributos)** como código **(métodos)**.
*Objeto especifico creado a partir de una clase*
**Clase:** Plano o *Template* que define los atributos y métodos que sus objetos (instancias) tendran.
Existe un concepto un poco avanzado que se vera más adelante, que es crear varios objetos a partir de una sola clase, esto permite reutilizar y facilitar código (#DRY)

##  Clases Python
>[!Example]- Protip
>Utilizamos `CamelCase`, para crear la clase más básica en python solo es necesario utilizar la palabra clave pass, pass permite crear un bloque de código vació sin la necesidad de caer en el error de tener un bloque de código sin definir.
>```python
>class MyFirstClass:
>	pass
>```
## Atributos de Clase
Los atributos de clase se pueden ver como **variables**  de los objetos en python, los atributos en las clases son las variables especificas asociadas a la clase misma, no a las instancias, todas las instancias que se crean a partir de la clase, tienen estas variable *(atributos)*, se definen en el cuerpo de la clase fuera de cualquier metodo, se pueden definir de la siguiente manera:
```python
class Point:
	definition: str = "Entidad Geometrica que representa una ubicación en el espacio"
point = Point()
print(point.definition)
```
## Atributos de Instancia
Y si queremos que cada instancia tenga algo que las diferencie? los atributos de instancia se pueden ver como variables específicas de cada instancia de una clase (esto no limita que haya dos objetos con los mismos atributos de instancia). Se definen dentro del método `__init__`, utilizando el prefijo `self` para explicar y definirlos como atributos de instancia (el objeto único).

```python
class Point:

	definition: str = "Entidad geometrica abstracta que representa una ubicación en un espacio."

	def __init__(self, x=0, y=0):
		self.x = x
		self.y = y
point = Point()

point2 = Point(3, 4)

print(point.definition, point.x, point.y)

print(point2.definition, point2.x, point2.y)
```
Note que incluso para llamar la definition, no es necesario llamar point2.definition, puede usar el mismo de point.definition, debido a que es una variable especifica de la clase.
## Inicializacion (`__init__`) y el si mismo (`self`)

Tags: #clase #instancia #abstracción #DRY #herencia 