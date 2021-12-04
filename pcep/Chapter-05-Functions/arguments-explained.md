# Arguments Explained

```python
age = 22
def multiply(num):
    num *= 2
    print("Inside function:", num)

multiply(age) 
print("Age:", age)
```
>Output:
```
Inside function: 44
Age: 22
```
* In this example, we have a variable _age_ which is equal to 22 and a function called multiply() that receives a parameter. 
* On passing the _age_ variable to our function, it multiplies and prints 44
* In the next line, when we print the value of age, the age variable still has the value of 22.
* This happened because Python basically creates a **copy in memory** for the parameter passed.
* We didn't modify the original _age_ variable that we passed, but instead we created another variable for the parameter and it receieved the same value as the _age_ variable.
* When we multiplied that value, only the value of the parameter got multiplied and _age_ remained 22.

### Lists as parameters work different

```python
nums = [1, 3, 5]
def change(my_list):
    my_list[0] = 2
change(nums)
print(nums)
```
>Output:
```
[2, 3, 5]
```
* We know that, variables that have list values are stored with a pointer to the location of the list in memory.
* In our example, the function change() receives list as a parameter. In this function, we change the first value of the parameter list to be 2
* We call our function and pass our _nums_ list to the function.
* The parameter now points to the same list object in a memory as a nums list. 
* So, when our function change() modifies the first item in the list, we also see that **modification on the original list**.