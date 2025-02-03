# File Operations

## The Objective: 
Write a script that creates a directory, navigates into it, creates a file inside it, writes some text to the file, and then displays the contents of the file. 

---

## 1: Create a script.
Before we conduct the file operations, we will first need to create a script. I will use the `touch` command followed by the name of the script. I will call the script `operations.sh`. The `.sh` is an extension which will indicate it is a bash script.
```
touch operations.sh
```
I will open the file using the `nano` text editor. This will allow me to input the intended bash script.
```
nano operations.sh
```

## 2: Start the bash script with the "Shebang" line (`#!/bin/bash`).
This is the first line of any bash script. Every bash script starts with `#!/bin/bash`. It tells the system to use the bash shell to interpret the script. 
```
#!/bin/bash
```

## 3: Get the users input using `read -p`.
As we will need to ask the user to input two numbers, the following will be used:





### Output:
```
#!/bin/bash

# This defines directory and file name
dir_name="my_directory"
file_name="my_file.txt"

# This creates the directory
mkdir -p "$dir_name"

# This navigates into the directory
cd "$dir_name" || exit

# This creates the file and writes text to it
echo "Hello, how are you?" > "$file_name"

# This display the contents of the file
cat "$file_name"
```
