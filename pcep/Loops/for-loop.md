# For Loop

For Loop is also known as a counting loop.
 
```python
for i in range(5):
    print(i)
```

* **range()** -
The range function is responsible for generating all the desired values of the _control variable_. In our example, the functions will create values from 0 to 4.
* **Control Variable** - Here, _i_ is the control variable of the loop. This variable _counts_ the loop turns automatically.

You can also add a first argument to the range function, inorder to determine the _initial value_.
```python
for i in range(2, 10):
    print(i)
```

## break Keyword
In some cases we don't want to continue the loop after a certain event. At these situations, Python allows us to _break_ out of the loop with the `break` keyword

```python
for i in range(5):
    if i == 2:
        break
    print("i:", i)
```

## continue Keyword
In some cases, instead of breaking out of the loop, we just want to skip the current iteration. This means that for specific values within that range, the codeblock won't get executed. You can do this with the `continue` keyword.

```python
for i in range(5):
    if i == 2:
        continue
    print("i:", i)
```

Both of these keywords are also applicable for the **while loop**.