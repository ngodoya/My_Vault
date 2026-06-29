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
public class Main (
	public static void main(String[] args){
		for (int i = 1; i <= 5; i++) {
			System.out.print(i * i)}})
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
Tags: #Scope #terminal
