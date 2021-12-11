# Modules

Modules allows us to split our codebase into smaller parts. 
* A **module** is a file containing Python definitons and statements, which can be imported and used when necessary.
* We can:
    * Write our own module.
    * Use a module that's written by someone else.
    * Use built-in modules in Python.

## Importing modules

math Module is one of Python's standard modules and it provides us functions and classes to make it really easy to perform mathematical calculations.

* In order to use the logic within this module,  we'll have to first import it into our own file. We can do this with the `import` keyword, followed by the name of the module, _math_ in our case. 
```python
import math
```

* If we need to import more than one module, we can append it to the list of imports seperated by a comma.
```python
import math, numpy
```
Although the _import_ instruction can be located anywhere in our code, it must be placed before the first use of the modules entities. It is the general convention to finish all the _import_ statements in the beginning of the code itself.
 
## Making use of the module

After importing the module, we can use the entities provided by writing the name of the module, followed by a dot and the name of the entity.
```python
import math

print(math.sin(90)) 
print(math.pi)
``` 
Since the _sin_ and _pi_ entities are in the math namespace, they don't enter the code's namespace. 
> A namespace is a space in which some unique names exist and don't conflict with each other.
* When we imported the _math_ module, Python imported it's contents on the math namespace. 
* If we had our own function called sin and pi, it wouldn't be a problem at all.
```python
import math

def sin(x):
    if 2*x == pi:
        return 0.99
    else:
        return None

pi = 3.14

print(sin(pi/2))             # Our own function
print(math.sin(math.pi/2))   # Function from the math module
```
* On the first print statement, we're printing the result of sin and pi in our own file.
* And in the second statement, we're printing the result of sin and pi entities provided by the _math_ module. 

## Importing only the entities from modules

If you do want to import the module's entities into your code's namespace, you can do so by changing the import instruction.
```python
from math import pi

print(pi)
``` 
* First, we have to tell Python from which module, we need to import the entitiy with the `from` keyword followed by the name of the module, then the `import` keyword followed by the name of the entity that we want to import, _pi_ in this case.
* Now, only the _pi_ entity is imported from the _math_ module, and we no longer have access to the _sin_ entity that we used before. 
* We need to note that, after importing only the entity, we use it without qualification. ie- pi, not math.pi

If you want to import multiple entities, you can do so by adding it to the list of entities to import, seperated by a comma. 

```python
from math import pi, sin
```
But, it is **NOT** recommended to import only the entities this way.
* Because, it's easy to cause **naming conflicts**.
* For example, when we also have a local declaration of sin and pi, that would overwrite the imported entites' values. 

Lastly, we can also import all entities offered by a module using an asterisk after the _import_ keyword.

```python
from math import *
print(sin(90))
print(pi)
```
* Without having to use the dot notation, we can just use the entities like _pi_ and _sin_. 
* The danger of **naming conflicts**, we saw before applies here aswell. For this reason, it is not recommended to use this notation in regular code. 

## Using aliases

If you want to import a module or an entity that has a name that conflicts with an already defined entity, or even if you just don't like it, you can alias the import with the `as` keyword.

```python
import math as m

print(m.sin(90))
print(m.pi)
```
* We now, no longer have access to the original module's name - _math_, but we can use use the alias name - _m_.

We can alias entities in a similar fashion as well.

```python
from math import pi as qt, sin as moon

print(moon(90)) # sin function of the math module
print(qt))      # pi entity of the math module
```