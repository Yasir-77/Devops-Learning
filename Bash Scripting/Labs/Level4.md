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
