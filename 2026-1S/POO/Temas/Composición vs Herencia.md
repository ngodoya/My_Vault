## Composición y Relaciones "Tiene Un"
Muchas veces puede llegar a ser útil el conceto de la composicón y  compararlo con #herencia, la composición de clases busca que una clase contenga una instancia dentro de sus campos, esto implica y facilita la idea de poder utilizar sus métodos sin la necesidad de heredar la clase.
***Ejemplo:***
 ```python
 class Book:
  def __init__(self, title, author):
    self.title = title
    self.author = author

class Library:
  def __init__(self):
    self.books = []

  def add_book(self, book): ## Composición, utiliza como atributo otra clase
    self.books.append(book)
 ```
 ```mermaid
 classDiagram
    class Book {
      -title: string
      -author: string
    }
    class Library {
      -books: list
      +add_book(book: Book)
    }
    Library --* "many" Book: contains

 ```

**Ejemplo:** Sistema de Computadora Una computadora tiene un procesador y una memoria.
```python
class Processor:
  def __init__(self, model):
    self.model = model

class Memory:
  def __init__(self, size):
    self.size = size

class Computer:
  def __init__(self, processor, memory):
    self.processor = processor
    self.memory = memory
```

```mermaid
classDiagram
    class Processor {
      -model: string
    }
    class Memory {
      -size: string
    }
    class Computer {
      -processor: Processor
      -memory: Memory
    }
    Computer --* Processor: has
    Computer --* Memory: has

```

## Herencia y Relaciones "Es Un"

ya analizamos la herencia con más profundidad en: [[Abstracción y Herencia]], donde utilizábamos conceptos generales (super clases) y las extendíamos utilizando una idea (clase derivada) siendo esta una especialización *(modificación)* de la clase base.
**Ejemplo:** Vehículos: Un coche es un tipo de vehículo.
```python
class Vehicle:
  def __init__(self, maker, model):
    self.maker = maker
    self.model = model

class Car(Vehicle):
  def __init__(self, maker, model, car_type):
    super().__init__(maker, model)
    self.car_type = car_type
```
Empleados: Un profesor es un tipo de empleado.
```python
class Employee:
  def __init__(self, name):
    self.name = name

class Teacher(Employee):
  def __init__(self, name, subject):
    super().__init__(name)
    self.subject = subject
```

## Comparación y Diferencias
- **Herencia:** se visualiza más como un *es un/una* , esto facilita mucho la reutilización de código, busca una jerarquia y además tiene una subclase especializada a diferencia de su clase padre
- **Composición:** se visualiza como un *Tiene un/una* , se utiliza cuando una clase tiene una o varias instancias de otras clases como parte de su estado. Favorece la flexibilidad y #encapulamiento
### Cuando usar Composición sobre herencia.
La composición se utiliza para construir clases complejas a partir de componentes simples y reutilizables, facilitando la modificación y extensión del código.
**Ejemplo de Composición:** Sistema de Audio:

```python
class Speaker:
  def play_sound(self, sound):
    print(f"Playing: {sound}")

class AudioSystem:
  def __init__(self):
    self.speaker = Speaker()

  def play(self, sound):
    self.speaker.play_sound(sound)
```
### Cuándo Usar Herencia
Usa herencia para representar relaciones jerárquicas entre clases donde las subclases comparten y extienden la funcionalidad de la superclase, promoviendo la reutilización de código.
**Ejemplo de Herencia:** Sistema de Empleados:
```python

class Employee:
  def __init__(self, name):
    self.name = name

class Manager(Employee):
  def __init__(self, name, department):
    super().__init__(name)
    self.department = department
```

# Ejercicio
1. Create class Line.
	```mermaid
	classDiagram
    class Line {
      +float length
      +float slope
      +Point start
      +Point end
      +__init__(self, start, end)
      +compute_length()
      +compute_slope()
      +compute_horizontal_cross()
      +compute_vertical_cross()
    }

	```
- _length_, _slope_, start, end: Instance attributes, two of them being points (so a line is composed at least of two points).
- compute_length(): should return the line´s length
- compute_slope(): should return the slope of the line from tje horizontal in deg.
- compute_horizontal_cross(): should return if exists the intersection with x-axis
- compute_vertical_cross(): should return if exists the intersection with y-axis

2. Redefine the class Rectangle, adding a new method of initialization using 4 Lines (composition at its best, a rectangle is compose of 4 lines).
    
3. **Optional:** Define a method called discretize_line() that creates an array on _n_ equally spaced points in the line and assigned as a instance attribute.
Tags: #Composición #herencia #encapulamiento
