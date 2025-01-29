# OverTheWire Bandit Game - Level 6-7

## The Objective :
Find the password in order to progress to the next level. The password for the next level is stored somewhere on the server and has all of the following properties:

owned by user bandit7 -
owned by group bandit6 -
33 bytes in size.

---

## Solution:

## 1: Connect to Server
We will use the password obtained from the previous level to connect to the level 6 SSH server.

```
ssh bandi6@bandit.labs.overthewire.org -p 2220
```

I was prompted for a password. I will use the password obtained from the previous level to enter the server.

```
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

The `ls` command was to identify files present, but nothing came back.

## 2: Search for the file using `find` command
As we already know the size (33 bytes), user(bandit7) and group(bandit6), the following was used:

```b
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

### Output: 
```
/var/lib/dpkg/info/bandit7.password
```




## 3: Display contents of file using `cat`.
As we have idenfied the file (`/var/lib/dpkg/info/bandit7.password`), we will now use `cat` to view the contents. This output will give us the password for the next level.

```
cat /var/lib/dpkg/info/bandit7.password
```

### Output
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

---

## 4: Note down the password 
The password will be noted down as it is needed to progress to the next level (`bandit7`).


---

