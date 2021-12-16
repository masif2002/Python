# Private Attributes

You use two underscores infront of a variable to make the variable private, which can be accessed only inside the class.
* What happens in the background is, the name of the class is also added to the front of the variable name preceeded by an underscore. So accessing the variable name directly, outside the class throws an error
* We can check this using the magic attribute `__dict__`.
```python
class Car:
    def __init__(self, name, dents=0):
        self.name = name
        self.__dents = dents # private attribute

c1 = Car("Volkswagen")
c2 = Car("Honda", 3)

print(c1.__dict__) # Returns all the attributes of the object
print(c2.__dict__)
print()

try:
    print(c1.__dents)
except Exception as e:
    print("Error trying to access the private attribute directly!", e)

print()
print("Accessing private attribute with the attribute name in __dict__...")
print(c1._Car__dents)
print(c2._Car__dents)
```
> Output:
```
{'name': 'Volkswagen', '_Car__dents': 0}
{'name': 'Honda', '_Car__dents': 3}

Error trying to access the private attribute directly! 'Car' object has no attribute '__dents'

Accessing private attribute with the attribute name in __dict__...
0
3
```