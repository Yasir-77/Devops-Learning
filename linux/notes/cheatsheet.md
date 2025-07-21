# 📄 Linux Commands Cheatsheet

## 🔍 Navigation
```
pwd               # Show current working directory  
ls                # List files in current directory  
ls -l             # List files with detailed info  
cd <dir>          # Change to a directory  
cd ..             # Go up one level  
cd ~              # Go to the home directory  
```
## 📂 File & Directory Management
```
mkdir <dir>       # Create a new directory  
rmdir <dir>       # Remove an empty directory  
rm <file>         # Delete a file  
rm -r <dir>       # Delete a directory and its contents  
cp <src> <dest>   # Copy file or directory  
mv <src> <dest>   # Move or rename file/directory  
touch <file>      # Create a new empty file
```
## 📝 Viewing & Editing Files
```
cat <file>        # View contents of a file  
less <file>       # View file one page at a time  
head <file>       # Show first 10 lines of a file  
tail <file>       # Show last 10 lines of a file  
nano <file>       # Edit file using Nano editor  
vim <file>        # Edit file using Vim
```
## 🔐 Permissions & Ownership
```
chmod +x <file> # Make a file executable  
chmod 755 <file> # Set specific permissions (rwx for owner, rx for others)  
chown <user>:<group> <file> # Change file owner and group
```
## 👤 User & System Info
```
whoami # Show current logged-in user  
id # Show user and group IDs  
uptime # Show how long system has been running  
uname -a # Show system information  
 ```
## 🔄 Redirection & Pipes
```
command > file # Redirect output to file (overwrite)  
command >> file # Append output to file  
command < file # Use file as input  
command1 | command2 # Pipe output of command1 to command2
```
## 📦 Package Management (Debian-based)
```
sudo apt update # Update package lists  
sudo apt upgrade # Upgrade installed packages  
sudo apt install <pkg> # Install a package  
sudo apt remove <pkg> # Remove a package
```
## 🔍 Search & Find
```
grep "text" <file> # Search for text in a file  
find . -name "*.txt" # Find files by name
```
## 🧪 Misc & Helpful
```
history # Show command history  
clear # Clear the terminal  
echo "text" # Print text to terminal
```
