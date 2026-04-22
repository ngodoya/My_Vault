# Abstracción
La #abstracción en POO implica destacar las caracteristicas esenciales de un objeto, ignorando los detalles que no tienen gran relevancia, esto se hace mediante la definición de #atributos y #metodos.
# Herencia
En esencia es un principio fundamental de la POO, donde una clase ***padre/base*** o super clase entrega y una clase ***hija/derivada*** o sub clase recibe *(copea)* todos las propiedades, atributos y métodos de la clase que heredo (clase padre). Importante notar que la #herencia permite #abstracción y eso facilita muchas cosas, ya que podemos hacer una clase general (la clase padre) que contiene todo lo común de un objeto (agrupando lo esencial) y luego derivar clases que toman como modelo la clase base.
## Utilidades
- **Reutilización de código** sin necesidad de escribirlo en las clases derivadas.
- **Extensibilidad**, la herencia permite extender la funcionalidad de las clases padre, permitiendo añadir, atributos e incluso métodos en las clases hijas.
- **Abstracción** permite establecer una relación jerárquica entre los objetos, así como ocurre en la vida real, que refleja las relaciones entre objetos (Ej: un *Estudiante* es un tipo de *Persona*)
```mermaid
classDiagram
    Person <|-- Student
    class Person {
      +string name
      +speak()
    }
    class Student {
      +int student_id
      +study()
    }

```
En código se puede visualizar de la siguiente manera 
```python
def class Person:
	pass # aquí debería haber métodos y atributos xd
def class Student(Person): #Permite HEREDAR, todo lo de Person
	pass
```
### Super
`super` se utiliza en la herencia para referirse a la clase padre, permitiendo llamar a sus métodos, pero especialmente el inicializador desde la clase hija.
***Ejemplo:***
```python
class Student(Person):
  def __init__(self, name, student_id):
    # Se llama la clase base y se instancia
    super().__init__(name) # Ojo, aquí manda el atributo, las clases no adivinan
    # y luego se agregan mas atributos
    self.student_id = student_id
```
Note que ahorra demasiado el hecho de tener que recurrir a volver a definir el constructor con variables que ya se definieron en la clase padre.
>[!Example] Otro ejemplo...

```python
class Vehiculo:
  def __init__(self, marca):
    self.marca = marca

  def mostrar_marca(self):
    print(f"Marca del vehículo: {self.marca}")

class Coche(Vehiculo):
  def __init__(self, marca, modelo):
    super().__init__(marca)
    self.modelo = modelo

  def mostrar_modelo(self):
    print(f"Modelo del coche: {self.modelo}")

carro = Coche(marca="Mazda", modelo="2020")
carro.mostrar_marca()
carro.mostrar_modelo()
```

### Es un...
Lo más importante de visualizar es que establece la posibilidad de hablar entre clases como *es un/a*, ejemplos hay muchos, pero los más recurrentes podrían ser:
- Un Auto *es un* vehículo
- Una Manzana *es una* fruta
- Los Tipo Fuego *son un* Pokemon
- Un iPhone *es un* teléfono
- La marihuana *es una* Droga
*hint:* a futuro se puede hablar de una relación tipo *tiene un/unos*
--- 
## Herencia Multiple
Un revuelto entre varias clases, una clase hija puede tener 2 padres ***(o más O_O)*** en código se denota como:
```python
class EmailSender:
	pass
class SMSSender:
	pass
class NotificacionManager(EmailSender, SMSSender):
	def __init__(self) -> None:
		super.()__init__(EmailSender)
		super.()__init__(SMSSender)
	pass
```
en UML se visualiza de la siguiente manera:
```mermaid
classDiagram
   class EmailSender {
     +send_email(message)
   }
   class SMSSender {
     +send_sms(message)
   }
   EmailSender <|-- NotificationManager
   SMSSender <|-- NotificationManager
   class NotificationManager {
   }

```
Suena como un concepto increíblemente poderoso... de hecho lo es, pero hay que ser muy precavidos con su implementación, se puede utilizar cuando una subclase necesita varios métodos de dos o más clases, trae ambigüedades consigo misma, se necesita una buena #abstracción e implementación.
* **Mixins:** Para añadir funcionalidades adicionales a una clase de manera modular. Los _mixins_ son clases que no están destinadas a ser instanciadas solas sino a añadir funcionalidades a otras clases mediante herencia múltiple.
### Problemas
**Problema del Diamante:** Cuando dos superclases derivan de una clase base común, y una subclase hereda de ambas, puede haber ambigüedad en la ruta de herencia, especialmente en cómo se inicializan las superclases y en qué orden se llaman los métodos.
```mermaid
classDiagram
   Base <|-- A
   Base <|-- B
   A <|-- C
   B <|-- C
   class Base {
     +__init__()
   }
   class A {
     +__init__()
   }
   class B {
     +__init__()
   }
   class C {
     +__init__()
   }

```

```python
class Base:
  def __init__(self):
    print("Base init")

class A(Base):
  def __init__(self):
    super().__init__()
    print("A init")

class B(Base):
  def __init__(self):
    super().__init__()
    print("B init")

class C(A, B):
  def __init__(self):
    super().__init__()
    print("C init")

# Orden de resolución de métodos (MRO)
print("Orden de resolución de métodos:", [cls.__name__ for cls in C.__mro__])
print("\nCreando instancia de C:")
c = C()
```
Esto nos permite visualizar el orden en que se va a ejecutar los inicializadores que utiliza ``super()``, iniciando con el init de C, que nos lleva a A, este nos lleva a B y este nos lleva a Base, por eso imprimimos primero "Base init" como terminamos el inicializador de Base, volvemos al inicializador de B, donde imprimimos "init B", para repetir el proceso con "init A" y "C init", todo eso gracias a seguir el __mro__
****Ambigüedad en la Resolución de Métodos****  Si varias superclases definen el mismo método, puede ser ambiguo cuál método hereda la subclase.
```python
class Base:
  def greet(self):
    return "Hola desde Base"

class A(Base):
  def greet(self):
    return "Hola desde A"

class B(Base):
  def greet(self):
    return "Hola desde B"

class C(A, B):
  pass

c = C()
print(c.greet())  # ¿Qué método greet() se llamará?
```
utilizamos el MRO ***(Method Resolution Order)***, python escoge el primero que encuentra y ahí para de buscar el método ``greet()``
```python
print("Orden de resolución de métodos:", [cls.__name__ for cls in C.__mro__])
```
***Conflicto de Métodos:*** el orden se determina de izquierda a derecha en la declaración de herencia.
***Resolución de Atributos:*** Los atributos pueden ser sobrescritos dependiendo del orden de inicialización.

--- 
## Ejercicio
1. Cree la clase Rectangle.
	```mermaid
	classDiagram
	class Rectangle {
      +float width
      +float height
      +Point center
      +__init__(self, method)
      +compute_area()
      +computer_perimeter()
    }

	```

- The rectangle should be inicialice using any of these 3 methods:
    
    - Method 1: Bottom-left corner(Point) + width and height
    - Method 2: Center(Point) + width and height
    - Method 3: Two opposite corners (Points) e.g. Bottom-left and Upper-right
- _width_, _height_, center: Instance attributes
    
- compute_area(): should return the area of the rectangle
    
- compute_perimeter(): should return the perimeter of the rectangle
    

2. Create a class Square() that inherited the required attributes and methods from Rectangle.
    
3. Create a method called compute_interference_point(Point) that returns if a point is inside or a rectangle.
    
4. **Optional:** Define a method called compute_interference_line() that return if a line or part of it is inside of a rectangle.

```python
class Point:

    def __init__(self, x: float, y: float) -> None:

        self.x = x

        self.y = y

class Rectangle:

    def __init__(self, width: float = None, height: float = None, center: "Point" = None,

                  bottom_left: Point = None, upper_right: "Point" = None) -> None:

        if bottom_left and width and height:

            self.width = width

            self.height = height

            self.center = Point(bottom_left.x + self.width / 2, bottom_left.y + self.height / 2)

        elif width and height and center:

            self.width = width

            self.height = height

            self.center = center

        elif upper_right and bottom_left:

            self.width = abs(upper_right.x - bottom_left.x)

            self.height = abs(upper_right.y - bottom_left.y)

            self.center = Point((bottom_left.x + upper_right.x) / 2, (bottom_left.y + upper_right.y) / 2)

  

    def compute_perimeter(self) -> float:

        return (2 * (self.height + self.width))

    def compute_area(self) -> float:

        return (self.height * self.width)

class Square(Rectangle):

    def __init__(self, side: float, center=None) -> None:

        super().__init__(center=center, width=side, height=side, bottom_left=None, upper_right=None)

  

    def compute_interference_point(self, point: Point) -> Bool:

        left = self.center.x - self.width / 2

        right = self.center.x + self.width / 2

        bottom = self.center.y - self.height / 2

        top = self.center.y + self.height / 2

        return left <= point.x <= right and bottom <= point.y <= top

  

point = Point(1, 2)

dosxdos = Rectangle(width=1, height=1, center=point)

dosxdos.compute_perimeter()
```
Tags: #abstracción #atributos #metodos #herencia
