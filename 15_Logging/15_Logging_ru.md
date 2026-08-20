# Логирование

## Журналы

| Команда | Описание |
|---------|----------|
| `journalctl` | Все логи systemd |
| `journalctl -b` | Логи текущей загрузки |
| `journalctl -b -1` | Логи прошлой загрузки |
| `journalctl --list-boots` | Список загрузок |

## Фильтрация

```bash
# По сервису
journalctl -u nginx

# По приоритету
journalctl -p err        # Только ошибки
journalctl -p warning    # Предупреждения
journalctl -p info       # Информационные

# По времени
journalctl --since "2024-01-01"
journalctl --since "1 hour ago"
journalctl --since "today"
journalctl --since "2024-01-01" --until "2024-01-31"

# Последние строки
journalctl -n 50

# Следить в реальном времени
journalctl -f

# Ядро
journalctl -k
```

## Стандартные логи

| Файл | Описание |
|------|----------|
| `/var/log/syslog` | Системный лог |
| `/var/log/auth.log` | Авторизация |
| `/var/log/kern.log` | Ядро |
| `/var/log/pacman.log` | Pacman |
| `/var/log/Xorg.0.log` | X Window |
| `~/.xsession-errors` | Ошибки сессии |

## Просмотр логов

```bash
# tail (последние строки)
tail -f /var/log/syslog

# head (первые строки)
head -n 20 /var/log/syslog

# grep (поиск)
grep "error" /var/log/syslog

# less (просмотр)
less /var/log/syslog
```

## logrotate

### Файл `/etc/logrotate.d/myapp`

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

### Команды

```bash
# Проверить конфиг
logrotate -d /etc/logrotate.conf

# Принудительно выполнить
logrotate -f /etc/logrotate.conf
```

## Управление размером journal

```bash
# Проверить размер
journalctl --disk-usage

# Ограничить размер
sudo journalctl --vacuum-size=500M

# Удалить старше 30 дней
sudo journalctl --vacuum-time=30d

# Настройка в /etc/systemd/journald.conf
SystemMaxUse=500M
```

## Шпаргалка

```bash
# Последние ошибки
journalctl -p err -b

# Логи Nginx
journalctl -u nginx -f

# Проверить размер логов
journalctl --disk-usage

# Очистить старые логи
sudo journalctl --vacuum-size=100M

# Посмотреть логи авторизации
grep "sshd" /var/log/auth.log
```
