# Linux Basic Commands

## Navigation

| Command | Description |
|---------|-------------|
| `pwd` | Print current directory |
| `ls` | List files |
| `ls -la` | List all files (including hidden) with details |
| `cd /path` | Change to directory |
| `cd ..` | Go up one level |
| `cd ~` | Go to home directory |
| `cd -` | Return to previous directory |

## File Operations

| Command | Description |
|---------|-------------|
| `touch file` | Create empty file |
| `mkdir dir` | Create directory |
| `mkdir -p a/b/c` | Create nested directories |
| `cp file1 file2` | Copy file |
| `cp -r dir1 dir2` | Copy directory recursively |
| `mv file1 file2` | Rename/move file |
| `rm file` | Delete file |
| `rm -r dir` | Delete directory |
| `rm -rf dir` | Force delete directory |
| `ln -s target link` | Create symbolic link |

## Viewing Files

| Command | Description |
|---------|-------------|
| `cat file` | Display file contents |
| `less file` | View file with scrolling |
| `head -n 20 file` | First 20 lines |
| `tail -n 20 file` | Last 20 lines |
| `tail -f file` | Follow file in real-time |
| `wc -l file` | Count lines |
| `file file` | Determine file type |

## Permissions

| Command | Description |
|---------|-------------|
| `chmod 755 file` | Set permissions (rwxr-xr-x) |
| `chmod +x file` | Make file executable |
| `chmod -R 755 dir` | Recursively change permissions |
| `chown user:group file` | Change owner |

### Permission Numbers

| Number | Permissions |
|--------|-------------|
| 7 | rwx (read + write + execute) |
| 6 | rw- (read + write) |
| 5 | r-x (read + execute) |
| 4 | r-- (read only) |
| 0 | --- (no permissions) |

Format: `Owner / Group / Others`

## Finding Files

| Command | Description |
|---------|-------------|
| `find / -name "*.txt"` | Find files by name |
| `find / -size +100M` | Files larger than 100MB |
| `find / -mtime -7` | Modified in last 7 days |
| `which command` | Path to executable |
| `whereis command` | Where command is located |

## Editing

| Command | Description |
|---------|-------------|
| `nano file` | Open in nano (simple editor) |
| `vim file` | Open in vim |
| `echo "text" > file` | Write text to file (overwrite) |
| `echo "text" >> file` | Append text to file |

## Bash Shortcuts

| Shortcut | Description |
|----------|-------------|
| `Ctrl+C` | Abort current command |
| `Ctrl+D` | Exit terminal |
| `Ctrl+R` | Search command history |
| `Ctrl+A` | Go to start of line |
| `Ctrl+E` | Go to end of line |
| `Ctrl+L` | Clear screen |
| `Tab` | Autocomplete |
| `↑ / ↓` | Navigate history |

## Quick Reference

```bash
# Copy file to home
cp /etc/config.conf ~/

# Find all .conf files
find /etc -name "*.conf"

# Last 50 lines of a log
tail -n 50 /var/log/pacman.log

# Delete all .tmp files
find /tmp -name "*.tmp" -delete
```
