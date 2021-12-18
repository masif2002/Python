# Generator
**Generators** are specialized code that's able to return a series of values, and to control the iteration process.

* It is usually invoked more than once
* the `range()` function in Python is actually a _generator_ and it returns an _iterator_ with which we use the for-loop to iterate through the values.
```python
for i in range(5):
    print(i)
```
## Iterator
An **iterator** is a data type that returns the iterator protocol.
* Iterator protocol is a set of rules by which an object should behave.
 
A value is an **iterator** when it provides two things.
* `__iter__()` - This method returns the object itself, and it's only invoked once.
* `__next__()` - This method returns the next value of the series of values, and is continuously invoked before in, to be able to iterate through the sequence.
    * This method raises a StopIteration error if there are no more values to provide.

## User-defined generator
We can make our own **generator** as long as it contains the methods that are necessary in order to confirm to the **iterator protocol**.
```python
class CustomRange:
    def __init__(self, rangee):
        self.__range = rangee
        self.__i = 0

    def __iter__(self):
        return self

    def __next__(self):
        res = self.__i # saving the current state
        self.__i += 1

        if self.__i > self.__range:
            raise StopIteration
        return res

for i in CustomRange(10):
    print(i)
```
> Output:
```
0
1
2
3
4
5
6
7
8
9
```
We just generated our own totally valid generator that we can use. However, you might notice that this implementation is pretty inconvenient. Because, we need to save the current state of the iteration with the _i_ variable.
* Luckily, Python offers a more elegant way of writing iterators with the `yield` keyword.

## yield keyword

The `yield` keyword is pretty similar to the `return` keyword in a function, in the sense that it provides a value.
* It is used to return *from a function*, without destroying the state of the function.
* And when the function is called, the execution starts from the last yield statement.
* Any function that contains a `yield` keyword is termed a generator.
```python
def gen():
    for i in range(10):
        if (i % 2 == 0):
            yield i

for x in gen():
    print(x)
```
> Output:
```
0
2
4
6
8
```
## next() function
The next() function returns the next item in an iterator.
```python
def gen():
    for i in range(10):
        if (i % 2 == 0):
            yield i
c = gen()
print(c)
```
> Output:
```
<generator object gen at 0x03A8FD70>
```
Here, we are going to use the next() function in the generator object. Previously, we used a for-loop to iterate over the generator object to print the values. Now, we'll use the next() function to do the same.
```python
def gen():
    for i in range(10):
        if (i % 2 == 0):
            yield i
c = gen()
print(next(c))
```
> Output:
```
0
```
Using next() once, returns the first item in the iterator object. Using it multiple times, will give us the next items.
```python
def gen():
    for i in range(10):
        if (i % 2 == 0):
            yield i
c = gen()
print(next(c))
print(next(c))
print(next(c))
print(next(c))
print(next(c))
``` 
> Output:
```
0
2
4
6
8
```
Here, _c_ is an iterator object , and is meant to be iterated over once until it is exhausted. Once the object has been exhausted, it will not produce any more elements.  At this point, the generator mechanism is designed to raise a **StopIteration** error if you attempt to iterate over it even after it has been exhausted. 
* In our example, we should have 5 elements in our iterator object as per the logic of our function. So we've used the next() function 5 times, and the object is now exhausted. If we try to use the next() function one more time, Python raises a StopIteration error.
```python
def gen():
    for i in range(10):
        if (i % 2 == 0):
            yield i
c = gen()
print(next(c)) #1
print(next(c)) #2
print(next(c)) #3
print(next(c)) #4
print(next(c)) #5
print(next(c))
```
> Output:
```
0
2
4
6
8
Traceback (most recent call last):
  File "C:\Users\User\Documents\Asif\test.py", line 11, in <module>
    print(next(c))
StopIteration
```
* Constructs such as for loops listen for this error, silently swallowing it, however, next returns the raw exception as soon as it has been raised.