# String methods 

Strings have some useful built-in methods and functions that we can use.

## index()
Returns the index of the first occurence of the provided character.
* Throws an error if the character is not found
```python
print('Manty Python'.index('t'))
```

## count()
Returns the total number of occurences of the provided character.
* Start and end index can be passed as second and third arguments to count within the specified range.
```python
print('Manty Python'.count('y'))
```

## list()
Returns a new list containing all the string characters.
```python
print(list("Hello"))
```

## capitalize()
Returns a new string with a capitalized first letter, if the first character in the string is a letter. It also converts the remaining letters to lowercase.
```python
print(' Hello!'.capitalize())
print("hello wORLd!".capitalize())
```

## center()
This method adds characters before and after the string and returns a new string.
* The character to add, is space, by default.
* The first argument to this method is the new length of the string.
* The second optional argument allows us to change the character used for padding.
```python
print("hello".center(9))
print("hello".center(9, '*'))
```

## endswith()
Checks if a string ends with specific characters. 
```python
print("hello!".endswith('!'))
print("hello!".endswith('o!'))
print("hello!".endswith('.'))
```

## startwith()
Checks if a string starts with certain characters.
```python
print("hello!".startswith('h'))
print("hello!".startswith('hell'))
print("hello!".startswith('H'))
```

## find()
Returns the index of the first occurence of the provided character
* Won't throw an error if the character is not found, like `index()` would do, instead returns -1.
* We also can pass in the second and third argument specifying the start and end index to find the character in the given range.
```python
print("hey there".find(' '))
print("hey there".find('!'))


print("hey there".find(' ', 2, 5))
print("hey there".find('t', 0, 4))
```

## rfind()
Returns the index of the last occurence of the provided character.
```python
print("hello world!", 'o')
```

## isalnum()
Returns True if all the characters are alphanumeric, namely alphabet letter (a-z) and numbers (0-9).
```python
print("hello".isalnum())
print("h3llo".isalnum())
```

## isaplha()
Returns True if the string only contains letters.
```python
print("hello".isalpha())
print("h3llo".isalpha())
```

## isascii() 
Check if all the characters in the text are ascii characters.
* Ascii characters are those which contains the numbers from 0-9, English letters from A to Z (upper and lower case), and some special characters. Total 128.
```python
print("hey".isascii())
print("¾".isa.scii())
```

## isdigit()
Returns True if all the characters are digits. Exponents, like ², are also considered to be a digit, but fractions are not.
```python
print("2002".isdigit())
print("²".isdigit())
print("¾".isdigit())
```

## isnumeric()
Returns True if all the characters are numeric (0-9). Exponents, like ² and ¾ are also considered to be numeric values.
```python
print("2002".isnumeric())
print("²".isnumeric())
print("¾".isnumeric()))
```

## isdecimal() 
Returns True if all the characters are decimals (0-9).
* This method is used on unicode objects.
```python
a = "\u0030" #unicode for 0
b = "\u0047" #unicode for G
print(a.isdecimal())
print(b.isdecimal())
print("2002".isdecimal())
```


## islower()
Returns true if all the characters in the string are lowercase.
```python
print("Hello World!".islower())
print("hello world!".islower())
```
## isupper()
Returns true if all the characters in the string are uppercase.
```python
print("Hello World!".isupper())
print("HELLO WORLD!".isupper())
```

## isspace()
Returns true if all the characters in the string are whitespaces.
```python
print("Hello World!".isspace())
print("  ".isspace())
print("\n".isspace())
```

## join()
This method allows you to join string elements from a list into one single string and returns the newly created string.
* The string on which the `join()` method is invoked is used as the seperator.
```python
print("#".join(['How', 'Are', 'You', 'Doing']))
print("*".join("Hello"))
```

## split()
This method returns a list seperating a string with the specified character.
```python
print("Hello World!".split())
print("Hello World!".split('o'))
```

## lower()
Returns a new string, converting all characters to lowercase.
```python
print("HELLO".lower())
print("Hello".lower())
print("hello".lower())
```

## upper()
Returns a new string, converting all characters to uppercase.
```python
print("HELLO".upper())
print("Hello".upper())
print("hello".upper())
```

## lstrip()
Returns a new string stripping all the leading white spaces in the string.
* If you want to remove other leading characters besides whitespaces, you can pass it as an argument
```python
print("   hey ".lstrip())
print("www.pypi.org".lstrip('w.'))
```
* Here, it removes all the _w_ and _._ that were leading characters in the string.
## rstrip()
Returns a new string stripping all the trailing white spaces in the string.
```python
print("   hey ".rstrip())
print("www.pypi.org".rstrip('.org'))
```

## strip()
Returns a new string removing both leading and trailing white spaces in the string.
```python
print("   Personal Space  ".strip())
print("*1203000".strip('*0'))
```
* Here, it removes all the _*_ and _0_ which were leading and trailing characters in the string. The _0_ in the middle, is not removed because it is in the middle :)
## replace()
Returns a new string replacing certain characters in a string, with the provided characters.
* We can pass a third argument to the replace method, which limits the number of replacements.
```python
print("Python is booming! Python is love!".replace("Python", "GoLang"))
print("Replace all spaces".replace(" ", "***"))
print("Python is booming! Python is love!".replace("Python", "GoLang", 1))
```

## swapcase()
Returns a new string swapping the case of each character in the string
```python
print("THiS is So WeIRd".swapcase())
```

## title()
Returns a new string converting the first letter of every word in the string to uppercase and the rest to lowercase.
```python
print("this is ONE good title".title())
```
