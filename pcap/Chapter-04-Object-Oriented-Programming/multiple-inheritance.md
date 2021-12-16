# Multiple Inheritance
Python also offers **multiple inheritance**.
* Multiple inheritance is when a class has more than one _superclass_.
```python
    class A:
        pass
    class B:
        pass
    class C(A, B):
        pass
```
* The subclass - _class C_ inherits all the functionalities from _class A_ aswell as from 
_class B_.
## Superclass priority
The priority for finding attributes and methods in the superclasses is from left to right. In our example, _class A_ has higher priority than _class B_.
* For example, if you have two methods with the same name in both the superclasses and the method is being invoked from the subclass, the method from class A will get invoked because it has a higher priority. If the method is not found in class A, then the method from class B gets invoked if it exists.
```python
class A:
    def greet(self):
        print("Hello from class A!")
class B:
    def greet(self):
        print("Hello from class B!")
class C(A, B):
    pass

obj = C()
obj.greet()
```
> Output:
```
Hello from class A!
``` 
## Module Resolution Order
The way that a programming language scans through the upper part of a class's hierarchy in order to find the entity it currently needs is called **Module Resolution Order (MRO)**.
* It's essentially a set of rules that Python follows in order to determine from which class to use an entity when you invoke it.
* The way that MRO works is that its algorithm scans  classes from bottom to top and from left to right.
* In MRO algorithm, **a class always appears before its ancestor**.
Let's take a look at an example
```python
class A:
    pass
class B(A):
    pass
class C(A):
    pass
class D(A, C):
    pass

obj = D()
```
Above, we intialize an object of the class D, which inherits from class A aswell as from class C. So according to MRO, Python looks for entities in class A first and then in class C.  Here in our case, class A is being searched before class C, which is the superclass. But, class C already inherits class A. So this contradicts the rule of MRO, ie- The class **should** appear before its ancestor. Then again, moving right, when the control goes to checking class C which inherits class A, it  has to go again back to class A which should not happen as per the MRO algorithm.
```
>> TypeError: Cannot create a consistent method resolution order (MRO) for bases A, C
```
So the correct order of inheritance in class D would be class C first and then class A.
```python
class A:
    pass
class B(A):
    pass
class C(A):
    pass
class D(C, A):
    pass

obj = D()
```
Doing this doesn't really make sense since class C already inherits from class A. We would achieve the exact same behaviour even if we only inherited class C instead. However, we used this example just to demonstrate what would happen if we did so.

## mro() method
Python offers the **mro()** method, which creates a linear list of the inheritance hierarchy.
```python
class A:
    def fun(self):
        return "Hi from A!"

class B(A):
    def fun(self):
        return "Hi from B!"

class AB(B, A):
    pass

print(AB.mro())
```
> Output:
```
[<class '__main__.AB'>, <class '__main__.B'>, <class '__main__.A'>, <class 'object'>]
```