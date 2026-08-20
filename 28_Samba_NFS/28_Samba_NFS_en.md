# Samba and NFS

## Samba (Windows Sharing)

### Installation

```bash
sudo pacman -S samba
sudo systemctl enable --now smb nmb
```

### Config `/etc/samba/smb.conf`

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

### Setup

```bash
# Create group
sudo groupadd sambagroup
sudo usermod -aG sambagroup myuser

# Create directory
sudo mkdir -p /srv/samba/share
sudo chown root:sambagroup /srv/samba/share
sudo chmod 2775 /srv/samba/share

# Add Samba user
sudo smbpasswd -a myuser

# Test config
testparm

# Restart
sudo systemctl restart smb nmb
```

### Connect

```bash
# Linux
smbclient //server/share -U myuser

# Windows
\\server\share

# GNOME/Nautilus
smb://server/share
```

## NFS (Linux Sharing)

### Server

```bash
# Install
sudo pacman -S nfs-utils

# Start
sudo systemctl enable --now nfs-server

# Config /etc/exports
/srv/nfs/share 192.168.1.0/24(rw,sync,no_subtree_check)

# Apply
sudo exportfs -ra
```

### Client

```bash
# Install
sudo pacman -S nfs-utils

# Mount
sudo mount -t nfs server:/srv/nfs/share /mnt/nfs

# In fstab
server:/srv/nfs/share  /mnt/nfs  nfs  defaults  0  0

# View exports
showmount -e server
```

## Quick Reference

```bash
# Samba: add user
sudo smbpasswd -a myuser

# Samba: test config
testparm

# NFS: apply changes
sudo exportfs -ra

# NFS: connect
sudo mount -t nfs server:/path /mnt/nfs
```
