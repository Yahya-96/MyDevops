# OverTheWire Bandit - Level 0 & 0-1 

## The Objective :
The task is to find the password in order to progress to the next level. I am told the password for the next level is stored in a file called `readme` located in the home directory.

---

## Solution:

## 1: Connect to Server
I used SSH to connect to the OverTheWire Bandit server. This allows us to securely access and manage remote systems over an unsecured network. The username provided is `bandit0` and the port is `2220`. The `-p` option is used to specify the port.

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

I was prompted for a password. The password was `bandit0`. This allowed me to enter the server.

## 2: List files in directory
Next, `ls` coomand will be used to identify the files present. The file present was `readme`. I then used the `cat readme` to show contents.

```bash
ls
```

### The output:

```bash
readme
```

### 3: Display contents of `readme`file
We will now use the `cat readme` to show contents of the file. This will contain the password.

```bash
cat readme
```

### Output:

```bash
Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walkthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!

The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```

### 4: Note down the password 
The password will be noted down as it is needed to progress to the next level (`bandit1`).

Password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If 

---
