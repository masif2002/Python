# Return Statement

* The `return` keyword is used in functions to return a value. 
* If Python encounters a `return` keyword, it stops the execution of the rest of the function body and _returns_ to the function call. 

```python
def add(a, b):
    sum1 = a + b
    return sum1
    print("Sum of", a, "and", b, "=", sum1) # This line can't be reached

add(5, 10)
```
The last _print_ statement won't be printed because, in the  previous line, the control _returned_ back to the function call.

In some cases, you might want to return early from a function. 
```python
def sub(a, b):
    diff = a - b
    if (diff < 0):
        return
    print("The difference is", diff)

sub(5, 10)
sub(10, 5)
```
In this example, we use `return` to come out of the function, if a certain condition is met, which is similar to using `break` in loops.  

---
* Besides the possibility to return a value from a function, the `return` keyword also gives a lot of control over the execution of your function.
* Although the return word isn't necessary in a function in order to return a value, Python still **always returns some value**. This value is called `None`.
