# Backup Script

## The Objective: 
Create a script that copies all .txt files from a specified directory to a backup directory. If the backup directory doesn’t exist, the script will create it first.

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

## 3: Define the source and backup directories.
```
# This defines the source and backup directories
SOURCE_DIR="/home/kuzan"
BACKUP_DIR="/home/kuzan/backup"
```

`SOURCE_DIR`: This will set the source directory where `.txt files` are located.

`BACKUP_DIR`: This defines the backup directory and it will be where `.txt` files will be copied.

---
## 4: Check if the source directory exists using `if` statement.
Before we copy all `.txt` files to the backup directory, we will need to check if the source directory exist. If it does not, it will return an error message telling the user the directory does not exist.
```
# This checks the existence of the source directory 
if [ ! -d "$SOURCE_DIR" ]; then
    echo "Error! Sorry, the source directory does not exist!"
    exit 1
fi
```
`[ ! -d "$SOURCE_DIR" ]`: This checks if the source directory does not exist. 

`!`="not".

`-d`: This checks if `$SOURCE_DIR`is a directory.

`exit 1`: This exits the script once the error message comes back.


If the source directory does not exist, it will return:
```
Error! Sorry, the source directory does not exist!
```
---

## 5: Create the backup directory if it does not exist.
Now it's time to create the backup directory. We will use the following lines of code to establish if the backup directory exists. If it does not exist, it will be created.

```
# This create the backup directory if it doesn't exist.
if [ ! -d "$BACKUP_DIR" ]; then
    mkdir -p "$BACKUP_DIR"
fi
```

 `[ ! -d "$BACKUP_DIR" ]`: This checks if the backup directory does not exist.

`mkdir -p`: This creates a directory if it does not exist. The `mkdir` command is used to create a directory. The `-p` that follows is important as the directory will only be created if it does not exist. This prevents any errors.


## 6: Copy all `.txt` files from the source directory to the backup directory.
```
# This copies all .txt files from the source to the backup directory
cp "$SOURCE_DIR"/*.txt "$BACKUP_DIR" 2>/dev/null
```

`cp "$SOURCE_DIR"/*.txt "$BACKUP_DIR"`: This will copy all `.txt` files from `$SOURCE_DIR` to `$BACKUP_DIR`.

 `2>/dev/null`: This is to suppress error messages from being displayed if no `.txt` files exist.

 ## 7: Check if any `.txt` files were copied.
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

If its unsuccessful, the following wil display:
```
Sorry, there are no .txt files.
```
---

#### We have succssfully completed this task !🚀

