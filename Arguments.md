## Day 03. Script Arguments in Bash

In Bash scripting, you can pass arguments to a script at runtime. These arguments can be used to make scripts more dynamic and versatile. Here's a step-by-step guide, from the basics to more advanced concepts.

---

### 1. **Basic Script Arguments**
Bash allows you to pass arguments to your script when you run it from the command line.

#### Syntax:
```bash
./script.sh arg1 arg2 arg3
```

#### Example:
Create a script `example.sh`:
```bash
#!/bin/bash
echo "First argument: $1"
echo "Second argument: $2"
echo "Third argument: $3"
```

Run the script:
```bash
./example.sh hello world 123
```

#### Output:
```
First argument: hello
Second argument: world
Third argument: 123
```

- `$1`, `$2`, `$3`, etc., represent the positional arguments passed to the script.

---

### 2. **Accessing All Arguments**
You can access all arguments passed to a script using special variables:

- **$@**: Represents all arguments as a list.
- **$#**: The number of arguments passed to the script.

#### Example:
```bash
#!/bin/bash
echo "All arguments: $@"
echo "Number of arguments: $#"
```

If you run:
```bash
./example.sh hello world 123
```

#### Output:
```
All arguments: hello world 123
Number of arguments: 3
```

---

### 3. **Looping Through Arguments**
You can loop through all the arguments using a `for` loop.

#### Example:
```bash
#!/bin/bash
for arg in "$@"; do
  echo "Argument: $arg"
done
```

If you run:
```bash
./example.sh hello world 123
```

#### Output:
```
Argument: hello
Argument: world
Argument: 123
```

---

### 4. **Using Flags and Options**
You can pass flags (like `-a` or `--help`) to scripts, which is common in command-line tools.

#### Example:
```bash
#!/bin/bash
while getopts ":a:b:c:" opt; do
  case $opt in
    a) echo "Option A, argument: $OPTARG";;
    b) echo "Option B, argument: $OPTARG";;
    c) echo "Option C, argument: $OPTARG";;
    \?) echo "Invalid option: -$OPTARG" >&2;;
  esac
done
```

Run the script with flags:
```bash
./example.sh -a 10 -b 20 -c 30
```

#### Output:
```
Option A, argument: 10
Option B, argument: 20
Option C, argument: 30
```

- **`getopts`** is used to parse command-line options.
- **`$OPTARG`** stores the argument passed to an option.

---

### 5. **Default Values for Arguments**
You can set default values for arguments if they are not provided.

#### Example:
```bash
#!/bin/bash
arg1=${1:-"default1"}
arg2=${2:-"default2"}

echo "First argument: $arg1"
echo "Second argument: $arg2"
```

Run without passing arguments:
```bash
./example.sh
```

#### Output:
```
First argument: default1
Second argument: default2
```

- The syntax `${VAR:-default}` assigns `default` if `VAR` is not set.

---

### 6. **Shift Command**
The `shift` command is used to move positional arguments to the left. This is useful when you need to process each argument one by one.

#### Example:
```bash
#!/bin/bash
while [[ $# -gt 0 ]]; do
  echo "Argument: $1"
  shift  # Moves all arguments to the left, $2 becomes $1, etc.
done
```

Run the script:
```bash
./example.sh hello world 123
```

#### Output:
```
Argument: hello
Argument: world
Argument: 123
```

---

### 7. **Advanced Parsing with Flags**
You can use `getopts` to handle more complex argument parsing with both short and long flags.

#### Example:
```bash
#!/bin/bash
while [[ "$#" -gt 0 ]]; do
  case $1 in
    -a|--arg1) echo "Arg1 passed: $2"; shift 2;;
    -b|--arg2) echo "Arg2 passed: $2"; shift 2;;
    --flag) echo "Flag passed"; shift;;
    *) echo "Unknown option: $1"; shift;;
  esac
done
```

Run the script:
```bash
./example.sh -a 100 --arg2 200 --flag
```

#### Output:
```
Arg1 passed: 100
Arg2 passed: 200
Flag passed
```

- This method handles both short (`-a`) and long (`--arg1`) options.

---

### 8. **Error Handling with Arguments**
You can handle errors in argument parsing by checking conditions.

#### Example:
```bash
#!/bin/bash
if [[ $# -lt 2 ]]; then
  echo "Error: Not enough arguments."
  exit 1
fi

echo "First argument: $1"
echo "Second argument: $2"
```

Run the script without enough arguments:
```bash
./example.sh hello
```

#### Output:
```
Error: Not enough arguments.
```

---

