# Flatpak and Snap

## Flatpak

### Installation

```bash
sudo pacman -S flatpak
```

### Commands

| Command | Description |
|---------|-------------|
| `flatpak install app` | Install app |
| `flatpak uninstall app` | Remove |
| `flatpak list` | List installed |
| `flatpak update` | Update all |
| `flatpak search keyword` | Find app |
| `flatpak run app` | Run |
| `flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo` | Add Flathub |

### Examples

```bash
# Add Flathub
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo

# Install Firefox
flatpak install flathub org.mozilla.firefox

# Install VS Code
flatpak install flathub com.visualstudio.code

# Install Discord
flatpak install flathub com.discordapp.Discord

# Run
flatpak run org.mozilla.firefox

# Update all
flatpak update
```

### Cleanup

```bash
# Remove unused runtimes
flatpak uninstall --unused

# Repair cache
flatpak repair
```

## Snap

### Installation

```bash
# Install snapd
sudo pacman -S snapd

# Start
sudo systemctl enable --now snapd.socket

# Symlink
sudo ln -s /var/lib/snapd/snap /snap
```

### Commands

| Command | Description |
|---------|-------------|
| `sudo snap install app` | Install |
| `sudo snap remove app` | Remove |
| `snap list` | List |
| `sudo snap refresh` | Update |
| `snap find keyword` | Find |
| `snap run app` | Run |

### Examples

```bash
# Install Firefox
sudo snap install firefox

# Install VS Code
sudo snap install code --classic

# Install Telegram
sudo snap install telegram-desktop

# List
snap list

# Update all
sudo snap refresh
```

## Comparison

| Criterion | Flatpak | Snap |
|-----------|---------|------|
| Packages | Flathub | Snap Store |
| Size | Larger | Larger |
| Launch | Faster | Slower |
| Isolation | Yes | Yes |
| Auto-update | No | Yes |

## Quick Reference

```bash
# Flatpak: add Flathub
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo

# Flatpak: install
flatpak install flathub org.mozilla.firefox

# Snap: install
sudo snap install firefox

# Flatpak: update
flatpak update

# Snap: update
sudo snap refresh
```
