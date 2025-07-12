## Level 7: File Sorting Script

### Mission: Write a script that sorts all .txt files in a directory by their size, from smallest to largest, and displays the sorted list.

---

### Solution:
```
#!/bin/bash

Directory="Arena"

if [ ! -d "$Directory" ]; then
    echo "Directory does not exist."
    exit 1
fi

ls -lS $Directory/*.txt | awk '{ print $5, $9 }'
```

---

### Code Breakdown:


- `Directory="Arena"` - This assigns the variable Directory the value "Arena". So anywhere you use $Directory, it refers to the Arena folder.
  
- `if [ ! -d "$Directory" ]; then` - This checks if the directory does not exist. `-d` tests if the given path is a directory. `!` negates the test, so this is: “if not a directory”.
  
- `echo "Directory does not exist."` - If the condition is true (i.e., Arena doesn't exist), this line prints a message.
  
- `ls -lS $Directory/*.txt` - `ls -lS` lists .txt files in the directory: `-l`: Long listing format (shows permissions, size, date, etc.) `-S`: Sorts files by size, largest first. `$Directory/*.txt`: Targets all .txt files in the Arena directory.
  
- `| awk '{ print $5, $9 }'`- The pipe (|) sends the output of ls into awk. `awk '{ print $5, $9 }'` extracts: $5: The file size (5th column from ls -l),  $9: The file name.



  
