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