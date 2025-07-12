# 🎮 The Game: Bash Battle Arena 

The "Bash Battle Arena" is a command-line game codero designed to teach and improve Bash scripting skills in a fun and interactive way. The game presents players with a series of increasingly complex challenges that they must solve by writing Bash scripts. Each challenge is structured like a level in a game, and as players progress, they learn new Bash concepts and best practices.

Objective: Players must complete various tasks or "missions" using Bash scripts. These tasks range from simple file manipulations to more complex system operations. The goal is to "defeat" each level by correctly solving the problem, with the ultimate aim of becoming a "Bash Master."

---
### 📝 NOTE


Now, there is no interactive VM to ssh into, or a website (yet) - so the game is played on your laptops, and your bash script solutions are shared on your learning GitHub repositories. 

---

### 🧱 Game Structure

The games are level-based. You begin at level 1, and the difficulty increases as you go up the levels.

There is a Boss Battle every 5 levels designed to combine and reinforce the knowledge from the previous 5 levels.

Right now, there is no interface for the app - but soon there will be, and players will be scored based on their scripts' efficiency and speed.

---

### 🎯 The Game Miisions

## [Level 1: The Basics](https://github.com/Yasir-77/Devops-Learning/blob/main/Bash%20Scripting/Labs/Level1.md#level-1-the-basics)
Mission: Create a directory named Arena and then inside it, create three files: warrior.txt, mage.txt, and archer.txt. List the contents of the Arena directory.

## [Level 2: Variables and Loops](https://github.com/Yasir-77/Devops-Learning/blob/main/Bash%20Scripting/Labs/Level2.md#level-2-variables-and-loops)
Mission: Create a script that outputs the numbers 1 to 10, one number per line.

## [Level 3: Conditional Statements](https://github.com/Yasir-77/Devops-Learning/blob/main/Bash%20Scripting/Labs/Level3.md#level-3-conditional-statements)
Mission: Write a script that checks if a file named hero.txt exists in the Arena directory. If it does, print Hero found!; otherwise, print Hero missing!.

## [Level 4: File Manipulation](https://github.com/Yasir-77/Devops-Learning/blob/main/Bash%20Scripting/Labs/Level4.md#level-4-file-manipulation)
Mission: Create a script that copies all .txt files from the Arena directory to a new directory called Backup.

## [Level 5: The Boss Battle - Combining Basics](https://github.com/Yasir-77/Devops-Learning/blob/main/Bash%20Scripting/Labs/Level5.md#level-5-the-boss-battle---combining-basics)
Mission: Combine what you've learned! Write a script that:

1. Creates a directory names 'Battlefield'
2. Inside Battlefield, create files named knight.txt, sorcerer.txt, and rogue.txt.
3. Check if knight.txt exists; if it does, move it to a new directory called Archive.
4. List the contents of both Battlefield and Archive.

## [Level 6: Argument Parsing](https://github.com/Yasir-77/Devops-Learning/blob/main/Bash%20Scripting/Labs/Level6.md#level-6-argument-parsing)
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


















































