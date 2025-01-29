# OverTheWire Bandit - Level 7-8

## The Objective :
Find the password in order to progress to the next level. The password for the next level is stored in the file data.txt next to the word millionth.

---

## Solution:

## 1: Connect to Server
We will use the password obtained from the previous level to connect to the level 7 SSH server.

```
ssh bandi7@bandit.labs.overthewire.org -p 2220
```

I was prompted for a password. I will use the password obtained from the previous level to enter the server.

```
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

## 2: List files in directory
The `ls` command will be used to list the files in the current directory. A file called `data.txt` was present.

```
ls
```
### Output:
```
data.txt
```
The cat command was used to display the files but it came back with a long list that was near impossible to manually go through.

## 2: Use `grep` to search for the word "millionth".
After doing research on the man page - `grep man`,  `grep` commmand was identified as the ideal command to use as it allows us to search for specific texts within files. As we're searching for the word "millionth", the following was used:

```bash
grep millionth data.txt
```
The output will give us the password.

### Output: 
```bash
dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```



## 4: Note down the password 
The password will be noted down as it is needed to progress to the next level (`bandit8`).

---
