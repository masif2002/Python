# List Methods

In order to change the data in lists, we can also use built-in Python methods.
```python
cars = ["BMW", "Honda", "Lexus"]
```
* `append()` - With this method, we can add add new items to the end of the list.
```python
cars.append("Toyota")
```
* `insert()` - This method can be used to insert a new item anywhere in the list.
    * The first argument this method requires is the **index** where the new item needs to be inserted.
    * After the new item is inserted, the existing items in the list shifts one place to the right.
```python
cars.insert(1, "Mazda")
```

* `pop()` - This method deletes the last element of the list by default. However, we also can pass the index of the element which is to be deleted.
```python
cars.pop()     # Pops the last element
cars.pop(1)    # Pops the element with index 1
```
* `index()` - This method returns the index of the item in array.
```python
num = [0, 3, 4, 1, 2]
print(num.index(1))
``` 
* `sort()` - This method sorts the array in ascending order. This method **modifies** the original array.
```python
ages = [45, 89, 54, 21, 26, 6]
ages.sort()
print(ages)
```
* `reverse()` - This method reverses all the elements in an array. 
```python
ages.reverse()
```
---
In some cases, we want to swap values within a list. Python allows us to do so in the most simplest way.
```
cars[0], cars[1] = cars[1], cars[0] 
```
Here, we swap the values in the list having indexes 0 and 1.

