# Constructors

* Until now, for each instance we created, we had to hardcode the attribute name for each attribute.

* It could be easier if there was a way in which we **have to** pass in the attributes inorder to instantiate an instance successfully, Otherwise, the instance would not be created.

* **Constructors** in python allows us to do so. We can call it by creating a very special method in python, which is called the `__init()__` method.
    * Methods which are surrounded by double underscores are called _**magic methods**_.
## Invoking the constructor
```python
class Item:
    def __init__(self):
        print("The constructor has been invoked!")
    def calculate_total_price(self, x, y):
        return x * y

item1 = Item()
```  
Now, whenever an instance of this class is created, the **constructor** is invoked automatically. And then the actions within the `__init()__` method is executed.
* As we now know, that everytime an object is initialized, the `__init()__` method is called by default. We could use it to do something that we've been doing manually for each instance that was created. ie- Adding attributes and assigning them. 

* So now, we can demand the attributes with  parameters for the `__init__()` method.

```python
class Item:
    def __init__(self, name, price, quantity):
        print("The construcor has been invoked!")
    def calculate_total_price(self, x, y):
        return x * y

item1 = Item("Noodles", 8, 5)
item1.name = "Noodles"
item1.price = 8
item1.quantity = 5
```

* The fact that we have `self` as a parameter here, would actually allow us to assign the attributes from the `__init()__` method so that we will not have to assign the attribute name for each of the instances we create.

```python
class Item:
    def __init__(self, name, price, quantity):
        self.name = name
        self.price = price
        self.quantity = quantity
    def calculate_total_price(self, x, y):
        return x * y

item1 = Item("Noodles", 8, 5)
item2 = Item("Chocolate", 4, 11)

print(item1.name)
print(item1.price)
print(item1.quantity)
print()                     
print(item2.name)
print(item2.price)
print(item2.quantity)
```

* Here, we're assigning the attribute, _name_, _price_ and _quantity_ to each instance that is going to be created, which is going to be the values passed in as the parameter. 
* So now, we can dynamically assign an attribute to an instance with this `__init()_` method.

For methods in classes, we know that the object itself is passed as the first parameter. So in our method `calculate_total_price()`, we can remove the additional parameters, _x_ and _y_.

```python
class Item:
    def __init__(self, name, price, quantity):
        self.name = name
        self.price = price
        self.quantity = quantity
    def calculate_total_price(self):
        return self.price * self.quantity
```
We could have done the same when we saw this example in the previous topic (Classes & Objects) itself. But, the author wanted to demonstrate how, we could also get extra parameters for methods inside classes.


## Specifying expected datatypes for parameters
* We know, in Python, there is no need to declare the data type of a variable before assigning values like in other programming languages.
* But, when dealing with classes and constructors, if the parameter of the required datatype is not passed, it could break your program logically.
* So, Python offers us a way to resolve this by specifying the datatype of the parameter we expect, using a `:` followed by the datatype we expect the parameter to be.
```python
class Item:
    def __init__(self, name: str, price: float, quantity=0):
        self.name = name
        self.price = price
        self.quantity = quantity
    def calculate_total_price(self):
        return self.price * self.quantity
```
In the constructor method, we've set the expected datatypes and for the last parameter _quantity_, we've set a default value like we set default values in a function.  
* Since the default value for the parameter _quantity_ is an integer, it marks the value of this parameter to be always an integer.
* So there is no need to specify seperately that, for the parameter _quantity_, we expect only an integer.
