* the division operator always returns a float.
* **, //, *, %, +, - follows floating point vs integer rule 
```
                                  ^
+   -             -> unary        |   Highest Priority
**                                |
*   /   //  %                     |
+   -             -> binary       |   Lowest Priority
                                  v
```
### typecasting
```
>>> a = '5.0'
>>> float(a)
5.0
>>> int(a)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: '5.0'
>>> a = 5
>>> float(a)
5.0
>>> int(a)
5
```
* There is no conversion of ascii to char, or char to ascii. All three [float(), int(), str()] only does typecasting    
### end & sep
```
print("Hello!", end = "") 
print("Python is a great language.")

print("Hello", "There", "World", sep="-" )
```
___
* The name of the variable must begin with a letter or an underscore, not a number.
* Uppercase and lowercase letters are treated different in Python
* A while statement can also accept an else block.
    * If the loop is exited normally, the control comes to the else block, and the code under it gets executed.
### del & enumerate
* del keyword in Python, allows us to delete an item in a list.
```py
letters = ["A", "B", "C", "D", "E"]
del countries[2]
```
* enumerate() adds a counter to an iterable and returns it in a form of enumerating object
```
>>> for i, j in enumerate(['a', 'b', 'c']):
...     print(i, j)
... 
0 a
1 b
2 c
```
### list methods
```py
cars.insert(1, "Mazda") #index, element

num = [0, 3, 4, 1, 2]
print(num.index(1))
```

* When we're slicing a list, were creating a whole NEW list in memory. 
```py
even = num[1::2]
```
* when we create a list, however, we're actually creating a variable whose value is simply a reference to the address where that list is stored in memory.
* return keyword is not necessary when writing functions.
* Positional argument follows Keyword argument. While passing arguments, passing a keyword argument first, followed by a positional argument will result in a syntax error.
```py
# default values for arguments
def sayHello(name="There"):
    print("Hello " + name + "!")
```
### Arbitrary Arguments
* Sometimes, we do not know in advance the number of arguments that will be passed into a function. Python allows us to handle this kind of situation through function calls with an arbitrary number of arguments.
In the function definition, we use an asterisk (*) before the parameter name to denote this kind of argument.
```py
def greet(*names):

    # names is a tuple with arguments
    for name in names:
        print("Hello", name)


greet("Monica", "Luke", "Steve", "John")
```

### global keyword
* If you want the variable declared within the function, to be accessible outside the function, you have to add the global keyword with the variable name that you want to make globally accessible.
```py
def getSecretMessage():
    global msg
    msg = input("Enter your secret message: ")

getSecretMessage() # YOU NEED TO CALL THE FUNCTION FOR IT TO BE ACCESSIBLE
print("The secret message is: " + msg)
```

* You cannot modify a global variable inside a function.
```
def change():
	n = n*5

>> change()
UnboundLocalError: local variable 'n' referenced before assignment
```

* If you already have a global variable, and you are also declaring a global variable with the same name inside a function, then the value of the global variable inside the function will be reflected outside the function.
```py
x = 30
def my_function():
  global x
  x = 20

my_function()
print(x)
```
___
* Although the return word isn't necessary in a function in order to return a value, Python still always returns some value. This value is called `None`.
### Bit Shifting
```py
print(22 >> 1)
```
* Here, we're basically telling Python that we want to move all the bits that represent the integer 22 to the right by 1.
* The result of performing a binary right shift of one bit is same as the result of dividing the integer by 2
```py
print(22 << 2)
```
* Here, we move all the bits that represent the integer 22 to the left by 2.
* Binary left shift by **one bit** is the same as multiplying the integer by 2.
### Dictionary
* Same reference like List.
```py
usernames = {} #dict
print(usernames.keys())
print(usernames.values())
print(usernames.items())
```
* In order to completely empty the dictionary, you can use the clear() method.
```py
usernames.clear()
```
* If you just want to remove the last item in the dictionary, you can use the popitem() method.
```py
usernames.popitem()
```
* If you want to copy a dictionary, you can use the copy() method.
```py
usernames_copy = username.copy()
```