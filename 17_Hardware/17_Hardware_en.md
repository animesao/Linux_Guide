# Hardware and Drivers

## Hardware Information

| Command | Description |
|---------|-------------|
| `lscpu` | CPU info |
| `lspci` | PCI devices |
| `lsusb` | USB devices |
| `lsblk` | Block devices |
| `lshw` | Detailed info |
| `sudo dmidecode` | BIOS info |
| `inxi -Fxxxz` | Comprehensive info |

## CPU

```bash
# Model and cores
lscpu | grep "Model name"
lscpu | grep "CPU(s):"

# Frequency
sudo pacman -S cpupower
cpupower frequency-info

# Temperature
sudo pacman -S lm_sensors
sensors
```

## Graphics Card

```bash
# Information
lspci | grep -i vga
lspci | grep -i nvidia
lspci | grep -i amd

# NVIDIA (proprietary drivers)
sudo pacman -S nvidia nvidia-utils

# AMD (open source)
sudo pacman -S mesa vulkan-radeon

# Intel
sudo pacman -S mesa vulkan-intel

# Check driver
lsmod | grep nvidia
lsmod | grep amdgpu
```

## Sound

```bash
# PulseAudio
sudo pacman -S pulseaudio pulseaudio-alsa
pactl list sinks

# PipeWire (modern)
sudo pacman -S pipewire pipewire-pulse wireplumber

# ALSA
aplay -l
arecord -l
```

## Printers

```bash
# CUPS
sudo pacman -S cups
sudo systemctl enable --now cups

# Add printer
sudo lpadmin -p printer -E -v socket://192.168.1.100 -m everywhere

# List printers
lpstat -p
```

## Bluetooth

```bash
# Installation
sudo pacman -S bluez bluez-utils
sudo systemctl enable --now bluetooth

# Management
bluetoothctl
> power on
> scan on
> pair XX:XX:XX:XX:XX:XX
> connect XX:XX:XX:XX:XX:XX

# Paired devices
bluetoothctl paired-devices
```

## Drivers

```bash
# View unloaded modules
lspci -k

# Load module
sudo modprobe module_name

# Autoload module
echo "module_name" | sudo tee /etc/modules-load.d/module.conf

# Module parameters
echo "options module_name option=value" | sudo tee /etc/modprobe.d/module.conf
```

## Quick Reference

```bash
# All hardware info
inxi -Fxxxz

# Graphics card
lspci | grep VGA

# USB devices
lsusb

# Sound
pactl list sinks short

# Bluetooth
bluetoothctl devices
```
