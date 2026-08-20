# Disks and Mounting

## Disk Information

| Command | Description |
|---------|-------------|
| `lsblk` | Tree of all block devices |
| `lsblk -f` | With filesystems and UUID |
| `sudo fdisk -l` | Partition table |
| `sudo blkid` | UUID and type of all partitions |
| `sudo blkid /dev/sda1` | Info about specific partition |
| `df -h` | Disk usage |
| `du -sh /path` | Directory size |
| `du -sh *` | Size of each file/folder |

## Mounting

### Create mount point

```bash
sudo mkdir /mnt/name
```

### Mount

```bash
sudo mount /dev/sdXN /mnt/name
```

### By filesystem type

| Type | Command |
|------|---------|
| ext4 | `sudo mount /dev/sdXN /mnt/name` |
| NTFS | `sudo mount -t ntfs-3g /dev/sdXN /mnt/name` |
| exFAT | `sudo mount -t exfat /dev/sdXN /mnt/name` |
| FAT32 | `sudo mount -t vfat /dev/sdXN /mnt/name` |

### With options

```bash
# Mount with user permissions
sudo mount -t ntfs-3g -o uid=1000,gid=1000 /dev/sda3 /mnt/windows

# Mount read-only
sudo mount -o ro /dev/sda3 /mnt/windows

# Mount with encoding
sudo mount -t vfat -o iocharset=utf8 /dev/sda1 /mnt/efi
```

## Permanent Mounting (fstab)

### Get UUID

```bash
sudo blkid /dev/sdXN
```

### Entry format in /etc/fstab

```
UUID=xxxx-xxxx   /mnt/name   filesystem   options   dump   pass
```

### Examples

```
# NTFS Windows
UUID=2EE0C9C2E0C9910F   /mnt/windows   ntfs-3g   defaults,uid=1000,gid=1000   0   0

# ext4
UUID=xxxx-xxxx          /mnt/data      ext4      defaults                      0   2

# exFAT
UUID=xxxx-xxxx          /mnt/usb       exfat     defaults,uid=1000,gid=1000   0   0
```

### Verify fstab

```bash
sudo mount -a
```

## Unmounting

```bash
sudo umount /mnt/name
```

If disk is busy:

```bash
sudo umount -l /mnt/name    # lazy unmount
sudo umount -f /mnt/name    # force
```

## Creating Filesystems

```bash
# ext4
sudo mkfs.ext4 /dev/sdXN

# NTFS
sudo mkfs.ntfs /dev/sdXN

# exFAT
sudo mkfs.exfat /dev/sdXN

# FAT32
sudo mkfs.vfat -F 32 /dev/sdXN
```

## Partition Management

```bash
# Partition disk (interactive)
sudo fdisk /dev/sdX

# parted (more modern)
sudo parted /dev/sdX

# GParted (GUI)
sudo gparted
```

## Repair Partition

```bash
# Unmount
sudo umount /dev/sdXN

# Check for errors
sudo fsck /dev/sdXN

# Fix errors
sudo fsck -y /dev/sdXN
```

## SWAP

```bash
# Create swap file
sudo fallocate -l 4G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile

# Add to fstab for persistence
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab

# Check
free -h
```

## Quick Reference

```bash
# View all disks
lsblk -f

# Mount Windows
sudo mkdir -p /mnt/windows
sudo mount -t ntfs-3g /dev/sda3 /mnt/windows

# Check space
df -h

# Folder size
du -sh ~/Downloads
```
