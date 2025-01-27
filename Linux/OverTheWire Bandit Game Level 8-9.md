# OverTheWire Bandit - Level 8-9

## The Objective :
The task is to find the password in order to progress to the next level. The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.

---

## Solution:

## 1: Connect to Server
We will use the password obtained from the previous level to connect to the level 8 SSH server.

```bash
ssh bandi8@bandit.labs.overthewire.org -p 2220
```

I was prompted for a password. I will use the password obtained from the previous level to enter the server.

```bash
dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

## 2: List files in directory
The `ls` command will be used to list the files in the current directory. A file called `data.txt` was present.

```bash
ls
```
