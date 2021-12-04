# Logical Operators

## AND operator

If you want to execute something **only if** multiple conditions are true, you use the `AND` keyword
```python
age = int(input("Enter your age: "))
if (age >= 18 and age <= 50):
    print("You are eligible to apply for the insurance scheme!")
```
Here, both the conditions need to be true, inorder for the code under the _if_ block to get executed.
## OR operator

If you want to execute a block of code, even if **any** one of the condition is true, then you use the `OR` keyword.
```python
color = input("Enter a color: ")
if (color == "Green" or color == "Yellow" or color == "Pink"):
    print("It is my favourite color!")
```
Here, even if one of the condition is true, the codeblock gets executed.

## NOT operator

This operator reverses the result.  
returns `True` if the result is `False` and similarly,  
returns `False` if the result is `True`.
```python
hungry = False
if (not hungry):
    print("You are not hungry!")
