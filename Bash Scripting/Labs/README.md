# The Game: Bash Battle Arena 🎮

The "Bash Battle Arena" is a command-line game I've designed to teach and improve Bash scripting skills in a fun and interactive way. The game presents players with a series of increasingly complex challenges that they must solve by writing Bash scripts. Each challenge is structured like a level in a game, and as players progress, they learn new Bash concepts and best practices.

Objective: Players must complete various tasks or "missions" using Bash scripts. These tasks range from simple file manipulations to more complex system operations. The goal is to "defeat" each level by correctly solving the problem, with the ultimate aim of becoming a "Bash Master."

## Level 1: The Basics

### Mission: Create a directory named Arena and then inside it, create three files: warrior.txt, mage.txt, and archer.txt. List the contents of the Arena directory.

### Solution:
```
#!/bin/bash

mkdir Arsena
cd Arena
touch warrior.txt image.txt archer.txt
ls
```
### Code Breakdown:

- **`mkdir Arena`** - Creates a directory named Arena
  
- **`cd`** Arena - Change Directory - This moves you into a directory named Arena

- **`touch warrior.txt image.txt archer.txt`** - Creates 3 empty text files: warrior.txt, image.txt, archer.txt If these files already exist, touch will update their timestamps without changing their contents.

- **`ls`** -  List all files in the current directory, after creating the files, this command shows them in your terminal.

### Expected output:
```
archer.txt  image.txt  warrior.txt
```

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














































