# OverTheWire Bandit Gane - Level 12-13

## The Objective : 
The task is to find the password in order to progress to the next level. The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed.

---

## Solution:

## 1: Connect to Server
We will use the password obtained from the previous level to connect to the level 12 SSH server.

```bash
ssh bandi12@bandit.labs.overthewire.org -p 2220
```

I was prompted for a password. I will use the password obtained from the previous level to enter the server.

```bash
7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
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

## 3: Create a directory (`mkdir`) to store temporary files.
We will create a directory under `/tmp` and name it `moon`.

```
mkdir /tmp/moon
```
`/tmp`: This is used to store temporary files.

## 4: Copy the file (`data.txt`) to the directory.
We will copy `data.txt` to the directory we created.

```
cp data.txt /tmp/moon
```

## 5: Use the `xxd` command to convert the hexdump to binary.
As we're dealing with a hexdump file (`data.txt`), we will use the following:
```
xxd -r data.txt > data0 
```
`xxd -r`: This command helps to convert the hexdump file to its original binary format using `-r` and then provide a file name (`data0`)

## 6: `ls` and then use the `file` command to identify the type of file.
```
file data0
```
The output returned a `gzip` compressed file.

## 7: Decompress the `gzip` file.
In order to decompress, as we're dealing with a `gzip` file, it will be renamed using the `mv` command and a gzip extension will be provided. I renamed the file `data01.gz`.
```
mv data0 data01.gz
gzip -d data01.gz
```
## 8: Check the file type.
```
file data01
```
The output returned a `bzip2` compressed file.

## 9: Decompress the `bzip2` file.
In order to decompress, as we're dealing with a `bzip2` file, it will be renamed using the `mv` command and a bzip2 extension will be provided. I renamed the file `data02.bz2`.

```
mv data01 data02.bz2
bzip2 -d data02.bz2
```
## 10: Check the file type.
```
file data02
```
The output returned a `gzip` compressed file.

## 11: Decompress the `gzip` compressed file.

In order to decompress, as we're dealing with a `gzip` file, it will be renamed using the `mv` command and a gzip extension will be provided. I renamed the file `data03.gz`.

```
mv data02 data03.gz
gzip -d data03.gz
```

## 12: Check the file type again.

```
file data03
```
This returned a `data03: POSIX tar archive (GNU)` file.
