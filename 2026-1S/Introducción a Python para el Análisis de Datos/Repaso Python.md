### What can Python do?

- Python can be used on a server to create web applications.
- Python can be used alongside software to create workflows.
- Python can connect to database systems. It can also read and modify files.
- Python can be used to handle big data and perform complex mathematics.
- Python can be used for rapid prototyping, or for production-ready software development.
## Why Python?

- Python works on different platforms (Windows, Mac, Linux, Raspberry Pi, etc).
- Python has a simple syntax similar to the English language.
- Python has syntax that allows developers to write programs with fewer lines than some other programming languages.
**Example:**
```python
for i in range(1, 6):
	print(i**2)
```
Same Code for `Java`
```java
public class Main {
    public static void main(String[] args) {
        for (int i = 1; i <= 5; i++) {
            System.out.print(i * i);
        }
    }
}

```
- Python runs on an interpreter system, meaning that code can be executed as soon as it is written. This means that prototyping can be very quick.
- Python can be treated in a procedural way, an object-oriented way or a functional way. (**Paradigms**)
- In this tutorial Python will be written in a text editor. It is possible to write Python in an Integrated Development Environment, such as Thonny, Pycharm, Netbeans or Eclipse which are particularly useful when managing larger collections of Python files.
### Python Syntax compared to other programming languages

- Python was designed for readability, and has some similarities to the English language with influence from mathematics.
- Python uses new lines to complete a command, as opposed to other programming languages which often use semicolons or parentheses.
- Python relies on indentation, using whitespace, to define scope; such as the #scope of loops, functions and classes. Other programming languages often use curly-brackets for this purpose.
# Install
To check if you have python installed on a Linux or Mac, then on linux open the command line or on Mac open the Terminal and type:
```bash
python --version
```
here is a tutorial for linux terminal (useful for beginners) [Tutorial](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview).
Commands for installing python:
```bash
sudo apt update
sudo apt install python3
# specific version
sudo apt-get install python<version>
python --version  # checking
```
If this doesn't work use `python3`
Python is an interpreted programming language, this means that as a developer you write Python (.py) files in a text editor and then put those files into the python interpreter to be executed.
Save files in any text editor (example: notepad), navigate to the directory in the terminal and  run:
```bash
import sys  
C:~/2026-1/Collabs/Intro_py_aut$ python3 file_name.py
print(sys.version) # for knowing ver
# it also work
python --version
```
it also can be run in our #terminal.
```bash
nick1604@Nick-Desktop:~/2026-1/Collabs/Intro_py_aut$ python3
Python 3.12.3 (main, Mar 23 2026, 19:04:32) [GCC 13.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> print("chamo")
chamo
>>> exit() #close python on terminal

```

# Python Syntax
## Python Indentation
Indentation refers to the spaces at the beginning of a code line.
Where in other programming languages the indentation in code is for readability only, the indentation in Python is very important.
Python uses indentation to indicate a block of code.

Python will give you an error if you skip the indentation:
```python
if 5 > 10:
print("Bloque vacío, error y esto nunca saldra")
```
The number of spaces is up to you as a programmer, the most common use is four, but it has to be at least one. ( #PEP8 recommends 4 spaces (in spanish the word is **Sangría**))
You have to use the same number of spaces in the same block of code, otherwise Python will give you an error:
```python
if 5 > 2:  
 print("Five is greater than two!")  
        print("Five is greater than two!")
```
## Python Variables
In Python, a variable is created when you assign a value to it, $x= 5$ , `y = "Hello, World!"`, the most common example is the box that you send values and it will save in your memory, that's bullshit, a variable is a space of memory in the software (RAM), in python we can explain variables in times, as we know we can use:
- int
- float
- bool
- list
- tuple
- dict
- set
- str
and a lot of types...
In Python there is a concept call *"dynamic typing"*, in some cases this will be problematic, because python has no command for declaring a variable **type**.
### Comments
Python has commenting capability for the purpose of in-code documentation.
Comments start with a `#`, and Python will render the rest of the line as a comment, this is so useful for explaining code, analog to raw code.
Comments can be used to explain Python code.
Comments can be used to make the code more readable.
Comments can be used to prevent execution when testing code.
## Statements
A **computer program** is a list of "instructions" to be "executed" by a computer.
In a programming language, these programming instructions are called **statements**.
The following statement prints the text "Python is fun!" to the screen:
```python
print("Python is fun!")
```
In Python, a statement usually ends when the line ends. You do _not_ need to use a semicolon (`;`) like in many other programming languages (for example, [Java](https://www.w3schools.com/java/default.asp) or [C](https://www.w3schools.com/c/index.php)).
## Many Statements
Most Python programs contain many statements.
The statements are executed one by one, in the same order as they are written.
Semicolons are optional in Python. You can write multiple statements on one line by separating them with `;` but this is rarely used because it makes it hard to read:
`print("Hello"); print("How are you?"); print("Bye bye!")`
This is more common when you want to define some variables.
>[!Tip]- Tip
>**Best practice:** Put each statement on its own line so your code is easy to understand.

## Python Output / Print
### Print Text
nothing especial, but also you can combine formats and call variables in a print function.
Doesn't matter if we use double quotes "" or only single quotes '' (If you forget to put the text inside quotes, Python will give an error)
## Print Without a New Line
By default, the `[print()](https://www.w3schools.com/python/ref_func_print.asp)` function ends with a new line.

If you want to print multiple words on the same line, you can use the `end` parameter:
```python
print("Hello World!", end=" ") #blank space  
print("I will print on the same line.")
# It also works
print("Hello World!", "I will print on the same line.")

```
notice the comma after the `str`, this is the beginning for functions and arguments, print is so useful when you need to output numbers, math operations and other things.
A comment does not have to be text that explains the code, it can also be used to prevent Python from executing code:
## Multiline Comments
Python does not really have a syntax for multiline comments.
To add a multiline comment you could insert a `#` for each line or...
Or, not quite as intended, you can use a multiline string, this is so good for define functions.
Since Python will ignore string literals that are not assigned to a variable, you can add a multiline string (triple quotes) in your code, and place your comment inside it #PEP8 
# Variables
## Creating Variables
Python has no command for declaring a variable.
A variable is created the moment you first assign a value to it.
Some IDE will track your variables in code (or datasets if you need), this is important cause the kernel usually save the information in his internal memory.
Variables do not need to be declared with any particular _type_, and can even change type after they have been set.
```python
x = 4       # x is of type int  
x = "Sally" # x is now of type str  
print(x)
```
## Casting
If you want to specify the data type of a variable, this can be done with casting.
```python
x = str(3)    # x will be '3'  
y = int(3)    # y will be 3  
z = float(3)  # z will be 3.0
```
also `type()` function is useful for knowking the data type of a variable
## Case-Sensitive

Variable names are case-sensitive. Doesn't matter if we put lower and upper.
```python
a = 4  
A = "Sally"  
#A will not overwrite a
```
## Variable Names
Rules for Python variables:

- A variable name must start with a letter or the underscore character
- A variable name cannot start with a number
- A variable name can only contain alpha-numeric characters and underscores (A-z, 0-9, and _ )
- Variable names are case-sensitive (age, Age and AGE are three different variables)
- A variable name cannot be any of the [Python keywords](https://www.w3schools.com/python/python_ref_keywords.asp).
>[!python]  Remember that variable names are case-sensitive
### Python keywords
| Keyword                                                               | Description                                                                                           |
| --------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| [and](https://www.w3schools.com/python/ref_keyword_and.asp)           | A logical operator                                                                                    |
| [as](https://www.w3schools.com/python/ref_keyword_as.asp)             | To create an alias                                                                                    |
| [assert](https://www.w3schools.com/python/ref_keyword_assert.asp)     | For debugging                                                                                         |
| [async](https://www.w3schools.com/python/ref_keyword_async.asp)       | Define an asynchronous function                                                                       |
| [await](https://www.w3schools.com/python/ref_keyword_await.asp)       | Wait for and get a result from an awaitable                                                           |
| [break](https://www.w3schools.com/python/ref_keyword_break.asp)       | To break out of a loop                                                                                |
| [case](https://www.w3schools.com/python/ref_keyword_case.asp)         | Pattern in a match statement                                                                          |
| [class](https://www.w3schools.com/python/ref_keyword_class.asp)       | To define a class                                                                                     |
| [continue](https://www.w3schools.com/python/ref_keyword_continue.asp) | To continue to the next iteration of a loop                                                           |
| [def](https://www.w3schools.com/python/ref_keyword_def.asp)           | To define a function                                                                                  |
| [del](https://www.w3schools.com/python/ref_keyword_del.asp)           | To delete an object                                                                                   |
| [elif](https://www.w3schools.com/python/ref_keyword_elif.asp)         | Used in conditional statements, same as else if                                                       |
| [else](https://www.w3schools.com/python/ref_keyword_else.asp)         | Used in conditional statements                                                                        |
| [except](https://www.w3schools.com/python/ref_keyword_except.asp)     | Used with exceptions, what to do when an exception occurs                                             |
| [False](https://www.w3schools.com/python/ref_keyword_false.asp)       | Boolean value, result of comparison operations                                                        |
| [finally](https://www.w3schools.com/python/ref_keyword_finally.asp)   | Used with exceptions, a block of code that will be executed no matter if there is an exception or not |
| [for](https://www.w3schools.com/python/ref_keyword_for.asp)           | To create a for loop                                                                                  |
| [from](https://www.w3schools.com/python/ref_keyword_from.asp)         | To import specific parts of a module                                                                  |
| [global](https://www.w3schools.com/python/ref_keyword_global.asp)     | To declare a global variable                                                                          |
| [if](https://www.w3schools.com/python/ref_keyword_if.asp)             | To make a conditional statement                                                                       |
| [import](https://www.w3schools.com/python/ref_keyword_import.asp)     | To import a module                                                                                    |
| [in](https://www.w3schools.com/python/ref_keyword_in.asp)             | To check if a value is present in a list, tuple, etc.                                                 |
| [is](https://www.w3schools.com/python/ref_keyword_is.asp)             | To test if two variables are equal                                                                    |
| [lambda](https://www.w3schools.com/python/ref_keyword_lambda.asp)     | To create an anonymous function                                                                       |
| [match](https://www.w3schools.com/python/ref_keyword_match.asp)       | Start a match statement (compare a value against cases)                                               |
| [None](https://www.w3schools.com/python/ref_keyword_none.asp)         | Represents a null value                                                                               |
| [nonlocal](https://www.w3schools.com/python/ref_keyword_nonlocal.asp) | To declare a non-local variable                                                                       |
| [not](https://www.w3schools.com/python/ref_keyword_not.asp)           | A logical operator                                                                                    |
| [or](https://www.w3schools.com/python/ref_keyword_or.asp)             | A logical operator                                                                                    |
| [pass](https://www.w3schools.com/python/ref_keyword_pass.asp)         | A null statement, a statement that will do nothing                                                    |
| [raise](https://www.w3schools.com/python/ref_keyword_raise.asp)       | To raise an exception                                                                                 |
| [return](https://www.w3schools.com/python/ref_keyword_return.asp)     | To exit a function and return a value                                                                 |
| [True](https://www.w3schools.com/python/ref_keyword_true.asp)         | Boolean value, result of comparison operations                                                        |
| [try](https://www.w3schools.com/python/ref_keyword_try.asp)           | To make a try...except statement                                                                      |
| [while](https://www.w3schools.com/python/ref_keyword_while.asp)       | To create a while loop                                                                                |
| [with](https://www.w3schools.com/python/ref_keyword_with.asp)         | Used to simplify exception handling                                                                   |
| [yield](https://www.w3schools.com/python/ref_keyword_yield.asp)       | To return a list of values from a generator                                                           |

## Multi Words Variable Names
Variable names with more than one word can be difficult to read.
There are several techniques you can use to make them more readable, if you want to know more about when is useful those types, read about the #PEP8 guide [PEP8 Guide](https://peps.python.org/pep-0008/0.)
## Camel Case

Each word, except the first, starts with a capital letter:

`myVariableName = "John"`
## Pascal Case

Each word starts with a capital letter:
`MyVariableName = "John"`
## Snake Case
Each word is separated by an underscore character:
`my_variable_name = "John""
## Many Values to Multiple Variables
Python allows you to assign values to multiple variables in one line:
```python
x, y, z = "Orange", "Banana", "Cherry"  
print(x)  
print(y)  
print(z)
```
>[!python] **Note:** Make sure the number of variables matches the number of values, or else you will get an error.

it also works for changing values in variables with other variables without losing info, for example:
```python
a = 5
b = 2
a, b = b, a
```
## One Value to Multiple Variables

And you can assign the _same_ value to multiple variables in one line:
```python
x = z = y = "uwu"
```
## Unpack a Collection

If you have a collection of values in a `list`, `tuple` etc. Python allows you to extract the values into variables. This is called _unpacking_.
## Print Variables
You can also use the `+` operator to output multiple variables:
```python
x = "Python "  
y = "is "  
z = "awesome"  
print(x + y + z)
```

>[!python] Notice the space character after `"Python "` and `"is "`, without them the result would be "Pythonisawesome".

Notice that x, y and are str, python can't combine different variables types in a print function.
The best way to output multiple variables in the `[print()]`functions support different data types.
## Global Variables

Variables that are created outside of a function (as in all of the examples in the previous pages) are known as global variables.
Global variables can be used by everyone, both inside of functions and outside.
If you create a variable with the same name inside a function, this variable will be local, and can only be used inside the function. The global variable with the same name will remain as it was, global and with the original value.
```python
x = "awesome"  
  
def myfunc():  
  x = "fantastic"  
  print("Python is " + x)  
  
myfunc()  
  
print("Python is " + x)
# output will be "Python is awesome"
```
we can also define global variables inside a function, using `global name_variable`.

## Built-in Data Types
#Built-in : is something that is defined in the core of the language, for example python `"print()"`function.
In programming, data type is an important concept.
Variables can store data of different types, and different types can do different things.
Python has the following data types built-in by default, in these categories:

| Text Type:      | `str`                              |
| --------------- | ---------------------------------- |
| Numeric Types:  | `int`, `float`, `complex`          |
| Sequence Types: | `list`, `tuple`, `range`           |
| Mapping Type:   | `dict`                             |
| Set Types:      | `set`, `frozenset` "immutable set" |
| Boolean Type:   | `bool`                             |
| Binary Types:   | `bytes`, `bytearray`, `memoryview` |
| None Type:      | `NoneType`                         |
## Python Numbers
There are three numeric types in Python:

- `int`
- `float`
- `complex`

Variables of numeric types are created when you assign a value to them:
## Int
Int, or integer, is a whole number, positive or negative, without decimals, of unlimited length.
## Float
Float, or "floating point number" is a number, positive or negative, containing one or more decimals.
Float can also be scientific numbers with an "e" to indicate the power of 10.
$x = 35e3, \quad y = 12E4$
## Complex
Complex numbers are written with a "j" as the imaginary part
## Type Conversion
You can convert from one type to another with the int(), float(), complex() methods:
```python
x = 1    # int  
y = 2.8  # float  
z = 1j   # complex  
  
#convert from int to float:  
a = float(x)  
  
#convert from float to int:  
b = int(y)  
  
#convert from int to complex:  
c = complex(x)  
  
print(a)  
print(b)  
print(c)  
  
print(type(a))  
print(type(b))  
print(type(c))
```

>[!python] **Note:** You cannot convert complex numbers into another number type.
## Random Number

Python does not have a `random()` function to make a random number, but Python has a built-in module called `[random]` that can be used to make random numbers
# Python Strings

Tags: #Scope #terminal #PEP8

