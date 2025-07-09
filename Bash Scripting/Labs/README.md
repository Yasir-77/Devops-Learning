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


### Expected Output:
```
Hero not found!
```
### Tip:

You don’t have to use variables if you prefer a shorter version. You can write the path directly by using if [ -f Arena/Hero.txt ]; then.


## Level 4: File Manipulation

### Mission: Create a script that copies all .txt files from the Arena directory to a new directory called Backup.

### Solution:
```
#!/bin/bash

mkdir -p Backup
cp Arena/*.txt Backup/
```

### Code Breakdown:

- **`mkdir -p Backup`** - Creates a new directory named Backup. The -p flag means: Don't throw an error if Backup already exists, Create any parent directories if needed.

- **`cp Arena/*.txt Backup/`** - Copies all .txt files from the Arena directory into the Backup directory. **`*.txt`** is a wildcard that matches all files ending in .txt.



















































