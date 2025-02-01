



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
