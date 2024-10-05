## Day 5:- Basic Operators in Bash

In Bash scripting, arithmetic operations can be performed using the `$(())` syntax for arithmetic expansion. Below is a guide covering the basic arithmetic operators available.

#### **Arithmetic Expression Syntax**

To perform arithmetic operations in Bash, we use double parentheses: `$(())`. Variables and constants are evaluated inside this expression.

```bash
result=$((expression))
```

For example:
```bash
A=3
B=$((100 * $A + 5)) # B will be 305
```

### **Basic Arithmetic Operators**

1. **Addition (`+`)**  
   Adds two numbers.
   ```bash
   a=5
   b=3
   sum=$((a + b)) # sum will be 8
   ```

2. **Subtraction (`-`)**  
   Subtracts the second number from the first.
   ```bash
   difference=$((a - b)) # difference will be 2
   ```

3. **Multiplication (`*`)**  
   Multiplies two numbers.
   ```bash
   product=$((a * b)) # product will be 15
   ```

4. **Division (`/`)**  
   Performs integer division (the result is an integer, fractional parts are discarded).
   ```bash
   quotient=$((a / b)) # quotient will be 1 (since 5 divided by 3 is 1 in integer division)
   ```

5. **Modulo (`%`)**  
   Returns the remainder when one number is divided by another.
   ```bash
   remainder=$((a % b)) # remainder will be 2
   ```

6. **Exponentiation (`**`)**  
   Raises one number to the power of another.
   ```bash
   power=$((a ** b)) # power will be 125 (since 5 raised to the power of 3 is 125)
   ```

### **Examples of Arithmetic Operations**

```bash
A=5
B=3

# Addition
add=$((A + B))   # add will be 8

# Subtraction
sub=$((A - B))   # sub will be 2

# Multiplication
mul=$((A * B))   # mul will be 15

# Division
div=$((A / B))   # div will be 1 (integer division)

# Modulo
mod=$((A % B))   # mod will be 2

# Exponentiation
exp=$((A ** B))  # exp will be 125
```

### **Key Points to Remember**
- Use `$(())` to perform arithmetic in Bash.
- Division always results in an integer (fractional part is discarded).
- Exponentiation is done using `**`.

This covers the basic arithmetic operators you can use in Bash scripts!
