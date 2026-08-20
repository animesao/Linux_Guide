# Archiving (zip)

## Installation

```bash
sudo pacman -S zip unzip
```

## Creating Archives

| Command | Description |
|---------|-------------|
| `zip archive.zip file` | Archive file |
| `zip archive.zip file1 file2` | Multiple files |
| `zip -r archive.zip dir/` | Archive directory |
| `zip -r archive.zip dir/ -x "*.log"` | Exclude files |
| `zip -e archive.zip file` | With password |

### Examples

```bash
# Archive one file
zip backup.zip config.txt

# Archive multiple files
zip backup.zip file1.txt file2.txt file3.txt

# Archive entire folder
zip -r project.zip myproject/

# Archive with exclusions
zip -r archive.zip folder/ -x "*.tmp" -x "*.cache"

# Archive with password
zip -e secret.zip private.txt
```

## Viewing Archives

```bash
# List files in archive
unzip -l archive.zip

# Test archive
zip -T archive.zip
```

## Extraction

| Command | Description |
|---------|-------------|
| `unzip archive.zip` | Extract to current directory |
| `unzip archive.zip -d /path` | Extract to specific directory |
| `unzip -o archive.zip` | Overwrite without asking |
| `unzip -n archive.zip` | Don't overwrite existing |
| `unzip -l archive.zip` | View contents |
| `unzip -t archive.zip` | Test archive |

### Examples

```bash
# Extract to current folder
unzip archive.zip

# Extract to specific folder
unzip archive.zip -d /home/user/extracted/

# Overwrite all files
unzip -o archive.zip

# Extract only specific file
unzip archive.zip file.txt

# Extract with wildcard
unzip archive.zip "*.txt"
```

## Updating Archives

```bash
# Add file to archive
zip archive.zip newfile.txt

# Update file in archive
zip -u archive.zip file.txt

# Delete file from archive
zip -d archive.zip file.txt
```

## Other Formats

### tar.gz

```bash
# Create
tar -czf archive.tar.gz dir/

# Extract
tar -xzf archive.tar.gz

# View
tar -tzf archive.tar.gz
```

### tar.bz2

```bash
# Create
tar -cjf archive.tar.bz2 dir/

# Extract
tar -xjf archive.tar.bz2
```

### tar.xz

```bash
# Create
tar -cJf archive.tar.xz dir/

# Extract
tar -xJf archive.tar.xz
```

### 7z

```bash
# Install
sudo pacman -S p7zip

# Create
7z a archive.7z dir/

# Extract
7z x archive.7z

# View
7z l archive.7z
```

## Quick Reference

```bash
# Quickly archive folder
zip -r backup.zip myproject/

# Quickly extract
unzip archive.zip

# Extract to folder
unzip archive.zip -d /tmp/extracted/

# View contents
unzip -l archive.zip
```
