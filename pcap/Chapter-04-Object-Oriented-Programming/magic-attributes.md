# Magic Attributes


Classes have some built-in attributes. These attributes come along whenever we create a class. These attributes, which are surrounded by double underscores, are also called **_magic attributes_**.

## `__name__` 
Returns the name of the class

## `__module__`
Stores the name of the module that contains the defintion of the class.
```python
from math import sin
print(sin.__module__)
```
## `__bases__`
Contains a tuple that contains the superclass of that particular class

## `__dict__`
It returns all the attributes of that class or that instance as key-value pairs in a dictionary.
```python
class Car:
    wheels = 4
    
class electricCar(Car):
    def __init__(self, name, price):
      self.name = name
      self.price = price

c1 = Car()
c2 = electricCar("Tesla", 58000)


print("__name__:", Car.__name__)
print()

print("__module__:", Car.__module__)
print()

print("__bases__:", electricCar.__bases__)
print()

print("Car.__dict__:", Car.__dict__) # Class attributes
print()

print("c2.__dict__:", c2.__dict__)   # Attributes at instance level
print()
```
> Output: 
```
__name__: Car

__module__: __main__

__bases__: (<class '__main__.Car'>,)

Car.__dict__: {'__module__': '__main__', 'wheels': 4, '__dict__': <attribute '__dict__' of 'Car' objects>, '__weakref__': <attribute '__weakref__' of 'Car' objects>, '__doc__': None}

c2.__dict__: {'name': 'Tesla', 'price': 58000}
```

* While printing `Car.__module__`, we get `__main__` returned since we are running the file directly.

## Magic Methods
We've covered quite a few **_magic methods_** in our previous OOPs tutorial. But we missed out the `__str__()` method.
* The `__str__()` method is the method that Python looks out for when we print an object.
* Normally, when we print an instance, Python prints a hexadecimal number. This hexadecimal number is an internal object identifier used by Python.
    * It's the address at which the object is stored in memory.
```python
class Car:
    def __init__(self, name, model):
        self.name = name
        self.model = model

c = Car("Tesla", 2020)
print(c)
```
> Output:
```
<__main__.Car object at 0x0344DCB0>
```
We can change what Python returns when we print an instance. By default, Python  looks for the `__str()__` method, in order to use the string that it returns.

```python
class Car:
    def __init__(self, name, model):
        self.name = name
        self.model = model

    def __str__(self):
        return f"It's a {self.model} {self.name}!"

c = Car("Tesla", 2020)
print(c)
```
> Output:
```
It's a 2020 Tesla!
```