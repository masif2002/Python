# Variables

* Variables can be seen as a container that allows you to store values.
* Python allows us to redeclare variables overtime, just by assigning it a new value.

A variable has a _name_ and a _value_  
```python
name = "Asif"
age = 19
```
Here, two variables _name_ and _age_ has been created with values _"Asif"_ and _19_ respectively.
## Rules for creating a variable name
* The name of a variable can consist of uppercase and lowercase letters, digits and underscores.
* The name of the variable must begin with a letter or an underscore, not a number.
> Uppercase and lowercase letters are treated different in Python
* The name of the variable cannot be any of Python's reserved _keywords_.

## Shortcut Operator
Let's say we have to increase the value of the variable _age_ by 2

This is what we normally do
```python
age = age + 2
```
But this also can be done in a more cleaner way 
```python
age += 2
```
The above line also means the same as the previous line.. which also increases the value of the variable _age_ by 2

Similarly we can do this for any kind of arithmetic operation

```python
age **= 2
age *= 2
age /= 2
age //=2
age %= 2
age -= 2
```