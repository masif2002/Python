# Static Methods

A **static method** is just like a regular function, not a  method. But since we use it is as a method to perform actions related with the class, we define it as a static method inside the class, ie- like a regular function, but inside the class.

* We use the **_decorator_** - `@staticmethod` to create a static method
* Static methods don't pass the object itself as the first argument. This is because, it is just like a regular function as they don't take instance as a parameter by default.

Now, we will create a **static method** to check if a _float_ is an _integer_.
* A float is an integer when the decimal part is zero
```python
    @staticmethod 
    def is_integer(num):
        # Checks if the floats are point zero
        # Ex: 5.0, 12.0
        if isinstance(num, float):
            return num.is_integer()
        elif isinstance(num, int):
            return True
        else:
            return False

print(Item.is_integer(7))
print(Item.is_integer(7.5))
print(Item.is_integer(7.0))            
```
* `isinstance(object, class)` is an in-built Python function to check is the specified _object_ is an instance of the particular _class_.
* The **is_integer** method is used to check if the num is an integer. It also returns True when the number is **a float and the decimal part is point zero**.
    * Ex: a = 5.0  
    * a.is_integer() returns True  

 A static method can also be accessed from the instance level. 

 ## Class methods vs Static methods

### When do we use a static method?
We use a static method when we want to do something that should not be unique per instance. Exactly like we did above. 
* We could use the static method as an isolated function. That is also completely fine **but** we prefer to not do that because, although it is a method that had nothing to do with the instance,  it is somehow related to the class.

### When do we use a class method?
We create a class method for instantiating instances from some structured data.
* Class methods are used to manipulate different structures of data to instantiate objects, like we did previously with the csv file.

And **static methods** do not pass the object reference as the first argument in the backgeound. Whereas, in **class methods** the object reference is a **mandatory parameter** we should receive in order for it to work.