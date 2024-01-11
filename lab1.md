*Using the `cd` command with no arguments*:
```
[user@sahara ~]$ cd
[user@sahara ~]$
```
The working directory for this command was `/home`. This output was given because no directory was passed as an argument, meaning the current directory stayed the same. This is not an error.


*Using the `cd` command with a directory as an argument:*
```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$
```
The working directory for this command was `/home`. This output was given because `lecture1` was specified as the new directory. When the command is run, the new working directory becomes `/home/lecture1`. This is not an error.


*Using the `cd` command with a file as an argument:*
```
[user@sahara ~/lecture1]$ cd Hello.java
bas: cd: Hello.java: Not a directory
[user@sahara ~/lecture1]$
```
The working directory for this command was `/home/lecture`. This output was given because `Hello.java` was specified as a directory. Because `Hello.java` is a file and not a directory, the `cd` command cannot change the working directory and instead throws an error.


---
*Using the `ls` command with no arguments:*
```
[user@sahara ~]$ ls
lecture1
```
The working directory for this command was `/home`. This output was given because `ls` lists all files and directories in the current working directory. Because the `ls` command was called in the `/home` directory, lecture1 was printed to the terminal. This is not an error.


*Using the `ls` command with a directory as an argument:*
```
[user@sahara ~]$ ls lecture1
Hello.java messages README
```
The working directory for this command was `/home`. This output was given because a directory was passed as an argument, meaning the `ls` command prints all files and directories in the directory that was passed as an argument. In this case, it printed all files and directories in the `/home/lecture1` directory. This is not an error.


*Using the `ls` command with a file as an argument:*
```
[user@sahara ~/lecture1]$ ls Hello.java
Hello.java
```
The working directory for this command was `/home/lecture1`. This output was given because the `ls` command received a file as an argument, meaning it only prints the file. This is not an error. 


---
*Using the `cat` command with no arguments:*
```
[user@sahara ~]$ cat

```
The working directory for this command was `/home`. This output was given because the `cat` command did not receive an argument. The `cat` command prints out the contents of whatever files are given, but because none were passed, nothing prints. This is not an error.


*Using the `cat` command with a directory as an argument:*
```
[user@sahara ~/lecture1]$ cat messages
cat: messages: Is a directory
```
The working directory for this command was `/home/lecture1`. This output was given because `cat` only receives files as arguments, not directories. Because of this, the command threw an error.


Using the `cat` command with a file as an argument:
```
[user@sahara ~/lecture1/messages]$ cat en-us.txt
Hello World!
```
The working directory for this command was `/home/lecture1/messages`. This output was given because the `cat` command received a file as an argument and proceeded to print the contents of the file back to the terminal. This is not an error. 


