# Backup Script

---

## The Objective: 
The script will prompt the user to input the paths of their source directory and backup directory. It will identify if the source directory exists. If it does not exist, it will come back with an error message. If it does exist, it will copy all `.txt` files to the backup directory. If the backup directory doesn’t exist, the script will create it first.

---

## 1: Create a script.
First, we will need to create a script. I will use the `touch` command followed by the name of the script. I will call the script `backup.sh`. The `.sh` is an extension which will indicate it is a bash script.
```
touch backup.sh
```
I will open the file using the `nano` text editor. `nano` is a text editor which allows us to edit the text files from the command-line. This will allow me to input the intended bash script.
```
nano backup.sh
```


---
## 2: Start the bash script with the "Shebang" line (`#!/bin/bash`).
This is the first line of any bash script. Every bash script starts with `#!/bin/bash`. It tells the system to use the bash shell to interpret the script. 
```
#!/bin/bash
```
---

## 3: Prompt the user for the source directory.
```
echo "Please enter the source directory:"
read source
```

`read source`: This stores the user’s input in the variable source.


---
## 4: Prompt the user for the backup directory
```
echo "Please enter the backup directory:"
read backup
```
`read backup`: This stores the user’s input in the variable backup.


## 5: Check if the source directory exists.
```
if [ ! -d "$source" ]; then
    echo "Sorry, the source directory $source does not exist."
    exit 1
fi
```
`[ ! -d "$source" ]`: This checks if the source directory ($source) does not exist. 

`!`="not".

`-d`: This checks if `$source`is a directory.

`exit 1`: This exits the script once the error message comes back.

If the source directory does not exist, it will return:
```
Sorry, the source directory $source does not exist.
```


---

## 6: Create the backup directory if it does not exist.

```
    mkdir -p "$backup"
```


`mkdir -p`: This creates a directory if it does not exist. The `mkdir` command is used to create a directory. The `-p` that follows is important as the directory will only be created if it does not exist. This prevents any errors.

---


## 7: Copy all `.txt` files from the source directory to the backup directory.
```
# This copies all .txt files from the source to the backup directory
cp -b "$source"/*.txt "$backup" 2>/dev/null
```

`cp -b`: This command cp -b → copies the `.txt` files from $source to $backup, keeping a backup of the existing files. Its a way of ensuring that `.txt` files are copied without overwriting existing files.

 `2>/dev/null`: This is to suppress error messages from being displayed if no `.txt` files exist, reducing confusion. 
 
---
 ## 8: Check if any `.txt` files were copied.
 An `if` statement will be used to check if the files were copied. 
```
# This checks if any .txt files were copied
if [ $? -eq 0 ]; then
    echo "Great,the backup was successful!"
else
    echo "Sorry, there are no .txt files."
fi
```

`$?`: This will store the exit of the last command ( in this case, its `cp`)

`-eq 0`: This checks if `cp` was sucessful (exit code `0` = success).

If its successful, the following will display:
```
Great,the backup was successful!
```

If its unsuccessful, the following will display:
```
Sorry, there are no .txt files.
```

#### We have succssfully completed this task !🚀

