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





























