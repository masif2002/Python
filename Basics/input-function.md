# Input

Prompts the user to _input_ some data from the console.

If you need to store the value, that the user inputs, you can assign a variable to the _input_ function.

It accepts optional parameter that can be used in order to write a message before the user input
```python
color = input("What is your favourite color?")
print("Your favourite color is " + color)
```
The value of the user input is always a _string_
```python
n = input(Enter a number: ")
print(type(n))
```
Here, even if the user inputs an integer, it is stored as a _string_ in the variable _n_.

If you want to actually make the string a number, you need to do what is called a **typecasting**. There are two types of functions you can use to _typecast_ data.  
* `int()` - Inorder to convert the string into an integer, we use **int()**. 
* `float()` - Similary, we use **float()** to convert  the string to a floating point number
```python
age = int(input("Enter your age: ))
print("Your age is ", age)
```
Here, the age is inputted from the user, which is then _typecasted_ to an integer and stored in the variable.

By this, we can input _integer_ and _float_ values aswell.

