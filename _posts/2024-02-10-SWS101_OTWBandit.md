---
Title: SWS101 OTW Bandit 
categories: (SWS101, OTW Bandit)
tags: (SWS101, Bandit)
---

### Topic: OTW Bandit 
----

# Bandit level0
>"ssh bandit0@bandit.labs.overthewire.org -p 2220"

use the above command to enter the bandit server and use the password(bandit0) to login.

# Bandit level0 - level1
>"ls"

use this command to list the files in the home directory
>"cat readme"

use this command to read the the contents in the file which contains the bandit level 1 password.

"NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL"(level1 password)

# Bandit level1 - level2 
In this case when we run the "ls" command the folder contains a file with "-" which can be onyl viewed by using "./"
>"cat ./-"

"rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi"(level2 password)

# Bandit level2 - level3
The available file is “spaces in this filename”. This file cannot be viewed normally so use “ \ ” instead of spaces .
>"ls"

>"cat spaces\ in\ this\ filename"

"aBZ0W5EmUfAf7kHtQe0wd8bauFJlAiG" (level3 password)

# Bandit level3 - level4
First, we go to the correct folder and then print all its files to find the filename.
> "cd inhere/"

> "ls -la"

>"cat .hidden"

"2EW7BBsr6aMMoJ2HjW06Tdm8EgX26xNe"(level4 password)

# Bandit level4 - level5
The password for the next level is stored in the only human-readable file in the inhere directory.
We again go into the ‘inhere’ directory and print out the files in the system
> "cd inhere"

> "ls -la"

>"file ./*"

Use the “ file ./* ” to find the data type.
file07 contains ASCII text so use the “cat ./-file07” command to view the password.

"lrIwMI6bB37kxfiCQZqUdOIYfr6eEeqR" (level5 password)

# Bandit level5 - level6
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
human-readable
1033 bytes in size
not executable
>"cd inhere/"

>"find ./ -type f -size 1033c ! -executable 2</dev/null"

>"cd maybehere07"

>"ls"

>"cat .file2"

"P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU"(level6 password)

# Bandit level6 -> level7
We use the find command with the following options:

-type f, because we are looking for a file

-user bandit7, to find files owned by the ‘bandit7’ user

-group bandit6, to find files owned by the ‘bandit6’ group

-size 33c, to find files of size 33 bytes.

>"find ./ -type f -size 33c -user bandit7 -groupbandit6 2</dev/null"

>"cat /var/lib/dpkg/info/bandit7.password"

"z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S" (level7 password)

#  Bandit Level 7 -> Level 8
Checking the file size of data.txt, we can see it is huge:
>"du -b data.txt"

=4184396 data.txt

We can try using grep, since the password is in the same line as the word ‘millionth’
>"sort data.txt | grep millionth"

-The command “ sort data.txt | grep millionth ” is used to filter the information.
"TESKZCOXvTetKOS9xNwm25STk5iWrBvP"(level8 password)

#  Bandit Level 8 -> Level 9
To find the line that occurs only once in the file, we first sort the lines and then filter for the unique one.

>“sort data.txt | uniq -u” 

The command “ sort data.txt | uniq -u ” to filter the only line of text that occurs only once.

"EN632PlfYiZbn3PhVK3XOGSlNInNE00t"(level9 password)

#  Bandit Level9 -> Level10
First, we need to distinguish human-readable strings in ‘data.txt’. We use the strings command.

>"strings data.txt | grep ="

"G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s" (level10 password)

#  Bandit Level10 -> Level11
The base64 command allows files as input, so we just need to use the command on the file.

>"ls"

>"strings data.txt | base64 -d"

"6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM" (level11 password)

#  Bandit Level11 -> Level12
The substitution for ROT13 is A->N,…,Z->M. With tr it would be:

>"cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m' "

"JVNBBFSmZwKKOPOXbFXOoW8chDz5yVRv" (level12 password)

#  Bandit Level12 -> Level13
This task can be divided into three sub-tasks. Setting up a directory, reverting the hexdump and finally decompressing.

### Create Directory and Move file
The first part of the task is to create a folder and copy the data

>"mkdir /tmp/file1"

>"cp data.txt /tmp/file1"

>"cd /tmp/file1"

>"ls"

>"mv data.txt hexdump_data"

### Revert hexdump of the file
Looking at the file, we see the format of the data. As stated it is a hexdump. It looks like this:

>"cat hexdump_data | head"

we revert the hexdump and get the actual data.

>"xxd -r hexdump_data compressed_data"

>"ls"

### Repeatedly decompress

>"bunzip2 -c data2>data3"

>"gunzip -c data3>data4"

> "file data4"

> "tar -xf data4"

> "file data5.bin"

>"tar -xf data5.bin"

>"tar -xf data6.bin"

>"file data6.bin"

>"bunzip2 -c data6.bin>file7"

>"file file7"

>"file data8.bin"

>"tar -xf data7"

>"file data8.bin"

>"gunfile -c data8.bin>data9.bin"

>"file data9.bin"

As data9 shows ASCII text we can view the contents in that file.
>"cat data9.bin"

"wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw" (level13 password)

# Bandit Level13 -> Level14
Use ssh command with the ‘-i’ switch and specify the private key as a parameter.

>"head sshkey.private"

>"ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220"

# Bandit Level14 -> Level15
From the clue we know that the password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

>"cat /etc/bandit_pass/bandit14 | nc localhost 30000"

"jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt" (level15 password)

# Bandit Level15 -> Level16
Since the task states that the password can be retrieved using SSL encryption, we can connect to the localhost server with the OpenSSL client and send the password from this level. The server then sends back the password for the next level.

>"openssl s_client -connect localhost:30001"

>"read R Block"

>"jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt"

"JQttfApK4SeyHwDlI9SXGR5@qcl0Ail1" (level16 password)

# Bandit Level16 -> Level17
First, we need to find open ports between 31000 to 32000 on localhost and check what services are running on them using nmap.

>nmap -sV localhost -p 31000-32000

So, nmap tells us that five ports are open. Only two ports (31518 and 31790) use SSL. Nmap also tells us that port 31518 runs only the echo service.

>openssl s_client -connect localhost:31790

The result is a private SSH key. So, we create a file to put the key into

-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

# Bandit Level17 -> Level18
>"ssh -i sshkey17.private bandit17@bandit.labs.overthewire.org -p 2220"

First we need to used this private SSH key from the previous level to login to the next level.

>"diff passwords.old passwords.new"

42c42

< p6ggwdNHncnmCNxuAtOKtKVq185ZU7AW
hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg>

# Bandit Level18 -> Level19
Instead of logging into the machine with SSH, we execute a command through SSH instead. First, we use ls to make sure the readme file is in the folder then we can use cat to read it.

>ssh bandit18@bandit.labs.overthewire.org -p 2220 ls

= bandit18@bandit.labs.overthewire.org's password: 

readme

>ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme

= bandit18@bandit.labs.overthewire.org's password: 

kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd (level19 password)

# Bandit Level18 -> Level19
First, we check who the owner of the setuid binary is:

>ls -la

>./bandit20-do 

>./bandit20-do id

>ls /etc/bandit_pass/bandit*

>ls /etc/bandit_pass/bandit20

>cat /etc/bandit_pass/bandit20

>./bandit20-do cat /etc/bandit_pass/bandit20

"GbKksEFF4yrVs6il55v6gwY5aVje5f0j" (level20 password)


















