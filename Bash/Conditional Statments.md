## The Objective: 
Write a script that checks if a file exists and prints a message indicating whether it exists or not. If it exists, the script should also check if the file is readable, writable, or executable.

---

## 1: Create a script.
First, wee will need to create a script. I will use the `touch` command followed by the name of the script. I will call the script `conditional.sh`. The `.sh` is an extension which will indicate it is a bash script.
```
touch conditional.sh
```
I will open the file using the `nano` text editor. `nano` is a text editor which allows us to edit the text files from the command-line. This will allow me to input the intended bash script.
```
nano conditional.sh
```


---
## 2: Start the bash script with the "Shebang" line (`#!/bin/bash`).
This is the first line of any bash script. Every bash script starts with `#!/bin/bash`. It tells the system to use the bash shell to interpret the script. 
```
#!/bin/bash
```
---

## 3: Identify the file path.
In order to find a file, i will prompt the user with a message, asking them to input the name of the file.
```
read -p "Hi, please enter the file path:" file
```
`read -p`: This command will be used in order to prompt the user for an input.

The user's input will be stored in the `file` variable.

---

## 4: Find out if the file exists.
As i will need to identify if the file exists, i will use an `if` statement. An `if` statement is a conditional structure and it is used to execute commands that are either true or false.
```
# Check if the file exists
if [ -e "$file" ]; then
    echo "Great news! The file '$file' exists."
```

`-e`: This checks the existence of the file.

---

## 5: Check if the file is readable.
I will again use the if statement to check if the file is readable.
```
 # This will check if the file is readable
    if [ -r "$file" ]; then
        echo "The file is readable."
    else
        echo "The file is NOT readable."
    fi

```
`-r`: This checks if the file is readable.

`else`: This will be used in case the condition is false. It will be used to define an alternative block of code that will run only if the condition is false.

`fi`: This will close the `if` statement.

---

## 6: Check if the file is writable
An `if` statement will be used to check if the file is writable.

```
    # Check if the file is writable
    if [ -w "$file" ]; then
        echo "The file is writable."
    else
        echo "The file is NOT writable."
    fi
```

`-w`: This checks if the file is writable.

`else`: This will be used in case the condition is false. It will be used to define an alternative block of code that will run only if the condition is false.

`fi`: This will close the `if` statement.

---

## 7: Check if the file is executable.
A final `if` statement will be used to check if the file is executable.
```
   # Check if the file is executable
    if [ -x "$file" ]; then
        echo "The file is  executable."
    else
        echo "The file is NOT executable."
    fi

```
`-x`: Checks if the file is executable. 

`else`: This will be used in case the condition is false. It will be used to define an alternative block of code that will run only if the condition is false.

`fi`: This will close the `if` statement.



## Output: 


```
