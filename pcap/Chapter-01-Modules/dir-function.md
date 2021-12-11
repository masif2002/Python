# dir() function
A useful function when working with modules is the _**dir**_ function.
* This function returns an alphabetically sorted list of all the entities that a certain module provides.
* Although, it'll be easy to guess what most of these entities can be used for, we can still find documentation on how to use them in the Python documentation.

```python
import math

print(dir(math))
```
> Output:
```
['__doc__', '__loader__', '__name__', '__package__', '__spec__', 'acos', 'acosh', 'asin', 'asinh', 'atan', 'atan2', 'atanh', 'ceil', 'copysign', 'cos', 'cosh', 'degrees', 'e', 'erf', 'erfc', 'exp', 'expm1', 'fabs', 'factorial', 'floor', 'fmod', 'frexp', 'fsum', 'gamma', 'gcd', 'hypot', 'inf', 'isclose', 'isfinite', 'isinf', 'isnan', 'ldexp', 'lgamma', 'log', 'log10', 'log1p', 'log2', 'modf', 'nan', 'pi', 'pow', 'radians', 'remainder', 'sin', 'sinh', 'sqrt', 'tan', 'tanh', 'tau', 'trunc']    
```
If an entity is not passed to dir() function, it returns the list of names in the current local scope, meaning all the entities which are initialized by default in the interpreter and all the modules we have imported.