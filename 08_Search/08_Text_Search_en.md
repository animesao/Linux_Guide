# Text and Search

## Search in Files

| Command | Description |
|---------|-------------|
| `grep "text" file` | Find text in file |
| `grep -r "text" /path` | Recursive search |
| `grep -i "text" file` | Case-insensitive search |
| `grep -n "text" file` | Show line numbers |
| `grep -c "text" file` | Count matches |
| `grep -v "text" file` | Exclude matches |
| `grep -A 3 "text" file` | 3 lines after match |
| `grep -B 3 "text" file` | 3 lines before match |

## Find Command

```bash
# Find files by name
find /path -name "*.txt"

# Find directories
find /path -type d -name "name"

# Find by size
find /path -size +100M

# Find by date
find /path -mtime -7

# Find and execute command
find /path -name "*.log" -exec rm {} \;
```

## Regular Expressions

| Pattern | Description |
|---------|-------------|
| `.` | Any character |
| `*` | 0 or more |
| `+` | 1 or more |
| `?` | 0 or 1 |
| `[abc]` | One of characters |
| `[^abc]` | Not one of characters |
| `^` | Start of line |
| `$` | End of line |
| `\b` | Word boundary |

## sed (text editing)

```bash
# Replace text
sed 's/old/new/g' file

# Replace in file (in-place)
sed -i 's/old/new/g' file

# Delete line
sed '/pattern/d' file

# Insert line
sed '3i\new line' file

# Show lines 5-10
sed -n '5,10p' file
```

## awk (text processing)

```bash
# Print first column
awk '{print $1}' file

# Print columns
awk '{print $1, $3}' file

# With delimiter
awk -F: '{print $1}' /etc/passwd

# Condition
awk '$3 > 100' file

# Sum
awk '{sum += $1} END {print sum}' file
```

## sort and uniq

```bash
# Sort
sort file

# Sort numbers
sort -n file

# Unique lines
sort file | uniq

# Count repeats
sort file | uniq -c

# Sort by count
sort file | uniq -c | sort -rn
```

## wc (counting)

```bash
# Lines
wc -l file

# Words
wc -w file

# Characters
wc -c file
```

## Quick Reference

```bash
# Find IP addresses in log
grep -oE "[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+" log.txt

# Replace text in file
sed -i 's/old_text/new_text/g' file.txt

# Show unique IPs
grep -oE "[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+" log.txt | sort | uniq

# Count lines
wc -l file.txt

# Find files larger than 100MB
find / -size +100M -type f
```
