# Nested Lists

## 2D Arrays
&rarr; A 2D Array is a list that consists of other lists.

Let's take a classroom for example. There are four rows, each with four students.
```python
classroom = [
    ["Sam", "Max", "Joe", "Anne"],
    ["Sofie", "Lisa", "Tim", "Sasha"],
    ["Claire", "Sara", "Leo", "Kim"],
    ["Zoe", "Guy", "Arun", "Eva"]
]
```
In Python, we can write this as following:
* We create a list with four elements.
* Each element represents a row of students.
* And each element, has four elements that represent each student.
* The list we created here, is called a **2D Array** or a **matrix**.
### Acessing elements
* Let's say we want to get an individual student. Let's say that we want to get _Arun_.
* First, we have to know which row they're on. In our case, it's the 4th row. In our 2D Array, that is the list on index 3.
* Within this list, _Arun_ is on index 2. We can get this value now by accessing the element on index 2.

```python
print(classroom[3][2])
```

## 3D Arrays
You can also have 3D Arrays in python. In 2D Arrays, we've used two square brackets to access an element. Similarly, in 3D Arrays, we use three square brackets to access an element.