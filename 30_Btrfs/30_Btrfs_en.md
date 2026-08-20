# Btrfs and Snapshots

## Btrfs

### Create Filesystem

```bash
# Create
sudo mkfs.btrfs /dev/sdXN

# Mount
sudo mount /dev/sdXN /mnt

# In fstab
UUID=xxxx  /mnt  btrfs  defaults,compress=zstd  0  0
```

### Subvolumes

```bash
# Create subvolume
sudo btrfs subvolume create /mnt/@home

# List subvolumes
sudo btrfs subvolume list /mnt

# Delete subvolume
sudo btrfs subvolume delete /mnt/@home
```

## Snapshots

### Create

```bash
# Full snapshot
sudo btrfs subvolume snapshot /mnt/@home /mnt/@home_backup

# Read-only snapshot
sudo btrfs subvolume snapshot -r /mnt/@home /mnt/@home_readonly
```

### Management

```bash
# List snapshots
sudo btrfs subvolume list /mnt

# Restore
sudo btrfs subvolume delete /mnt/@home
sudo btrfs subvolume snapshot /mnt/@home_backup /mnt/@home

# Mount snapshot
sudo mount -o subvol=@home_backup /dev/sdXN /mnt/backup
```

## Timeshift

### Installation

```bash
sudo pacman -S timeshift
```

### Usage

```bash
# Launch
sudo timeshift-gtk

# Or CLI
sudo timeshift --create --comments "Before update"
sudo timeshift --list
sudo timeshift --restore
```

### Automatic Snapshots

```bash
# Add to crontab
sudo crontab -e

# Daily at 3:00
0 3 * * * timeshift --create --comments "Daily"
```

## Compression

| Algorithm | Description |
|-----------|-------------|
| `zstd` | Fast, good ratio |
| `lzo` | Fast, poor ratio |
| `gzip` | Medium |

```bash
# Mount with compression
sudo mount -o compress=zstd /dev/sdXN /mnt
```

## Quick Reference

```bash
# Create snapshot
sudo btrfs subvolume snapshot /mnt/@home /mnt/@backup

# List snapshots
sudo btrfs subvolume list /mnt

# Timeshift: create
sudo timeshift --create --comments "before update"

# Timeshift: restore
sudo timeshift --restore
```
