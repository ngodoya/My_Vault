## What is OOP?

**OOP** stands for **Object-Oriented Programming**.

Python is an object-oriented language, allowing you to structure your code using classes and objects for better organization and reusability.
## Advantages of OOP

- Provides a clear structure to programs
- Makes code easier to maintain, reuse, and debug
- Helps keep your code DRY (**Don't Repeat Yourself**)
- Allows you to build reusable applications with less code
**Tip:** The DRY principle means you should avoid writing the same code more than once. Move repeated code into functions or classes and reuse it.
## What are Classes and Objects?

Classes and objects are the two core concepts in object-oriented programming.

A class defines what an object should look like, and an object is created based on that class. For example:

| Class | Objects              |
| ----- | -------------------- |
| Fruit | Apple, Banana, Mango |
| Car   | Volvo, Audi, Toyota  |
## Python Classes/Objects

Python is an object oriented programming language.

Almost everything in Python is an object, with its properties and methods.

A Class is like an object constructor, or a "blueprint" (template) for creating objects.
## Delete Objects

You can delete objects by using the `[del]` keyword:

>[!tip] **Note:** Each object is independent and has its own copy of the class properties.
## The pass Statement

`[class](https://www.w3schools.com/python/ref_keyword_class.asp)` definitions cannot be empty, but if you for some reason have a `[class](https://www.w3schools.com/python/ref_keyword_class.asp)` definition with no content, put in the `[pass](https://www.w3schools.com/python/ref_keyword_pass.asp)` statement to avoid getting an error.

## The __init__() Method

All classes have a #built-in method called `__init__()`, which is always executed when the class is being initiated.

The `__init__()` method is used to assign values to object properties, or to perform operations that are necessary when the object is being created.

>[!python] **Note:** The `__init__()` method is called automatically every time the class is being used to create a new object.

## Why Use __init__()?

Without the `__init__()` method, you would need to set properties manually for each object:
class Person:  
  pass  
  
p1 = Person()  
p1.name = "Tobias"  
p1.age = 25

## Default Values in __init__()

You can also set default values for parameters in the `__init__()` method, the same idea when you used default values in functions.
The `__init__()` method can have as many parameters as you need, sometimes we will use others parameters from the `__init__`constructor for creating new variables or parameters in our objects, example: class Line receive class Point, and  use coordinates for computing distance.
# Python self Parameter
## The self Parameter
The `self` parameter is a reference to the current instance of the class.

It is used to access properties and methods that belong to the class.

>[!python] **Note:** The `self` parameter must be the first parameter of any method in the class.
## Why Use self?

Without `self`, Python would not know which object's properties you want to access, self Does Not Have to Be Named "self"

It does not have to be named `self`, you can call it whatever you like, but it has to be the first parameter of any method in the class:
>[!python] **Note:** While you _can_ use a different name, it is strongly recommended to use `self` as it is the convention in Python and makes your code more readable to others. #PEP8
## Calling Methods with self

You can also call other methods within the class using `self`:
```python
class Person:  
  def __init__(self, name):  
    self.name = name  
  
  def greet(self):  
    return "Hello, " + self.name  
  
  def welcome(self):  
    message = self.greet()  
    print(message + "! Welcome to our website.")  
  
p1 = Person("Tobias")  
p1.welcome()
```
## Class Properties

Properties are variables that belong to a class. They store data for each object created from the class.
You can access object properties using dot notation:
```python
class Car:  
  def __init__(self, brand, model):  
    self.brand = brand  
    self.model = model  
  
car1 = Car("Toyota", "Corolla")  
  
print(car1.brand)  
print(car1.model)
```
You can modify the value of properties on objects:
```python
p1 = Person("Tobias", 25)  
print(p1.age)  
  
p1.age = 26
# Delete the age property:
del p1.age
```
## Class Properties vs Object Properties

Properties defined inside `__init__()` belong to each object (instance properties).

Properties defined outside methods belong to the class itself (class properties) and are shared by all objects:
```python
class Person:  
  species = "Human" # Class property  
  
  def __init__(self, name):  
    self.name = name # Instance property  
  
p1 = Person("Emil")  
p2 = Person("Tobias")  
  
print(p1.name)  
print(p2.name)  
print(p1.species)  
print(p2.species)
```
## Modifying Class Properties

When you modify a class property, it affects all objects:
```python
class Person:  
  lastname = ""  
  
  def __init__(self, name):  
    self.name = name  
  
p1 = Person("Linus")  
p2 = Person("Emil")  
  
Person.lastname = "Refsnes"  
  
print(p1.lastname)  
print(p2.lastname)
# Adding propierties
class Person:  
  def __init__(self, name):  
    self.name = name  
  
p1 = Person("Tobias")  
  
p1.age = 25  
p1.city = "Oslo"  
  
print(p1.name)  
print(p1.age)  
print(p1.city)
```
>[!python] **Note:** Adding properties this way only adds them to that specific object, not to all objects of the class.

# Class Methods

Methods are functions that belong to a class. They define the behavior of objects created from the class
## Methods with Parameters

Methods can accept parameters just like regular functions:
>[!note] **Note:** All methods must have `self` as the first parameter.
## Methods Accessing Properties

Methods can access and modify object properties using `self`:
## Methods Modifying Properties

Methods can modify the properties of an object:
## The __str__() Method

The `__str__()` method is a special method that controls what is returned when the object is printed:
```python
class Person:

def __init__(self, name, age):

self.name = name

self.age = age

  

def __str__(self):

return f"{self.name} ({self.age})"

  

p1 = Person("Tobias", 36)

print(p1)
```


## Multiple Methods

A class can have multiple methods that work together:

```python
class Playlist:  
  def __init__(self, name):  
    self.name = name  
    self.songs = []  
  
  def add_song(self, song):  
    self.songs.append(song)  
    print(f"Added: {song}")  
  
  def remove_song(self, song):  
    if song in self.songs:  
      self.songs.remove(song)  
      print(f"Removed: {song}")  
  
  def show_songs(self):  
    print(f"Playlist '{self.name}':")  
    for song in self.songs:  
      print(f"- {song}")  
  
my_playlist = Playlist("Favorites")  
my_playlist.add_song("Bohemian Rhapsody")  
my_playlist.add_song("Stairway to Heaven")  
my_playlist.show_songs()
```
## Delete Methods

You can delete methods from a class using the `[del]` keyword:
# Python Inheritance
## Python Inheritance

Inheritance allows us to define a class that inherits all the methods and properties from another class.

**Parent class** is the class being inherited from, also called base class.

**Child class** is the class that inherits from another class, also called derived class.
## Create a Parent Class

Any class can be a parent class, so the syntax is the same as creating any other class:
## Create a Child Class
To create a class that inherits the functionality from another class, send the parent class as a parameter when creating the child class:
Create a class named `Student`, which will inherit the properties and methods from the `Person` class:
Now the Student class has the same properties and methods as the Person class.
## Add the __init__() Function

So far we have created a child class that inherits the properties and methods from its parent.

We want to add the `__init__()` function to the child class (instead of the `[pass](https://www.w3schools.com/python/ref_keyword_pass.asp)` keyword).

**Note:** The `__init__()` function is called automatically every time the class is being used to create a new object.

When you add the `__init__()` function, the child class will no longer inherit the parent's `__init__()` function.

**Note:** The child's `__init__()` function **overrides** the inheritance of the parent's `__init__()` function.

To keep the inheritance of the parent's `__init__()` function, add a call to the parent's `__init__()` function:
```python
class Student(Person):  
  def __init__(self, fname, lname):  
    Person.__init__(self, fname, lname)

```
Now we have successfully added the `__init__()` function, and kept the inheritance of the parent class, and we are ready to add functionality in the `__init__()` function.
## Use the super() Function

Python also has a `[super()]` function that will make the child class inherit all the methods and properties from its parent:
```python
class Student(Person):  
  def __init__(self, fname, lname):  
    super().__init__(fname, lname)
```
By using the `[super()]` function, you do not have to use the name of the parent element, it will automatically inherit the methods and properties from its parent.
## Add Properties
In the example below, the year `2019` should be a variable, and passed into the `Student` class when creating student objects. To do so, add another parameter in the `__init__()` function:
```python
class Student(Person):  
  def __init__(self, fname, lname, year):  
    super().__init__(fname, lname)  
    self.graduationyear = year  
  
x = Student("Mike", "Olsen", 2019)

```

## Add Methods
```python
class Student(Person):  
  def __init__(self, fname, lname, year):  
    super().__init__(fname, lname)  
    self.graduationyear = year  
  
  def welcome(self):  
    print("Welcome", self.firstname, self.lastname, "to the class of", self.graduationyear)


```
If you add a method in the child class with the same name as a function in the parent class, the inheritance of the parent method will be overridden.
# Python Polymorphism
The word "polymorphism" means "many forms", and in programming it refers to methods/functions/operators with the same name that can be executed on many objects or classes.
## Function Polymorphism

An example of a Python function that can be used on different objects is the `[len()](https://www.w3schools.com/python/ref_func_len.asp)` function.

### String

For strings `[len()]` returns the number of characters:
### Tuple

For tuples `[len()]` returns the number of items in the tuple:

### Dictionary

For dictionaries `[len()]` returns the number of key/value pairs in the dictionary:
## Class Polymorphism

Polymorphism is often used in Class methods, where we can have multiple classes with the same method name.

For example, say we have three classes: `Car`, `Boat`, and `Plane`, and they all have a method called `move()`:
```python
class Car:  
  def __init__(self, brand, model):  
    self.brand = brand  
    self.model = model  
  
  def move(self):  
    print("Drive!")  
  
class Boat:  
  def __init__(self, brand, model):  
    self.brand = brand  
    self.model = model  
  
  def move(self):  
    print("Sail!")  
  
class Plane:  
  def __init__(self, brand, model):  
    self.brand = brand  
    self.model = model  
  
  def move(self):  
    print("Fly!")  
  
car1 = Car("Ford", "Mustang")       #Create a Car object  
boat1 = Boat("Ibiza", "Touring 20") #Create a Boat object  
plane1 = Plane("Boeing", "747")     #Create a Plane object  
  
for x in (car1, boat1, plane1):  
  x.move()
```
>[!Important] Look at the for loop at the end. Because of polymorphism we can execute the same method for all three classes.

## Inheritance Class Polymorphism

What about classes with child classes with the same name? Can we use polymorphism there?

Yes. If we use the example above and make a parent class called `Vehicle`, and make `Car`, `Boat`, `Plane` child classes of `Vehicle`, the child classes inherits the `Vehicle` methods, but can override them:

### Example

Create a class called `Vehicle` and make `Car`, `Boat`, `Plane` child classes of `Vehicle`:
```python
class Vehicle:  
  def __init__(self, brand, model):  
    self.brand = brand  
    self.model = model  
  
  def move(self):  
    print("Move!")  
  
class Car(Vehicle):  
  pass  
  
class Boat(Vehicle):  
  def move(self):  
    print("Sail!")  
  
class Plane(Vehicle):  
  def move(self):  
    print("Fly!")  
  
car1 = Car("Ford", "Mustang")       #Create a Car object  
boat1 = Boat("Ibiza", "Touring 20") #Create a Boat object  
plane1 = Plane("Boeing", "747")     #Create a Plane object  
  
for x in (car1, boat1, plane1):  
  print(x.brand)  
  print(x.model)  
  x.move()
```
Child classes inherits the properties and methods from the parent class.
In the example above you can see that the `Car` class is empty, but it inherits `brand`, `model`, and `move()` from `Vehicle`.
The `Boat` and `Plane` classes also inherit `brand`, `model`, and `move()` from `Vehicle`, but they both override the `move()` method.
Because of polymorphism we can execute the same method for all classes.
Also we can use #Duck-typing if we want use Polymorphism, this mean we need to check the classes not by his use, we are going to use them by his methods and atributtes (example: "if it quacks and walks like a duck, must be a duck").
# Python Encapsulation
## Python Encapsulation

Encapsulation is about protecting data inside a class.

It means keeping data (properties) and methods together in a class, while controlling how the data can be accessed from outside the class.

This prevents accidental changes to your data and hides the internal details of how your class works.

```python
class Person:  
  def __init__(self, name, age):  
    self.name = name  
    self.__age = age # Private property  
  
p1 = Person("Emil", 25)  
print(p1.name)  
print(p1.__age) # This will cause an error
```

>[!Bug] **Note:** Private properties cannot be accessed directly from outside the class (only using name mangling `p1._Person__age`).

## Get Private Property Value

To access a private property, you can create a getter method:

### Example

Use a getter method to access a private property:
```python
class Person:  
  def __init__(self, name, age):  
    self.name = name  
    self.__age = age  
  
  def get_age(self):  
    return self.__age  
  
p1 = Person("Tobias", 25)  
print(p1.get_age())
```
## Set Private Property Value

To modify a private property, you can create a setter method.

The setter method can also validate the value before setting it:
## Why Use Encapsulation?

Encapsulation provides several benefits:

- **Data Protection:** Prevents accidental modification of data
- **Validation:** You can validate data before setting it
- **Flexibility:** Internal implementation can change without affecting external code
- **Control:** You have full control over how data is accessed and modified
## Protected Properties

Python also has a convention for protected properties using a single underscore `_` prefix:
```python
class Person:  
  def __init__(self, name, salary):  
    self.name = name  
    self._salary = salary # Protected property  
  
p1 = Person("Linus", 50000)  
print(p1.name)  
print(p1._salary) # Can access, but shouldn't
```
Also is so useful for #PEP8 and explaining code for other programmers
>[!Abstract] **Note:** A single underscore `_` is just a convention. It tells other programmers that the property is intended for internal use, but Python doesn't enforce this restriction.
## Private Methods

You can also make methods private using the double underscore prefix:
```python
class Calculator:  
  def __init__(self):  
    self.result = 0  
  
  def __validate(self, num):  
    if not isinstance(num, (int, float)):  
      return False  
    return True  
  
  def add(self, num):  
    if self.__validate(num):  
      self.result += num  
    else:  
      print("Invalid number")  
  
calc = Calculator()  
calc.add(10)  
calc.add(5)  
print(calc.result)  
# calc.__validate(5) # This would cause an error
```
only inside the class we can use this method, notice that in the previous code.
>[!Warning] **Note:** Just like private properties with double underscores, private methods cannot be called directly from outside the class. The `__validate` method can only be used by other methods inside the class.

## Name Mangling

Name mangling is how Python implements private properties and methods.

When you use double underscores `__`, Python automatically renames it internally by adding `_ClassName` in front.

For example, `__age` becomes `_Person__age`.
```python
class Person:  
  def __init__(self, name, age):  
    self.name = name  
    self.__age = age  
  
p1 = Person("Emil", 30)  
  
# This is how Python mangles the name:  
print(p1._Person__age) # Not recommended! 
```
>[!Warning] **Note:** While you _can_ access private properties using the mangled name, it's not recommended. It defeats the purpose of encapsulation.

# Python Inner Classes
## Python Inner Classes

An inner class is a class defined inside another class. The inner class can access the properties and methods of the outer class.

Inner classes are useful for grouping classes that are only used in one place, making your code more organized.

## Accessing Inner Class from the Outside

To access the inner class, create an object of the outer class, and then create an object of the inner class:
```python
class Outer:  
  def __init__(self):  
    self.name = "Outer"  
  
  class Inner:  
    def __init__(self):  
      self.name = "Inner"  
  
    def display(self):  
      print("Hello from inner class")  
  
outer = Outer()  
inner = outer.Inner()  
inner.display()
```
## Accessing Outer Class from Inner Class

Inner classes in Python do not automatically have access to the outer class instance.

If you want the inner class to access the outer class, you need to pass the outer class instance as a parameter:
```python
class Outer:  
  def __init__(self):  
    self.name = "Emil"  
  
  class Inner:  
    def __init__(self, outer):  
      self.outer = outer  
  
    def display(self):  
      print(f"Outer class name: {self.outer.name}")  
  
outer = Outer()  
inner = outer.Inner(outer)  
inner.display()
```
## Practical Example

Inner classes are useful for creating helper classes that are only used within the context of the outer class:
```python
class Car:  
  def __init__(self, brand, model):  
    self.brand = brand  
    self.model = model  
    self.engine = self.Engine()  
  
  class Engine:  
    def __init__(self):  
      self.status = "Off"  
  
    def start(self):  
      self.status = "Running"  
      print("Engine started")  
  
    def stop(self):  
      self.status = "Off"  
      print("Engine stopped")  
  
  def drive(self):  
    if self.engine.status == "Running":  
      print(f"Driving the {self.brand} {self.model}")  
    else:  
      print("Start the engine first!")  
  
car = Car("Toyota", "Corolla")  
car.drive()  
car.engine.start()  
car.drive()
```
## Multiple Inner Classes

A class can have multiple inner classes:
```python
class Computer:  
  def __init__(self):  
    self.cpu = self.CPU()  
    self.ram = self.RAM()  
  
  class CPU:  
    def process(self):  
      print("Processing data...")  
  
  class RAM:  
    def store(self):  
      print("Storing data...")  
  
computer = Computer()  
computer.cpu.process()  
computer.ram.store()

```




---

## Private Properties

In Python, you can make properties private by using a double underscore `__` prefix:
###  Reto
🏆 Reto 3: Motor de Regresión Lineal 

**Objetivo:** Desarrollar un simulador estadístico que prediga valores futuros basados en datos históricos.

- **Clase Base `ModeloPredictivo`**:
    - Clase abstracta con métodos vacíos `entrenar(x, y)` y `predecir(x)`.
- **Clase `RegresiónLineal` (Hereda de `ModeloPredictivo`)**:
    - Atributos: Pendiente (m) e intersección (b).
    - Método `entrenar()`: Calcula m y b usando las fórmulas de mínimos cuadrados.
    - Método `predecir()`: Aplica la ecuación y = mx + b.
    - Método `coeficiente_correlacion()`: Calcula el valor R de Pearson para medir la fuerza de la relación.
- **Concepto POO clave:** Herencia, polimorfismo y clases abstractas.
- 
Tags: #Built-in #pep8 #Duck-typing 