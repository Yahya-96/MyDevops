# OverTheWire Bandit Game - Level 18-19

## The Objective : 
The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.


---

## Solution:

## 1: Connect to Server
We will use the password obtained from the previous level to connect to the level 18 SSH server.

```
ssh bandi18@bandit.labs.overthewire.org -p 2220
```

I was prompted for a password. I will use the password obtained from the previous level to enter the server.

```
x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```
The connection was unsuccessful. 

Someone has modified `.bashrc` so that it logs me out when I try to log in with SSH.

## 2: Use `cat` to read the `readme` file.
We are told the password for the next level is stored in the home directory inside a file called “readme”. This means the file can be read using the “cat” command. The `ssh` command will be used in conjunction with the `cat` command to display the contents of the `readme` file.
```
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
```

## 3: Input the password from the previous level.
I was prompted for a password. I will use the password obtained from the previous level to enter the server. The output will give us the password for the next level.
```
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
```
This is the password for `bandit19`

---



 
 
