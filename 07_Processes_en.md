# Processes

## Viewing Processes

| Command | Description |
|---------|-------------|
| `top` | Real-time monitoring |
| `htop` | Better top (install needed) |
| `ps aux` | All running processes |
| `ps aux \| grep name` | Find process by name |
| `pstree` | Process tree |
| `pgrep name` | PID by name |
| `pidof name` | PID of process |

## Process Management

| Command | Description |
|---------|-------------|
| `kill PID` | Stop process |
| `kill -9 PID` | Force stop |
| `killall name` | Stop all with name |
| `pkill name` | Stop by pattern |
| `kill -STOP PID` | Suspend |
| `kill -CONT PID` | Resume |

## Priorities

| Command | Description |
|---------|-------------|
| `nice -n -5 command` | Run with high priority |
| `nice -n 5 command` | Run with low priority |
| `renice -n -5 PID` | Change priority |
| `renice -n 5 PID` | Lower priority |

## Running in Background

```bash
# Run in background
command &

# Run in background (detach from terminal)
nohup command &

# Run in new session
setsid command

# Move current process to background
Ctrl+Z
bg
```

## systemd (Services)

| Command | Description |
|---------|-------------|
| `systemctl status name` | Service status |
| `systemctl start name` | Start |
| `systemctl stop name` | Stop |
| `systemctl restart name` | Restart |
| `systemctl enable name` | Enable autostart |
| `systemctl disable name` | Disable autostart |
| `systemctl list-units` | All services |
| `systemctl list-unit-files` | All available services |

## Quick Reference

```bash
# Top 10 processes by memory
ps aux --sort=-%mem | head -10

# Top 10 processes by CPU
ps aux --sort=-%cpu | head -10

# Kill process by name
pkill -f "process_name"

# Run in background and detach
nohup python script.py &

# Service status
systemctl status NetworkManager
```
