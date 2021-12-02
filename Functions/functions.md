# Functions

A function is a part of your code that's used to cause an effect or evaluate a value.

## Types of functions:
* Built-in functions 
* Functions from Modules
* User-defined functions

Some of the built-in functions we have used so far are `print()`, `int()`, `input()`, `range()` and so on ....

## Creating a function

* We can create a function using Python's `def` keyword. _def_ stands for definiton. It lets Python know that we want to create a new function.
* After the `def` keyword, we type the name of the function followed by parantheses and a semicolon.
* Next, we have the function body. It contains the instructions that we want the function to execute. 

```python
def sayHello():
    print("Hello there!")

sayHello()
```
*  The `return` keyword in Python is used in functions. It tells Python, that this function shouldn't just execute a certain block of code, but  also should _return_ a certain value. Hoewever, the `return` keyword is not necessary when writing functions.
```python
def getNumber():
    return 47

num = getNumber()
print(num())
```
Here, in our function `getNumber()`, the integer 47 is returned and stored in the variable _num_, which is then printed to the console.

## Why Functions?

The more we repeat a certain part of our code, higher are the chances of accidentally introducing bugs, and just overall decreasing the readability of our code.

So, we use functions to have our code more structured by dividing it into various blocks of code.