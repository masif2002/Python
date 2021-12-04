# Understanding Lists

* There is one *important* difference when working with lists and working with regular variables.

* When we define a normal variable, for example, a named variable that holds the value of a string. Python stores its value in memory directly with the string.

* But, when we create a list, however, we're actually creating a variable whose value is **simply a reference to the address** where that list is stored in memory.

* Whenever we're trying to create a new variable, that should have the same value as the old _list_, we're actually **copying the reference** to the same spot in memory that the old list variable refers to.

* This means that whenever we change the value of an element on the old list, it is also reflected in the new list since,the new list variable also refers to the **address** of the old list variable.

```python
age1 = [56, 72, 24, 46]
age2 = age1
print(age2)

age1[0] = 92
print(age2)
```