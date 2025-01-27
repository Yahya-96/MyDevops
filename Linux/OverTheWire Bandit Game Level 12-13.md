# OverTheWire Bandit Gane - Level 12-13

## The Objective : 
The task is to find the password in order to progress to the next level. The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed.

---

## Solution:

## 1: Connect to Server
We will use the password obtained from the previous level to connect to the level 12 SSH server.

```bash
ssh bandi12@bandit.labs.overthewire.org -p 2220
```

I was prompted for a password. I will use the password obtained from the previous level to enter the server.

```bash
7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

## 2: List files in directory
The `ls` command will be used to list the files in the current directory. A file called `data.txt` was present.

```bash
ls
```

### Output:
```
data.txt  
```
