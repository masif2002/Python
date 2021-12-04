# List Slicing

We can slice a list by using square brackets by specifying a **start** and **end** index which specifies how we want to slice that list.

**When we're slicing a list, were creating a whole NEW list in memory**. This means that if we modify that list, we won't modify the original list.
```
list[start:end:step]
```
* **step** stands for the step value. ie- how far we want to move in every iteration. The default step value is 1.
* The elements on the start index is the **first** element that should be included in the new list.
* And the element on the end index won't be included in the sliced list, but it will be sliced exactly before that element.

```python
num = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
even = num[1::2]
odd = num[:10:2]
print("New list of even numbers:", even)
print("New list of odd numbers:", odd)
``` 

* If we only specify a beginning index, we're slicing it from that index all the way through the **end**.
* And similarly, if we only specify an end index, we start from the very beginning until that index.

Negative indexing can also be used to slice lists.

* You can also use the `del` keyword when slicing the list.
* if we delete multiple items by using the `del` keyword and slicing elements, **we are modifying the original array**.

```python
letters = ['D', 'I', 'S', 'A', 'P', 'P', 'E', 'A', 'R']
del letters[:3]
print(letters)
```