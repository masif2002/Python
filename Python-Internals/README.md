# Python Internals

## Basic Terminology

* **JVM** stands for Java Virtual Machine

* An **Interpreter** translates and executes program code line by line rather than the whole program in one step
----
* Python is an interpreted language. 

* In order for our computer to understand our human-friendly Python code, the Python **interpreter** takes our Python code and parses it line by line. 

* It then creates machine-friendly code, which is the code that our computers can understand and execute.

## Versions of Python

### CPython

* The implementation of Python we work on is also referred to as **Cpython**.
* It's Python that was written in C programming language 

### Cython

* Cython makes it possible to translate valid Python code directly to C in order to speed up the execution of our code because the resulting code in Python isn't always as efficient as if it were implemented in C. 
* Cython can run on Linux, MacOS and Windows aswell.

### Jython

* Jython is written in the programming language, **Java**. This can be useful if we want to use Python in an environment that already has a lot of Java code.

* At the moment, there is no Jython available for Python3, only available for Python2.

### RPython

* RPython is a subset of Python
* Used by programmers that develop Python itself, since it doesn't need an interpreter to run.