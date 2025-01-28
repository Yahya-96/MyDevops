# OverTheWire Bandit - Level 16-17

## The Objective : 
The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

---

## Solution:

## 1: Connect to Server
We will use the password obtained from the previous level to connect to the level 16 SSH server.

```bash
ssh bandi16@bandit.labs.overthewire.org -p 2220
```

I was prompted for a password. I will use the password obtained from the previous level to enter the server.

```bash
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
```

## 2: Use `nmap` and `-sV` to find open ports.
We will need find open ports on localhost in the range 31000 to 32000. `nmap`is a network scanning tool. It helps to identify services and security vulnerabilities. is a service version detection. `-sV` scans for open ports and attempts to identify the version of the services running on the open ports. 

```bash
nmap -sV localhost -p 31000-32000
```

### Output: 
```
```

The output returned 5 open ports. However, there are only 2 ports that use SSL/TLS: `31518` and `31790`.

## 3: Use `openssl s_client` to connect to SSL/TLS
Similar to the previous level, we will use a Pipe(`|`) in between the `cat` command and `openssl s_client`. We will enter the 2 ports (`31518` and `31790`) 
```

