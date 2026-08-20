# Btrfs и снапшоты

## Btrfs

### Создание файловой системы

```bash
# Создать
sudo mkfs.btrfs /dev/sdXN

# Смонтировать
sudo mount /dev/sdXN /mnt

# В fstab
UUID=xxxx  /mnt  btrfs  defaults,compress=zstd  0  0
```

### Подvolюмы

```bash
# Создать подvolюм
sudo btrfs subvolume create /mnt/@home

# Список подvolюмов
sudo btrfs subvolume list /mnt

# Удалить подvolюм
sudo btrfs subvolume delete /mnt/@home
```

## Снапшоты

### Создание

```bash
# Полный снапшот
sudo btrfs subvolume snapshot /mnt/@home /mnt/@home_backup

# Read-only снапшот
sudo btrfs subvolume snapshot -r /mnt/@home /mnt/@home_readonly
```

### Управление

```bash
# Список снапшотов
sudo btrfs subvolume list /mnt

# Восстановить
sudo btrfs subvolume delete /mnt/@home
sudo btrfs subvolume snapshot /mnt/@home_backup /mnt/@home

# Монтировать снапшот
sudo mount -o subvol=@home_backup /dev/sdXN /mnt/backup
```

## Timeshift

### Установка

```bash
sudo pacman -S timeshift
```

### Использование

```bash
# Запустить
sudo timeshift-gtk

# Или через CLI
sudo timeshift --create --comments "Before update"
sudo timeshift --list
sudo timeshift --restore
```

### Автоматические снапшоты

```bash
# Добавить в crontab
sudo crontab -e

# Ежедневно в 3:00
0 3 * * * timeshift --create --comments "Daily"
```

## Сжатие

| Алгоритм | Описание |
|----------|----------|
| `zstd` | Быстрый, хороший коэффициент |
| `lzo` | Быстрый, плохой коэффициент |
| `gzip` | Средний |

```bash
# Монтировать со сжатием
sudo mount -o compress=zstd /dev/sdXN /mnt
```

## Шпаргалка

```bash
# Создать снапшот
sudo btrfs subvolume snapshot /mnt/@home /mnt/@backup

# Список снапшотов
sudo btrfs subvolume list /mnt

# Timeshift: создать
sudo timeshift --create --comments "before update"

# Timeshift: восстановить
sudo timeshift --restore
```
