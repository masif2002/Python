# Lambda functions
In Python, we use _lambda functions_ to simplify code. 
* A **lambda functon** is nothing but a function without a name, also called an anonymous function.
* We can create a _lambda function_ with the `lambda` keyword directly followed by  the parameters, a colon, and the expression.

Syntax:
```
lambda <parameters>: <expression>
```

* In order to use the lambda, we need to assign it to a variable.
* We can invoke the lambda like we would invoke a regular function.
* Let's create a lambda function that returns the square of a number
```python
sqr = lambda x: x*x
print(sqr(2))
```
* We can also create a lambda function that takes no arguments
```python
greet = lambda: "Hello"
print(greet())
```
* If we need to get multiple parameters in lambda function, we do so by seperating the parameters by a comma
```python
add = lambda a, b: a+b
print(add(7, 12))
```

Lambda can be really useful when working with some built-in functions such as `map()` and `filter()`.

## map() function
The map() function receives a function and then a list which **maps** the function to all of the provided list elements.
```python
num = [1, 2, 3]

double = list(map(lambda x:x*2, num))
print(double)
```
> Output:
```
[2, 4, 6]
```

## filter() function
The filter() function is somewhat similar to map(), but the function that it receives **filters** the list provided as its second argument, based on whether the function returns true or false. So the _lambda_ function should return a boolean value when used in filter() function.

```python
nums = [x for x in range(10)]

eve = list(filter(lambda x:x%2==0, nums))
odd = list(filter(lambda x:x%2!=0, nums))

print(eve)
print(odd)
```
> Output:
```
[0, 2, 4, 6, 8]
[1, 3, 5, 7, 9]
```
## sorted() function
`sorted()` sorts any sequence and always returns a list with the elements in a sorted manner, without modifying the original sequence.

Syntax:
```
sorted(<iterable>, <key>, <reverse>)
```
* The optional parameter **reverse** is set to True for sorting in the reverse order, ie- descending order.

* The optional parameter **key** takes a function as its value. This key function transforms each element before sorting, it takes the value and returns 1 value which is then used within sort instead of the original value. 

 For example, if we pass a list of strings in sorted(), it gets sorted alphabetically. But if we specify key = len, i.e. give len function as key, then the strings would be passed to len, and the value it returns, i.e. the length of strings will be sorted. Which means that the strings would be sorted based on their lengths instead.
 ```python
 L = ["cccc", "b", "dd", "aaa"]

print("Normal sort :", sorted(L))
print("Sort with len :", sorted(L, key=len))
```
> Output:
```
Normal sort : [3, 7, 11, 15]
Sorted with key: [7, 15, 3, 11]
```
Another example, where we sort _events_ according to the _date_.
```python
events = [
        {'date': 11212021, 'name': 'Bengali wedding'},
        {'date': 11012021, 'name': 'Project meeting'},
        {'date': 11112021, 'name': 'Guitar class'},
]

sorted_events = sorted(events, key=lambda x: x['date'])
print(sorted_events)
```
> Reference for sorted() function: geeksforgeeks.org/sorted-function-python/
