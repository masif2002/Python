# Getters and Setters

```python
item1 = Item("Biryani", 150)
item1.name = "Pulav"

print(item1.name)
```
* When creating a program, users can easily modify the value of our attributes, like we've seen above.
* What if we want to restrict our users to change the value of an attribute, once it has been initalized 
* It is possible in Python to do so by creating a **read-only** attribute.

## Creating Read-Only Attributes

* Creating a read only attribute means that we have only one opportunity to set the value of our attribute and we cannnot update the value of it later.
* We should have errors if we try to overwrite the value of the attribute.
* This is also known as **encapsulation**, one of the key principles of Object Oriented Programming.

We can create a read-only attribute by using the _decorator_ `@property` 
* Then we create a function with a function name which is going to be the **name of the read-only attribute**. 
* Here, for the example, we create an attribute with the name *read_only_attribute*.
```python
@property
def read_only_attribute(self):
    return "You have successfully accessed the read-only attribute. Try changing me! :)" 

item1 = Item("Biryani", 100)
print(item1.read_only_attribute)
item1.read_only_attribute = "Mango" # Throws an error
``` 
> Output:
```
You have successfully accessed the read-only attribute. Try changing me! :)
Traceback (most recent call last):
  File "C:\Users\User\Documents\Asif\test.py", line 53, in <module>
    item1.read_only_attribute = "Mango"
AttributeError: can't set attribute
```
As we can see, we are not allowed to change the value of a read-only attribute. 

### Converting already present attributes to read-only  attributes

```python
@property
def name:
    return self.name
```
* We may think this is how we do it. But, this method is invalid because, In the constructor, we've assigned `self.name` to be the parameter `name`. We know, that for a read-only attribute it is not possible to assign a value. Hence, Python throws an error doing this.

* To, avoid this, we could try renaming the actual attribute 
```python
class Item:
    array = []     # Array of objects
    def __init__(self, name: str, price: float, quantity=0):
        # Run validations to received arguments
        assert price >= 0, "Price cannot be negative!"
        assert quantity >= 0, "Quantity cannot be negative!"

        # Assign to self object    
        self.name1 = name
        self.price = price
        self.quantity = quantity

        Item.array.append(self) 
   
    @property
    def name(self):
        return self.name1

item1 = Item("Biryani", 100)
print(item1.name)
```
* We've renamed the attribute, _name_ to _name1_. Now, we've converted the attribute _name_ to a read-only attribute. 
* Now, when a user attemps to reassign, the attribute _name_ it would throw an error, because it is a read-only attribute now.
* **BUT**, when the user tries to access the variable _name1_, he can do it, because **IT IS** accessible.
```python
item1.name1 = "lion"
```
* The above line will not throw an error, since _name1_ is accessible. Because we've changed only _name_ to be a read-only attribute. Again, we came back to where we started

The actual solution to this problem is converting the attribute into a _private_ attribute.
* We can do so by adding two underscores infront of the name of the attribute. This makes the attribute inaccessible outside the class.
```python
class Item:
    array = []     # Array of objects
    def __init__(self, name: str, price: float, quantity=0):
        # Run validations to received arguments
        assert price >= 0, "Price cannot be negative!"
        assert quantity >= 0, "Quantity cannot be negative!"

        # Assign to self object    
        self.__name = name
        self.price = price
        self.quantity = quantity

        Item.array.append(self) 
   
    @property
    def name(self):
        return self.__name

item1 = Item("Biryani", 100)
print(item1.name)
print(item1.__name)
```
>Output:
```
Biryani
Traceback (most recent call last):
  File "C:\Users\User\Documents\Asif\test.py", line 21, in <module>
    print(item1.__name)
AttributeError: 'Item' object has no attribute '__name'
```
We can see that, the attribute `__name` is inaccessible and Python throws an error stating there is no attribute with such a name.

## Assigning values for a Read-Only attribute
We can also set values to read-only attributes. Again, we do it with the help of a decorator.
* So, we create a seperate method for setting the value.
```python
@name.setter
def name(self, value):
    self.__name = value

item1 = Item("Biryani", 100)
item1.name = "Mango"
print(item1.name)
```
* The _name_ in the decorator `@name.setter` refers to the name of the read-only attribute, we want to set the value to. In our case, we like to change the value of the read-only attribute _name_.
* This allows us to set the value of a read-only attribute even after the value of the attribute was initialised the first time. 

You can also raise an exception if a particular condition is not met, while receiving the value.

```python
@name.setter
    def name(self, value):
        if len(value) > 5:
            raise Exception("Name is too long!")
        self.__name = value

item1 = Item("Biryani", 100)
print(item1.name)
item1.name = "Mango"
print(item1.name)
item1.name = "Mangoes"
print(item1.name)
```