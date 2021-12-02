# Dictionaries

A dictionary is a collection that is ordered, changeable and does not allow dupilacates.

A dictionary consists of **keys** and **values**. Together, they make key-value pairs. 

* All the key-value pairs in the dictionary are surrounded by curly braces.
* And the _keys_ are seperated from the _values_ with a colon.

```python
usernames = {
    "Asif": "masif2002",
    "Shrikanth": "ShrikanthDeva",
    "Priyanka": "priyaskumar",
    "Ashwanthram": "AshwanthramKL"
}
```
## Accessing elements in a dictionary

We can get specific elements within a dictionary by writing the name of the dictionary and writing the key of whose value we want, between the square brackets. 
```python
print(usernames["Shrikanth"])
```

## Dictionary methods
* `keys()` - When invoking the `keys()` method on a dictionary, an iterable keys list gets returned. This list is a sequence of all the keys within the dictionary. We can iterate through this list over a for-loop.

```python
print(usernames.keys())

for key in usernames.keys():
    print(key, "-", usernames[key])
```

* `values()` - This method returns an iterable containing the dictionary's values 
```python
print(usernames.values())
```
* `items()` - This method is a little bit different. It returns a list of tuples containing all the key-value pairs in the dictionary.
```python
print(usernames.items())

for key, value in usernames.items():
    print(key, "-", value)
```

## Modifying elements in a dictionary

If you want to update an existing value in a dictionary, we can do so by accessing the value using the right key, and assigning the value that it should have.
```python
usernames["Ashwanthram"] = "TheAshwanthram"
```

* You also can add a new key-value pair using the `update()` method.
```python
usernames.update({"sarah": "SarahB123"})
``` 

* You can delete a key-value pair from a dictionary using `del` keyword and accessing the key of the key-value pair that we want to delete.
```python
del usernames["Shrikanth"]
```

* In order to completely empty the dictionary, you can use the `clear()` method.
```python
usernames.clear()
```

* If you just want to remove the last item in the dictionary, you can use the `popitem()` method. 
```python
usernames.popitem()
``` 

* If you want to copy a dictionary, you can use the `copy()` method.
```python
usernames_copy = username.copy()
```