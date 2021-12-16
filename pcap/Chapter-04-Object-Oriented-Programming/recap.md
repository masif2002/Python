# OOPs Recap

* An **instance variable** is a variable that is created and added to the object on initialisation (in the constructor).

* A **method** is a function embedded in a class.

* **Constructor** is a default method, which is called every time a new instance of a class is created.
    * The constructor method `__init__()` **cannot** return a value.
    * You also cannot invoke the constructor method from the object itself, or inside the class.

* When you inherit a class, the child class calls the constructor of the parent class by default, if the constructor for the child class is not created.

* Python looks higher up in the inheritance chain **ONLY** when it cannot find the property associated with a class from which our object derives.  

* The `isinstance()` function checks if the object  is an instance of the given class
    ```python
    class A:
        pass

    a = A()
    print(isinstance("duh", str))
    print(isinstance(a, A))
    ```
    
> Note: The two built-in Python functions below has not been covered in the previous OOPs tutorial.
## hasattr()

If you want to know if a certain object contains a certain attribute, we can make use of `hasattr()` function, short for _has attribute_.
* The first parameter is the object that we want to check and the second argument is the _attribute_ we're looking for.

```python
class Car:
    def __init__(self, name):
        self.name = name

car1 = Car("Volkswagen")
# We check if the class 'Car' has an attribute name
print(hasattr(car1, "name"))
```
> Output:
```
True
```

## issubclass()
Checks if a class is a subclass of another class or not.
```
issubclass(<subclass>, <class>)
```
```python
class One:
    pass

class Two(One):
    pass

class Three(Two):
    pass`

print(issubclass(Two, One))
print(issubclass(Three, One))
print(issubclass(One, One))
```
> Output:
```
True
True
True
```