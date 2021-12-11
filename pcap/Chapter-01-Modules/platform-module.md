# platform Module

When writing programs, it can be useful to know on what platform the code is being executed. This can mean _hardware_, _operating system_, and _interpreter information_.
* The _platform_ function from the _platform_ module gives us access to these details. It allows us to control how the data is presented with two arguments:
    1. _aliased_ - If aliased is set to True or any non-zero value, it **may** present the alternative underlying layer names instead of the common ones. 
    2. _terse_ - If terse is set to a non-zero value, it may present a briefer form of the result. However, this is platfrom dependent.
```
>>> import platform
>>> platform.platform()
'Windows-10-10.0.19041-SP0'
>>> platform.platform(aliased=True)
'Windows-10-10.0.19041-SP0'
>>> platform.platform(terse=True)
'Windows-10'
```
## machine()
The machine function provided by the platform module, returns the architecture that runs our program with Python in your code.

```
>>> import platform
>>> platform.machine()
'AMD64'
```
## system()
The system function returns the name of the operating system

```
>>> import platform
>>> platform.system()
'Windows'
```

## version()
And lastly, the version function returns the version of the operating system. 
```
>>> import platform
>>> platform.version()
'10.0.19041' 
```
## python_version()
This function returns the python version as a string.
```
>>> import platform
>>> platform.python_version()
'3.7.0'
```
## python_implementation()

In some cases, it's also useful to know what version of Python is running your code. 
* `python_implementation()` from the platform module returns a string with the Python implementation.

```
>>> import platform
>>> platform.python_implementation()
'CPython'
```
## python_version_tuple()
This function returns a three element tuple, with:
* The major part of Python's version,
* the minor part,
* and the patch level number.

```
>>> import platform
>>> platform.python_version_tuple()
('3', '7', '0')
```