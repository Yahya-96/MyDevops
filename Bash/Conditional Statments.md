## The Objective: 
Write a script that creates a directory, navigates into it, creates a file inside it, writes some text to the file, and then displays the contents of the file. 

---

## 1: Create a script.
Before we conduct the file operations, we will first need to create a script. I will use the `touch` command followed by the name of the script. I will call the script `operations.sh`. The `.sh` is an extension which will indicate it is a bash script.
```
touch operations.sh
```
I will open the file using the `nano` text editor. `nano` is a text editor which allows us to edit the text files from the command-line. This will allow me to input the intended bash script.
```
nano operations.sh
```


---
## 2: Start the bash script with the "Shebang" line (`#!/bin/bash`).
This is the first line of any bash script. Every bash script starts with `#!/bin/bash`. It tells the system to use the bash shell to interpret the script. 
```
#!/bin/bash
```
---



## Output: 
```
!/bin/bash

# Ask user for the file path
read -p "Hi. Please enter the file path: " file

# Check if the file exists
if [ -e "$file" ]; then
    echo "This file '$file' exists."

    # Check if the file is readable
    if [ -r "$file" ]; then
        echo "The file is readable."
    else
        echo "The file is NOT readable."
    fi

    # Check if the file is writable
    if [ -w "$file" ]; then
        echo "The file is writable."
    else
        echo "The file is NOT writable."
    fi

    # Check if the file is executable
    if [ -x "$file" ]; then
        echo "The file is  executable."
    else
        echo "The file is NOT executable."
    fi
else
    echo "The file '$file' does not exist."
fi
```
