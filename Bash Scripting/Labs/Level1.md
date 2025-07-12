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
