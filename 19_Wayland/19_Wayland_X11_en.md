# Wayland and X11

## Which Protocol is Used

```bash
# Check
echo $XDG_SESSION_TYPE

# Wayland
wayland

# X11
x11
```

## Wayland

### Compositors

| Compositor | Description |
|------------|-------------|
| `sway` | i3 for Wayland |
| `hyprland` | Modern compositor |
| `kwin_wayland` | KDE |
| `mutter` | GNOME |

### Install sway

```bash
sudo pacman -S sway waybar wofi wl-clipboard grim slurp
```

### sway Config

File `~/.config/sway/config`:

```
# Modifier
set $mod Mod4

# Launch terminal
bindsym $mod+Return exec alacritty

# Close window
bindsym $mod+Shift+q kill

# Switch focus
bindsym $mod+Left focus left
bindsym $mod+Right focus right
bindsym $mod+Up focus up
bindsym $mod+Down focus down

# Launch
bindsym $mod+d exec wofi --show drun
```

### Utilities

```bash
# Screenshot
grim -g "$(slurp)" screenshot.png

# Clipboard
wl-copy "text"
wl-paste

# Monitors
swaymsg -t get_outputs
```

## X11

### Configuration

```bash
# Xorg config directory
/etc/X11/xorg.conf.d/

# Generate config
sudo Xorg -configure
```

### Resolution Setup

```bash
# View resolution
xrandr

# Set resolution
xrandr --output DP-1 --mode 1920x1080

# Refresh rate
xrandr --output DP-1 --mode 1920x1080 --rate 144
```

### xinit

```bash
# Start X
startx

# Config ~/.xinitrc
exec sway
# or
exec i3
```

## Clipboard

```bash
# Wayland
wl-copy "text"
wl-paste

# X11
xclip -selection clipboard
xsel --clipboard

# Universal
sudo pacman -S xclip
echo "text" | xclip -selection clipboard
```

## Compatibility Mode

```bash
# Run X apps in Wayland
QT_QPA_PLATFORM=xcb program

# Via XWayland (automatic)
# Most apps work
```

## Quick Reference

```bash
# Check protocol
echo $XDG_SESSION_TYPE

# Wayland screenshot
grim -g "$(slurp)" screen.png

# X11 resolution
xrandr

# Clipboard
wl-copy "hello"
wl-paste
```
