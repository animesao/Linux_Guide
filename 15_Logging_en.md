# Logging

## Journals

| Command | Description |
|---------|-------------|
| `journalctl` | All systemd logs |
| `journalctl -b` | Current boot logs |
| `journalctl -b -1` | Previous boot logs |
| `journalctl --list-boots` | List boots |

## Filtering

```bash
# By service
journalctl -u nginx

# By priority
journalctl -p err        # Errors only
journalctl -p warning    # Warnings
journalctl -p info       # Informational

# By time
journalctl --since "2024-01-01"
journalctl --since "1 hour ago"
journalctl --since "today"
journalctl --since "2024-01-01" --until "2024-01-31"

# Last lines
journalctl -n 50

# Follow in real-time
journalctl -f

# Kernel
journalctl -k
```

## Standard Logs

| File | Description |
|------|-------------|
| `/var/log/syslog` | System log |
| `/var/log/auth.log` | Authorization |
| `/var/log/kern.log` | Kernel |
| `/var/log/pacman.log` | Pacman |
| `/var/log/Xorg.0.log` | X Window |
| `~/.xsession-errors` | Session errors |

## Viewing Logs

```bash
# tail (last lines)
tail -f /var/log/syslog

# head (first lines)
head -n 20 /var/log/syslog

# grep (search)
grep "error" /var/log/syslog

# less (view)
less /var/log/syslog
```

## logrotate

### File `/etc/logrotate.d/myapp`

```
/var/log/myapp/*.log {
    daily
    rotate 7
    compress
    delaycompress
    missingok
    notifempty
    create 644 root root
}
```

### Commands

```bash
# Check config
logrotate -d /etc/logrotate.conf

# Force execute
logrotate -f /etc/logrotate.conf
```

## Managing journal Size

```bash
# Check size
journalctl --disk-usage

# Limit size
sudo journalctl --vacuum-size=500M

# Delete older than 30 days
sudo journalctl --vacuum-time=30d

# Config in /etc/systemd/journald.conf
SystemMaxUse=500M
```

## Quick Reference

```bash
# Last errors
journalctl -p err -b

# Nginx logs
journalctl -u nginx -f

# Check log size
journalctl --disk-usage

# Clean old logs
sudo journalctl --vacuum-size=100M

# View auth logs
grep "sshd" /var/log/auth.log
```
