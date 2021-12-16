# Method overriding
If there is a method with the same name in a child class as well as the parent class, by default, the method in the child class only will be invoked.
* If you need to invoke the method of the parent class, with an existing method with the same name in the child class. You can do so:
    * with the name of the class followed by the dot operator and then the name of the method.
    * But here you need to pass in _self_ as a mandatory parameter, while calling the method because we call the method from the class level.
```python
A().method1(self)
``` 
* Or using the `super()` function, which is the preferred method
```python
super().method1()
```

```python
class A:
    def method1(self):
        return "Hi from class A"

class B(A):
    def method1(self):
        return "Hi from class B"
    def method2(self):
        # Accessing method1 from child class calls the child class's method only
        return self.method1()
    def method3(self):
        # Using super() we can access the parent class's method1
        return super().method1()
    

a = A()
b = B()

print(a.method1())
print(b.method1())
print()

print(b.method2()) 
print(b.method3())
```
> Output: 
```
Hi from class A
Hi from class B

Hi from class B
Hi from class A
```