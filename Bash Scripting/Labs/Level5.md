## Level 5: The Boss Battle - Combining Basics

### Mission: Combine what you've learned! Write a script that:

1. Creates a directory names 'Battlefield'
2. Inside Battlefield, create files named knight.txt, sorcerer.txt, and rogue.txt.
3. Check if knight.txt exists; if it does, move it to a new directory called Archive.
4. List the contents of both Battlefield and Archive.

---

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

---

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

---

### Expected Outcome: 
```
Contents in Battlefield
rouge.txt
sorcerer.txt
Contents in Archive
knight.txt
```
