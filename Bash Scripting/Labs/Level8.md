## Level 8: Multi-File Searcher

### Mission: Create a script that searches for a specific word or phrase across all .log files in a directory and outputs the names of the files that contain the word or phrase.

---

### Solution:
```
#!/bin/bash

Directory="$1"
Word="$2"

if [ -z "$Directory" ] || [ ! -d "$Directory" ]; then
    echo "Error: Directory does not exist or not provided."
    exit 1
fi

grep -l "$Word" "$Directory"/*.log

```

### Code Breakdown:

- `if [ -z "$Directory" ] || [ ! -d "$Directory" ]; then` - This checks two conditions: `-z "$Directory"`: True if Directory is empty (no argument passed). `! -d "$Directory"`: True if the path is not a valid directory. If either condition is true, it goes into the then block.

- `echo "Error: Directory does not exist or not provided."` - Prints an error message if the directory check failed.

- `grep -l "$Word" "$Directory"/*.log` - Searches for the given Word inside all .log files in the specified directory.`-l`: Makes grep print only the names of the files where matches were found.




  
