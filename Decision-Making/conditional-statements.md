# Conditional Statements


```
if [condition1]:                    
    print("Condition1 is true)  
elif [condition2]:                    
    print("Condition2 is true)  
elif [condition3]:                    
    print("Condition3 is true)  
else:
    print("This block gets executed when none of the condition is True)
```

* Only, if the _condition_ after the _**if**_ statement is true, code under the `if` block gets executed and rest of the `elif` statements are ignored.
* If _condition1_ is false, Python checks the next `elif` statement (if present). If that condition is true, that particular `elif` blocks get executed.
* If _condition2_ is also false, Python checks for the next `elif` statement. The cycle keeps on going.
* If **none** of the conditions are true, code under the else block gets executed.