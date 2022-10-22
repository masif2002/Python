## classes & objects
* When we use a method on an object, Python automatically passes the object itself as the first parameter. Hence, we pass _self_ (user-defined, can name it anything) as the first parameter in every method inside the class
___
```py
# You can specify the datatypes of the passed in arguments
def __init__(self, name: str, price: float, quantity=0):
```
### Formatted Strings
```py
name = 'ok;'
f"The name - {name} is not valid"
```

## assert statements
```py
class Item:
    def __init__(self, name: str, price: float, quantity=0):
       
        # Run validations to received arguments
        assert price >= 0, "Price cannot be negative!"
        assert quantity >= 0, "Quantity cannot be negative!"
```

## check is num is int/float
* `isinstance(object, class)` is an in-built Python function to check if the specified object is an instance of the particular class.