# OverTheWire Bandit - Level 11-12

## The Objective : 
The task is to find the password in order to progress to the next level. The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.

---

## Solution:

## 1: Connect to Server
We will use the password obtained from the previous level to connect to the level 11 SSH server.

```bash
ssh bandi11@bandit.labs.overthewire.org -p 2220
```

I was prompted for a password. I will use the password obtained from the previous level to enter the server.

```bash
dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr 
```

## 2: List files in directory
The `ls` command will be used to list the files in the current directory. A file called `data.txt` was present.

```bash
ls
```

### Output:
```
data.txt  
```


## 3: Decode the encoded `ROT13` text in `data.txt`.
The contents of the `data.txt` file will need to be decoded. This is due to it being encoded using `ROT13`. This is a substitution cipher which rotates the characters by 13 positions. We will make use of the `tr` command to decode the `ROT13` text in `data.txt`. To decode, we will do the following:

```
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
`tr`: This command translates or deletes characters from standard input and writes the result to standard output.

`A-Za-z` matches uppercase(A-Z) and lowercase(a-z) letters. 
`N-ZA-Mn-za-m` rotates the letters by the 13 positions and warps around the alphabet.

The output will give us the password.


### Output:
```
7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

## 4: Note down the password 
The password will be noted down as it is needed to progress to the next level (`bandit12`).

## 5: Exit Session

We will logout of the session by typing:

```bash
exit
```
---
