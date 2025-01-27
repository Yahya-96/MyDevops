# OverTheWire Bandit - Level 5-6

## The Objective :
The task is to find the password in order to progress to the next level. The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

human-readable -
1033 bytes in size -
not executable.

---

## Solution:

## 1: Connect to Server
We will use the password obtained from the previous level to connect to the level 5 SSH server.

```bash
ssh bandi5@bandit.labs.overthewire.org -p 2220
```

I was prompted for a password. I will use the password obtained from the previous level to enter the server.

```bash
 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

## 2: List files in directory
The `ls` command will be used to list the files in the current directory. The `inhere` directory was present.

```bash
ls
```
This will show a directory called `inhere`



## 3: Go to the `inhere` directory
We will change to the `inhere` directory using the `cd` command following:

```bash
cd inhere
```

## 4: Show all files in the directory `ls -al`
Using the `ls-al` command will allow us to list all the files in the directory, including hidden files. It will also include information about permissions and file types. The output gave me many directories named "maybehere" starting with `maybehere00` all the way to `maybehere19.




## 5: Check manpage and research to identify an efficient command to use. 
After some digging using the manpage, the `find` command was identified as a good tool when it comes to searching for files in directories.

```bash
man find
```

## 6: Use The `find` command to find the file.
The following command was used: `find . -type f -size -1033c ! -executable`. This filters and finds files less than 1033 bytes. 

```bash
find . -type f -size -1033c ! -executable
```
I then used:
```bash
find inhere -type f -size 1033c ! -executable.
```

## Output:
```bash
inhere/maybehere07/.file2`
```

## 6: Use `cat` command to find password. 
We now know that `.file2` contains the password. We will use the `cat` command to open the file and it will reveal the password.

```bash
cat ./maybehere07/.file2
```

### Output
Password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

## 7: Note down the password 
The password will be noted down as it is needed to progress to the next level (`bandit6`).


## 8: Exit Session

We will logout of the session by typing:

```bash
exit
```
---
