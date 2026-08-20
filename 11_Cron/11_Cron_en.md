# Cron and Schedulers

## crontab

| Command | Description |
|---------|-------------|
| `crontab -e` | Edit schedule |
| `crontab -l` | Show schedule |
| `crontab -r` | Remove schedule |
| `crontab -u user -l` | Another user's schedule |

## crontab Format

```
* * * * * command
│ │ │ │ │
│ │ │ │ └─ Day of week (0-7, 0 and 7 = Sunday)
│ │ │ └─── Month (1-12)
│ │ └───── Day of month (1-31)
│ └─────── Hour (0-23)
└───────── Minute (0-59)
```

## Examples

```bash
# Every day at 3:00
0 3 * * * /usr/local/bin/backup.sh

# Every 5 minutes
*/5 * * * * /usr/local/bin/check.sh

# Every Monday at 9:00
0 9 * * 1 /usr/local/bin/report.sh

# Every hour
0 * * * * /usr/local/bin/hourly.sh

# First day of month at midnight
0 0 1 * * /usr/local/bin/monthly.sh

# Weekdays every 30 minutes
*/30 * * * 1-5 /usr/local/bin/workday.sh
```

## Special Variables

| Variable | Meaning |
|----------|---------|
| `@reboot` | On boot |
| `@daily` | Once a day |
| `@weekly` | Once a week |
| `@monthly` | Once a month |
| `@yearly` | Once a year |

```bash
# Run on boot
@reboot /usr/local/bin/start.sh

# Daily
@daily /usr/local/bin/backup.sh
```

## System Cron

```bash
# Directories
/etc/cron.d/          # User tasks
/etc/cron.daily/      # Daily tasks
/etc/cron.hourly/     # Hourly tasks
/etc/cron.weekly/     # Weekly tasks
/etc/cron.monthly/    # Monthly tasks

# Restriction files
/etc/cron.allow       # Who can use cron
/etc/cron.deny        # Who cannot
```

## at (one-time tasks)

```bash
# Schedule task
at now + 5 minutes
at> /usr/local/bin/script.sh
at> Ctrl+D

# Schedule for time
echo "/usr/local/bin/script.sh" | at 14:00

# View queue
atq

# Delete task
atrm job_number
```

## Anacron

```bash
# File /etc/anacrontab
# period  delay  command
1         5      cron.daily
7         25     cron.weekly
@monthly  45     cron.monthly
```

## Quick Reference

```bash
# Open crontab
crontab -e

# Backup every day at 2:30
30 2 * * * tar -czf /backup/home-$(date +\%Y\%m\%d).tar.gz /home

# Check internet every 10 minutes
*/10 * * * * ping -c 1 google.com || notify-send "No internet"

# View tasks
crontab -l
```
