# Tuples

A **tuple** is a collection of items that are ordered, unchangeable, and allow duplicate values.

* A **mutable** data can be updated anytime. Lists in Python are **mutable datatypes**.
* **Immutable** data is the data that cannot be modified. Tuples in Python is an example for an **immutable datatype**.

We can create a **tuple** by enclosing data in parantheses, seperated by commas OR simply as a set of values seperated by commas.

```python
tuple1 = (1, 2, 3)
tuple2 = 1, 2, 3
tuple3 = 1,
```
When creating a tuple of just one element, make sure to leave a comma after the element, otherwise Python has no way of distinguishing a regular variable from the one-element tuple.
## Accessing data in tuples
In order to read data from a tuple, we can use many of the same methods, we've previously seen on a list.

For example:
* Using a for loop
```python
for item in tuple1:
    print(item)
```
* Using the index
```python
print(tuple1[1])
```
* Slicing the tuple
```python
tuple1[0:]
```
---
Using methods to modify the contents is not possible because as we saw earlier, a tuple is **immutable**.