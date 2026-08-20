# Arch Linux Specific

## mkinitcpio

| Команда | Описание |
|---------|----------|
| `sudo mkinitcpio -P` | Пересобрать все |
| `sudo mkinitcpio -g /boot/initramfs.img` | Собрать образ |

### Конфиг `/etc/mkinitcpio.conf`

```
MODULES=(i915 nvidia)      # Модули ядра
BINARIES=()                 # Бинарники
FILES=()                    # Файлы
HOOKS=(base udev autodetect modconf kms keyboard keymap consolefont block filesystems fsck)
```

### HOOKS

| Hook | Описание |
|------|----------|
| `base` | Базовая система |
| `udev` | Управление устройствами |
| `autodetect` | Автоопределение |
| `kms` | Kernel Mode Setting |
| `keyboard` | Клавиатура |
| `block` | Блочные устройства |
| `filesystems` | Файловые системы |
| `fsck` | Проверка файловой системы |
| `encrypt` | Шифрование LUKS |
| `lvm2` | LVM |
| `plymouth` | Красивая загрузка |

## Bootloader

### systemd-boot

```bash
# Установить
sudo bootctl install

# Конфиг /boot/loader/loader.conf
default arch.conf
timeout 3
console-mode max
editor no

# Конфиг /boot/loader/entries/arch.conf
title Arch Linux
linux /vmlinuz-linux
initrd /initramfs-linux.img
options root=UUID=xxxx rw

# Обновить
sudo bootctl update
```

### GRUB

```bash
# Установить
sudo pacman -S grub efibootmgr
sudo grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB
sudo grub-mkconfig -o /boot/grub/grub.cfg

# Обновить конфиг
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

## AUR

### yay

```bash
# Установить
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si

# Команды
yay -S package
yay -R package
yay -Syu
```

### paru

```bash
# Установить
git clone https://aur.archlinux.org/paru.git
cd paru
makepkg -si
```

## pacman

### Конфиг `/etc/pacman.conf`

```
# Цвета
Color

# Параллельная загрузка
ParallelDownloads = 5

# Multilib (32-бит)
[multilib]
Include = /etc/pacman.d/mirrorlist
```

### Мirrorlist

```bash
# Генератор зеркал
sudo pacman -S reflector
sudo reflector --latest 10 --sort rate --save /etc/pacman.d/mirrorlist
```

## Нижняя загрузка

```bash
# initramfs
sudo mkinitcpio -P

# Ядро
sudo pacman -S linux linux-headers

# Обновление
sudo pacman -Syu
```

## Конфигурация

```bash
# /etc/fstab
# Монтирование дисков

# /etc/hostname
# Имя компьютера

# /etc/hosts
# Локальные хосты

# /etc/locale.conf
LANG=en_US.UTF-8

# /etc/timezone
America/New_York

# sudoers
sudo visudo
```

## Шпаргалка

```bash
# Пересобрать initramfs
sudo mkinitcpio -P

# Установить bootloader
sudo bootctl install

# Обновить систему
sudo pacman -Syu

# Установить AUR helper
git clone https://aur.archlinux.org/yay.git
cd yay && makepkg -si

# Обновить зеркала
sudo reflector --latest 10 --sort rate --save /etc/pacman.d/mirrorlist
```
