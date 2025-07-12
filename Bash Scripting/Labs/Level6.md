## Level 6: Argument Parsing

### Mission: Write a script that accepts a filename as an argument and prints the number of lines in that file. If no filename is provided, display a message saying 'No file provided'.

---

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

---

### Code Breakdown:

- `if [ $# -eq 0 ]:` - Checks if no arguments were passed to the script. **`$#`** is the number of arguments given. **`-eq 0`** means "equal to zero".

- `echo "No file provided"`: - Prints a message if no file was given. **`exit 1`**: Stops the script and returns exit code 1 (indicates an error).

- `if [ ! -f "$1" ]:` - Checks if the file does not exist. **`$1`** is the first argument to the script (expected to be the filename). **`-f`** checks if the file exists and is a regular file. **`!`** negates the check (so this means "if the file does not exist").

- `echo "File not found!"`: Informs the user that the specified file is missing. **`exit 1`**: Again, exits the script with error code 1.

- `LINE_COUNT=$(wc -l < "$1")` - LINE_COUNT=$(...): Stores the line count in a variable called LINE_COUNT. **`wc -l < "$1"`**: Counts the number of lines in the file. wc -l counts lines. Using **`< "$1"`** redirects the file contents into wc -l without printing the filename in the output.

- `echo "The file '$1' has $LINE_COUNT lines."` - Prints the final message showing: The file name ($1) & The number of lines ($LINE_COUNT).
