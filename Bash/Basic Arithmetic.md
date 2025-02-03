# Basic Arithmetic

## The Objective: 
Write a script that takes two numbers as input from the user and performs basic arithmetic operations (addition, subtraction, multiplication, and division) and then displays all the answers of those operations in the terminal. 

---

## 1: Create a script.
Before we put together the basic arithmetic operations, we will first need to create a script. I will use the `touch` command followed by the name of the script. I will call the script `math.sh`. The `.sh` is an extension which will indicate it is a bash script.
```
touch math.sh
```
I will open the file using the `nano` text editor. This will allow me to input the intended bash script.
```
nano math.sh
```

## 2: Start the bash script with the "Shebang" line (`#!/bin/bash`).
This is the first line of any bash script. Every bash script starts with `#!/bin/bash`. It tells the computer to use bash to run the script. 
```
#!/bin/bash
```

## 3: Get the users input using `read -p`.
As we will need to ask the user to input two numbers, the following will be used:

```
# Prompts user input
read -p "Enter first number: " num1
read -p "Enter second number: " num2
```

# Perform calculations
sum=$((num1 + num2))
diff=$((num1 - num2))
prod=$((num1 * num2))
div=$(echo "scale=2; $num1 / $num2" | bc)  # Floating-point division

# Display results
echo "Addition: $sum"
echo "Subtraction: $diff"
echo "Multiplication: $prod"
echo "Division: $div"
