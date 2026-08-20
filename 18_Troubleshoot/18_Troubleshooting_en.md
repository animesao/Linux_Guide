# Troubleshooting

## Diagnostics

| Command | Description |
|---------|-------------|
| `dmesg` | Kernel messages |
| `journalctl -b -p err` | Boot errors |
| `systemctl --failed` | Failed services |
| `sudo fsck /dev/sdXN` | Check filesystem |
| `sudo smartctl -a /dev/sd` | Disk health |

## Common Problems

### System won't boot

```bash
# Live USB → chroot
sudo mount /dev/sdb2 /mnt
sudo mount /dev/sdb1 /mnt/boot
sudo arch-chroot /mnt

# Check fstab
cat /etc/fstab

# Rebuild initramfs
mkinitcpio -P

# Check bootloader
bootctl status
```

### Network problems

```bash
# Check interfaces
ip link

# Start NetworkManager
sudo systemctl start NetworkManager

# Check DNS
ping 8.8.8.8
nslookup google.com

# Restart network
sudo systemctl restart NetworkManager
```

### Package problems

```bash
# Dependency errors
sudo pacman -Syu

# Force update keys
sudo pacman -S archlinux-keyring

# Clean cache
sudo pacman -Sc

# Rebuild packages
sudo pacman -S $(pacman -Qnq)
```

### Disk problems

```bash
# Check space
df -h

# Check errors
sudo fsck /dev/sdXN

# SMART status
sudo smartctl -a /dev/sda

# Disk monitoring
sudo pacman -S smartmontools
sudo smartctl -t long /dev/sda
```

### Memory problems

```bash
# Check memory
sudo pacman -S memtest86+

# Run from BIOS or
sudo memtest

# Check swap
free -h
```

## Recovery

```bash
# Fix pacman
sudo pacman -Syyu

# Reinstall all packages
sudo pacman -S $(pacman -Qnq) --force

# Fix grub
sudo grub-install /dev/sda
sudo grub-mkconfig -o /boot/grub/grub.cfg

# Reset root password
# From recovery mode:
passwd root
```

## Useful Tools

```bash
# strace (system call tracing)
strace command

# ltrace (library call tracing)
ltrace command

# perf (performance)
sudo pacman -S perf
perf stat command

# valgrind (memory leaks)
valgrind ./program
```

## Quick Reference

```bash
# Last errors
journalctl -b -p err

# Failed services
systemctl --failed

# Check disk
sudo fsck /dev/sda2

# Check memory
free -h

# Check space
df -h
```
