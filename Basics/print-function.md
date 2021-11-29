# print()
* It is a built-in function
* Allows us to print values to the console
* We can invoke it with parantheses. Infact, every function in Python is invoked with parantheses
* We can pass the value we want to print, as _arguments_ between the parantheses  

```
print("Hello World")
```

If we want to print multiple lines at once, we can do so by invoking multiple print functions 

**Or** you also can use the _newline character_ &rarr; \n   
* \ -  Lets python know the next character after the backslash has a special meaning
* *n* - stands for newline

```
print("Hello \nWorld")
```

We also can pass multiple arguments to the print function seperated by commas
```
print("Hello", "There",  "World")
```
When we pass multiple arguments to the print function, python combines the arguments together and prints them all on one line

## Keyword Arguments for print()
Python allows you to pass special arguments to the print function namely **keyword arguments**.
+ **end** - This _keyword argument_ determines the characters that the print function sends to the output, once it reaches the end of its  _positional arguments_

Python passes a newline charcter by default when it reaches the end of its positional arguments 

```
print("Hello!", end = "") 
print("Python is a great language.")
```
With this *end* keyword that just consists of an empty string, we tell Python to use an empty string instead of a newline. Similarly, You can pass any values for the keyword _end_.

```
Hello! Python is a great language.
```

+ **sep** - This _keyword_ allows you to control how Python seperates the outputted arguments, which is just one blank space by default

```
print("Hello", "There", "World", sep="-" )
```
With this *sep* keyword consisting of a hyphen (-), we tell Python to seperate the arguments using a hyphen instead of a blank space. 

You also can combine multiple keyword arguments in a single print function.