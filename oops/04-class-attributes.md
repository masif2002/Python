# Class attributes

These attributes are declared in the class level. However, it also can be accessed in the instances aswell.
```python
class Item:
    discount = 0.2 # 20% Discount -> Class Attribute
    def __init__(self, name: str, price: float, quantity=0):
        # Run validations to received arguments
        assert price >= 0, "Price cannot be negative!"
        assert quantity >= 0, "Quantity cannot be negative!"

        # Assign to self object    
        self.name = name
        self.price = price
        self.quantity = quantity
    def calculate_total_price(self):
        return self.price * self.quantity

item1 = Item("Noodles", 8, 5)
item2 = Item("Chocolate", 4, 11)

print(Item.discount)    # Accessible in class level
print(item1.discount)   # Accessible in instance level aswell
print(item2.discount)
```
* When we try to acccess the **class attribute** in the instance level, first it checks in the instance level, and when it realises it couldn't find the specified attribute, it checks the attributes in the class level.

There is a _magic_ attribute in Python that displays all the attributes of that specific object.

* the `__dict__` attribute returns all the attributes of that class or that instance as key-value pairs in a dictionary.
```python
print(Item.__dict__)    # All the attributes at class-level
print(item1.__dict__)   # All the attributes at instance-level
print(item2.__dict__)
```
Now, let's get back to our example, where we create a method to apply the discount, using the **class attribute** we created.

```python
class Item:
    discount = 0.2 # 20% Discount
    def __init__(self, name: str, price: float, quantity=0):
        # Run validations to received arguments
        assert price >= 0, "Price cannot be negative!"
        assert quantity >= 0, "Quantity cannot be negative!"

        # Assign to self object    
        self.name = name
        self.price = price
        self.quantity = quantity
    def calculate_total_price(self):
        return self.price * self.quantity
    def apply_discount(self):
        self.price -= self.price * Item.discount # Class Attribute

item1 = Item("Noodles", 100, 5)
item1.apply_discount()
print(item1.price)
```
The **class attribute** is accessed using the class name, with a `.` followed by the attribute name.
```python
Item.discount 
```
However, it can also be accessed at the instance level as we saw earlier. So we replace the above line in our code with
```python
self.discount
```
This can be helpful when you want to apply a different discount rate on specific items. 
* So python checks for the discount rate at instance level first and then goes to check for the class level. 
* So for speicifc items, you can have the different discount rates stored in the instance level.

For example

```python
class Item:
    discount = 0.2 # 20% Discount
    def __init__(self, name: str, price: float, quantity=0):
        # Run validations to received arguments
        assert price >= 0, "Price cannot be negative!"
        assert quantity >= 0, "Quantity cannot be negative!"

        # Assign to self object    
        self.name = name
        self.price = price
        self.quantity = quantity
    def calculate_total_price(self):
        return self.price * self.quantity
    def apply_discount(self):
        self.price -= self.price * self.discount # Class Attribute

item1 = Item("Noodles", 100, 5)
item1.apply_discount()
print(item1.price)

item2 = Item("Biryani", 1000, 1)
item2.discount = 0.3
item2.apply_discount()
print(item2.price)
```
