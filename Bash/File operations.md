




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
