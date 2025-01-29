# OverTheWire Bandit - Level 9-10

## The Objective :
Find the password in order to progress to the next level. The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

---

## Solution:

## 1: Connect to Server
We will use the password obtained from the previous level to connect to the level 9 SSH server.

```
ssh bandi9@bandit.labs.overthewire.org -p 2220
```

I was prompted for a password. I will use the password obtained from the previous level to enter the server.

```
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
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
We will use the `string` command. This command prints character sequences that are at least 4 characters long. We will also use `grep` to assist in filtering the lines that have `=`.
```
strings data.txt | grep ====
```

### Output: 
```
}========== the 

3JprD========== passwordi 

~fDV3========== is 

D9========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey 
```
The password for the next level is: `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`.

## 4: Note down the password 
The password will be noted down as it is needed to progress to the next level (`bandit10`).

---
