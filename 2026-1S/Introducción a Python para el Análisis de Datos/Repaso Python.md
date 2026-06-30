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
notice the comma after the `str`, this is the beginning for functions and arguments

Tags: #Scope #terminal #PEP8
