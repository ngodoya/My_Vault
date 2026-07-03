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
Tags: #Built-in #pep8