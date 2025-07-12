## Level 2: Variables and Loops

### Mission: Create a script that outputs the numbers 1 to 10, one number per line.

### Solution:
```
#!/bin/bash

number=1

while [ $number -le 10 ]
do
    echo "number: $number"
    ((number++))
done    
```
### Code Breakdown:

- **`number=1`** - Sets a variable called number to 1.

- **`while [ $number -le 10 ]`** - While Loop Starts Begins a loop that will continue running as long as the value of number is less than or equal to 10. [ $number -le 10 ] is a test condition. le means “less than or equal to”.

- **`echo "number: $number"`** - Prints the current value of number to the terminal.

- **`((number++))`** - Increment, Increases the value of number by 1 with each loop iteration.

### Expected Output:
```
number: 1
number: 2
number: 3
...
number: 10
```
