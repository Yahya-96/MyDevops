




### Output:
```
#!/bin/bash

# Define directory and file name
dir_name="my_directory"
file_name="my_file.txt"

# Create the directory
mkdir -p "$dir_name"

# Navigate into the directory
cd "$dir_name" || exit

# Create the file and write text to it
echo "Hello, how are you?" > "$file_name"

# Display the contents of the file
cat "$file_name"
```
