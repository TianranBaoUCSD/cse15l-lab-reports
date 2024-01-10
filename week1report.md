# Examples of using cd, ls, and cat... 
## With no arguments:
### cd: 
```
[user@sahara: ~]$ cd
[user@sahara: ~]$
```
Working Directory: /home  
Explanation: The change directory function was given no path, so it just changed the directory to the directory it was currently in.  
Error?: This is not an error, even though the effect isn't very useful to us.  

### ls: 
```
[user@sahara: ~]$ ls
lecture1
```
Working Directory: /home  
Explanation: The list function listed the files that are currently in the directory /home.  
Error?: ls is working as intended in this case.   

### cat: 
```
[user@sahara: ~]$ cat


hello
hello


what
what
```
Working Directory: /home  
Explanation: If the cat function is called on its own, it just echoes back the inputs put into the terminal from this point forward until the function is cancelled.  
Error?: This may or may not be an error because cat *is* working and doing something, but it is not taking the output of multiple files and printing them together.   

## With a path to a directory as an arugment:

### cd: 
```
[user@sahara: ~]$ cd lecture1/
[user@sahara: ~/lecture1]$
```
Working Directory: /home  
Explanation: The cd function moves our working directory into the lecture1 file.   
Error?: This is not an error, cd is working as intended.  

### ls: 
```
[user@sahara: ~]$ ls lecture1/
[user@sahara: ~]$ Hello.class Hello.java messages README
```
Working Directory: /home  
Explanation: The ls command goes into the lecture1 folder and reads out the files that are in the folder.   
Error?: This is not an error, ls is working as intended  

### cat: 
```
[user@sahara: ~]$ cat lecture1/
cat: lecture1/: Is a directory
```
Working Directory: /home  
Explanation: The cat command tries to access a file at lecture1/, but finds a directory instead.   
Error?: This is an error since cat cannot work on a directory. It can only work on files.   

## With a path to a file as an argument:

### cd: 
```
[user@sahara: ~/lecture1/messages]$ cd en-us.txt
bash: cd: en-us.txt: Not a directory
```
Working Directory: /home/lecture1/messages    
Explanation: The cd command goes to the en-us text file and tries to access a directory, but finds a file instead.  
Error?: This is an error since cd cannot work on a file. It can only work on directories.  

### ls: 
```
[user@sahara: ~/lecture1/messages]$ ls en-us.txt
en-us.txt
```
Working Directory: /home/lecture1/messages  
Explanation: The ls command goes to the en-us text file and lists the name of the file.  
Error?: This is not an error since it is listing out elements as intended.   

### cat: 
```
[user@sahara: ~/lecture1/messages]$ cat en-us.txt
Hello World!
```
Working Directory: /home/lecture1/messages  
Explanation: The cat command goes to the en-us text file and prints out the text inside the file.   
Error?: This is not an error because even though it isn't concatenating and printing the contents of multiple files, it still is producing a correct output.   
