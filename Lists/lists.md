# Lists

If we want to have a collection of multiple elements, we can create a **list**.

```python
countries = ["USA", "UK", "Canada"]
```

Each element in the list has an **index**.
* The first element in the list has the index 0.
* The second element has index 1.
* The third element has index 2 and so on..

## Accessing elements in a list
If we want to get a specific element from the list, we can **access** this value by specifying the index in square brackets after the name of the list.
```python
print(countries[0])
print(countries[1])
print(countries[2])
```
However, Python also supports **negative indexing**. So, we can also get an item in a list with the negative index.

Negative indexing begins from the end of the list.
* The last element is indexed as `-1`
* The second last element is indexed as `-2`
* The third last element is iindexed as `-3` and so on..
```python
print(countries[-1])
print(countries[-2])
print(countries[-3])
```
## Updating elements in a list
We can also change the value on a specific index
```python
countries[1] = "India"
print(countries)
```
## Traversing a list
With a for-loop, we can traverse a list. 
```python
careers = ["Pilot", "Teacher", "Developer", "Doctor"]
for i in careers:
    print(i)
```
## len() function
The built-in `len()` function allows us to get the length of a list.
```python
print(len(countries))
```
The `len()` function can also be used to get the length of a string.

## del keyword
`del` keyword in Python, allows us to delete an item in a list. 

For example, if we need to delete the third item in our list, we do
```python
del countries[2]
print(countries)
```