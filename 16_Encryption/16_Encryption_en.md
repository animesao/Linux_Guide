# Encryption

## GPG (GnuPG)

| Command | Description |
|---------|-------------|
| `gpg --gen-key` | Generate key |
| `gpg --list-keys` | List keys |
| `gpg --list-secret-keys` | List secret keys |
| `gpg --export -a "name"` | Export public key |
| `gpg --export-secret-keys -a "name"` | Export private key |
| `gpg --import key.gpg` | Import key |
| `gpg --delete-key "name"` | Delete key |
| `gpg --sign file` | Sign file |
| `gpg --verify file` | Verify signature |

### File Encryption

```bash
# Encrypt
gpg -c file.txt

# Decrypt
gpg file.txt.gpg

# Encrypt for specific recipient
gpg -e -r "email@example.com" file.txt
```

## SSH Keys

### Generation

```bash
# Ed25519 (recommended)
ssh-keygen -t ed25519 -C "email@example.com"

# RSA (legacy)
ssh-keygen -t rsa -b 4096 -C "email@example.com"
```

### Management

```bash
# Copy key to server
ssh-copy-id user@host

# Test connection
ssh -T git@github.com

# List keys
ls ~/.ssh/

# ssh-agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

### Config `~/.ssh/config`

```
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed2559

Host server
    HostName 192.168.1.100
    User myuser
    Port 22
```

## LUKS (Disk Encryption)

```bash
# Encrypt partition
sudo cryptsetup luksFormat /dev/sdXN

# Open encrypted partition
sudo cryptsetup open /dev/sdXN myvolume

# Create filesystem
sudo mkfs.ext4 /dev/mapper/myvolume

# Mount
sudo mount /dev/mapper/myvolume /mnt

# Close partition
sudo umount /mnt
sudo cryptsetup close myvolume
```

## age (Modern GPG Replacement)

```bash
# Installation
sudo pacman -S age

# Generate keys
age-keygen -o key.txt

# Encrypt
age -r age1public_key... -o file.txt.age file.txt

# Decrypt
age -d -i key.txt -o file.txt file.txt.age
```

## OpenSSL

```bash
# Encrypt file
openssl enc -aes-256-cbc -salt -in file.txt -out file.enc

# Decrypt
openssl enc -d -aes-256-cbc -in file.enc -out file.txt

# Generate key
openssl rand -base64 32

# Hash password
openssl passwd -6 "password"
```

## Quick Reference

```bash
# Generate SSH key
ssh-keygen -t ed25519

# Copy key
ssh-copy-id user@server

# Encrypt file
gpg -c important.txt

# Decrypt
gpg important.txt.gpg
```
