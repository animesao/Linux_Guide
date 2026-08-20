# Users and Groups

## Information

| Command | Description |
|---------|-------------|
| `whoami` | Current user |
| `id` | UID, GID and groups |
| `who` | Who is logged in |
| `w` | Who is logged in and what they're doing |
| `last` | Login history |
| `cat /etc/passwd` | All users |
| `cat /etc/group` | All groups |

## User Management

| Command | Description |
|---------|-------------|
| `sudo adduser name` | Create user (interactive) |
| `sudo useradd -m name` | Create user |
| `sudo useradd -m -G wheel name` | Create with wheel group |
| `sudo passwd name` | Set password |
| `sudo usermod -aG group name` | Add to group |
| `sudo userdel -r name` | Delete user |

## Group Management

| Command | Description |
|---------|-------------|
| `sudo groupadd name` | Create group |
| `sudo groupdel name` | Delete group |
| `groups` | Current user's groups |
| `getent group wheel` | Group members |

## sudo

### Add user to wheel

```bash
sudo usermod -aG wheel username
```

### Check

```bash
groups username
```

### Configure sudoers

```bash
sudo visudo
```

Add line (for full access):

```
username ALL=(ALL:ALL) ALL
```

## Switching Users

```bash
# Switch user
su - username

# Become root
sudo -i
sudo su

# Run command as root
sudo command
```

## Passwords

```bash
# Change own password
passwd

# Change another user's password
sudo passwd username

# Lock account
sudo passwd -l username

# Unlock
sudo passwd -u username
```

## Quick Reference

```bash
# Create user
sudo adduser newuser
sudo usermod -aG wheel newuser

# Become root
sudo -i

# View groups
groups

# Change password
passwd
```
