Linux Fundamentals 💻🚀
===============================

Getting started with Linux with Exercises


a) Managing packages - Ubuntu
----
**1. Install the package "nano"**
```sh
# before installing a new package we should update the Database package
$ apt update  					
$ apt install nano
```

----
**2. Uninstall the package "nano"**
```sh
$ apt remove nano
```

b) Navigating the File System / Manipulating Files and Directories
----
**1. Go the home directory and create a directory named "folder1"**
```sh
$ cd ~
$ mkdir folder1
```

**2. Rename the directory "folder1" to "new-folder" and create a file "hello.txt" inside this directory**
```sh
$ mv folder1 new-folder
$ touch hello.txt
```


**3. Create 4 additional files using only one command: file1.txt file2.txt file3.txt**
```sh
$ touch file{1..4}.txt
```

**4. Remove 2 files: "file1.txt" and "file2.txt"**
```sh
$ rm file1.txt file2.txt
```

**5. Remove all files starting with "file"**
```sh
$ rm file*
```

**6. Remove the directory "new-folder"**
```sh
$ rm -r new-folder
```

**7. List all the files that contain either the letter "c" or "d"**
```sh
$ ls -l *[cd]
```

**8. List all the files whose name contain "ile"**
```sh
$ ls -l ?ile*
```

c) Editing and viewing files
----

**1. Go the home directory, create a new file named "file.txt", install nano and edit this file**
```sh
$ cd ~
$ apt update
$ apt install nano
$ nano file1.tx
```

**2. Print out the content of the file.txt**
```sh
$ cat file.txt 	                    # "cat" for files with short text
$ less /etc/adduser.conf 			# "less" for files with long text
$ head -n 5 /etc/adduser.conf 		# it shows the first 5 lines of this file
$ tail -n 5 /etc/adduser.conf       # it shows the last 5 lines of this file
```


d) Redirection
----

Standard input - represents the keyboard
Standard output - represents the screen

**1. Read the content from both "file1.txt" and "file2.txt" and print to the screen**
```sh
$ cat file1.txt file2.txt
```

**2. Redirection - take the content of "file1.txt" and put it into "file2.txt"**
```sh
$ cat file1.txt > file2.txt 
```

**3. Redirection: take the content of "file1.txt" and "file2.txt", and put it into "combined.txt"**
```sh
$ cat file1.txt file2.txt > combined.txt
```

**4. do "echo Hello World" and put this into the whatever.txt file**
```sh
$ echo Hello World > whatever.txt
```

**5. Add the following to the "whatever.tx" file: "I am Alain Afonso"**
```sh
$ echo "I am Alain Afonso" >> whatever.txt
```

**6. Get the long list of the files in the "etc" directory and write the output to a file called "files.txt"**
```sh
$ ls -l /ect > files.txt
```

**7. Using only one command, write a text "xxxxx", save it into a file and displays the result on the screen.**
```sh
$ echo "Learning linux is so much fun" | tee file.txt
```

**8. Append the following sentence to the file.txt file you created above: "Learning Linux is easy, it feels like learning English."**
```sh
$ echo "Learning Linux is easy, it feels like learning English." | tee -a file.txt
```


**9. # Split file.txt into 300 lines per file and output to childfileaa, childfileab and childfileac**
```sh
$  split –l 300 file.txt childfile
```

e) Searching for text
----

**1. Search for the word "hello" in the file.txt**
```sh
$ grep hello file.text 			# case sensitive
$ grep -i hello file.text 		# case insensitive
```

**2. Search for the word "root" in /etc/password**
```sh
$ grep -i root /etc/passwd
```

**3. Search for the word "hello" inside multiple files "file1.txt", "file2.txt"**
```sh
$ grep -i hello file1.txt file2.txt
$ grep -i hello file*
```


**4. Search for the word "hello" in the files inside the current directory and all its sub-directory**
```sh
$ grep -i -r hello .
$ grep -ir hello .
```

f) Filters / Text Processors Commands
----
Create a file named "my-group" with the following content below:
```
Jerry Seinfeld
Cosmo Kramer
Eliane Benes
George Costanza
Newman mailman
Frank Costanza
Morty Seinfeld
Babes Kramer
Alton Benes
J Peterman
George Steinbrenner
Uncel Leo
David Puddy
Justin Pitt
Kenny Bania
```

**1. Get the first character / letter of everyline of the file**
```sh
$ cut -c1 my-group
```
**2. Get the first, second and fourth character / letter of every line of the file**
```sh
$ cut -c1,2,4 my-group
```
**3. List range of characters - get from the first character all the way until the fourth character / letter of every line of the file**
```sh
$ cut -c1-4 my-group
```
**4. List a specific range of character - get from the first until the third character and from fourth until the seventh character of every line of the file**
```sh
$ cut -c1-3,4-7 my-group
```
**5. Get the list of character by the byte size - display a character of 3 bytes of every line of the file**
```sh
$ cut -b1-3 my-group
```
**6. Display a list of a column of this file by specifying the delimeter - List the first 6th column separated by :**
e.g. alain:x:1000:1000:Alain Afonso:/home/iafzal:/bin/bash

```sh
$ cut -d: -f 6 new-file -> the output should be "/home/iafzal"
```

**7. Display a list of a column of this file by specifying the delimeter - List the first 6th and 7th column separated by :**
e.g. alain:x:1000:1000:Alain Afonso:/home/iafzal:/bin/bash

```sh
$ cut -d: -f 6-7 new-file -> the output should be "/home/iafzal:/bin/bash"
```

**8. From your home directory get a list of everything in there and display the second all the way to the fourth character.**
```sh
$ ls -l | cut -c2-4
```

**9. Display the first column of the file**
```sh
$ awk '{print $1}' my-group
```
**10. List 1 and 3rd field of "ls –l" command output**
```sh
$ ls –l | awk '{print $1,$3}'
```

**11. List the last column of "ls -l" comand output**
```sh
$ ls –l | awk '{print $NF}'
```

**12. Print the column that that contains the word "Jerry"**
```sh
$ awk '/Jerry/ {print}' my-group
```

**13. Ouput only 1st field of /etc/passwd**
```sh
$ awk -F: '{print $1}' /etc/passwd
```

**14. Do this command << echo "Hello Alain" >> and output replace the word "Alain" with "Adam"**
```sh
$ echo "Adam" | awk '{$2="Adam"; print $0}'
```

**15. Change every surnames of the list with "Smith"**
```sh
$ cat my-group | awk '{$2="Imran"; print $0}'
```

**16. Get lines that have more than 15 byte size**
```sh
$ awk 'length($0) > 15' my-group 
```

**17. Get the column matching "Music" in /home/username**
```sh
$ ls -l | awk '{if($9 == "seinfeld") print $0;}'  # $9 -> last column
```

**18. Find the total number of columns of the file**
```sh
$ ls -l | awk '{print NF}'
```

**19. Search for the word "Seinfeld" in my-group file.**
```sh
$ grep Seinfeld my-group
```

**20. Search for "Seinfeld" and count how many times it shows up in the file.**
```sh
$ grep -c Seinfeld my-group
```

**21. Search for "Seinfeld" and ignore case-sensitive.**
```sh
$ grep -i seinfeld my-group
```

**22. Search for "Seinfeld", display the matched lines and their line numbers.**
```sh
$ grep -n Seinfeld my-group
```

**23. Display every lines that don't contain the word "Seinfeld".**
```sh
$ grep -vi seinfeld my-group
```

**24. Search for all the lines that don't contain the word "Seinfeld" and print only the first column.**
```sh
$ grep -i seinfeld my-group | awk '{print $1}'
```

**25. Search for all the lines that don't contain the word "Seinfeld" and print only the first column with a range (get from the first until the third character).**
```sh
$ grep -i seinfeld my-group | awk '{print $1}' | cut -c1-3
```

**26. From your home directory print only the line that matches the file or directory "desktop".**
```sh
$ ls -l | grep Desktop
```

**27. Search for 2 keywords "" "" on the my-group file.**
$ egrep -i "Seinfeld|Costanza" my-group

**28. Sort the file in alphabetical order**
```sh
$ sort my-group
```

**29. Sort in reverse alphabetical order**
```sh
$ sort -r my-group
```

**30. Sort by the second column**
```sh
$ sort -k2 my-group
```

**31. Removes duplicates line from the files**
```sh
$ sort my-group | uniq
```

**32.Sort the list, filters it, and counts how many times a duplicate showed up**
```sh
$ sort file | uniq –c
```

**33. Only show repeated lines.**
```sh
$ sort file | uniq –d
```

**34. Check file line count, word count and byte count**
```sh
$ wc file
```

**35. Get the number of lines in a file**
```sh
$ wc –l file
```

**36. Get the number of words in a file**
```sh
$ wc –w file
```

**37. Get the number of bytes in a file**
```sh
$ wc –c file
```

**38. Get the number of files in a particular directory**
```sh
$ ls –l | wc -l
```

g) Finding Files and Directories
----

**1. Find all the files and directories in the current directory**
```sh
$ find
```

**2. Find all the files and directories starting from "etc"**
```sh
$ find /etc
```

**3. Using "find" command, find only the directories in the current directory**
```sh
$ find -type d
```

**4.  Using "find" command, find only the files in the current directory**
```sh
$ find -type f
```

**5. Using "find" command, find all the files whose names start with "f" in the current directory**
```sh
$ find -type f -name "f*"			# case sensitive
$ find -type f -iname "f*"			# case insensitive
```

**6. Find all the python files and write the result to a file called pythonfile.txt**
```sh
$ find / -type f -name "*.py" > python-files.txt
$ cat python-files.txt
```


h) Chaining commands
----

**1. Create a directory "test", enter this directory and echo "done"**
```sh
$ mkdir test ; cd test ; echo done
```

**2. Uses the AND / OR operator and the task above**
```sh
$ mkdir test && cd test && echo done
$ mkdir test || cd test || echo done
```

**3. Create a pipe (what comes out of the 1st command, goes inside the second and so on) - Get the list of every files inside the bin directory and print it**
```sh
$ ls /bin | less
```

**4. Break up a long command into multiple lines by using the backslash**
```sh
$ mkdir test;\ 
> cd test;\
> echo done
```

i) Environment Variables
----
**1. Viewing environment varibales**
```sh
$ printenv
$ printenv PATH
$ echo $PATH
```

**2. Setting and viewing Environment varibales**
```sh
$ export DB_USER=mosh 					# this variable is only available in the current terminal session!!!!
$ printenv DB_USER | echo $DB_USER
```

**3. Permanent environment variables must be written inside file ".bashrc" located in the ~**
```sh
$ echo DB_USER=mosh >> .bashrc   # appending the DB_USER inside .bashrc file
```

**4. Reload the .bashrc file - must be reloaded from ~ directory**
```sh
$ source .bashrc
$ source ~/.bashrc  
```

j) Managing Users
----

**1. create the home directory for user "john"**
```sh
$ useradd -m john
```

**2. find where this user is stored**
```sh
$ cat /etc/passwd  					# in the configure file at "etc" directory
```

**3. Use "usermod" to modify the records of the user you just created - modify the /bin/sh to /bin/bash**
```sh
$ usermod -s /bin/bash john
```

**4. Locate the password for this user**
```sh
$ cat /etc/shadow 					# file only accessible for the root user
```

**5. Open another terminal and login as John**
```sh
$ docker exec -it -u john 52eb2ec0b5de bash
```

k) Managing groups
----
**1. Create a new group called "developers" and locate it**
```sh
$ groupadd developers
$ cat /etc/group
```

**2. Add "John" to this group and displays john's password**
```sh
$ usermod -G developers john
$ cat /etc/passwd | grep john  OR  grep john /etc/passwd
```

**3. Display the groups John is part of**
```sh
$ groups john
```

**4. Add John to a new group called "artists"**
```sh
$ groupadd artists
$ usermod -G artists john
$ groups john
```

l) File Permissions
----

**1. create a shell script called "deploy" with a message "echo hello"**
```sh
$ echo echo hello > deploy.sh
```

**2. grant "execute permission" to "deploy.sh" file and execute it**
```sh
$ chmod u+x deploy.sh
$ ./deploy.sh
```



****
```sh
```

----


Reference
----
[link 1 ](https://www.kaggle.com/)
[Wildcards](https://tldp.org/LDP/GNU-Linux-Tools-Summary/html/x11655.htm)