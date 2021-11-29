# Literals

We use literals in python to enocde data and put them into our code

## Types Of Literals

* **Integer**  
&rarr; An integer is a number that doesn't have a fraction.

    * Octal Numbers (Starts with 0o)  
    &rarr;  An octal number uses 8 as the base  
    &rarr; You can find the value of an octal number by multiplying each digit from the **right** with 8<sup>0</sup>, 8<sup>1</sup>, 8<sup>2</sup> ... 
    and so on and then summing it.  
    Ex: 0o123 = (8<sup>2</sup>)(1) + (8<sup>1</sup>)(2) +   (8<sup>0</sup>)(3) = 64 + 16 + 3 = 83 

    * Hexadecimal Numbers (Starts with 0x)  
    &rarr;  A hexadecimal number uses 16 as the base  
    &rarr; We find the value of hexadecimal number just the way as we did for octal numbers, but here we use the _base_ as 16.  
    Ex: 0x123 = (16<sup>2</sup>)(1) + (16<sup>1</sup>)(2) +   (16<sup>0</sup>)(3) = 256 + 32 + 3 = 291 

* **Floating point number**  
&rarr; A floating point number has a non-e,pty decimal fraction.  
&rarr; Floating point numbers that contain a lot of decimals can also be written with an 'e' in order to represent the number in an economical form.  
Ex: 0.0000000000000000000001 can also be written as 1e-22
* **Strings**  
&rarr; Strings are used to represent text. In order for Python to recognize the value as a _String_, the value needs to be wrapped in single quotes (') or double quotes (")  
&rarr; In order to use quotes within the string itself, we use the escape character ( \ ).
```
"Hello \"Python\" is cool"
```
* **Booleans**  
&rarr; `True` and `False` are two boolean values. If boolean values were to be represented as numbers,  _True_ can be represented as 1, while _False_ as 0.




