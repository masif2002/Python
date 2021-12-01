# Bitwise Operators

Bitwise operators allow you to manipulate single bits of data.

* `&` &rarr; Conjunction (Bitwise AND)
* `|` &rarr; Disjunction (Bitwise OR)
* `~` &rarr; Negation (Bitwise NOT)
* `^` &rarr; Exclusive OR (Bitwise XOR)

```python
print(15 & 22)
print(15 | 22)
print(15 ^ 22)
print(~22)       #Output: -23 | Follows a pattern 
```

## Bit Shifting
With Bit Shifting, we can move bits a certain amount of places.
### Binary right shift
```python
print(22 >> 1)
```
Here, we're basically telling Python that we want to move all the bits that represent the integer 22 to the **right** by 1.

The result of performing a _binary right shift_ of one bit is same as the result of dividing the integer by 2
### Binary left shift
```python
print(22 << 2)
```
Here, we move all the bits that represent the integer 22 to the **left** by 2.  

_Binary left shift_ by one bit is the same as multiplying the integer by 2.

>Note:  
>bin() returns the binary value of the integer passed