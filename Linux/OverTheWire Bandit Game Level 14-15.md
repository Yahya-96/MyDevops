# OverTheWire Bandit - Level 14-15

## The Objective : 
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

---

## Solution:

## 1: Retrieve the password for the current level
We are logged into `bandit14` level due to the actions taken in the previous level. In order to display the password for `bandit14`, we will use the `cat` command.

```bash
cat /etc/bandit_pass/bandit14
```

### Output:
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

```bash
dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr 
```

## 2: Use the Netcat(`nc`) command to connect to localhost.
We will make use of the Netcat command (`nc`) to connect to localhost via port `30000` in conjunction with the `cat` commmand. 

```bash
cat /etc/bandit_pass/bandit14 | nc localhost 30000
```
`nc localhost 30000`: This connects to port 30000 localhost. 

`cat /etc/bandit_pass/bandit14`: This reads and displays the current password.
 
The Pipe (|) : This sends the password as an input to the program running on port`30000`. This will then respond with the next password. 

### Output:
```
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```
This is the password for `bandit15`. 

---
