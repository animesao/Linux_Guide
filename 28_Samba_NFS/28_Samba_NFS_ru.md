# Samba и NFS

## Samba (общий доступ к Windows)

### Установка

```bash
sudo pacman -S samba
sudo systemctl enable --now smb nmb
```

### Конфиг `/etc/samba/smb.conf`

```ini
[global]
   workgroup = WORKGROUP
   server string = Arch Server
   security = user
   map to guest = never

[share]
   path = /srv/samba/share
   browseable = yes
   writable = yes
   valid users = @sambagroup
```

### Настройка

```bash
# Создать группу
sudo groupadd sambagroup
sudo usermod -aG sambagroup myuser

# Создать директорию
sudo mkdir -p /srv/samba/share
sudo chown root:sambagroup /srv/samba/share
sudo chmod 2775 /srv/samba/share

# Добавить пользователя Samba
sudo smbpasswd -a myuser

# Проверить конфиг
testparm

# Перезапустить
sudo systemctl restart smb nmb
```

### Подключение

```bash
# Linux
smbclient //server/share -U myuser

# Windows
\\server\share

# GNOME/Nautilus
smb://server/share
```

## NFS (общий доступ к Linux)

### Сервер

```bash
# Установить
sudo pacman -S nfs-utils

# Запустить
sudo systemctl enable --now nfs-server

# Конфиг /etc/exports
/srv/nfs/share 192.168.1.0/24(rw,sync,no_subtree_check)

# Применить
sudo exportfs -ra
```

### Клиент

```bash
# Установить
sudo pacman -S nfs-utils

# Монтировать
sudo mount -t nfs server:/srv/nfs/share /mnt/nfs

# В fstab
server:/srv/nfs/share  /mnt/nfs  nfs  defaults  0  0

# Просмотреть экспорты
showmount -e server
```

## Шпаргалка

```bash
# Samba: добавить пользователя
sudo smbpasswd -a myuser

# Samba: проверить конфиг
testparm

# NFS: применить изменения
sudo exportfs -ra

# NFS: подключиться
sudo mount -t nfs server:/path /mnt/nfs
```
