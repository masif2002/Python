# More on Exceptions
## Hierarchy of Exceptions
Python3 has 64 built-in exceptions, which all form a tree hierarchy.
* For example, a ZeroDivisonError is a special case of a more general exception named class ArithmeticError. 
* An ArithmeticError is a special case of a more general exception class named just Exception. 
* And, an Exception is a special case of a even more general class named BaseException. 

Since, the ZeroDivisonError is a sepcial case of ArithmeticError, we could replace the dedicated exception branch to only look for any ArithmeticError instead.
```python
try:
    x = int(input("Enter a number: "))
    y = 1/x
    print(y)
except ValueError:
    print("Please enter an integer: ")
except ArithmeticError:         `# Also catches ZeroDivisionError
    print("Calculation Failed!")
except:
    print("Something else went wrong!")

print("This prints no matter what")
```
* If we have both a ZeroDivisionError and an ArithmeticError branch, it'll only execute the first matching branch. This means that your **order of the branches matter**.

If you want to handle two or more exceptions the same way, you can add the names into a comma seprated list, 

```python
try:
    x = int(input("Enter a number: "))
    y = 1/x
    print(y)
except (ValueError, TypeError):
    print("Invalid Value")
except ArithmeticError:    
    print("Calculation Failed!")
except:
    print("Something else went wrong!")

print("This prints no matter what")
```

## Rasing exceptions manually
You can manually raise an exception with the `raise` keyword. This can be useful if you want to stimulate raising actual exceptions.

```python
def divide(n):
    return 100/n

num = int(input("Enter a number: "))
if num == 0:
    raise Exception("Input cannot be zero")
else:
    divide(num)
```
* You could raise any exception, not just `Exception`, but also exceptions like `ArithmeticError`, `ValueError` and so on.
* You also can give an optional error message in paranthesis after the exception.
* You can also use the `raise` keyword unnamed inside an except block.

## assert keyword
The `assert` keyword evaluates an expression and if this expression evaluates to be True, the execution  would continue normally. If it evaluates to be False, it automatically raises an exception named AssertionError.
* This can be useful if you want to be absolutely safe from wrong data. It secures your code from producing invalid results. 
```python
num = int(input("Enter a non-negative integer: "))
assert num >= 0, "Number is negative!"
```
* An optional error message can be displayed, by specifying the message after the expression, seperated by a comma.

> Note:
> The Python documentation gives you a clear overview of all possible exceptions that can be raised by Python. 