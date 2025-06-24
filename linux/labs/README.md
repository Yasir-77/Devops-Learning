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

Start by navigating tpo the root user by typing the command **`cd`** /. Then click **`ls`** you should see a /tmp, navigate to the directory by typing cd **`/tmp`**. Then create a temporary directory by typing the following:
```
mktemp -d
```

Then navigate back to the directory where the data.txrt file was stored so type **`cd ~`**. From here copy the file name and move it to the temporary directory that was created. Type the follwoing
```
cpo data.txt /tmp/tmp1234
```

Type: (This will reverse the hex dump back to binaray form)
```
xxd -r data.txt > data
```

Then type: ( This will show you what file type data is)
```
file data 
```

Then rename and decompress accordingly:

Example:
If it's gzip:

```
mv data data.gz
gunzip -d data.gz
```

If it's tar:

```
mv data data.tar
tar -xf data.tar
```

If it's bzip2:

```
mv data data.bz2
bunzip2 -d data.bz2
```
At one point a new file will come in data6.bin and data8.bin read the files using the file comman and change to the relevant file type accordingly and continue the process.

The password is: FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

## Level 13 to 14:

To find the private SSH key type **`ls`** and the SSH key is sshkey.private.

Then type the following into the terminal:
```
sshi -i sshkey.private bandit14@localhost -p 2220
```

The password is: MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

## Level 14 to 15:

On the same local host without exiting the environment type:

```
nc localhost 30000
```

Then enter the previous level password which is: MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

The password to level 14 is: 

8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

## Level 15 to 16:

Once entering the environment for Level 15.

You would need to use the command ncat --ssl . The ncat command with -ssl is used to create SSL/TLS-encrypted connections using Ncat. This is simply done by typing **`ncat --ssl <hostname> <port>`**

```
ncat --ssl localhost 300001
```

Then typed in the password to get into level 15 which is: 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

The password for level 15 is 

kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

## Level 16 to 17:

When in the bandit 16 server type:

```
nmap -p 31000-32000 localhost
```

This command scans ports 31000 to 32000 on your local machine to check which ones are open (i.e., have a server listening on them). **`nmap`** (short for network mapper) is a powerful tool used for: scanning networks, auditing security, finding open ports and detecting services and operating systems

Once you get a list of open ports type the following command:

```
ncat --ssl localhost <port numbers> 
```

Then type the password obtaines form the previous level kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx.

The result opbtained should be a key with multiple letters and numbers. copy the text

Then type **`vim key`** into your linux terminal. Paste the key obtained from the level and then type **`chmod +x key`**. To log into the next level type:

```
ssh -i key bandit17@bandit.labs.overthewire.org -p 2220
```





























