# Package Management (pacman — Arch Linux)

## Basic Commands

| Command | Description |
|---------|-------------|
| `sudo pacman -Syu` | Update all packages |
| `sudo pacman -Syyu` | Force update repos and packages |
| `sudo pacman -S name` | Install package |
| `sudo pacman -R name` | Remove package |
| `sudo pacman -Rs name` | Remove package and dependencies |
| `sudo pacman -Rns name` | Remove package, dependencies and configs |
| `sudo pacman -Sc` | Clean package cache |
| `sudo pacman -Scc` | Fully clean cache |

## Search

| Command | Description |
|---------|-------------|
| `pacman -Ss keyword` | Search packages by keyword |
| `pacman -Qs keyword` | Search among installed |
| `pacman -Qi name` | Info about installed package |
| `pacman -Ql name` | List package files |
| `pacman -Qo /path/file` | Which package owns file |
| `pacman -Qdt` | Orphaned packages |

## Package Groups

```bash
# Install group
sudo pacman -S gnome          # GNOME desktop
sudo pacman -S base-devel     # build tools
sudo pacman -S xorg           # X Window System

# View group packages
pacman -Sg gnome
```

## AUR (Arch User Repository)

### Install AUR helper

```bash
# yay (recommended)
sudo pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si

# paru
git clone https://aur.archlinux.org/paru.git
cd paru
makepkg -si
```

### yay/paru Commands

| Command | Description |
|---------|-------------|
| `yay -S name` | Install from AUR |
| `yay -R name` | Remove package |
| `yay -Syu` | Update everything (including AUR) |
| `yay -Ss keyword` | Search in AUR |
| `yay -Qi name` | Package info |

## Useful Packages

```bash
# System
sudo pacman -S htop tree neofetch unzip

# Network
sudo pacman -S networkmanager network-manager-applet

# Multimedia
sudo pacman -S vlc mpv ffmpeg

# Development
sudo pacman -S git nodejs npm python

# Fonts
sudo pacman -S ttf-liberation ttf-dejavu noto-fonts
```

## Quick Reference

```bash
# Full system update
sudo pacman -Syu

# Install package
sudo pacman -S name

# Remove with dependencies
sudo pacman -Rns name

# Clean cache
sudo pacman -Sc

# View disk usage
pacman -Qi | grep Size
```
