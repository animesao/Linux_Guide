# Gaming on Linux

## Steam

### Installation

```bash
# Enable multilib
sudo nano /etc/pacman.conf
[multilib]
Include = /etc/pacman.d/mirrorlist

sudo pacman -Syu

# Install Steam
sudo pacman -S steam
```

### Setup

1. Open Steam
2. Settings → Compatibility
3. Enable "Enable Steam Play for all titles"
4. Select Proton

## Proton

### Versions

| Version | Description |
|---------|-------------|
| Proton Experimental | Newest |
| Proton 8.0 | Stable |
| Proton GE | Modified (best compatibility) |

### Install Proton GE

```bash
# Install protonup-qt
sudo pacman -S protonup-qt

# Or via yay
yay -S protonup-qt-bin

# Run and select Proton GE
```

## Lutris

### Installation

```bash
sudo pacman -S lutris
```

### Usage

1. Open Lutris
2. "+" → Import game
3. Select installer (exe/setup)
4. Configure Proton/Wine

## Wine

### Installation

```bash
sudo pacman -S wine
```

### Run .exe

```bash
wine game.exe
```

### Configuration

```bash
# Wine configuration
winecfg

# Install libraries
winetricks
```

## Optimization

### Drivers

```bash
# NVIDIA
sudo pacman -S nvidia nvidia-utils lib32-nvidia-utils

# AMD
sudo pacman -S mesa vulkan-radeon lib32-vulkan-radeon

# Intel
sudo pacman -S mesa vulkan-intel lib32-vulkan-intel
```

### Monitoring

```bash
# MangoHud (FPS, temperature)
sudo pacman -S mangohud

# Run with MangoHud
mangohud %command%

# In Steam: settings → compatibility → enter
MANGOHUD=1 %command%
```

### Gamemode

```bash
# Install
sudo pacman -S gamemode lib32-gamemode

# In Steam: settings → compatibility → enter
gamemoderun %command%
```

## Troubleshooting

```bash
# Install 32-bit libraries
sudo pacman -S lib32-mesa lib32-vulkan-radeon lib32-nvidia-utils

# Rebuild font cache
fc-cache -fv

# Check Vulkan
vulkaninfo
```

## Quick Reference

```bash
# Install Steam
sudo pacman -S steam

# Install Lutris
sudo pacman -S lutris

# MangoHud
sudo pacman -S mangohud

# Gamemode
sudo pacman -S gamemode
```
