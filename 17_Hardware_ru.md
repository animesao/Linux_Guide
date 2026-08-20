# Железо и драйверы

## Информация о железе

| Команда | Описание |
|---------|----------|
| `lscpu` | Информация о CPU |
| `lspci` | PCI устройства |
| `lsusb` | USB устройства |
| `lsblk` | Блокочные устройства |
| `lshw` | Подробная информация |
| `sudo dmidecode` | Информация из BIOS |
| `inxi -Fxxxz` | Комплексная информация |

## CPU

```bash
# Модель и ядра
lscpu | grep "Model name"
lscpu | grep "CPU(s):"

# Частота
sudo pacman -S cpupower
cpupower frequency-info

# Температура
sudo pacman -S lm_sensors
sensors
```

## Видеокарта

```bash
# Информация
lspci | grep -i vga
lspci | grep -i nvidia
lspci | grep -i amd

# NVIDIA (proprietary drivers)
sudo pacman -S nvidia nvidia-utils

# AMD (open source)
sudo pacman -S mesa vulkan-radeon

# Intel
sudo pacman -S mesa vulkan-intel

# Проверить драйвер
lsmod | grep nvidia
lsmod | grep amdgpu
```

## Звук

```bash
# PulseAudio
sudo pacman -S pulseaudio pulseaudio-alsa
pactl list sinks

# PipeWire (современный)
sudo pacman -S pipewire pipewire-pulse wireplumber

# ALSA
aplay -l
arecord -l
```

## Принтеры

```bash
# CUPS
sudo pacman -S cups
sudo systemctl enable --now cups

# Добавить принтер
sudo lpadmin -p printer -E -v socket://192.168.1.100 -m everywhere

# Список принтеров
lpstat -p
```

## Bluetooth

```bash
# Установка
sudo pacman -S bluez bluez-utils
sudo systemctl enable --now bluetooth

# Управление
bluetoothctl
> power on
> scan on
> pair XX:XX:XX:XX:XX:XX
> connect XX:XX:XX:XX:XX:XX

# Пaired устройства
bluetoothctl paired-devices
```

## Драйверы

```bash
# Посмотреть незагруженные модули
lspci -k

# Загрузить модуль
sudo modprobe module_name

# Автозагрузка модуля
echo "module_name" | sudo tee /etc/modules-load.d/module.conf

# Параметры модуля
echo "options module_name option=value" | sudo tee /etc/modprobe.d/module.conf
```

## Шпаргалка

```bash
# Всё о железе
inxi -Fxxxz

# Видеокарта
lspci | grep VGA

# USB устройства
lsusb

# Звук
pactl list sinks short

# Bluetooth
bluetoothctl devices
```
