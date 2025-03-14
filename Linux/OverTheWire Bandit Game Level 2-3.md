# OverTheWire Bandit Game - Level 2-3

## The Objective :
Find the password in order to progress to the next level. The password for the next level is stored in a file called `spaces in this filename` located in the home directory.

---

## Solution:

## 1: Connect to Server
We will use the password obtained from the previous level to connect to the level 2 SSH server.

```
ssh bandit2@bandit.labs.overthewire.org -p 2220
```

I was prompted for a password. I will use the password obtained from the previous level to enter the server.

```
 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

## 2: List files in directory
Next, `ls` coomand will be used to identify the files present. The file present was `spaces in this filename`.

```
ls
```

### Output:

```
spaces in this filename
```

### 3: Display contents of `spaces in this filename` file
Its imprtant to be mindful when dealing with files that have spaces. We can either use a backslash (`\`) between each word, or quotation marks (`"`). I decided to use the backslash.

```
cat spaces\in\this\filename
```

### Output:

```bash
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

### 4: Note down the password 
The password will be noted down as it is needed to progress to the next level (`bandit3`).

Password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx 

---
