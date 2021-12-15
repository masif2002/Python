# Inheritance
We could  create a new class that **inherits** all the attributes and functionalities from the parent class.

* Class that we inherit from, is called a **parent class**.
* And multiple classes that inherits from that _parent class_, are called **child classes**.

```python
class Snack(Item):
    pass

snack1 = Snack("Chips", 5, 10)
snack2 = Snack("Chocolate", 4, 12)

print(isinstance(snack1, Snack))
print(isinstance(snack1, Item))
```
* Here, a new class _Snack_ is created which inherits from the class _Item_. 
* As all the functionalities are inherited when we inherit the parent class, the constructor of the parent class is invoked automatically, when an object is instantiated (of the child class).
    * This is because there is no **constructor** defined in the child class as of now.

## Calling constructor of the parent class

* `super()` function in Python allows us to have full access to the constructor of the parent class, without actually having to copy and paste the constructor code of the parent class, everytime we create a child class.
```python
super().__init__(name, price, quantity)
```
* Here, _name_, _price_ and _quantity_ are the three arguments that our parent constructor expects. So we pass them.

```python
import csv

class Item:
    discount = 0.2 # 20% Discount
    array = []     # Array of objects
    def __init__(self, name: str, price: float, quantity=0):
        # Run validations to received arguments
        assert price >= 0, "Price cannot be negative!"
        assert quantity >= 0, "Quantity cannot be negative!"

        # Assign to self object    
        self.name = name
        self.price = price
        self.quantity = quantity

        Item.array.append(self) # Appending the object itself to the array
    def calculate_total_price(self):
        return self.price * self.quantity
    def apply_discount(self):
        self.price -= self.price * self.discount # Class Attribute

    @classmethod
    def instantiate(cls):
        with open("items.csv", "r") as f:
            reader = csv.DictReader(f)
            items = list(reader)

        for item in items:
            Item(
                 item.get('name'),
                 float(item.get('price')),
                 int(item.get('quantity'))
                )
                        
    def __repr__(self):
        return f"{self.__class__.__name__}(\"{self.name}\", {self.price}, {self.quantity})" 

class Snack(Item):
    def __init__(self, name, price, quantity, flavouring):
        super().__init__(name, price, quantity)

        # Assigning the extra attributes
        self.flavouring = flavouring
        

snack1 = Snack("Chips", 5, 10, "E5103")
print(snack1.calculate_total_price())
snack2 = Snack("Chocolate", 4, 12, "E2647")
print(snack2.calculate_total_price())

print(Item.array)
```
