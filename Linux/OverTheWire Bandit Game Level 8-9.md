# OverTheWire Bandit - Level 8-9

## The Objective :
Find the password in order to progress to the next level. The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.

---

## Solution:

## 1: Connect to Server
We will use the password obtained from the previous level to connect to the level 8 SSH server.

```bash
ssh bandi8@bandit.labs.overthewire.org -p 2220
```

I was prompted for a password. I will use the password obtained from the previous level to enter the server.

```
dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
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

## 3: Use manpage to research the suitable commands to use.
We will use the `sort` command to sort the files by grouping together identical lines. We will also use`uniq-u`. This will only leave unique lines once it has filtered out lines that appear more than once.

```
sort data.txt | sort | uniq -u
```

### Output: 
```
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```
This is the password for the next level.

## 4: Note down the password 
The password will be noted down as it is needed to progress to the next level (`bandit9`).

---
