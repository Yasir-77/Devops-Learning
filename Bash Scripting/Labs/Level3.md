## Level 3: Conditional Statements

### Mission: Write a script that checks if a file named hero.txt exists in the Arena directory. If it does, print Hero found!; otherwise, print Hero missing!.

### Solution:
```
#!/bin/bash

directory="Arena"
filename="Hero.txt"

if [ -f "$directory/$filename" ]; then
    echo "Hero found!"
else 
    echo "Hero not found!"

fi
```

### Code Breakdown: 

- **` directory="Arena" filename="Hero.txt"`** - These lines define two variables: directory holds the name of the folder you're checking (in this case, Arena). Filename holds the name of the file you're looking for (Hero.txt).

- **`if [ -f "$directory/$filename" ]; then`** - This line checks whether the file exists: -f means: Is this a regular file?, "${directory}/${filename}" combines both variables to form the full path: Arena/Hero.txt. If the file does exist, the code inside the then block runs.

- **`echo "Hero found!"`** - If the file exists, this line prints: Hero found!

- **`else 
    echo "Hero not found!"`** - If the file does not exist, this block runs instead and prints:

