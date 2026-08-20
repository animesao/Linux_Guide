# Диски и монтирование

## Информация о дисках

| Команда | Описание |
|---------|----------|
| `lsblk` | Дерево всех блочных устройств |
| `lsblk -f` | С файловыми системами и UUID |
| `sudo fdisk -l` | Таблица разделов |
| `sudo blkid` | UUID и тип всех разделов |
| `sudo blkid /dev/sda1` | Информация о конкретном разделе |
| `df -h` | Использование дисков |
| `du -sh /path` | Размер директории |
| `du -sh *` | Размер каждого файла/папки |

## Монтирование

### Создать точку монтирования

```bash
sudo mkdir /mnt/name
```

### Смонтировать

```bash
sudo mount /dev/sdXN /mnt/name
```

### По типу файловой системы

| Тип | Команда |
|-----|---------|
| ext4 | `sudo mount /dev/sdXN /mnt/name` |
| NTFS | `sudo mount -t ntfs-3g /dev/sdXN /mnt/name` |
| exFAT | `sudo mount -t exfat /dev/sdXN /mnt/name` |
| FAT32 | `sudo mount -t vfat /dev/sdXN /mnt/name` |

### С опциями

```bash
# Монтировать с правами пользователя
sudo mount -t ntfs-3g -o uid=1000,gid=1000 /dev/sda3 /mnt/windows

# Монтировать только для чтения
sudo mount -o ro /dev/sda3 /mnt/windows

# Монтировать с кодировкой
sudo mount -t vfat -o iocharset=utf8 /dev/sda1 /mnt/efi
```

## Постоянное монтирование (fstab)

### Узнать UUID

```bash
sudo blkid /dev/sdXN
```

### Формат записи в /etc/fstab

```
UUID=xxxx-xxxx   /mnt/name   filesystem   options   dump   pass
```

### Примеры

```
# NTFS Windows
UUID=2EE0C9C2E0C9910F   /mnt/windows   ntfs-3g   defaults,uid=1000,gid=1000   0   0

# ext4
UUID=xxxx-xxxx          /mnt/data      ext4      defaults                      0   2

# exFAT
UUID=xxxx-xxxx          /mnt/usb       exfat     defaults,uid=1000,gid=1000   0   0
```

### Проверить fstab

```bash
sudo mount -a
```

## Размонтирование

```bash
sudo umount /mnt/name
```

Если диск занят:

```bash
sudo umount -l /mnt/name    # lazy unmount
sudo umount -f /mnt/name    # принудительно
```

## Создание файловой системы

```bash
# ext4
sudo mkfs.ext4 /dev/sdXN

# NTFS
sudo mkfs.ntfs /dev/sdXN

# exFAT
sudo mkfs.exfat /dev/sdXN

# FAT32
sudo mkfs.vfat -F 32 /dev/sdXN
```

## Управление разделами

```bash
# Разметка диска (интерактивно)
sudo fdisk /dev/sdX

# parted (современнее)
sudo parted /dev/sdX

# GParted (GUI)
sudo gparted
```

## Замена раздела

```bash
# Отмонтировать
sudo umount /dev/sdXN

# Проверить ошибки
sudo fsck /dev/sdXN

# Восстановить
sudo fsck -y /dev/sdXN
```

## SWAP

```bash
# Создать swap-файл
sudo fallocate -l 4G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile

# Добавить в fstab для постоянного использования
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab

# Проверить
free -h
```

## Шпаргалка

```bash
# Посмотреть все диски
lsblk -f

# Смонтировать Windows
sudo mkdir -p /mnt/windows
sudo mount -t ntfs-3g /dev/sda3 /mnt/windows

# Проверить место
df -h

# Размер папки
du -sh ~/Downloads
```
