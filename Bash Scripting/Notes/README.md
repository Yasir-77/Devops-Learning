## Introduction to BASH Scripting

### What is Bash Scripting?

- Bash: A command-line tool to interact with your computer.
- Bash Script: A file containing a series of commands you want the computer to execute automatically.

### Why do we learn Bash Scripting?

- Automate tasks: Save time on repetitive actions.
- Manage systems: Handle files, software installs, and system configurations.
- Boost efficiency: Get more done with less typing.

### How to get started Bash scrpting

- Shebang line: The first line of the script should be **`#!/bin/bash
- This tells your computer to use Bash to run the script.

### How to write first simple script:

First create a simple script using the **`touch`** command For example:
```
touch first_script.sh
```
open the file using vim type:
```
vim first_script.sh
```
The first line of every file starts with a Shebang line type:

press i to inter insert mode and type:
```
#!/bin/bash

echo "Hello World!"
```
To exit the vim type: :wq!

Then add executable to the script by running the chmod command:
```
chmod +x first_script.sh
```
To run the script type:
```
./first_script.sh
```
The Shebang line always starts with a # followed by an !, it specifies the interpreter/shell that handles the script, it enables consistent executional scripts across different environment regardless of whatever shell is used and you can specifiy different interpreters for different types of scripts. It is always the first line of the script.

### How to write comments in a file?

- To write single line comments that you dont want appearing in a file for others simply use the **`#`** at the beginning of the line.

- If you want to write multiple lines of comment write **`: '`** before the first line of the comment and then **`'`** under the last line. For example:
```
line 1: :  '

Line 2 to 10 : Comments ........

Line 11: '
```
Comments can also be used when debugging or when not wanting to run a line of code.

Adding comments to your script improves readability, better collaboration with team and help ensures scripts purpose remains evidents

### How to run scripts from anywhere

The file my-first-script.sh can only be run in its current directory. To run the file from anywhere without specifying the Path do the following:

First Place the file in one of the directiories thats in the PATH enviornment variable to do this type:
```
echo $PATH
```
This will give you a list of PATHS. The PATH is an envirmonet variable that tell the shell which directories to search, to search for executable files in response to commands.

A list of several directories seperated by colons will show, any executable file placed in one will run from anywhere. To place the my-first-file.sh folder in the directory use the **`sudo mv`** command followed by the file name followed by the selected PATH in this case /usr/local/bin followed by what you want to name the file in this case greet. For example:

```
sudo mv first_script.sh /usr/local/bin/greet
```

Then add executables on the script again using chmod command:
```
sudo chmod +x /usr/local/bin/greet
```
Now you can type greet anywhere and "Hello World" will appear.

### Variables

In Bash, you can define variables without any special symbols or keywords. Just assign a value to a name, but do not use spaces around the = sign. For example to assign the variable name to Yasir type:
```
name="Yasir"
```
To use the value of a variable, you need to prefix the variable with a **`$`**
```
echo "Hello,$name"
```
The output would be Hello Yasir

### Parameters

Parameters are values you pass to a script when you execute it. These parameters allow you to make your script dynamic, flexible, and capable of handling various inputs.

When you pass arguments to a Bash script, they are stored in special variables called positional parameters. These variables are $1, $2, $3, etc., representing the first, second, and third arguments passed to the script.
First cretea a file in this case a file called script.sh was created. Then set the parameters in the text. 
```
#!/bin/bash

echo "First parameter: $1"
echo "Second parameter: $2"
echo "Third parameter: $3"
```
When you run the script like this
```
./script.sh hello hi
```
It will output:
```
parameter 1: hello
parameter 2: hi
parameter 3:
```
If we were to add a third parameter on the line ./script.sh  hello hi (3rd parameter), it will poutput the 3rd parmeter.

To access all parameters passed into a script use the following tect in the file:
```
#!/bin/bash

echo "First parameter: $1"
echo "Second parameter: $2"
echo "Third parameter: $3"

echo "All Parameters: $@"
```
It will output:
```
parameter 1: hello
parameter 2: hi
parameter 3:
All Parameters: hello hi 
```
### Arithmetic expansion

Arithmetic expansion in Bash allows you to perform arithmetic operations directly within your scripts. You can use arithmetic expressions inside $(( ... )), which allows basic and complex mathematical operations.

some examples:

e.g. 1
```
#!/bin/bash
num1=5
num2=10
result=$((num1 + num2))  
echo "Sum of $num1 + $num2 is: $result"
```

When you run your script it will output:
```
sum of 5 and 10 is: 15
```

e.g. 2
```
#!/bin/bash
length=5
width=10
area=$((length * width))
perimeter=$((2 * (length + width))

echo "Rectangle area: $area"
echo "Rectangle perimeter: $perimeter"
```
When you run your script it will output:
```
Rectangle area: 40
Rectangle permiter: 25

### if statements

In Bash scripting, if statements are used to execute a block of code based on a condition. The basic structure of an if statement can be extended to handle multiple conditions and complex logic.

The general stucture is:
```
#!/bin/bash

if condition
then
	# code block to be executed
fi
```
conditions in if statements are formed using comparison operators for example:
- eq = equals
- ne = npot equals to
- lt = less than or equal to
- ge = greater than or equal to

These can be used to create more complex conditions.

Some examples:

e.g.1

```
#!/bin/bash

age=25

if [ $age -gt 18 ]
then
	echo "You are an adult!"
fi

```
This script should printt "You are an adult".

If statments become more powerful when combined with logical operators for example:
- && = AND
- || = OR

e.g.2

```
#!/bin/bash

grade=85

if [ $grade -ge 90 ] && [ $grade -le 100] 
then
	echo "Excellent"
fi

```
The script will print nothing as 85 doesnt fall in this range, however if **`grade=95`** then the script would print "Excellent".

e.g.3 

To compare strings operators that are used are:

- == which is equals to
- != which is not equals to

```
#!/bin/bash

name="Alice"

if [ $name == "Alice"] 
then
	echo "Hello, Alice"
fi

```
The script in this case will print "Hello, Alice". If any other name is the variable nothing will appear.
