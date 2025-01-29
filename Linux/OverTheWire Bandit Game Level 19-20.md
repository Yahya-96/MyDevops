# OverTheWire Bandit - Level 19-20

## The Objective :
To gain access to the next level(`bandit20`), we will use the setuid binary in the homedirectory. The password for this level can be found in the usual place (`/etc/bandit_pass`).

---

## Solution:

## 1: Connect to Server
We will use the password obtained from the previous level to connect to the level 19 SSH server.

```
ssh bandit19@bandit.labs.overthewire.org -p 2220
```

I was prompted for a password. I will use the password obtained from the previous level to enter the server.

```
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
```

## 2: List files in directory
Next, `ls` coomand will be used to identify the files present. The file present was `bandit20-do`.

```
ls
```

### Output:

```
bandit20-do
```

## 3: Inspect the `bandit20-do` file. 
I used `ls -l` to look into the permissions of the file.  We can see that the binary file can be executed by the current user (`bandit19`) and it is owned by `bandit20`.

### Output:
```
-rwsr-x--- 1 bandit20 bandit19 14880 Sep 19 07:08 bandit20-do
```

## 4: Use the "Setuid binary" and execute it without arguments
The level informs me I should use the setuid binary and execute it without arguments. A setuid binary is a program that runs with elevated privileges. The following was used:
```
./bandit20-do
```
### Output:
```
Run a command as another user. 
  Example: ./bandit20-do id
```
This hint, coupled with the fact that the password can be found in the usual place (`/etc/bandit_pass`), encouraged me to do the following: 

```
./bandit20-do cat /etc/bandit_pass/bandit20
```
The output gave me the password.
### Output:
```
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
```

`./bandit20-do cat /etc/bandit_pass/bandit20`: This executes the binary to read the password file with elevated privileges. This is required to access such files. 

---
