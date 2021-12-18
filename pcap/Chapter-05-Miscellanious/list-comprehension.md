# List Comprehension 

**List Comprehension** is nothing but a shorter implementation of a list in a more elegant way.
```python
l1 = []
l2 = []

for x in range(10):
    if x % 2 != 0:
        l1.append(x)
        
for x in range(10):
    l2.append(x if x % 2 != 0 else 0)

print(l1)
print(l2)
```
This is the way how we normally create a list. We can do the same using **list comprehension** in a single line.
```python
l1 = [x for x in range(10) if x % 2 != 0 ]
print(l1)

l2 = [x if x % 2 != 0 else 0 for x in range(10)]
print(l2)
```

* It's actually easy to turn any list comprehension into a generator, by replacing square brackets with parantheses. 
* We can iterate over the returned generator with a for-loop.

```python
l = (x for x in range(10) if x % 2 != 0 )

print(l)
for i in l:
    print(i, end=", ")
```
> Output:
```
<generator object <genexpr> at 0x03B1FEB0>
1, 3, 5, 7, 9, 
```