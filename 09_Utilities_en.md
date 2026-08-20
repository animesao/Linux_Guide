# Useful Utilities

## Archives

| Command | Description |
|---------|-------------|
| `tar -czf archive.tar.gz dir/` | Create .tar.gz |
| `tar -xzf archive.tar.gz` | Extract .tar.gz |
| `tar -cjf archive.tar.bz2 dir/` | Create .tar.bz2 |
| `tar -xjf archive.tar.bz2` | Extract .tar.bz2 |
| `unzip archive.zip` | Extract .zip |
| `zip -r archive.zip dir/` | Create .zip |

## Downloading

| Command | Description |
|---------|-------------|
| `wget url` | Download file |
| `wget -c url` | Resume download |
| `curl -O url` | Download file |
| `curl url -o file` | Download with name |

## Conversion

```bash
# Text encoding
iconv -f FROM -t TO file

# Video encoding
ffmpeg -i input.mp4 output.avi

# Audio encoding
ffmpeg -i input.mp3 output.flac

# Resize image
convert input.jpg -resize 800x600 output.jpg
```

## Monitoring

| Command | Description |
|---------|-------------|
| `htop` | Process monitor |
| `btop` | Beautiful monitor |
| `iotop` | Disk monitor |
| `nload` | Network monitor |
| `glances` | All-in-one |
| `dstat` | System stats |

## Comparing Files

```bash
# Compare two files
diff file1 file2

# Side-by-side diff
diff -y file1 file2

# Ignore whitespace
diff -b file1 file2

# Compare directories
diff -r dir1 dir2

# Compare files (vimdiff)
vimdiff file1 file2
```

## Backups

```bash
# Rsync (backup)
rsync -av source/ dest/

# From remote server
rsync -avz user@host:/path/ /local/path/

# With exclusions
rsync -av --exclude='*.log' source/ dest/
```

## Screenshots

```bash
# Screenshot (scrot needed)
scrot screenshot.png

# With delay
scrot -d 5 screenshot.png

# Screen area
scrot -s screenshot.png

# flameshot (GUI)
flameshot gui
```

## Terminal

| Command | Description |
|---------|-------------|
| `tmux` | Terminal multiplexer |
| `screen` | Terminal emulator |
| `script session.log` | Record session |
| `clear` | Clear screen |

### tmux basics

```bash
# Create session
tmux

# Detach
Ctrl+B, D

# Attach
tmux attach

# New window
Ctrl+B, C

# Switch
Ctrl+B, 0-9
```

## Autocompletion

```bash
# Enable autocompletion
source /usr/share/bash-completion/bash_completion

# Add to .bashrc
echo 'source /usr/share/bash-completion/bash_completion' >> ~/.bashrc
```

## Quick Reference

```bash
# Create backup
tar -czf backup.tar.gz /important/dir/

# Download file
wget https://example.com/file.zip

# List archive contents
tar -tzf archive.tar.gz

# Extract archive
tar -xzf archive.tar.gz

# Record terminal session
script session.log
```
