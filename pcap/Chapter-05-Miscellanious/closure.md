# Closure

**Closure** is a technique that allows the storing of values in spite of the fact that the context in which they have been created doesn't exist anymore.
* Closure allows a function that can pass a previous state of its invocation to its next.
* Closures help to invoke functions outside their scope.

```python
def outer(x):
    def inner(y):
        return x * y
    return inner

res = outer(2)
print(res(3))
```
* When we call the outer() function, it returns the inner function. So, the variable _res_ is equal to the inner function. 
* The outer() function actually returns a copy of inner() and its environment including all local variables.
* So _res_ is invoked with  the parameters as it now contains the inner() function.
* Python was able to access the inner() function even though the context of outer() function didn't exist anymore which is due to the **closure** property of Python.