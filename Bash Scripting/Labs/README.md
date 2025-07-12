# The Game: Bash Battle Arena 🎮

The "Bash Battle Arena" is a command-line game codero designed to teach and improve Bash scripting skills in a fun and interactive way. The game presents players with a series of increasingly complex challenges that they must solve by writing Bash scripts. Each challenge is structured like a level in a game, and as players progress, they learn new Bash concepts and best practices.

Objective: Players must complete various tasks or "missions" using Bash scripts. These tasks range from simple file manipulations to more complex system operations. The goal is to "defeat" each level by correctly solving the problem, with the ultimate aim of becoming a "Bash Master."

### NOTE

Now, there is no interactive VM to ssh into, or a website (yet) - so the game is played on your laptops, and your bash script solutions are shared on your learning GitHub repositories. 

Game Structure

The games are level-based. You begin at level 1, and the difficulty increases as you go up the levels.

There is a Boss Battle every 5 levels designed to combine and reinforce the knowledge from the previous 5 levels.

Right now, there is no interface for the app - but soon there will be, and players will be scored based on their scripts' efficiency and speed.

The Game

## [Level 1: The Basics](https://github.com/Yasir-77/Devops-Learning/blob/main/Bash%20Scripting/Labs/Level1.md#level-1-the-basics)
Mission: Create a directory named Arena and then inside it, create three files: warrior.txt, mage.txt, and archer.txt. List the contents of the Arena directory.

## [Level 2: Variables and Loops](https://github.com/Yasir-77/Devops-Learning/blob/main/Bash%20Scripting/Labs/Level2.md#level-2-variables-and-loops)
Mission: Create a script that outputs the numbers 1 to 10, one number per line.

## Level 3: Conditional Statements
Mission: Write a script that checks if a file named hero.txt exists in the Arena directory. If it does, print Hero found!; otherwise, print Hero missing!.

## Level 4: File Manipulation
Mission: Create a script that copies all .txt files from the Arena directory to a new directory called Backup.

## Level 5: The Boss Battle - Combining Basics
Mission: Combine what you've learned! Write a script that:

1. Creates a directory names 'Battlefield'
2. Inside Battlefield, create files named knight.txt, sorcerer.txt, and rogue.txt.
3. Check if knight.txt exists; if it does, move it to a new directory called Archive.
4. List the contents of both Battlefield and Archive.

## Level 6: Argument Parsing
Mission: Write a script that accepts a filename as an argument and prints the number of lines in that file. If no filename is provided, display a message saying 'No file provided'.

## Level 7: File Sorting Script
Mission: Write a script that sorts all .txt files in a directory by their size, from smallest to largest, and displays the sorted list.

## Level 8: Multi-File Searcher
Mission: Create a script that searches for a specific word or phrase across all .log files in a directory and outputs the names of the files that contain the word or phrase.

## Level 9: Script to Monitor Directory Changes
Mission: Write a script that monitors a directory for any changes (file creation, modification, or deletion) and logs the changes with a timestamp.

## Level 10: Boss Battle 2 - Intermediate Scripting
Mission: Write a script that:

1. Creates a directory called Arena_Boss.
2. Creates 5 text files inside the directory, named file1.txt to file5.txt.
3. Generates a random number of lines (between 10 and 20) in each file.
4. Sorts these files by their size and displays the list.
5. Checks if any of the files contain the word 'Victory', and if found, moves the file to a directory called Victory_Archive.

## Level 11: Automated Disk Space Report
Mission: Create a script that checks the disk space usage of a specified directory and sends an alert if the usage exceeds a given threshold.

## Level 12: Simple Configuration File Parser
Mission: Write a script that reads a configuration file in the format KEY=VALUE and prints each key-value pair.

## nLevel 13: Backup Script with Rotation
Mission: Create a script that backs up a directory to a specified location and keeps only the last 5 backups.

## Level 14: User-Friendly Menu Script
Mission: Create an interactive script that presents a menu with options for different system tasks (e.g., check disk space, show system uptime, list users), and executes the chosen task.

## Level 15: Boss Battle 3 - Advanced Scripting
Mission: Combine the skills you've gained! Write a script that:

1. Presents a menu to the user with the following options:

- Check disk space
- Show system uptime
- Backup the Arena directory and keep the last 3 backups
- Parse a configuration file settings.conf and display the values

2. Execute the chosen task.



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

## Level 5: The Boss Battle - Combining Basics

### Mission: Combine what you've learned! Write a script that:

1. Creates a directory names 'Battlefield'
2. Inside Battlefield, create files named knight.txt, sorcerer.txt, and rogue.txt.
3. Check if knight.txt exists; if it does, move it to a new directory called Archive.
4. List the contents of both Battlefield and Archive.

### Solution:
```
#!/bin/bash

mkdir -p Battlefield
touch Battlefield/knight.txt Battlefield/sorcerer.txt Battlefield/rouge.txt

if [ -f Battlefield/knight.txt ]; then
    mkdir Archive
    mv Battlefield/knight.txt Archive/

fi

echo "Contents in Battlefield"
ls Battlefield

echo "Contents in Archive"
ls Archive
```

### Code Breakdown:

- **`mkdir -p Battlefield`** - mkdir creates a directory named Battlefield. The -p flag ensures the script doesn't throw an error if the directory already exists.

- **`touch Battlefield/knight.txt Battlefield/sorcerer.txt Battlefield/rogue.txt`** - Creates three empty files inside the Battlefield directory: knight.txt, sorcerer.txt, and rogue.txt.

- **`if [ -f Battlefield/knight.txt ]; then`** then Checks if the file knight.txt exists inside Battlefield. **`-f`** ensures it's a regular file (not a directory or symlink).

- **`mkdir -p`** - Archive Creates a directory named Archive. Again, -p ensures no error if Archive already exists.

- **`mv Battlefield/knight.txt Archive/`** - Moves the file knight.txt from Battlefield to Archive.

- **`echo "Contents in Battlefield"
ls Battlefield`** - Prints the heading "Contents in Battlefield". Lists all files and directories inside Battlefield.

- **`echo "Contents in Archive"
ls Archive`** - Prints the heading "Contents in Archive". Lists all files and directories inside Archive.

### Expected Outcome: 
```
Contents in Battlefield
rouge.txt
sorcerer.txt
Contents in Archive
knight.txt
```
## Level 6: Argument Parsing

### Mission: Write a script that accepts a filename as an argument and prints the number of lines in that file. If no filename is provided, display a message saying 'No file provided'.

### Solution:
```
#!/bin/bash

if [ $# -eq 0 ]; then
    echo "No file provided"
    exit 1
fi
    
if [ ! -f "$1" ]; then
    echo "File not found!"
    exit 1
fi

LINE_COUNT=$(wc -l < "$1")
echo "The file '$1' has $LINE_COUNT lines."
```

### Code Breakdown:

- **`if [ $# -eq 0 ]:**` - Checks if no arguments were passed to the script. **`$#`** is the number of arguments given. **`-eq 0`** means "equal to zero".

- **`echo "No file provided"`**: - Prints a message if no file was given. **`exit 1`**: Stops the script and returns exit code 1 (indicates an error).

- **`if [ ! -f "$1" ]:`** - Checks if the file does not exist. **`$1`** is the first argument to the script (expected to be the filename). **`-f`** checks if the file exists and is a regular file. **`!`** negates the check (so this means "if the file does not exist").

- **`echo "File not found!"`**: Informs the user that the specified file is missing. **`exit 1`**: Again, exits the script with error code 1.

- **`LINE_COUNT=$(wc -l < "$1")`** - LINE_COUNT=$(...): Stores the line count in a variable called LINE_COUNT. **`wc -l < "$1"`**: Counts the number of lines in the file. wc -l counts lines. Using **`< "$1"`** redirects the file contents into wc -l without printing the filename in the output.

- **`echo "The file '$1' has $LINE_COUNT lines."`** - Prints the final message showing: The file name ($1) & The number of lines ($LINE_COUNT)



















































