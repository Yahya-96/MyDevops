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
---

## 2: Start the bash script with the "Shebang" line (`#!/bin/bash`).
This is the first line of any bash script. Every bash script starts with `#!/bin/bash`. It tells the system to use the bash shell to interpret the script. 
```
#!/bin/bash
```
---

## 3: Validate numeric function.
```

# Function to validate numeric input
is_number() {
    [[ $1 =~ ^-?[0-9]+(\.[0-9]+)?$ ]]
}

# Get first number with validation
while true; do
    read -p "Enter first number: " num1
    if is_number "$num1"; then
        break
    else
        echo "❌ Invalid input. Please enter a number."
    fi
done

# Get second number with validation
while true; do
    read -p "Enter second number: " num2
    if is_number "$num2"; then
        break
    else
        echo "❌ Invalid input. Please enter a number."
    fi
done
```

This will make sure the user inputs numbers rather than letters. If user enters something other than a number, they will be met with an error message.

---

## 4: Get the users input using `read -p`.
As we will need to ask the user to input two numbers, the following will be used:

```
# Prompts user input
read -p " Please enter the first number: " num1
read -p "Please enter the second number: " num2
```
`read -p`: This command will be used in order to prompt the user for an input.

`num1` & `num2`: This will store the numbers entered by the user.

---

## 5: It's time to perform the calculations!
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

---

## 6: Display the results of the calculations.
Once the users inputs the two number and the system does it's calculations, the results will need to be displayed. The `echo` command will be used to display the results to the terminal.
```
# This will display the results.
echo "Addition: $sum"
echo "Subtraction: $diff"
echo "Multiplication: $prod"
echo "Division: $div"
```

---

## 7: Make it executable and run the script.
In order to run the script, we will first need to make it executable. The `chmod =x` will be used to make the `math.sh` executable. Once done, i will run the file using `./`.
```
chmod +x math.sh
./math.sh
```
### Output:
```
Please enter the first number: 10
Please enter the second number: 5
```
---

### Final result:
```
Addition: 15
Subtraction: 5
Multiplication: 50
Division: 3.33
```

#### We have succssfully completed this task !🚀

---
