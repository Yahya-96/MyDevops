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
PORT      STATE SERVICE     VERSION
31046/tcp open  echo
31518/tcp open  ssl/echo
31691/tcp open  echo
31790/tcp open  ssl/unknown
31960/tcp open  echo

```

The output returned 5 open ports. However, there are only 2 ports that use SSL/TLS: `31518` and `31790`.

## 3: Use `openssl s_client` to connect to SSL/TLS
Similar to the previous level, we will use a Pipe(`|`) in between the `cat` command and `openssl s_client`. We will enter the 2 ports (`31518` and `31790`).

After trying both ports, only port `31790` returned a "RSA private key".

## Output :
```
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----
```

## 4: Create a directory before creating a Private Key using the `nano` command.
We will need to first create a directory in the `/tmp` directory using the `mkdir` command. It will be called `bandit333`.

```
mkdir /tmp/bandit333
```

Once created, we will go the directory using the `cd` command.

```
cd /tmp/bandit333
```

## 5: Use `nano` to create a private key.
We will need to create a private key in order to use the RSA key. We can do this by using the `nano` command. 
`nano` is a text editor which allows us to edit text files from the command-line.  I created a private key using the `nano` command and called the file “sshkey17.private”.

```
nano sshkey17.private
```

Once the `nano` command was run, I was prompted to press ‘Enter’ key to continue. Once done, the private key will be opened to edit using nano. I pasted the RSA key from earlier. It then allowed me to save the updates. 

## 6: Change permissions to read-only via the `chmod` command.
To finish up, I used “chmod 400 sshkey17.private”. This made is secure by changing the permissions to read-only. 
```
chmod 400 sshkey17.private
```

## 7: Log into `bandit17` using the Private Key.
Now that i have the private key, we will use this to log into `bandit17`.
```
ssh -i sshkey17.private bandit17@bandit.labs.overthewire.org -p 2220
```
This successfully logged me into `bandit17`

---



