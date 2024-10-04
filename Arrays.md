## Day 4:- **Arrays in Bash Scripting** 

An **array** in Bash is a collection of multiple values that are stored under a single variable name. Each value can be accessed individually, making arrays useful for storing lists of data (e.g., names, items, etc.). Arrays in Bash are zero-indexed, meaning the first element has an index of 0.

### **1. Basics of Arrays**

#### **Declaring an Array:**
You can declare an array by assigning multiple values enclosed in parentheses `()` and separated by spaces.

```bash
my_array=(apple banana "Fruit Basket" orange)
```

In this example:
- `my_array[0] = apple`
- `my_array[1] = banana`
- `my_array[2] = Fruit Basket`
- `my_array[3] = orange`

#### **Accessing Array Elements:**
To access an individual element in an array, use the index inside square brackets `[]`.

```bash
echo ${my_array[0]}   # Outputs: apple
echo ${my_array[2]}   # Outputs: Fruit Basket
```

#### **Modifying an Array Element:**
You can modify an element by specifying the index and assigning a new value.

```bash
my_array[1]="grape"
echo ${my_array[1]}   # Outputs: grape
```

#### **Printing the Entire Array:**
Use `[*]` or `[@]` to print all elements of the array.

```bash
echo ${my_array[@]}    # Outputs: apple grape "Fruit Basket" orange
```

#### **Array Length:**
You can get the total number of elements in an array using `${#array_name[@]}`.

```bash
echo ${#my_array[@]}    # Outputs: 4
```

### **2. Working with Array Elements**

#### **Looping Through an Array:**
You can loop through each element in an array using a `for` loop.

```bash
for item in "${my_array[@]}"
do
    echo $item
done
```

This outputs each item:
```bash
apple
grape
Fruit Basket
orange
```

#### **Accessing Indexes with a Loop:**
To print both indexes and values:

```bash
for i in "${!my_array[@]}"
do
    echo "Index: $i, Value: ${my_array[$i]}"
done
```

Output:
```bash
Index: 0, Value: apple
Index: 1, Value: grape
Index: 2, Value: Fruit Basket
Index: 3, Value: orange
```

### **3. Advanced Array Operations**

#### **Adding Elements to an Array:**
You can add elements to an array by directly assigning values to a new index.

```bash
my_array[4]="kiwi"
echo ${my_array[@]}    # Outputs: apple grape "Fruit Basket" orange kiwi
```

#### **Appending Elements Dynamically:**
To append a value at the next available index, use the `+=` operator.

```bash
my_array+=("mango")
echo ${my_array[@]}    # Outputs: apple grape "Fruit Basket" orange kiwi mango
```

#### **Removing Elements from an Array:**
You can remove an element from the array by using the `unset` command.

```bash
unset my_array[2]
echo ${my_array[@]}    # Outputs: apple grape orange kiwi mango
```

The element at index 2 (`Fruit Basket`) is removed.

#### **Array Slicing:**
You can extract a portion of an array using slicing. The syntax is `${array[@]:start:length}`.

```bash
echo ${my_array[@]:1:3}   # Outputs: grape orange kiwi
```

This extracts 3 elements starting from index 1.

### **4. Associative Arrays (Key-Value Pairs)**

In Bash, you can also use **associative arrays**, which allow you to store key-value pairs. However, they must be declared differently.

#### **Declaring an Associative Array:**

```bash
declare -A fruits
fruits[apple]="red"
fruits[banana]="yellow"
fruits[kiwi]="green"
```

#### **Accessing Values in an Associative Array:**

```bash
echo ${fruits[apple]}    # Outputs: red
```

#### **Looping Through an Associative Array:**

```bash
for key in "${!fruits[@]}"
do
    echo "$key is ${fruits[$key]}"
done
```

Output:
```bash
apple is red
banana is yellow
kiwi is green
```

### **5. Multi-Dimensional Arrays**
Bash doesn't support true multi-dimensional arrays, but you can simulate them using nested arrays (array of arrays).

#### **Simulating Multi-Dimensional Arrays:**

```bash
my_array1=(1 2 3)
my_array2=(4 5 6)

my_2d_array=("${my_array1[@]}" "${my_array2[@]}")

# Access elements like this:
echo ${my_2d_array[0]}  # Outputs: 1 (from my_array1)
echo ${my_2d_array[3]}  # Outputs: 4 (from my_array2)
```

### **6. Array Functions**

You can use functions to handle arrays. For example, passing an array as a function argument:

#### **Passing Arrays to Functions:**

```bash
function print_array {
    local array=("$@")
    for item in "${array[@]}"
    do
        echo $item
    done
}

print_array "${my_array[@]}"
```

This function will print all elements of the array.

---

### **Summary of Key Commands**

| **Action**                    | **Command**                                |
|-------------------------------|--------------------------------------------|
| Declare an array               | `my_array=(item1 item2 "item 3")`          |
| Access array element           | `echo ${my_array[index]}`                  |
| Modify array element           | `my_array[index]="new_value"`              |
| Print all elements             | `echo ${my_array[@]}`                      |
| Get array length               | `echo ${#my_array[@]}`                     |
| Add elements                   | `my_array+=(new_element)`                  |
| Remove element                 | `unset my_array[index]`                    |
| Loop through array             | `for item in "${my_array[@]}"; do ... done`|
| Declare associative array      | `declare -A my_assoc_array`                |
| Access associative element     | `echo ${my_assoc_array[key]}`              |
| Loop through associative array | `for key in "${!my_assoc_array[@]}"; do ... done`|

Now you're equipped with the basics through to advanced usage of arrays in Bash scripting!
