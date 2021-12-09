# Code Organization

As our project grows, we need to start working with multiple files, to have everything clean and organized.
* So, we create a seperate file for each class
* And have a main file where we import all the classes and create instances of it

For example,
### item.py
```python
class Item:
    def some_method(self):
        pass
```
* item.py contains the class `Item`
### snack.py
```python
from item import Item

class Snack(Item):
    pass
```
* We import the class `Item` from item.py since we inherit the class

### main.py

```python
from item import Item
from snack import Snack 

item = Item()
snack = Snack()
snack.some_method()
```
* We instantiate objects and call methods for our actual program in the main.py file