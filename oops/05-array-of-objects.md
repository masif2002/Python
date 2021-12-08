
# Array of Objects
It would be nice, if we could store all the objects in a single place, from where we could access it. For this, we use the concept of **Array of Objects**.
* We basically create an array as a class attribute, and find a way to add every new instance created to that array. We can do this in the constructor method.

```python
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

item1 = Item("Noodles", 100, 5)
item2 = Item("Biryani", 1000, 1)
item3 = Item("Chocolate", 50, 8)

print(Item.array)
```
> Output:
```
[<__main__.Item object at 0x03EADCD0>, <__main__.Item object at 0x04309A30>, <__main__.Item object at 0x04309A10>]
```
* You could see that, the way the object is being represented is not too friendly.
* We could change that using a **magic method**, which is `__repr__`
    * _repr_ stands for represntation.
    * It changes the way how an object is being represented.
```python
def __repr__(self):
    return f"{self.__class__.__name__}(\"{self.name}\", {self.price}, {self.quantity})"
```
> Output:
```
[
    Item("Noodles", 100, 5),
    Item("Biryani", 1000, 1),
    Item("Chocolate", 50, 8)
]
```
* You can return anything with this method, but we returned a formatted string with the attributes which would make the array of objects more readable.
* `self.__class__.__name__` returns the name of the class of which the object was created.

 Using **array of objects** also can be helpful when you want to display the value of a particular attribute of all the instances.
```python
for instance in Item.array:
    print(instance.name)
```
This displays the attribute _name_ of all the objects created till now.