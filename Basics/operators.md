# Operators

To calculate values, we use Arithmetic Operators.

## Arithmetic Operators  
* Exponentiation Operator (**)  
&rarr; Ex: `a**b` where _a_ is the base and _b_ is the exponent   
&rarr; If both the values are _integers_, the result will also be an _integer_, however even if one of the values is a _floating point number_, the result will be a _floating point number_ aswell.
* Multiplication Operator (*)  
&rarr; Ex: `a*b` where _a_ and _b_ are the two operands for multiplication  
&rarr; The _floating point_ vs _integer_ rule applies here aswell.  
* Division Operator (/)  
&rarr; Ex: `a/b` where _a_ divides _b_  
&rarr; Unlike previous operators we saw, the _division_ operator always returns a _float_.
* Floor Division Operator (//)  
&rarr; Ex: `a//b` divides _a_ by _b_ but also _floors_ the value, meaning it rounds the value to the _lesser integer value_  
&rarr; This operator returns an integer as long as both the operands are integers. And it follows the _floating point_ vs _integer_ rule.
```
>>> print(6./4)
1.5
>>> print(6.//4)
1.0
>>> print(6./-4)
-1.5
>>> print(6.//-4)
-2.0
``` 
* Modulo Operator (%)  
&rarr; Ex: `a%b` gives the remainder when _a_ is divided by _b_
* Addition Operator (+)  
&rarr; Ex: `a+b` gives the sum of _a_ and _b_
* Subtraction Operator (-)  
&rarr; Ex: `a-b` gives the difference of _a_ and _b_ 
> Except the _division operator_, every operater goes by the _floating point_ vs _integer_ rule

&rarr; These are all **Binary Operators** which require **two** arguments.  
&rarr; But the _subtraction operator_ (-)  is also an **_unary operator_**. We can use this operator to specify that the value after this operator is negative.  
Ex: -6 &rarr; Negative 6 (_or_ minus 6)

## Priority Of Operators
```                               
                                  ^
+   -             -> unary        |   Highest Priority
**                                |
*   /   //  %                     |
+   -             -> binary       |   Lowest Priority
                                  v
```

* When we use multiple operators in a single expression, Python follows the priority mentioned above.
* And when we come across two operators with the same priority, we do the operation on the leftmost side first and the move towards the right
* Let's take an example: 
```
print(10 - 6 ** 2 / 9 * 10 + 1) 
```
1. In the above expression, the first prioority is for the _exponential operator_ (**).
```
10 - 36 / 9 * 10 + 1
```
2. The next priority goes to the _division_ (/) and _multiplication_ (*) operators. Since, the _division operator_ is on the lefthand side, we do the _divison_ first and then the _multiplication_.
```
10 - 4 * 10 + 1
```
```
10 - 40 + 1
```
3. Finally, we have the _least priority_ opeerators left (- and +). Again, we calculate the result from the lefthand side.
```
-30 + 1
```
```
-29
```
4. So, the final ouput that Python prints to the console is _-29_.

With _sub-expressions, which are the expression between parantheses, we can change the default hierarchy.

Sub Expressions are always calculated first.

```
print(2 * (2 + 3))
```
In this case, the sub-expression _2+3_ is calculated first, after which the result is multiplied by _2_ and the final result _10_ is printed out to the console.

Even though the operator within the sub-expression had a lower priority, than the multiplication operator, Python calculates the result of the sub-expression _first_, since **sub-expressions** have the _highest priority_ 