## Level 6: File Sorting Script

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


