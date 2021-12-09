# OOP Principles

Object Oriented Programming comes with four key principles - **encapsulation**, **abstraction**, **inheritance** and **polymorphism**.

## Encapsulation
This concept refers to the mechanism of restricting the direct access to some of our attributes in a program.
* In the previous topic, we've implemented _encapsulation_, where the user was not given direct access to set the value of an attribute
* As we saw earlier, we restrict the access of our attributes outside the class by adding two underscores infront of the name of the attribute.
* So, restricting the ability to overwrite the values for your objects within your setters, is exactly what the _encapsulation_ principle is about.

In **encapsulation**, we don't allow direct access to the attributes, but we can create methods inside the class, which will enable the user to modify the value of an attribute.

## Abstraction
Abstraction is the concept of Object Oriented Programming that only shows the necessary attributes and hides the unnecessary information. 
* The main purpose of _abstraction_ is basically hiding unnecessary details from the users.
* For an example, if we need to send an email within our program, we will create a method to do so. But in that method, we call other methods which are responsible for sending an email. For example, 
    * Establishing a connection to the SMTP server
    * Generating content for an email body 
    * Sending the email
* But to the user, all these methods, won't make sense and isn't necessary for them to view all these methods. 
* So, In Python, we hide the methods, just like we hid attributes, by adding two underscores infront of the name of the method, when defining it. This makes the method inaccessible outside the class.

So the concept of **abstraction** follows the principle of _abstracting_ the information that is unnecessary.

## Inheritance
Inheritance is a mechanism that allows us to reuse a code across our classes.
* Previously, we've came up with classes that are child classes of the _item_ class, where each child class represents each kind of an item. 
* In the child class,  we could create methods and attributes which can be limited only to that child class, and wouln't make sense for it to be in the parent class, beacause the parent class could contain a wide variety of objects.
* This helps us to keep our code organized and respresent it in a way that is more readable. 

By inheriting a class, we are allowed to use all the non-private functions and attributes present in the parent class.

## Polymorphism
Polymorphism is a very important concept in programming.
* It refers to the use of a single entity that knows how to handle different kinds of objects.
* A great example, where _polymorphism_ is applied would be in the `len()` built-in function.
```python
name = "Asif"
print(len(name))

l = ["Hello", "There"]
print(len(l))
```
* Here, the `len()` function in python knows how to handle different kinds of objects that it receives as an argument, and returns the result accordingly.
* As we can see, when we use the _len_ function, with a string it returns the total number of characters in the string. At the same time, when we pass a list to the function, it counts the number of elements in the list, not the number of characters stored. 
* So this is a great example of _polymorphism_, where the _len_ function handles the different types of arguments passed and acts accordingly.

Polymorphism means - "many forms"
* poly &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &rarr;  many
* morphism &rarr; forms

Polymorphism isn't something that is specifically applied to just classes. It is actually something that refers globally to our entire program.