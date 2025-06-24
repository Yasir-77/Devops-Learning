# Linux labs

# The OverTheWireBandit game challenge

## Level 0

To complete this level type:
```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```
Then type the password:
```
bandit0
```

## Level 0 to 1

To complete this level type:
```
ls
```
Then:
```
cat readme
```

The password is ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

## Level 1 to 2

To complete this level type:
```
ls
```
Then:
```
cat ./-
```

The password is 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

## Level 2 to 3

To complete the level type:
```
ls
```
Then 
```
cat "spaces in this filename"
```

The password is MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

## Level 3 to 4

To complete this level type:
```
ls -a
```
Then:
```
cd inhere
```
Then:
```
cat ...Hiding-From-You
```

Thes poassword is 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

## Level 4 to 5

To complete this level type:
```
ls -a
```
Then:
```
cd inhere/
```
Then all the files listed will show up, to find the only human-readable file the **`file`** command is used. As we are searching for the type of file for all the files in the directory it is followed by **`./*`**. Type:
```
file ./*
```
Then:
```
cat ./-file09
```

The password is 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

## Level 5 to 6

To complete this level type:
```
ls 
```
Then:
```
cd inhere
```
To find a file based on the specific size of the file use the command **`find [path] -size [size]`**

Then:
```
find . -type f -size 1033c
```
Then:
```
cat ./maybehere07/.file2
```
The password is HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

## Level 6 to 7

To find the paaword type:

The following command will show all the files/directories that have bandit7 as a user, bandit6 as a group and a file size of 33 bytes.
```
find / -user bandit7 -group bandit6 -size 33c
```

Then a list of files will show, find the one that hasnt got permission denied written on it

Then:
```
cat /var/lib/dpkg/info/bandit7.password
```

The password is morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

## Level 7 to 8:

To complete this level type:
```
ls
```
Then:
```
cat data.txt
```
The amount of data in the text is extemely long to find the password type:
```
grep "millionth" data.txt
```
The password is dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

## Level 8 to 9:

To find the password type:
```
ls
```
Then:
```
cat data.txt
```
Then:

Use the **`sort`** command combined with uniq -c to count the occurrences of each line in the file:

sort filename.txt: Sorts the lines in the file, which is necessary because uniq -c only counts adjacent duplicate lines.

uniq -c: Prefixes each line with the number of occurrences.
```
sort data.txt | uniq -c
```

or 

```
sort data.txt | uniq -u
```

uniq -u will only print the unique lines that havent been duplicated.

The password is 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

## Level 9 to 10

To find the password type:
```
ls
```
Then:
```
cat data.txt
```
Then:

Use the **`string`** command followed by the **`grep`** command to narrow down the output to the lines that contain =.

The strings command is used to extract all readable text
```
string data.txt | grep "="
```
The password is FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

## Level 10 to 11:

To find the password type:
```
ls
```
Then:
```
cat data.txt
```
Then:

Use the **`base64`** command followed by the **`-d`**. The base64 command is used to encode or decode data in Base64 format. The -d is used to decode the data.
```
base64 -d data.txt
```

The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

## Level 11 to 12:

To find the password type:
```
ls
```
Then:
```
cat data.txt
```
Then use the **`tr`** command - The tr command in Linux is used to translate, squeeze, or delete characters from standard input short for translate.

To decode ROT13 encoded files you would use tr followed by: **`'A-Za-z' 'N-ZA-Mn-za-m'`**

- 'A-Za-z' — matches all uppercase and lowercase letters
- 'N-ZA-Mn-za-m' — maps each letter to its counterpart 13 letters ahead, wrapping around at the end of the alphabet

Type:
```
tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt
```

The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

## Level 12 to 13:


```
ls
```
Then:
```
cat data.txt
```
Then use the **`tr`** command - The tr command in Linux is used to translate, squeeze, or delete characters from standard input short for translate.

To decode ROT13 encoded files you would use tr followed by: **`'A-Za-z' 'N-ZA-Mn-za-m'`**

- 'A-Za-z' — matches all uppercase and lowercase letters
- 'N-ZA-Mn-za-m' — maps each letter to its counterpart 13 letters ahead, wrapping around at the end of the alphabet

Type:
```
tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt
```

The password is: FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn





























