# OverTheWire Bandit - Level 1-2

## The Objective :
The task is to find the password in order to progress to the next level. The password for the next level is stored in a file called `-` located in the home directory.

---

## Solution:

## 1: Connect to Server
We will use the password obtained from the previous level to connect to the level 1 SSH server.

```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

I was prompted for a password. I will use the password obtained from the previous level to enter the server.

```bash
ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If 
```

## 2: List files in directory
Next, `ls` coomand will be used to identify the files present. The file present was `-`.

```bash
ls
```

### The output:

```bash
-
```

### 3: Display contents of `-`file
I was mindful of the fact that it is a special character. Since `-` is interpreted as an option in many commands, we need to explicitly tell the command it is a file. To do this, we will use `cat`and prefix it with `./`. This will give us the password.

```bash
cat ./-.
```

### The output:

```bash
263JGJPfgU6LtdEvgfWU1XP5yac29mFx 
```

### 4: Note down the password 
The password will be noted down as it is needed to progress to the next level (`bandit2`).

Password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx 

### 5: Exit Session

We will logout out of the session by typing:

```bash
exit
```
