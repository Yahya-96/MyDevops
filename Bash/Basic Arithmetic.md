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
This is the first line of any bash script. Every bash script starts with `#!/bin/bash`. It tells the system to use the bash shell to interpret the script. 
```
#!/bin/bash
```

## 3: Get the users input using `read -p`.
As we will need to ask the user to input two numbers, the following will be used:

```
# Prompts user input
read -p " Please enter the first number: " num1
read -p "Please enter the second number: " num2
```
read -p: This command will be used in order to prompt the user for an input.
num1 & num2: This will store the numbers entered by the user.

## 4: It's time to perform the calculations!
In order to perform the calculations, we will need to start with `$(( )))`. This allows us to perform arithmetic calculations. As i will need to use addition, subtraction, multiplication, and division, i will do the following:

```
# This perform the calculations
sum=$((num1 + num2))
diff=$((num1 - num2))
prod=$((num1 * num2))
div=$(echo "scale=2; $num1 / $num2" | bc)  # Floating-point division

```
`sum`: This will store the addition operation. For example, we will assign number 10 to `num1` and the number 5 to `num2`( 10 + 5 )

`diff`: This will store subtraction operation (10 - 5). 

`prod`:This will store the multiplication operation (10 * 5).

`div`: This will store the division operation.

`scale=2`: This sets the number of decimal places to 2 (for precise division).

`| bc`: The pipe (`|`) sends the command output to bc (Basic Calculator), which handles floating-point arithmetic in bash. 


By default, bash only supports integer division, so `bc` is needed for accurate decimal results. This means that bash does not use decimals but rather rounds it up as a whole number. This allows bash to perform the operation in decimals.  


## 5: Display the results of the calculations.
Once the users inputs the two number and the system does it's calculations, the results will need to be displayed. The `echo` command will be used to display the results to the terminal.
```
# This will display the results.
echo "Addition: $sum"
echo "Subtraction: $diff"
echo "Multiplication: $prod"
echo "Division: $div"
```

### Output:
```
Addition: 15
Subtraction: 5
Multiplication: 50
Division: 3.33
```

#### We have succssfully completed this task !🚀

---
