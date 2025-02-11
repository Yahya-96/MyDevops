# Conditional Statements

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

## 5: Check if the file is readable, writable and executable.
I will again use the if statement to check if the file is readable, writable and executable.
```

    # Check file permissions
    [ -r "$file" ] && echo "It is readable." || echo "It is NOT readable."
    [ -w "$file" ] && echo "It is writable." || echo "It is NOT writable."
    [ -x "$file" ] && echo "It is executable." || echo "It is NOT executable."
else
    echo "The file '$file' does not exist."
fi

```
`-r`: This checks if the file is readable.

`-w`: This checks if the file is writable.

`-x`: Checks if the file is executable. 

`else`: This will be used in case the condition is false. It will be used to define an alternative block of code that will run only if the condition is false.

`fi`: This will close the `if` statement.

---



## 6: Make it executable and run the script.
In order to run the script, we will first need to make it executable. The `chmod =x` will be used to make the `conditional.sh` executable. Once done, i will run the file using `./`.
```
chmod +x conditional.sh
./conditional.sh
```


## Output: 
```
Hi, please enter the file path:

```


#### We have succssfully completed this task !🚀

---
