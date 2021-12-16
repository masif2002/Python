# Errors and Exceptions

When Python tries to execute your code and something goes wrong, Python raises an exception. This means that it stops your program and it creates an exception.
* If an exception has been raised, the exception expects something to take care of it. However, if there's nothing to take care of it, the program will be terminated and you'll see an error message instead.
* Otherwise, if you do handle the exception well, the suspended program can be resumed and its execution can continue. 
* You can handle an exception with the `try` and `except` keywords. 

```python
try:
    name = "Asif"
    print("My name is", nmae)
except:
    print("There's an error in the try block")

print("End..")
```
* The code under the `try` block may or may not perform correctly. 
* If it fails, the code under the `except` block gets executed.
* After the try-except block, the execution resumes and rest of the code gets executed.
* If we didn't have a try-except block in this case, Python would've thrown an error and the program would terminate.

However, there are many different things that can go wrong in your program, and many different types of error can be thrown.
* Python allows you to create except blocks that only run when a specific error has been thrown. For example,
```python
try:
    x = int(input("Enter a number: "))
    y = 1/x
    print(y)
except ValueError:
    print("Please enter an integer: ")
except ZeroDivisionError:
    print("You cannot divide by a zero")
except:
    print("Something else went wrong!")

print("This prints no matter what")
```
* In the above example, when we enter a string as an input, the **ValueError** specific except block gets executed, since Python raises a ValueError.
* When we give zero as an input, a **ZeroDivisionError** gets raised, as in the second line we divide 1 by the input we asked for which is 0 in our case. So the codeblock of ZeroDivisionError gets executed. 
* The unnamed exception branch will be executed if there are no dedicated branches for the exception that got raised. 
* If you're working with named except branches , make sure you specify the unnamed except block last.
* If any of the except branches is executed, no other branches will be visited.  

## else block
Besides **try** and **except**, there's an additional branch that you can add, namely **else**.
* You can add this block after the last _except_ statement.
* The **else** codeblock only gets executed if there was no exception raised in the _try_ block. 

```python
def calc(x):
    try:
        num = 1/x
        print(num)
    except ZeroDivisionError:
        print("Division with zero is not allowed!")
    else:
        print("No exceptions raised! All good!")
    
calc(0)
print()
calc(2)
```

## finally branch
This branch always gets executed regardless of what happens. Even if an exception was raised or even if everything worked perfectly!
```python
def calc(x):
    try:
        num = 1/x
        print(num)
    except ZeroDivisionError:
        print("Division with zero is not allowed!")
    else:
        print("No exceptions raised! All good!")
    finally:
        print("I don't care. I execute always!")
calc(0)
print()
calc(2)
```
## User-defined Exceptions

We can create our own **exception class** by creating a normal class and which inherits from any _Exception_ class like _ValueError_, _TypeError_, _IndexError_ and so on.. Or from the _Exception_ class itself.
```python
class EmailError(Exception):

    def __str__(self):
        return "pending! wrong format!"
    
email = "admin#libray.net"
try:
    if "@" not in email:
        raise EmailError()
except EmailError as e:
    print(e)
```