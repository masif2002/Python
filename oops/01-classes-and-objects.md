# Classes & Objects
So, in Python, each data type is an object that has been instantiated earlier by some class. 
```python
name = "Asif"
age = 19

print(type(name))
print(type(age))
```
> Output:
```
<class 'str'>
<class 'int'>
```
* Here, the _name_ variable has already been instantiated from a string type of class.

* Similarly, for the _age_ variable , it has been instantiated from a **class** that is named _int_ meaning integer!

## Creating a class
You can create a new class using the `class` keyword in python, followed by the name of the class 
```python
class Item:
    pass
```
* The `pass` keyword is used to tell Python that there is nothing here, so that Python won't throw an error. It is often used when you don't write the implementation of a _function_ or a _class_ but you want to implement it in the future.

## Initializing an object
Now that we have created our class, we are allowed to create some instances of this class, namely an **object**.
```python
item1 = Item()
```
Above, we have insantiated an **object** of the class _Item_.

* We are allowed to assign some attributes to instances of the class. 
* That can be done by using `.` symbol after the name of the object followed by the name of the attribute.

```python
item1.name = "Noodles"
item1.price = 8
item1.quantity = 5
```
## Creating Methods inside class
We can create **methods** in our classes, which we will to be able to use it with our instances ie- objects.

* Functions inside classes are referred to as **methods** in Python. 
```python
class Item:
    def calculate_total_price(self):
        pass
```

* When we use a method on an object, Python automatically passes the object itself as the first parameter.
* So, while creating methods inside classes, it is necessary to have a parameter called `self`, so that when using the method with an instance, Python can pass the instance itself as the parameter.
* `self` stands for passing the object it*self*, as a parameter.
* You can give any name to the paramater, but calling it `self` is the common convention.

```python
class Item:
    def calculate_total_price(self, x, y):
        return x * y

item1 = Item()
item1.name = "Noodles"
item1.price = 8
item1.quantity = 5
print(item1.calculate_total_price(item1.price, item1.quantity))

item2 = Item()
item2.name = "Chocolate"
item2.price = 4
item2.quantity = 11
print(item2.calculate_total_price(item2.price, item2.quantity))
```
* We access a class's method using the `.` symbol after the name of the object followed by the method name.
