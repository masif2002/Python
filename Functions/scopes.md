# Scopes

* An important thing to remember is that parameters and all the values that are declared within the function body are **scoped** to just that function.

* This means that variables that are declared within the function body are only available, within that function itself, not outside of it. 

```
def multiply(num):
    result = num * 2
    return result

print(result)
>> NameError: name 'result' is not defined.
```
Here, the variable _result_ is only available within the scope of the function. Hence, Python throws an error when we try to access the variable outside the function.

* However, we can use variables that are declared outside of the function, within the function body.

* It can happen that we have a variable with the same name, both outside of the function body, namely in the **global scope** and inside the function body or in the function scope. 
    * In that case, Python will use the variable that's declared inside the function scope. 
    * Only if it sees that we're trying to reference a variable that it cannot find inside the function scope, it will look for the global scope.
## global keyword
If you still want the variable declared within the function, to be accessible outside the function, you have to add the `global` keyword with the variable name that you want to make globally accessible.

```python
def getSecretMessage():
    global msg
    msg = input("Enter your secret message: ")

getSecretMessage()
print("The secret message is: " + msg)
```

* You cannot declare a variable **global** if you are having the same variable as a parameter for the function.
```
def change(n):
	global n
	n = n*5

SyntaxError: name 'n' is parameter and global
```
* You **cannot modify** a global variable inside a function.
```
def change():
	n = n*5

>> change()
UnboundLocalError: local variable 'n' referenced before assignment
```
* If you already have a global variable, and you are also declaring a global variable with the same name inside a function, then the value of the global variable inside the function will be reflected outside the function.
```python
x = 30
def my_function():
  global x
  x = 20

my_function()
print(x)
```