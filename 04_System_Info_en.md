# System Information

## System

| Command | Description |
|---------|-------------|
| `uname -a` | Full system info |
| `uname -r` | Kernel version |
| `hostnamectl` | Hostname and OS |
| `lsb_release -a` | Distro info |
| `neofetch` | Beautiful system info |
| `uptime` | Uptime and load |
| `date` | Current date and time |
| `timedatectl` | Time and timezone |

## Hardware

| Command | Description |
|---------|-------------|
| `lscpu` | CPU info |
| `lscpu \| grep "Model name"` | CPU model |
| `free -h` | RAM usage |
| `lspci` | All PCI devices |
| `lspci \| grep VGA` | Graphics card |
| `lsusb` | USB devices |
| `lsblk` | Block devices |
| `sudo dmidecode` | Detailed hardware info |

## Disks and Memory

| Command | Description |
|---------|-------------|
| `df -h` | Disk usage |
| `du -sh /path` | Directory size |
| `fdisk -l` | Partition table |
| `lsblk -f` | Filesystems |

## Processes and Boot

| Command | Description |
|---------|-------------|
| `top` | Process monitor |
| `htop` | Better top |
| `ps aux` | All running processes |
| `journalctl -b` | Current boot logs |
| `dmesg` | Kernel messages |
| `systemctl list-units` | Service status |

## Temperature

```bash
# If lm_sensors is installed
sudo pacman -S lm_sensors
sudo sensors-detect
sensors

# For SSD
sudo pacman -S smartmontools
sudo smartctl -a /dev/sda
```

## Quick Reference

```bash
# Quick system info
neofetch

# RAM usage
free -h

# Disk space
df -h

# Hardware
lscpu && lspci && lsusb

# System load
uptime && top -bn1 | head -5
```
