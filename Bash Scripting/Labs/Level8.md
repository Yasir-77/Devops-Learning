## Level 8: Multi-File Searcher

### Mission: Create a script that searches for a specific word or phrase across all .log files in a directory and outputs the names of the files that contain the word or phrase.

---

### Solution:
```
#!/bin/bash

DIRECTORY="Arena"
SEARCH_TERM="Error"

if [ ! -d "$DIRECTORY" ]; then
    echo "Directory does not exist."
    exit 1
fi

grep -l "$SEARCH_TERM" "$DIRECTORY"/*.log

```

---

### Code Breakdown:





  
