# Character and String Standards

When we're working with strings in Python, computers don't actually store them as string values. 
* Instead, computers store characters as _numbers_.
* Each character used by a computer corresponds to a unique number.
* The most commonly used character number assignment is **ASCII**.
    * ASCII - American Standard Code for Information Interchanged
    * It provides space for 256 different characters. It uses 8 bits for each sign.
* However, ASCII isn't flexible enough to add internationalization to account for different alphabets.
* So the concept which solved the problem was **Unicode**.
    * Unicode assigns unique characters to a million code points.
        * A code point is a unique number which makes a character.
        * For example, 65 is a codepoint which makes the uppercase letter 'A' in ASCII encoding.
    * The first 128 unique code points are identical to ASCII.
* The most commonly used Unicode is **UTF-8**. 
    * UTF - Unicode Transformation Format
    * UTF-8 uses as many bits for each codepoint as it really needs to represent them.
* Since Python fully supports Unicode and UTF-8, it means that Python3 is completely internationalized. 

## Functions to work with Strings 
Strings are **immutable** sequences. Python also provides functions to work with characters and their code points.
* If you want to know a character's code point, you can use the `ord()` function for _ordinal_. After passing a single character to this function, it returns the correspoding code point. 

```python
print(ord('A'))
```
---
 * To get the corresponding character for a code point, we can make use of the `chr()` function.
```python
print(chr(65))
```
---
* Python also provides a function called `min()`. This function returns the minimum of the sequence we pass to it.
```python
print(min("Asif"))
print(min("Hello World!"))
```
With lists, it simply returns the lowest value in that list. With strings, however, it returns the character with the **lowest code point** value.

---
* The function `max()` returns the element with the highest value in the list. Or with strings, it returns the character with the highest code point value. 
```python
print(max("Asif"))
print(max("Hello World!"))
```