# OverTheWire Bandit Game - Level 4-5

## The Objective :
Find the password in order to progress to the next level. The password for the next level is stored in the only human-readable file in the inhere directory.

---

## Solution:

## 1: Connect to Server
We will use the password obtained from the previous level to connect to the level 4 SSH server.

```
ssh bandi4@bandit.labs.overthewire.org -p 2220
```

I was prompted for a password. I will use the password obtained from the previous level to enter the server.

```
 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

## 2: List files in directory
The `ls` command will be used to list the files in the current directory. The `inhere` directory was present.

```
ls
```
This will show a directory called `inhere`



## 3: Go to the `inhere` directory
We will change to the `inhere` directory using the `cd` command following:

```
cd inhere
```

## 4: Show all files in the directory - including hidden files using `ls -la`
Using the `ls-la` command will allow us to list all the files in the directory, including hidden files. It will also include information about permissions and file types. The output will list 10 files.

```
ls -a
```

### Output:
```
total 48
drwxr-xr-x 2 root    root    4096 Sep 19 07:08 .
drwxr-xr-x 3 root    root    4096 Sep 19 07:08 ..
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file00
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file01
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file02
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file03
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file04
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file05
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file06
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file07
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file08
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file09
```

## 5: Check the file type using `file` command. 
By using the `file` command, it will help us identify the the file types by checking the contents of all files.

```
file ./*
```

### The output:

```
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
```

## 6: Check the contents of the human-readable file `-file07`. 
The `file07` file is the only file that came back as "ASCII text". This tells us it is the readable file we want. We will use the `cat` command to open the file and it will reveal the password.

```
cat ./file07
```

### Output
Password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw


## 7: Note down the password 
The password will be noted down as it is needed to progress to the next level (`bandit5`).


---
