



#!/bin/bash

# Get user input
read -p "Enter first number: " num1
read -p "Enter second number: " num2

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
