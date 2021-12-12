# User-defined Modules

So far, we've seen only modules that were shipped with Python. However, we can also write our own modules.
* A **module** is basically a container filled with functions that you want to distrbute.
* If you've created many modules, you can even group modules together into a **package**.

Contents of a module file gets implicitly executed by Python when we import the file.   
For example,

### module.py
```python
print("Hello there!")
```
### main.py
```python
import module
```
> Output:
```
Hello There!
```
The initalization of the module only happens once!  

## `__name__` variable
When we create a module, Python initializes some extra values. One of them is a variable called `__name__`.
* The value of the variable is dependent on how the file is run.
### module.py
```python
print(__name__)

if __name__ == "__main__":
    print("I am not in a module")`
```
### main.py
```python
import module
```
* If we run _module.py_ directly, you'll see it prints `__main__`.
* However, if we run _main.py_ which imports the _module.py_ file, you'll see that it's value is the name of the module.
* The `__name__`variable makes it easy for us to detect in which context the code has been activated.
* In this case, the codeblock of the if statement will only run if the module.py file is executed directly, instead of as a module.
---
The entities inside a module can be accessed using the dot notation
### module.py
```python
secret_number = 5
```
### main.py
```python
import module

print(module.secret_number)
```
In some cases, you do't want to expose some values within a file. 
* Unfortunately, Python has no way to hide module content from users.
* So instead, we follow a convention by preceeding the variable name with one or two underscores.
* If you see a value, preceeded by underscores, just know that it should be considered a private value.

## Structure of a module
### module.py
```python
#!/usr/bin/env python3 

""" module.py - an example of Python module """

__secretNumber = 0

def get_sum(list):
    pass

if __name__ == "__main__":
    print("I'm running on my own!")
    print("Yayyyy!")
```
* On the first line, we see the line starting with a _hashbang(or a shebang)_. We can use this to tell Unix and Unix-like operating system, how to execute contents of the file.
* Next, we see a line explaining the purpose and contents of the module. It is usually called a _doscstring_.
* Then, we see functions defined inside the module that can be imported.
* And lastly,  we have a block that executes, in case the file is run standalone.
* We can import the module and use its contents in a _main,py_ file.
### main.py
```python
import module

l = [4, 6, 8, 10]
module.get_sum(l)
```
## Importing module from a different directory
In some cases, we won't create modules with the same folder like we did till now.
* When we import a module, Python searches through specific files inorder to find the module that we want to import. 
* There is a specific variable called **path** from the _sys_ module, that stores the location of the Python searches inorder to find this module. 
```python
import sys

print(sys.path)
```
> Output:
```
['C:\\Users\\User\\AppData\\Local\\Programs\\Python\\Python37-32\\Lib\\idlelib', 'C:\\Users\\User\\AppData\\Local\\Programs\\Python\\Python37-32\\python37.zip', 'C:\\Users\\User\\AppData\\Local\\Programs\\Python\\Python37-32\\DLLs', 'C:\\Users\\User\\AppData\\Local\\Programs\\Python\\Python37-32\\lib', 'C:\\Users\\User\\AppData\\Local\\Programs\\Python\\Python37-32', 'C:\\Users\\User\\AppData\\Local\\Programs\\Python\\Python37-32\\lib\\site-packages', 'C:\\Users\\User\\AppData\\Local\\Programs\\Python\\Python37-32\\lib\\site-packages\\win32', 'C:\\Users\\User\\AppData\\Local\\Programs\\Python\\Python37-32\\lib\\site-packages\\win32\\lib']
```
* The first element is the folder in which the execution starts.
* You may also see some zip folders, because Python is able to **treat zip files as ordinary folders**, which can be more memory efficient.
* If Python cannot find the module in these folders, the import fails. 

So to import the module from a different directory, we need to append the path to the _sys.path_ variable
### module1.py
```python
# My Location-> C:\MyModules\module1.py

message = "Python Forever!"
```
### module2.py
```python
# My Location-> C:\MyModules\module2.py

message = "C# is the best!"
```
### main.py
```python
import sys
sys.path.append("C:\\MyModules")

import module1, module2
print(module1.message)
print(module2.message)
```
----
If the modules folder is in the same directory as the _main.py_ file, we can use the _from_ keyword to import the modules inside it.
### module1.py
```python
# My Location-> C:\Python\MyModules\module1.py

message = "Python Forever!"
```
### module2.py
```python
# My Location-> C:\Python\MyModules\module2.py

message = "C# is the best!"
```
### main.py
```python
# My Location -> C:\Python\main.py
from MyModules import module1, module2
print(module1.message)
print(module2.message)
```

## Creating Packages

As your application gets bigger, you'll probably want to write multiple modules, that we might want to group together. We can do this by creating a **package**.
* A package is basically a subtree of folders and files.
* You can also import subfolders. In that case, we'll have to specify the fully qualified path. 
* We can zip the subdirectory inorder to save some memory. Since Python is able to treat zip files as ordinary folders, we tell Python to import modules from the zip file. 

### operations.py
```python
# My Location -> C:\Python\MyPackage\MathematicModules\operations.py
def add(x, y):
    return x+y
def sub(x, y):
    return x-y
```

### operations.py
```python
# My Location -> C:\Python\MyPackage\ScientificModules\operations.py
def powerhouse():
    pass
def mitochondria():
    pass
```

### main.py
```python
# My Location -> C:\Python\main.py
from MyPackage.MathematicModules import operations as m
from MyPackage.ScientificModules import operations as s


print(m.add(5, 10))
print(m.sub(11, 5))

s.powerhouse()
s.mitochondria()
```
* The subfolders in a package can be accessed using the dot notation.