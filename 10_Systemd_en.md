# Systemd and Services

## Basic Commands

| Command | Description |
|---------|-------------|
| `systemctl status name` | Service status |
| `systemctl start name` | Start |
| `systemctl stop name` | Stop |
| `systemctl restart name` | Restart |
| `systemctl reload name` | Reload config |
| `systemctl enable name` | Enable autostart |
| `systemctl disable name` | Disable autostart |
| `systemctl enable --now name` | Enable and start |
| `systemctl mask name` | Block completely |
| `systemctl unmask name` | Unblock |

## Viewing

| Command | Description |
|---------|-------------|
| `systemctl list-units` | Active units |
| `systemctl list-units --type=service` | All services |
| `systemctl list-unit-files` | All available units |
| `systemctl list-dependencies name` | Service dependencies |
| `systemctl cat name` | Show service config |
| `systemctl show name` | All properties |

## Journal (journalctl)

```bash
# Service logs
journalctl -u name

# Last 50 lines
journalctl -u name -n 50

# Follow in real-time
journalctl -u name -f

# System logs
journalctl -b

# Error logs
journalctl -p err

# Logs for period
journalctl --since "2024-01-01" --until "2024-01-31"
```

## Creating Your Own Service

### File `/etc/systemd/system/myservice.service`

```ini
[Unit]
Description=My Custom Service
After=network.target

[Service]
Type=simple
User=myuser
WorkingDirectory=/home/myuser/project
ExecStart=/usr/bin/python3 /home/myuser/project/main.py
Restart=always
RestartSec=5

[Install]
WantedBy=multi-user.target
```

### Activation

```bash
# Reload systemd
sudo systemctl daemon-reload

# Enable and start
sudo systemctl enable --now myservice

# Check status
sudo systemctl status myservice
```

## Timers (instead of cron)

### File `/etc/systemd/system/mytimer.timer`

```ini
[Unit]
Description=Run myscript daily

[Timer]
OnCalendar=daily
Persistent=true

[Install]
WantedBy=timers.target
```

### File `/etc/systemd/system/mytimer.service`

```ini
[Unit]
Description=Run myscript

[Service]
Type=oneshot
ExecStart=/usr/local/bin/myscript.sh
```

### Management

```bash
sudo systemctl enable --now mytimer.timer
systemctl list-timers
sudo journalctl -u mytimer
```

## Journal Management

```bash
# Clean journal
sudo journalctl --vacuum-size=100M

# Check size
journalctl --disk-usage

# List boots
journalctl --list-boots
```

## Quick Reference

```bash
# Restart NetworkManager
sudo systemctl restart NetworkManager

# Check why service isn't starting
sudo systemctl status myservice
sudo journalctl -u myservice

# Enable autostart
sudo systemctl enable myservice

# Block service
sudo systemctl mask unwanted-service
```
