# Linux notes

## What is Linux?
Linux is a versatile and powerful open-source operating system that forms the backbone of countless technological infrastructures, from servers and desktops to mobile devices and embedded systems. Known for its stability, security, and flexibility, Linux provides a robust platform that can be customized to suit a wide range of applications. It is supported by a vibrant global community of developers and users, which contributes to its continuous evolution and ensures a rich ecosystem of software and tools. Whether for personal use, enterprise environments, or innovative tech projects, Linux offers a reliable and adaptable solution for modern computing needs.

### Why use Linux?

- Linux is known for its flexibility, customisation and security features, which makes it popular in both professional and personal environments.

- Open Source Nature - Linux is open source, which means its source code is freely available to anyone. This allows users to modify, distribute, and even sell modifications to the OS under their own terms. 

- Cost-Effectiveness - Most Linux distributions are free to download and use, which can result in significant cost savings, especially for businesses and developers who need to deploy multiple machines.

- Customizability - Linux is highly customizable. Users can modify everything from the kernel (the core of the operating system) up to the desktop environment, allowing for a tailored experience that meets specific needs or preferences.

- Security -  Linux is considered highly secure compared to many other operating systems. Its permission and user role features, along with a strong community and frequent updates, help keep systems secure from malware and other vulnerabilities.

- Stability and Reliability - Linux systems are known for their stability and reliability. They can run for years without needing a reboot, which is a critical requirement for servers and continuous operation systems.

- Community Support - The Linux community is one of its greatest assets. A large, active community means users often get rapid support and help through forums, blogs, and community-driven projects.


There are many different versions of Linux called distributions some examples include Ubuntu, Fedora and CentOs.

### Why are there different distributions?

- Different distributions cater to differetn needs, which help beginners choose which one fits their requirements.

## How to install Linux

#### Method 1: Install Ubuntu via Virtual Machine 

Step 1: Download & Install VirtualBox
Go to the VirtualBox website and download the latest version for Windows.
Run the installer and follow the instructions.

Step 2: Download Ubuntu Latest Version
Visit the Ubuntu official website.
Download the latest Ubuntu ISO file.

Step 3: Create a Virtual Machine
Open VirtualBox and click New.
Name it Ubuntu, set Type to "Linux", and Version to "Ubuntu (64-bit)".
Allocate at least 2GB RAM (4GB recommended).
Create a virtual hard disk 

Step 4: Install Ubuntu
Select your new virtual machine and click Start.
Choose the Ubuntu ISO file you downloaded.
Follow the on-screen instructions to install Ubuntu.

#### Method 2: Install Ubuntu via WSL

WSL allows you to run Ubuntu directly on Windows without a virtual machine or dual-booting.

Step 1: Enable WSL
Open PowerShell as Administrator (Search for "PowerShell", right-click, and select "Run as Administrator").
Run the following command:

```
wsl --install
```
Wait for the installation to complete, then restart your computer.

Step 2: Install Ubuntu from Microsoft Store
Open the Microsoft Store on Windows.
Search for Ubuntu (you’ll see different versions like Ubuntu 20.04, Ubuntu 22.04, etc.).
Click Get or Install to download and install it.

Step 3: Launch Ubuntu & Set Up
Open the Start Menu and search for Ubuntu. Click to open it.
The first time you launch, Ubuntu will install files and ask you to create a username and password.
Once done, you can use the Linux terminal inside Windows!

## Basic Linux Commands

### What are commands?

Commands are textual instructions that tell the operating system what to do, they are usually typed into the terminal and are case sensitive. Commands have various options and arguments that can modify their behaviour and have instructions via a manual.

### What is the structure of a command?

The command itself, options and an arguemnt e.g. ls -a.

In this example command is **`ls`**, option is **`-a`** and argument is **`.`**

In this case the **`-a`** means that you are using the ls command to list the contents in the current directory but in this case all the contents including the hidden files and directories.

In this case the **`.`** means that the argument is in the current working directory.

### Examples of Basic Linux Commands:

- To print the present working directory. Run **`pwd`** command.
- To see the contents of the directory. Run **`ls`** command.
- To change the current directory. Run **`Cd`** command. For example, to change to the home directory type:
```
cd /home
```
- To make (or) create a directory. Run **`mkdir`** command. For example to creacte a new directory called myfolder type:
```
mkdir myfolder
```
- To remove (or) delete a directory. Run **`rmdir`** command. For example to delete a directory called my folder type:
```
rmdir myfolder
```
- To make (or) create a file. Run **`touch`** command. For example to create a file called file.txt type:
```
touch file.txt 
```
- To remove (or) delete a file. Run **`rm`** command. For example to remove a file called file.txt type:
```
rm file.txt
```

### More Examples of Basic Linux Commands:
### - echo command
To add text into a file. Run **`echo`** command. An example of how to add "Hello World" into an already made file.txt would be:
```
echo "Hello World" > file.txt
```
To add another line of text without removing any content already in the file simply use >> instead of >:
```
echo "Test" >> file.txt
```
If the file doesnt exist, the echo command can also be used to create a file. An example of creating a file2.txt would be:
```
echo "This is the second file" >> file2.txt
```

### - grep command
To search for specific content of text within a file. Run command **`grep`**. An example of how to search for the word "Hello" in the already made file.txt would be:
```
grep "Hello" file.txt
```

### - cat command
To search up all the contents in a file. Run the **`cat`** command. 
```
cat file.txt
```
The cat command could also be used to combine the contents of 2 files together creating a new file also. For Example:
```
cat file.txt file2.txt > combined.txt
```
To transfer the contents of one file to another file without creating a new file can be done using the cat command. For example transferring everthing in file2.txt to file.txt could be done by:
```
cat file2.txt >> file.txt
```

### - head and tail command
The **`head`** command displays the first part of files. By default, it shows the first 10 lines of a file. For example lets say filename.txt has 20 lines. Typing the following would show the first 10 lines:
```
head filename.txt
```
To display the first n lines only, use the head command in the following way. The number after -n stating how many lines to show, so for first 5 lines:
```
head -n 5 filename.txt
```
The **`tail`** command displays the last part of files. By default, it shows the last 10 lines of a file. 
```
tail filename.txt
```
To display the last n lines only, use the tail command in the following way. The number after -n stating how many lines to show, so for last 5 lines:
```
tails -n 5 filename.txt
```
Both head and tail can be used in combination with other commands using pipes (|). For example, you might want to view the last 10 lines of a file and then the first 5 lines of that result:
```
tail -n 10 filename.txt | head -n 5
```

## The SHELL

### What is the SHELL

The SHELL is a user interface that provides access to the operating system services, the layer between the user and the core of the operating system. Translates commands into actions.

### Types of SHELLS

- Bash shell

- Csh/Tcsh Shell

- Ksh Shell

- Zsh Shell

- Fish

Each shell has its own features and capabilities but all serve the same purpose to provide a userface that allows access to the operating system.

The default shell for most operating systems is the bash shell, to check this type:
```
echo $SHELL
```
To install a shell, type the following command **`sudo apt-get install`** followed by the desired **`<shell_name>`**. For example to install zsh shell type the following:
```
sudo apt install zsh
```
To then switch to the zsh shell just type the zsh command **`zsh`**.

To set zsh as the default shell type the following:

```
sudo chsh -s $(which zsh) $(whoami)
```
Then refresh the instance and restart the windows powershell.

### How to customize ZSH to OhMyZSH

- Run this command to install OhMyZsh:
```  
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
- To customise OhMyZsh to a specific theme run the command:
```
cd ~/ .oh-my-zsh/themes
```
- Then paste the command:
``` 
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/.oh-my-zsh/custom/themes/powerlevel10k 
```

### Zshrc Configuration File + Powerlevel10k Theme
- Return to home directory, type the following:
```
cd ~
```
- Open the zshrc file by typing:
```
vim .zshrc
```
- Then to edit the text editor type i to instert. Then find the line **`ZSH_THEME="robbyrussell"`** and replace it with **`ZSH_THEME="powerlevel10k/powerlevel10k"`**. Then exit the text editor by typing **`:wq!`** 
- Configure the Powerlevel 10k theme to your liking.

### Adding .zshrc plugins
- Open the zshrc file by typing:
```
vim .zshrc
```
- Scroll down until you find plugins or type /plugins then go on instert mode and type:
```
plugins=(git zsh-syntax-highlighting zsh-autosuggestions)
```
Exit the file by pressing Esc on keyboard and type **`:wq!`**

If the terminal shows plugin not found the plugins need to be installed. Type the following in the terminal:
```
git clone https://github.com/zsh-users/zsh-autosuggestions.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
Then run the command:
```
source .zshrc
```

## File management commands

### - cp command

The **`cp`** command is used to copy files and directories from one location to another. It stands for copy. For example you wanted to copy a file called myfiles1.txt to myfiles2.txt simply write the following:
```
cp myfile1.txt myfile2.txt
```
If file2.txt does not exist, it will be created.

When trying to use a cp command to copy a directory, use **`-r`** before writing which file to copy. -r : Copy directories recursively. This is required when copying directories. For example if you want to make a copy of my_directory type:
```
cp -r my_directory my_directory_copy
```

### - mv and rm commands

The **`mv`** command is used to move or rename files and directories. The mv command stands for move, but it functions as both a move and rename command, depending on how it is used.

To rename a file use the mv command and write the name of the old file and then the name of the new file. For example changing the name from oldname.txt to newname.txt type:
```
mv oldname.txt newname.txt
```

When moving a file into a directory simply type mv [File_name] [Directory_name]. For example newname.txt needs to be moved into New_directory type:
```
mv newname.txt new_directory
```
The **`rm`** command is used to remove (delete) files and directories. It stands for remove and is a powerful command because it deletes files and directories permanently, without moving them to a trash or recycle bin.

To remove a file simply type rm [File_name]. For example to reemove newname.txt type:
```
rm newname.txt
```
To remove a directory and the contents inside it type -r [directory_name] after the rm command. For example to delete new_directory type:
```
rm -r new_directory
```

### - mkdir, rmdir and rm -r commands

As already mentioned **`mkdir`** is used to make directories. 

To make nested/parent directories simply type mkdir and add -p followed by [Directory1/directory2/directory3] For example you wanted components directory in a src directory in a project directory simply type the following:
```
mkdir -p project/src/components
```

To list all files and subdirectories in the current directory type **`ls -R`** [Directory_name]. For example to list the directories created above under the project directopry type:
```
ls -R project
```

As already mentioned **`rmdir`** is used to delete empty directories.

In the example above project and src directories cant be removed using rmdir as they have subdirectories. The components direcotory has no subdirectory so to remove the components directory type:
```
rmdir project/src/components
```

The **`rm -r`** command is used to remove directories and their contents recursively. This means it will delete the specified directory, all files within it, and all subdirectories and their contents. To delete the project directory and all the subdirectories and the content within type:
```
rm -r project
```

### Dealing with spaces in folder names

When working with folder names that contain spaces, Linux interprets spaces as separators between commands and arguments. For example typing **`My Project`** creastes two folders names My and Project. There are two ways of creating the folder "My Project".

1. Use Quotes (" ") For example: To create the folder name "My Project" type:
```
mkdir "My Project"
```

2. Use Backslash (\) to Escape Spaces
```
mkdir My\ Project"
```

## VIM

To start vim, type **`vim`** followed by a file name in the terminal: For example to start vim in example.txt type:
```
$ vim example.txt

```
If the file filename.txt does not exist, Vim will open a new empty file. If it exists, Vim will open it for editing.

vim has multiple modes but the 3 most important ones are:

- command mode: This mode is used for entering commands, such as saving a file or exiting Vim. You enter Command-Line Mode by pressing : in Normal Mode. This is also the default mode when you enter vim.
  
- insert mode: In this mode, Vim behaves like a standard text editor, allowing you to input and edit text. You can enter Insert Mode from Normal Mode by pressing i.

- visual mode: This mode allows for text selection using the keyboard. You can enter Visual Mode by pressing v in Normal Mode.

### Navigating in Vim 

| Command | Action |
|---------|--------|
| `h` | Move the cursor left |
| `j` | Move the cursor down |
| `k` | Move the cursor up |
| `l` | Move the cursor right |
| `0` | Move to the beginning of the line |
| `$` | Move to the end of the line |
| `gg` | Move to the beginning of the file |
| `G` | Move to the end of the file |
| `w` | Move forward to the next word |
| `b` | Move backward to the previous word |
| `:n` | Move to line on n number |
| `/` | Word that follows the foward slash will be searched for. |
| `n` | If multiple of the same word is found, moves to next one down |
| `N` | If multiple of the same word is found, moves to next one up |

### Editing in vim

| Command   | Action |
|-----------|--------|
| `i`       | Enter Insert Mode before the cursor |
| `a`       | Enter Insert Mode after the cursor |
| `o`       | Insert a new line below the current line and enter Insert Mode |
| `O`       | Insert a new line above the current line and enter Insert Mode |
| `x`       | Delete the character under the cursor |
| `dd`      | Delete the current line |
| `yy`      | Yank (copy) the current line |
| `p`       | Paste the yanked or deleted text after the cursor |
| `u`       | Undo the last change |
| `Ctrl + r` | Redo the undone change |


### Saving and Exiting

To save and exit the file, use the Command-Line Mode:

| Command  | Action |
|----------|--------|
| `:w`     | Save the current file |
| `:q`     | Quit Vim (only works if no changes have been made) |
| `:wq`    | Save and quit Vim |
| `:q!`    | Quit Vim without saving changes |

## Sudo command

### What is the Sudo command

The sudo command stands for "superuser do." It allows a permitted user to execute a command as the superuser (root). The sudo command is typically used to perform tasks that require administrative privileges.

Examples of using sudo would be to run a command as a root. For example:
```
sudo apt-get update
```
This command runs apt-get update with root privileges, allowing you to update packages.

To edit protected files youll also need to use a sudo command. For example /etc/host is a protected root user file. To edit the file type:
```
sudo vim /etc/hosts
```
This command opens the /etc/hosts file with the vim text editor using root privileges, allowing you to edit the file.

When you need to switch to the root user to perform administritive taskts type the following:
```
sudo su
```
This is used when you are running multiple commands that require super user permissions.

To exit root user simply type **`exit`** in the terminal.

### rm -rf / **Very dangerous command**

The **`rm -rf /`** command is a very dangerous command and shoulbe be avoided. 

#### What does the command do?

Delete All Files and Directories: It will recursively delete every file and directory on the filesystem. This includes system files, user files, and everything else stored on the device

No Confirmation: Because of the -f option, rm will not ask for any confirmation before deleting files, regardless of their permissions or whether they are protected or critical system files.

#### Potential Consequences

System Crash: The command will start deleting essential system files and directories immediately, causing the system to become unstable and eventually crash.

Data Loss: All data on the system will be deleted, including personal files, system files, configurations, and applications. This data loss is typically unrecoverable without backups.

Unrecoverable State: After executing this command, the operating system will not function properly, if at all. The system would require a complete reinstall, and all data would be lost unless backed up elsewhere.


## Users

To create a new user type **`sudo useradd`** then the new username. For example to creat a user called newuser type:
```
sudo useradd newuser
```

To set a password for the user type **`sudo passwd`** followed by the [username]. For example to add a password to the username newuser type:
```
sudo passwd newuser
```

You would then need to type in a password and confirm the password again

To switch to the new user use the **`su`** command followed by [-] , followed by the user. For example to switch to the newuser created type:
```
su - newuser
```
You will then need to type the password you created.

To give the newuser sudo privellages, first exit the newuser by typing exit then type the following:
```
sudo usermod -aG sudo newuser
```
To check if this is complete the newuser should be able to read the contents of the root directory by typing:
```
sudo ls /root
```
The directories should then be listed, if not permission will be denied.

To remove sudo privellages, you would need to leave the new user by typing exit, this will take you to the ubunto user then type:
```
sudo deluser newuser sudo
```

## Groups:

To create a new group run the command **`sudo groupadd`** followed by [group-name]. For example to create a new devops group type:
```
sudo groupadd devops
```
To verify that this has been created type the command:
```
cat /etc/groups
```
To add users to the group that has been created the command **`sudo usermod`** is used followed by [-aG] followed by the [group-name] followed by the [user-name]. For exxample to add newuser to the devops group type:
```
sudo usermod -aG devops newuser
```
To remove a user from the group use the comman **`sudo gpasswd`** followed by [-d] followed by the [user-name] followed by [group-name] for example to remove the newuser from the devops group type:
```
sudo gpasswd -d newuser devops
```
To delete a group use the command **`sudo groupdel`** followed by the [group-name], for example to delete the devops group type:
```
sudo groupdel devops
```
Users can be in multiple groups, to add users into multiple groups the command **`sudo usermod`** followed by [-aG] followed by [group-name1,group-name2] followed by the [user-name]
Fore example to add a newuser into groups called group1 and group2 (these havent beeen created) type:
```
sudo usermod -aG group1,group2 newuser
```

## File permissions

### Introduction to File permissions

File permissions are represented by a combination of three types of permissions for three categories of users:

Types of Permissions:

- Read (r): Allows viewing the contents of a file or directory listing.
- Write (w): Allows modifying the contents of a file or creating/deleting files within a directory.
- Execute (x): Allows running a file as a program/script or accessing a directory's contents.

Categories of Users:

- Owner (u): The user who owns the file.
- Group (g): Users who are members of the file's group.
- Others (o): All other users.

A file's permissions can be viewed with the **`ls -l`** command, which shows them in the format:

-rwxr-xr--

Here, the first character represents the file type (e.g., - for a regular file, d for a directory). The next nine characters are grouped in sets of three, representing the permissions for the owner, group, and others respectively:

rwx (owner): Read, write, and execute.

r-x (group): Read and execute, no write.

r-- (others): Read only, no write or execute.

### Binary,Octal and String representation:

| Binary  | Octal | String (Symbolic) | Permission |
|---------|-------|-------------------|---------|
| 000 | 0(0+0+0)   | --- | No permissions |
| 001 | 1(0+0+1)   | --x | Execute |
| 010 | 2(0+2+0)   | -w- | Write |
| 011 | 3(0+2+1)   | -wx | Write & execute |
| 100 | 4(0+0+4)   | r-- | Read only |
| 110 | 6(0+0+6)   | rw- | Read & write |
| 111 | 7(4+2+1)   | rwx | Read & write & execute |

### Chmod command: symoblic and numeric

Using Symbolic Notation

Symbolic notation uses letters to modify permissions:

- u: User (owner)
- g: Group
- o: Others

You can add, remove, or set specific permissions using +, -, or =:

- +: Adds a permission.
- -: Removes a permission.
- =: Sets a specific permission, overriding the current setting.

Examples:

To grant the user execute permissions, groups read permissions and remove write permissions from others on file example.txt type the following:
```
chmod u+x,g+r,o-w example.txt
```
Set Read and Write Permissions for User, and Read for Group and Others Type:
```
chmod u=rw,go=r example.txt
```

Using Octal notation 

Set Permissions to rwxr-xr-x (755) for file example.txt:
```
chmod 755 example.txt
```
Gives the owner all permissions (read, write, execute), and read and execute permissions to group and others.

### Changing file/direcorty ownership for user/group

To change the owner of a file or directory the command **`sudo chown`** is used followed by the [new-user] followed by [file-name]. For example to change the owner to newuser of the file called example.txt type:
```
sudo chown newuser example.txt
```

To change the group of a file or directory run the command **`sudo chgrp`** followed by the [new-group] followed by the [file-name]. For example to change the group to group1 of the file called example.txt type:
```
sudo chgrp group1 example.txt
```

To change both the owner and the group the command **`sudo chown`** command is used followed by [new-user:new-group] followed by the [file-name]. For example to change the user and group to newuser and group1 at the same time for file example.txt type:
```
sudo chown newuser:group1 example.txt
```

To Change Ownership of a Directory and Its Contents the command **`sudo chown`** is used, followed by [-R] followed by [new-user:new-group] followed by the [directory-name]. For example to change the user and group to newuser and group1 at the same time for a directory called my_directory_copy (hasnt been created) type:
```
sudo chown -R newuser:group1 my_directory_copy  
```

## Standard Streams (standard input, output and error streams)
Redirection allows you to control where the output of a command goes or where the input comes from. Here's a some examples:

>: Redirect standard out to a file.
Example: echo "text" > file.txt writes "text" to file.txt.

<: Redirect a file to standard din.
Example: cat < file.txt reads input from file.txt instead of the keyboard.

>>: Append standard to a file. Add more text
Example: echo "more text" >> file.txt appends "more text" to file.txt.

2>: Redirect standard error to a file.
command 2> error.log redirects errors to error.txt

Example: 

Type **`ls nonexistent`**, The terminal should show ls: cannot access `nonexisitent`: No such file or directory. Then type the following;
```
ls nonexistent 2> error.txt
```
Then type:
```
cat error.txt
```
The error that came up is redirected to error.txt.

&>: Redirect both standard error and standard out to a file (bash shorthand).
Example: command &> combined.log writes both to combined.log.

```
ls nonexistent my_directory_copy &> /dev/null
```

This command attempts to list the contents of two directories, nonexistent and my_directory_copy, while redirecting both standard output (stdout) and standard error (stderr) to /dev/null.

## Introduction to Environment Variables

Environment variables play a crucial role in defining the environment in which a process is run. These are variables that are set in the environment and affect the behaviour of processes on your system

### Common Examples and setting variables

| Variable  | Description |
|-----------|------------|
| `$HOME`   | Current User’s home directory (e.g., `/home/user`) |
| `$USER`   | Current user's username |
| `$PATH`   | Directories where executables are searched for |
| `$SHELL`  | The shell program in use (e.g., `/bin/bash`) |
| `$PWD`    | Current working directory |

When setting environment variables theres 2 ways:

1. Temporarily (Session-Only)
Use export to set a variable for the current session For exmple:

export Name = VALUE

export JAVA_HOME = /usr /bin /java

2. Permanently

When setting them permanently .zshrc and .bashrc files are used

1. Bash
- configuartion file: .bashrc
- Location: Typically located in the user's home directory (-/). Its used for configuring the interactive Bash shell.
- Usage: Customizations such as setting aliases, environment variables, defining functions, and configuring the shell prompt are done in this file.

2. Zsh
- Configuration file: .zshrc
- Location: Also typically located in the users home directory (-/). Its the main configuration file for the zsh shell.
- Usage: Similar to .bashrc. Its used for customizing the zsh interactive shell, including defining aliases setting environment variables, and configuring the prompt.

If you want to add /home/ubuntu to $PATH:

```
export PATH=$PATH:/opt/my_program/bin
```
To make it permanent, add this line to ~/.zshrc

























