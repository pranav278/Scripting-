### Day  6: Array Comparison in Shell

#### What is an Array?
- **Array** is a variable that can hold multiple values. 
- Arrays in Shell are **zero-based**, meaning the first element of the array starts at index 0.

#### Key Points:
- **No limit to size**: You can store as many elements as needed.
- **Non-contiguous assignment**: You don't need to assign values in a continuous order.
  
#### Basic Syntax for Array Declaration:
```bash
# Declaring an array
array=(value1 value2 value3 ... valueN)
```
Example:
```bash
array=(23 45 34 1 2 3)
```

#### Accessing Array Elements:
1. **Access a single element**:
   - To access the 3rd element (remember it's zero-based, so 3rd value has index 2):
   ```bash
   echo ${array[2]}
   ```
   Output: `34`

2. **Access all elements**:
   - To print all values in the array:
   ```bash
   echo ${array[@]}
   ```
   Output: `23 45 34 1 2 3`

3. **Get the number of elements**:
   - To find out how many elements are in the array:
   ```bash
   echo ${#array[@]}
   ```
   Output: `6`

This way, Shell allows you to easily store and manipulate multiple values using arrays!
