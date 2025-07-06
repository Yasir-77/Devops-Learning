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

press i to enter insert mode and type:
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
This script should print "You are an adult".

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

### else and elif

The else clause provides an alternative code block to be executed when the if condition evaluates to false. It provides an alternative path in your scripts flow offering flexibility and versatility.

The structure of an else clause:
```
#!/bin/bash

if condition
then
	# code block if condition is true
else
  	# code block if condition is false
fi
```

Some examples:

e.g.1
```
#!/bin/bash

age=15

if [ $age -gt 18 ]
then
	echo "You are an adult!"
else
  	echo "You are not an adult!"
fi
```
The script will print "You are not an adult!"

e.g.2
```
#!/bin/bash

score=85

if [ $score -ge 90 ]
then
	echo "Excellent!"
elif [ $score -ge 80 ]
then
  	echo "Good!"
else
  	echo "Better luck nect time"
fi
```

The elif clause allows us to add another condition if nthe first condition is false. The else clause only executes when the condition for the if statements arent met

With the score being 85 the script will print "Good!".

### Nested if statements

Nested if statements allow you to check multiple conditions in a more complex manner. When you nest if statements, an inner if block is executed only if the outer if condition is true. This is useful when decisions depend on more than one condition.

For Example:
```
#!/bin/bash

age=18
grade=85

if [ "$age" -gt 18 ]; then
    echo "You are eligible based on age."
  if [ "$grade -ge 80" ]; then
    echo "You are eligible based on grade."
    echo "Congrats! You are eligible for scholarship"
  else
    echo "sorry your grade is not high enough"
  fi 
else
   echo "sorry, you are not eligible"
  fi
```

In this case the response will say "sorry you are not eligible" this is due to the age, however if the age=19, the script will read "You are eligible based on age. You are eligible based on grade. Congrats! you are eligible for scholarship".

### While loops

While loops allow you to repeatedly execute a block of code as long as a specified condition is true. These loops are useful when you don't know in advance how many iterations you'll need, and the loop continues until a condition is no longer met.

The general structure of a while loop is:
```
#!/bin/bash

while condition
do
	# code to be executed
done
```

Some examples:

e.g.1
```
#!/bin/bash

count=1

while [ $count -le 5 ]
do
	echo "count: $count"
        ((count++))  
done
```
When this is run the count will continue until it reaches 5, once it does the loop ends. ((count++)) adds 1 for each iteration of this while loop.  The script will show:
```
count: 1
count: 2
count: 3
count: 4
count: 5 
```

e.g.2 
```
#!/bin/bash

fruits=("apple" "banana" "orange") 
index=0 

while [ $index -lt ${#fruits[@]} ]
do
	echo "Fruit: ${fruits[$index]}" 
        ((index++))  
done
```

When running the script the output would be:
```
Fruit: apple
Fruit: banana
Fruit: orange
```

Explaining the code:


fruits=("apple" "banana" "orange") - This line declares an array called fruits with three elements: "apple", "banana", and "orange".

index=0  - A variable called index is initialized with a value of 0. This will be used to keep track of the current position (or index) as we loop through the array.

while [ $ index -lt ${#fruits[@]} ] - This is a while loop that continues as long as the condition is true.
Condition: [ $ index -lt ${#fruits[@]} ] checks if the value of index is less than the number of elements in the array

echo "Fruit: ${fruits[$index]}" -  This line prints the current fruit in the array.
${fruits[$index]} accesses the element in the array at the position specified by index. For example, if index is 0, it accesses fruits[0], which is "apple".
        
((index++))  #This is a shorthand for incrementing the value of index by 1.

### for loops

The for loop is a versatile construct used to iterate over a series of items or to execute a block of code a specific number of times. 

The structure for a for loop is:
```
#!/bin/bash

for variable in sequence
do
    ~code block to be executed
done
```
Some examples:

e.g.1
```
#!/bin/bash

for (( i=1; i<=5; i++))
do
    echo "Number: $i"
done
```
The script will print:
```
Number: 1
Number: 2
Number: 3
Number: 4
Number: 5
```
Break down of script:

for (( i=1; i<=5; i++ )): This is a for loop. i=1 initializes the variable i to 1. i<=5 specifies the loop should continue as long as i is less than or equal to 5. i++ increments the value of i by 1 after each iteration.

do:
Begins the block of code that will be executed in each iteration of the loop.

echo "Number: $i":
Prints the current value of i with the prefix "Number: ". $i represents the current value of the loop variable.

e.g.2
```
#!/bin/bash

fruits=("apple" "banana" "orange")

for fruit in "${fruits[@]}"
do
    echo "Fruits: $fruit"
done
```
The script will print:
```
Fruit: apple
Fruit: banana
Fruit: orange
```
Breakdown of script:

fruits=("apple" "banana" "orange"): This line declares an array named fruits containing three elements: "apple", "banana", and "orange".

for fruit in "$ {fruits[@]}": This for loop iterates over each element in the fruits array. $ {fruits[@]} expands to all elements of the fruits array. Fruit is a loop variable that takes each value of the array in turn.

echo "Fruit: $fruit": This command prints the current value of the fruit variable, prefixed by "Fruit: ".

e.g.3 
```
#!/bin/bash

for number in $(seq 1 5)
do 
    echo "Number: $number"
done
```
The script will print:
```
Number: 1
Number: 2
Number: 3
Number: 4
Number: 5
```
Break down of script:

for number in $(seq 1 5):

$ (seq 1 5) generates a sequence of numbers from 1 to 5. seq is a command that outputs a sequence of numbers, and $(...) captures this output as a list.
The for loop iterates over each number generated by seq, assigning each number to the variable number in turn.

do: Marks the beginning of the loop body.

echo "Number: $number": This command prints the current value of the number variable, prefixed by "Number: ".  

### Break and Continue

In Bash scripting, break and continue are control flow statements used to alter the flow of execution within loops. The break statement is used to exit from a loop prematurely. It terminates the loop and transfers control to the statement immediately following the loop. The continue statement skips the remaining code in the current iteration of the loop and proceeds to the next iteration. It does not exit the loop but rather jumps to the next iteration.

For example 

e.g. 1a
```
#!/bin/bash

for (( i=1; i<=5; i++))
do

    if [ $i -eq 3 ]
    then
        break 
    fi
    echo "Number: $i"

done
```
The output will show:
```
Number: 1
Number: 2
```
The loop will execute and print values of i from 1 to 2. When i reaches 3, the break statement will be triggered, and the loop will terminate before printing 3 or any subsequent numbers.

e.g. 1b
```
#!/bin/bash

for (( i=1; i<=5; i++))
do

    if [ $i -eq 3 ]
    then
        continue 
    fi
    echo "Number: $i"

done
```
The output will show:
```
Number: 1
Number: 2
Number: 4
Number: 5
```
The script iterates from 1 to 5. When i is 3, the continue statement causes the loop to skip the echo command for that iteration. The result is that "Number: 3" is not printed, but all other numbers in the range are printed.

The break and continue statements also work for while loops, the behaviour is the same:

e.g.2

```
#!/bin/bash

while true
do

    echo "count: $count"
    ((count++))
    if [ $count -eq 4 ]
    then
        break
    fi

done
```
The output will show:
```
count: 1
count: 2
count: 3
```
The while true loop runs infinitely until the break condition is triggered. The count variable is incremented on each iteration and is printed, the loop stops when count equals 4 due to the break statement.

e.g.3 

```
#!/bin/bash

count=1

while [ $count -le 5 ]
do

    if [ $count -eq 3 ]
    then	
    	((count++))
    	continue
    fi
    echo "count: $count"
    ((count++))	

done
```
The output of the script:
```
count: 1
count: 2
count: 4
count: 5
```
The script prints the numbers 1, 2, 4, and 5, but skips printing 3 because of the if and continue logic.

Breakdown of script

while [ $count -le 5 ] - This starts a while loop, It will keep running as long as count is less than or equal to 5.

if [ $count -eq 3 ] - Checks if the current value of count is equal to 3, The -eq operator means "equal" in Bash integer comparisons.

((count++)) - Increments the count variable by 1 using arithmetic syntax. This ensures the loop moves forward even if the continue is used.

continue -  Skips the rest of the loop body for the current iteration and goes back to the while condition. So, if count is 3, the script skips the echo and jumps to the next loop.

echo "count: $count" - Prints the current value of count, prefixed by "count: ". This line is skipped when count == 3 due to the continue.

((count++)) Increments the count variable again to ensure the loop progresses. This happens for all values except when count == 3 (because in that case, the continue skips it).

### Basics of functions

A function in Bash is a block of reusable code that can be defined once and called multiple times in a script. Functions make scripts easier to manage and reduce code duplication.

The structure of a function in bash:
The structure for a for loop is:
```
#!/bin/bash

function_name() {

    #code block to be executed
}
```
Some examples:

e.g.1
```
#!/bin/bash

hello_world() {
      echo "Hello world!"
}

hello_world
```
The function hello_world is defined and called to display "Hello world!".

e.g.2
```
#!/bin/bash

hello_world() {
      echo "Hello world!"
}

greet_person() {
      local name="$1"
      echo "Hello, $name!"
}

greet_person "Ahmed"
greet_person "Sam"
```
The output of the script:
```
Hello, Ahmed!
Hello, Sam!

```
Breakdown of the script:

hello_world(): This function is defined to print "Hello world!", although it’s not called in this version of the script.

greet_person(): This function takes one argument, which is the name of a person, and assigns it to the local variable name using the $1 positional parameter.

local name="$1": Declares name as a local variable, scoped only to this function, and assigns it the value of the first argument passed to the function.

echo "Hello, $name!": Prints a greeting message, replacing $name with the actual value passed.

Function Calls:

greet_person "Ahmed": Calls the greet_person function with "Ahmed" as the argument. The function prints "Hello, Ahmed!".

greet_person "Sam": Calls the greet_person function with "Sam" as the argument. The function prints "Hello, Sam!".

### Function parameters

Function parameters provide a way to pass data to functions enabling them to perform specific tasks based on provided input. There are 2 types:

- Positional parameters - Allows to pass data to functions and access them using numbered variables e.g. $1, $2/ 

```
#!/bin/bash

print_args(){
	echo "Number of arguments: $#"
	echo "Script name: $0"
	echo "First argument: $1"
	echo "Second argument: $2"
	echo "All arguments: $@"
}

print_args "Alice" "Bob" "Ahmed"
```

The output for this script will show:
```
Number of arguments: 3
Script name: ./parameters.sh
First argument: Alice
Second argument: Bob
All arguments: Alice Bob Ahmed
```
Breakdown:

print_args() Function: The function accepts an arbitrary number of arguments. These arguments are accessed using positional parameters ($1, $2, etc.).
Inside the Function:

$#: The number of arguments passed to the function.

$0: The name of the script (in this case, the name of the script that is being executed).

$1: The first argument passed to the function (Alice).

$2: The second argument passed to the function (Bob).

$@: All the arguments passed to the function as separate words (Alice Bob Ahmed).
Function Call:

The print_args function is called with three arguments: "Alice", "Bob", and "Ahmed".

### User inputs:

User input allows the script to interact with the users and make them more dynamic and responsive. By accepting user input within functions interactive scripts can be created. 

e.g.1

```
#!/bin/bash

greet_user(){
	echo "What is your name?"
	read name
	echo "Hello, $name!"
}

greet_useer
```
the output of this script will be:

When you run this script, it will prompt you to enter your name, and then it will greet you:
```
What is your name?
Ahmed
Hello, Ahmed!
```
Breakdown:

greet_user(): The function prompts the user for their name, reads the input, and then prints a personalized greeting using the input.

read name: The read command stores the user's input in the variable name.

echo "Hello, $name!": Prints a greeting using the value stored in the name variable.

Function Call: The function is called correctly as greet_user, which matches the function's definition.

e.g.2

```
#!/bin/bash

greet(){
	local name

	if [ $# -eq 0 ]; then
	echo "what is your name?"
	read name
else
	name="$1"
fi

echo "Hello, $name!"
}

greet
```
The out putput of the script will be the same as above. The difference is:

$# - Checks the number of arguments passed to the function. If no arguments are passed, it prompts the user for their name. If an argument is passed, it uses the argument as the name. This flexibility allows the function to work both interactively (with read) and with pre-supplied arguments.

### Handling bad data

Bad data refers to invalid or unexpected user inputs that may casue errors or undesired behaviour in our scripts. Implementing eror handling techniques can ensure the functions handle bad data with no issues.

Examples
```
validate_age() {
    local age=$1

    if [[ ! $age =~ ^[0-9]+$ ]]; then
        echo "Invalid age. Please provide a numeric value."
        return 1
    fi

    if (( age < 18 )); then
        echo "Sorry, you must be at least 18 years old."
        return 1
    fi

    echo "Congratulations! You are eligible."
    return 0
}
echo "please enter your age:"
read user_age

validate_age "$user_age"
exit_code=$?

if (( exit_code !=0 )); then
	echo "Input validation failed"
fi
```
Breakdown:

Numeric Check: [[ ! $age =~ ^[0-9]+$ ]] uses a regular expression to ensure that the input is numeric.

Age Check: (( age < 18 )) checks if the age is below 18.

return 1: If the input is not numeric or the age is less than 18, it returns 1, signaling a failure.

return 0: If the age is valid and at least 18, the function returns 0, signaling success.

exit_code=$?:

$? holds the exit status of the last executed command (in this case, the validate_age function). This is stored in exit_code.
if (( exit_code != 0 )):

If the exit code is not 0 (i.e., validation failed), it prints "Input validation failed".









































