# OverTheWire Bandit - Level 15-16

## The Objective :
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

---

## Solution:

## 1: Connect to Server
We will use the password obtained from the previous level to connect to the level 15 SSH server.

```bash
ssh bandi15@bandit.labs.overthewire.org -p 2220
```

I was prompted for a password. I will use the password obtained from the previous level to enter the server.

```bash
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```

## 2: Use `openssl s_client` to connect to SSL/TLS
Similar to the previous level, we will use a Pipe(`|`) in between the following commands:
```
cat /etc/bandit_pass/bandit15 | openssl s_client -connect localhost:30001 -quiet
```
`openssl s_client -connect localhost:30001 -quiet`: This sets up an SSL/TLS connection to the program running on port 30001.  

### Output:
```
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
```
This is the password for the next level (`bandit16`).

---
