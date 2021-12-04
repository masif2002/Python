# `assert` statements

When we want to accept certain parameters only if they follow a certain condition, we can make use of the `assert` statement

* It helps us to check for the condition and throw an error if the condition is not met.

Syntax:
```
assert <condition>, <error message to display> 
```
Example:
```python
class Item:
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

item1 = Item("Broom", -8, 1)
```
Here, we also can use a formatted string to throw an error message, which can contain values inside curly brackets
```
f"The name - {name} is not valid"
```
