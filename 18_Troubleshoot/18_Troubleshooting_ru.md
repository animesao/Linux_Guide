# Проблемы и отладка

## Диагностика

| Команда | Описание |
|---------|----------|
| `dmesg` | Сообщения ядра |
| `journalctl -b -p err` | Ошибки загрузки |
| `systemctl --failed` | Упавшие сервисы |
| `sudo fsck /dev/sdXN` | Проверка файловой системы |
| `sudo smartctl -a /dev/sd` | Здоровье диска |

## Распространённые проблемы

### Система не загружается

```bash
# Live USB → chroot
sudo mount /dev/sdb2 /mnt
sudo mount /dev/sdb1 /mnt/boot
sudo arch-chroot /mnt

# Проверить fstab
cat /etc/fstab

# Пересобрать initramfs
mkinitcpio -P

# Проверить bootloader
bootctl status
```

### Проблемы с сетью

```bash
# Проверить интерфейсы
ip link

# Запустить NetworkManager
sudo systemctl start NetworkManager

# Проверить DNS
ping 8.8.8.8
nslookup google.com

# Перезапустить сеть
sudo systemctl restart NetworkManager
```

### Проблемы с пакетами

```bash
# Ошибки зависимостей
sudo pacman -Syu

# Принудительно обновить ключи
sudo pacman -S archlinux-keyring

# Очистить кэш
sudo pacman -Sc

# Пересобрать пакеты
sudo pacman -S $(pacman -Qnq)
```

### Проблемы с диском

```bash
# Проверить место
df -h

# Проверить ошибки
sudo fsck /dev/sdXN

# SMART статус
sudo smartctl -a /dev/sda

# Мониторинг диска
sudo pacman -S smartmontools
sudo smartctl -t long /dev/sda
```

### Проблемы с памятью

```bash
# Проверить память
sudo pacman -S memtest86+

# Запустить при загрузке (из BIOS)
# или
sudo memtest

# Проверить swap
free -h
```

## Восстановление

```bash
# Восстановить pacman
sudo pacman -Syyu

# Переустановить все пакеты
sudo pacman -S $(pacman -Qnq) --force

# Восстановить grub
sudo grub-install /dev/sda
sudo grub-mkconfig -o /boot/grub/grub.cfg

# Сбросить пароль root
# Из recovery mode:
passwd root
```

## Полезные инструменты

```bash
# strace (трассировка системных вызовов)
strace command

# ltrace (трассировка библиотечных вызовов)
ltrace command

# perf (производительность)
sudo pacman -S perf
perf stat command

# valgrind (утечки памяти)
valgrind ./program
```

## Шпаргалка

```bash
# Последние ошибки
journalctl -b -p err

# Упавшие сервисы
systemctl --failed

# Проверить диск
sudo fsck /dev/sda2

# Проверить память
free -h

# Проверить место
df -h
```
