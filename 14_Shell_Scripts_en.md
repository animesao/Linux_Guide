# Shell Scripts

## Script Structure

```bash
#!/bin/bash

# Comment

echo "Hello, World!"
```

## Variables

```bash
# Declaration
name="Linux"
age=25

# Usage
echo "OS: $name"
echo "Age: ${age}"

# Read input
read -p "Enter name: " username
echo "Hello, $username"

# System variables
echo $HOME
echo $USER
echo $PWD
echo $PATH
```

## Arithmetic

```bash
a=10
b=3

echo $((a + b))     # 13
echo $((a - b))     # 7
echo $((a * b))     # 30
echo $((a / b))     # 3
echo $((a % b))     # 1
echo $((a ** 2))    # 100

# More complex calculations
echo "scale=2; 10/3" | bc
```

## Conditions

```bash
# if/elif/else
if [ "$a" -gt "$b" ]; then
    echo "a is greater"
elif [ "$a" -lt "$b" ]; then
    echo "a is less"
else
    echo "equal"
fi

# String comparison
if [ "$str1" = "$str2" ]; then
    echo "equal"
fi

# File check
if [ -f "file.txt" ]; then
    echo "file exists"
fi

if [ -d "dir" ]; then
    echo "directory exists"
fi

# Command check
if command -v git &> /dev/null; then
    echo "git is installed"
fi
```

### Comparison Operators

| Operator | Description |
|----------|-------------|
| `-eq` | Equal |
| `-ne` | Not equal |
| `-gt` | Greater than |
| `-lt` | Less than |
| `-ge` | Greater or equal |
| `-le` | Less or equal |
| `=` | Strings equal |
| `!=` | Strings not equal |
| `-f` | File exists |
| `-d` | Directory exists |
| `-z` | String is empty |
| `-n` | String is not empty |

## Loops

```bash
# for
for i in 1 2 3 4 5; do
    echo "Number: $i"
done

# for with range
for i in {1..10}; do
    echo $i
done

# for (C-style)
for ((i=0; i<10; i++)); do
    echo $i
done

# while
while [ condition ]; do
    echo "loop"
    sleep 1
done

# until
until [ condition ]; do
    echo "waiting"
    sleep 1
done

# Infinite loop
while true; do
    echo " forever"
    sleep 1
done
```

## Functions

```bash
# Simple function
greet() {
    echo "Hello, $1!"
}

# Call
greet "World"

# Function with return
add() {
    echo $(( $1 + $2 ))
}

result=$(add 5 3)
echo "Sum: $result"
```

## Arguments

```bash
#!/bin/bash

echo "Script name: $0"
echo "Arg 1: $1"
echo "Arg 2: $2"
echo "All args: $@"
echo "Number of args: $#"
```

## Error Handling

```bash
#!/bin/bash

set -e  # Stop on error
set -u  # Error on undefined variable
set -o pipefail  # Error in pipe

# Check command
if ! command -v docker &> /dev/null; then
    echo "Docker not installed"
    exit 1
fi
```

## Useful Patterns

```bash
# Check if file exists
[ -f "$file" ] && echo "exists" || echo "not found"

# Run with sudo if needed
[ $EUID -ne 0 ] && exec sudo "$0" "$@"

# Change to script directory
cd "$(dirname "$0")"

# Measure execution time
time {
    # commands
}
```

## Quick Reference

```bash
#!/bin/bash
set -euo pipefail

NAME="Linux"
echo "Hello, $NAME"

for i in {1..5}; do
    echo "Count: $i"
done

if [ -f "/etc/passwd" ]; then
    echo "File exists"
fi
```
