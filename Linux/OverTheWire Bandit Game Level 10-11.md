# OverTheWire Bandit - Level 10-11

## The Objective:

The task is to find the password in order to progress to the next level. The password for the next level is stored in the file data.txt, which contains base64 encoded data.
---

## Solution:

## 1: Connect to Server
We will use the password obtained from the previous level to connect to the level 10 SSH server.

```bash
ssh bandi10@bandit.labs.overthewire.org -p 2220
```

I was prompted for a password. I will use the password obtained from the previous level to enter the server.

```bash
FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey 
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
The `cat` command was used to identify the encoded file and it gave the following output:
### Output:
```
VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==
```
## 3: Decode the encoded base64 file.
After doing some digging using the manpage, the follwoing command will be used:
```
base64 -d data.txt
```
`base64 -d` helps to decode the "base64" content within the file `data.txt`. This will then return the password.

### Output:
```
dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

## 4: Note down the password 
The password will be noted down as it is needed to progress to the next level (`bandit11`).

## 5: Exit Session

We will logout of the session by typing:

```bash
exit
```
---
