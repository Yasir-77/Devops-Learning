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

## Commands

### What are commands?

Commands are textual instructions that tell the operating system what to do, they are usually typed into the terminal and are case sensitive. Commands have various options and arguments that can modify their behaviour and have instructions via a manual.

### Examples of basic Linux commands:

To print the present working directory. Run **`pwd`** command.
  
To see the contents of the directory. Run **`ls`** command.

To change the current directory. Run **`Cd`** command.  

To make (or) create a directory. Run **`mkdir`** command.

To remove (or) delete a directory. Run **`rmdir`** command.

To make (or) create a file. Run **`touch`** command.

To remove (or) delete a file. Run **`rm`** command.  

