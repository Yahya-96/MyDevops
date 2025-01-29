# OverTheWire Bandit Game - Level 17-18

## The Objective : 
There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

---

## Solution:

## 1: Connect to Server
We will use the private key from the previous level to log into `bandit17`.

```
ssh -i sshkey17.private bandit17@bandit.labs.overthewire.org -p 2220
```


## 2: List files in directory
The `ls` command will be used to list the files in the current directory. Two files were present: `password.new` and `password.old`.

```
ls
```

### Output:
```
password.new  password.old
```

## 3: Use the `diff` command to compare the two files.
We need to find the password that has been changed between the old password file and the new one. The following command was used:
```
diff passwords.old passwords.new
```

### Output:
```
“42c42 
< ktfgBvpMzWKR5ENj26IbLGSblgUG9CzB 
--- 
> x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```

`diff passwords.old passwords.new`: This compares the two files, line by line, and displays the difference. 

 

`>`: This marks the line that exists only in passwords.new. 

## 4: Note down the password for the next level.
The password for `bandit18` is: x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO. 

---
