# While Loop

A while loop is known as a conditional loop. 
* The while keyword allows you to execute a block of code repeatedly as long as a certain condition is True.
* This means that that code block can run repeatedly as long as the conditon is true
* If the condition is false, it exits the loop.

A while statement can also accept an else block.

* If the loop is exited normally, the _control_ comes to the else block, and the code under it gets executed.
* `else` statement is not mandatory. A loop can work without an _else_ block aswell.
> The loop can also be exited using the `break` keyword in Python
* If the loop _breaks_, the else block is ignored.

```python
num = 3
guess = int(input("Guess a number: "))
while guess != num:
    guess = int(input("Guess a number: "))
else:
    print("Congratulations! You got it!)
```