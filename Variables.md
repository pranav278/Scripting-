### Day 2. Variables 

### Variables in Shell Scripting 

- **What are Variables?**
  - Variables are like containers where you can store information (values) such as numbers, characters, or strings (a series of characters).
  
- **Creating Variables**
  - Variables are created when you assign a value to them.
  - Example: `name="Pranav"`

- **Variable Naming Rules**
  - **Case-sensitive**: This means `NAME` and `name` are treated as different variables.
  - Can only include letters (a-z, A-Z), numbers (0-9), and the underscore (`_`).
  - The variable name **cannot start with a number**.

- **Assigning Values**
  - You use the `=` sign to assign a value to a variable.
  - No spaces are allowed before or after the `=` sign.
  - Example: `age=25` is correct, but `age = 25` is wrong.

- **Examples**
  ```bash
  name="John"   # Correct
  number=123    # Correct
  greeting="Hello, World!"  # Correct
  ``` 

These are the basic things you need to know about variables in shell scripting!



### Referencing Variables in Shell Scripting (Simple Examples)

- **Escaping Special Characters**
  - To use special characters like `$`, we need to escape them using a backslash `\`.
  - Example:
    ```bash
    PRICE_PER_APPLE=5
    echo "The price of an Apple today is: \$HK $PRICE_PER_APPLE"
    ```
    - Output: `The price of an Apple today is: $HK 5`
    - Here, `\$HK` makes sure `$HK` is printed as text, not treated as a variable.

- **Using `${}` to Avoid Ambiguity**
  - When you're combining a variable with other characters, use `${}` to clearly show where the variable name ends.
  - Example:
    ```bash
    MyFirstLetters=ABC
    echo "The first 10 letters in the alphabet are: ${MyFirstLetters}DEFGHIJ"
    ```
    - Output: `The first 10 letters in the alphabet are: ABCDEFGHIJ`
    - `${MyFirstLetters}` ensures the shell correctly combines the variable with other letters.

- **Preserving White Spaces with Quotes `""`**
  - When your variable has spaces, wrap it in double quotes `""` to keep those spaces.
  - Example:
    ```bash
    greeting='Hello        world!'
    echo "$greeting now with spaces: $greeting"
    ```
    - Output: `Hello        world! now with spaces: Hello        world!`
    - Without the quotes, the extra spaces would be removed.

- **Command Substitution (Using Command Output as Variable Value)**
  - You can store the output of a command (like `pwd` to show the current directory) in a variable using back-ticks `` `command` `` or `$()`.
  
  - Example 1 (using back-ticks):
    ```bash
    Pranav=`pwd`
    echo "$Pranav is good"
    ```
    - This stores the current directory in the variable `Pranav` and prints it.
  
  - Example 2 (using `$()`):
    ```bash
    P=$(pwd)
    echo "$P"
    ```
    - Output: `/your/current/directory` (depending on your system's directory)
    - `$()` runs the `pwd` command and stores its output in `P`.

**Key Takeaway**: Commands inside `$()` or `` ` ` `` run first, and their output is saved into the variable.
