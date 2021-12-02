# Arguments
Python also allows us to pass values to a function. We can pass these values **between the parantheses**, which are called **Arguments**.

```python
def sayHello(name):
    print("Hello " + name + "!")

sayHello("Asif")
```
`sayHello()` function now has a parameter called _name_. In order to specify the value of _name_, we pass an **argument**.

---

* Functions can also have multiple parameters, which are all seperated by a comma.
* In that case, the position of the arguments we pass matters

```python
def multiply(num1, num2):
    return num1 * num2

prod = multiply(5, 10)
print(prod)
```
Here, the first value that we pass is the value of num1, and   
the second value that we pass is the value of num2.
## Named Arguments

* If you don't want the position of the arguments to matter, you can pass **named arguments**.

```python
def subtract(num1, num2):
    return num1 - num2

diff = subtract(num2=10, num1=60)
```
Here, in the function _subtract_, num1 is taken as 60 and num2 is taken as 10, although the order of the parameter in the function statement differs from the order of the arguments passed. Named arguments allows us to do so.
## Default Parameters
* We can also set default values for parameters.
```python
def sayHello(name="There"):
    print("Hello " + name + "!")

sayHello()
sayHello("Sidharth")
```
If we did pass a value, to a function which has a _default parameter_, Python wouldn't use the default value but uses the value that we passed. 

## Arbitrary Arguments

Sometimes, we do not know in advance the number of arguments that will be passed into a function. Python allows us to handle this kind of situation through function calls with an **arbitrary** number of arguments.

In the function definition, we use an asterisk (*) before the parameter name to denote this kind of argument. Here is an example.
```python
def greet(*names):

    # names is a tuple with arguments
    for name in names:
        print("Hello", name)


greet("Monica", "Luke", "Steve", "John")
```
_Output:_
```
Hello Monica
Hello Luke
Hello Steve
Hello John
```

> Reference for Arbitary Arguments:  
> &rarr; https://www.programiz.com/python-programming/function-argument