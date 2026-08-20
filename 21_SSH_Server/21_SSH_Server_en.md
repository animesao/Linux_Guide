# SSH Server

## Installation

```bash
sudo pacman -S openssh
sudo systemctl enable --now sshd
```

## Configuration

### File `/etc/ssh/sshd_config`

```bash
# Port
Port 22

# Deny root login
PermitRootLogin no

# Key only (recommended)
PasswordAuthentication no
PubkeyAuthentication yes

# Users
AllowUsers myuser

# Encryption
KexAlgorithms curve25519-sha256
Ciphers chacha20-poly1305@openssh.com
MACs hmac-sha2-512-etm@openssh.com
```

### Apply changes

```bash
sudo systemctl restart sshd
```

## Keys

### Generation

```bash
# On client
ssh-keygen -t ed25519 -C "email@example.com"

# Copy to server
ssh-copy-id -p 22 user@server
```

### Auto-connect

File `~/.ssh/config`:

```
Host server
    HostName 192.168.1.100
    User myuser
    Port 22
    IdentityFile ~/.ssh/id_ed25519
```

## Agent Forwarding

```bash
# Start agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Connect with agent
ssh -A user@server

# Or in config
Host server
    ForwardAgent yes
```

## Tunnels

```bash
# Local port → remote server
ssh -L 8080:localhost:80 user@server

# Remote port → local
ssh -R 8080:localhost:80 user@server

# SOCKS proxy
ssh -D 1080 user@server
```

## Testing

```bash
# Status
sudo systemctl status sshd

# Logs
sudo journalctl -u sshd

# Test connection
ssh -v user@server
```

## Security

```bash
# Fail2ban (brute-force protection)
sudo pacman -S fail2ban
sudo systemctl enable --now fail2ban

# Config /etc/fail2ban/jail.local
[sshd]
enabled = true
port = 22
maxretry = 3
bantime = 3600
```

## Quick Reference

```bash
# Generate key
ssh-keygen -t ed25519

# Copy to server
ssh-copy-id user@server

# Connect
ssh user@server

# Check sshd
sudo systemctl status sshd
```
