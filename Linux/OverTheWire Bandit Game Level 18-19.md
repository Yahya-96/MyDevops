 OverTheWire Bandit - Level 10-11

## The Objective : 
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
