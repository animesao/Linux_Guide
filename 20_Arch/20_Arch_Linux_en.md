# Arch Linux Specific

## mkinitcpio

| Command | Description |
|---------|-------------|
| `sudo mkinitcpio -P` | Rebuild all |
| `sudo mkinitcpio -g /boot/initramfs.img` | Build image |

### Config `/etc/mkinitcpio.conf`

```
MODULES=(i915 nvidia)      # Kernel modules
BINARIES=()                 # Binaries
FILES=()                    # Files
HOOKS=(base udev autodetect modconf kms keyboard keymap consolefont block filesystems fsck)
```

### HOOKS

| Hook | Description |
|------|-------------|
| `base` | Base system |
| `udev` | Device management |
| `autodetect` | Auto-detection |
| `kms` | Kernel Mode Setting |
| `keyboard` | Keyboard |
| `block` | Block devices |
| `filesystems` | Filesystems |
| `fsck` | Filesystem check |
| `encrypt` | LUKS encryption |
| `lvm2` | LVM |
| `plymouth` | Boot splash |

## Bootloader

### systemd-boot

```bash
# Install
sudo bootctl install

# Config /boot/loader/loader.conf
default arch.conf
timeout 3
console-mode max
editor no

# Config /boot/loader/entries/arch.conf
title Arch Linux
linux /vmlinuz-linux
initrd /initramfs-linux.img
options root=UUID=xxxx rw

# Update
sudo bootctl update
```

### GRUB

```bash
# Install
sudo pacman -S grub efibootmgr
sudo grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB
sudo grub-mkconfig -o /boot/grub/grub.cfg

# Update config
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

## AUR

### yay

```bash
# Install
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si

# Commands
yay -S package
yay -R package
yay -Syu
```

### paru

```bash
# Install
git clone https://aur.archlinux.org/paru.git
cd paru
makepkg -si
```

## pacman

### Config `/etc/pacman.conf`

```
# Colors
Color

# Parallel downloads
ParallelDownloads = 5

# Multilib (32-bit)
[multilib]
Include = /etc/pacman.d/mirrorlist
```

### Mirrorlist

```bash
# Mirror generator
sudo pacman -S reflector
sudo reflector --latest 10 --sort rate --save /etc/pacman.d/mirrorlist
```

## Boot

```bash
# initramfs
sudo mkinitcpio -P

# Kernel
sudo pacman -S linux linux-headers

# Update
sudo pacman -Syu
```

## Configuration

```bash
# /etc/fstab
# Disk mounting

# /etc/hostname
# Computer name

# /etc/hosts
# Local hosts

# /etc/locale.conf
LANG=en_US.UTF-8

# /etc/timezone
America/New_York

# sudoers
sudo visudo
```

## Quick Reference

```bash
# Rebuild initramfs
sudo mkinitcpio -P

# Install bootloader
sudo bootctl install

# Update system
sudo pacman -Syu

# Install AUR helper
git clone https://aur.archlinux.org/yay.git
cd yay && makepkg -si

# Update mirrors
sudo reflector --latest 10 --sort rate --save /etc/pacman.d/mirrorlist
```
