# File Operations

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
## 3: Define the directory and file names.
Before we create our directory and file, we will first need to assign names to them. i will keep things simple and so i will call the directory `my_directory`. I also call the file `the_file.txt`.
```
# This defines directory and file name
dir_name="my_directory"
file_name="the_file.txt"
```
`dir_name`: This is a variable that stores the directory name.

`file_name`: This is a variable that stores the file name.


---
## 4: Create a directory.
```
# This creates the directory
mkdir -p "$dir_name
```

`mkdir -p`: This creates a directory if it does not exist. The `mkdir` command is used to create a directory. The ‘-p’ that follows is important as the directory will only be created if it does not exist. This prevents any errors.

---
## 5: Navigate into the directory.
Next, we will need to navigate to the directory. we will use the following command:
```
#This navigates into the directory
cd "$dir_name" || exit
```

`cd "$dir_name"`: This changes into the directory stored in the `dir_name` variable. 


`|| exit`:  The script stops immediately if the required directory is missing, preventing unexpected errors later. This is used to stop the script if the preceding command fails.   

---


## 6: Create the file and input text.
The `echo` command will be used to create the file and write to it.
```
echo "Hello friend, how are you?" > "$file_name"
```

`>`: This redirects output to the file via the variable `$file_name`.

This will print the text to the terminal.




## 7: Make it executable and run the script.
In order to run the script, we will first need to make it executable. The `chmod =x` will be used to make the `operations.sh` executable. Once done, i will run the file using `./`.
```
chmod +x operations.sh
./operations.sh
```



### Output:
```

Hello friend, how are you?
```


#### We have succssfully completed this task !🚀
---


