# OverTheWire Bandit - Level 13-14

## The Objective : 
The password for the next level is stored in `/etc/bandit_pass/bandit14` and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level.

---

## Solution:

## 1: Connect to Server
We will use the password obtained from the previous level to connect to the level 13 SSH server.

```
ssh bandi13@bandit.labs.overthewire.org -p 2220
```

I was prompted for a password. I will use the password obtained from the previous level to enter the server.

```
FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```

## 2: List files in directory
The `ls` command will be used to list the files in the current directory. A file called `sshkey.private` was present.

```
ls
```

### Output:
```
sshkey.private 
```

## 3: Use the `sshkey.private` to access the next level.
The objective tells us the we will need to use a "private SSH key" to progress to the next level (`bandit14`). We've identified the key through the previous output (`sshkey.private`) and so we will use the following:
```
ssh -i sshkey.private bandit14@localhost -p 2220
```
This command uses the SSH private key(`sshkey.private`) to access `bandit14` on `localhost` via the usual `2220` port.

`ssh-i sshkey.private`: This specifies the private SSH file(sshkey.private) to authenticate the connection without the need of a password. 

## 4: Login successful.
Once we run the command, we are given access to `bandit14` without the need of a password. 

---
