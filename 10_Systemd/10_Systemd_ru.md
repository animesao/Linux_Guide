# Systemd и службы

## Основные команды

| Команда | Описание |
|---------|----------|
| `systemctl status name` | Статус службы |
| `systemctl start name` | Запустить |
| `systemctl stop name` | Остановить |
| `systemctl restart name` | Перезапустить |
| `systemctl reload name` | Перезагрузить конфиг |
| `systemctl enable name` | Автозапуск |
| `systemctl disable name` | Отключить автозапуск |
| `systemctl enable --now name` | Включить и запустить |
| `systemctl mask name` | Заблокировать полностью |
| `systemctl unmask name` | Разблокировать |

## Просмотр

| Команда | Описание |
|---------|----------|
| `systemctl list-units` | Активные юниты |
| `systemctl list-units --type=service` | Все сервисы |
| `systemctl list-unit-files` | Все доступные юниты |
| `systemctl list-dependencies name` | Зависимости сервиса |
| `systemctl cat name` | Показать конфиг сервиса |
| `systemctl show name` | Все свойства |

## Журнал (journalctl)

```bash
# Логи сервиса
journalctl -u name

# Последние 50 строк
journalctl -u name -n 50

# Следить в реальном времени
journalctl -u name -f

# Системные логи
journalctl -b

# Логи с ошибками
journalctl -p err

# Логи за период
journalctl --since "2024-01-01" --until "2024-01-31"
```

## Создание своего сервиса

### Файл `/etc/systemd/system/myservice.service`

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

### Активация

```bash
# Перезагрузить systemd
sudo systemctl daemon-reload

# Запустить и включить автозапуск
sudo systemctl enable --now myservice

# Проверить статус
sudo systemctl status myservice
```

## Таймеры (вместо cron)

### Файл `/etc/systemd/system/mytimer.timer`

```ini
[Unit]
Description=Run myscript daily

[Timer]
OnCalendar=daily
Persistent=true

[Install]
WantedBy=timers.target
```

### Файл `/etc/systemd/system/mytimer.service`

```ini
[Unit]
Description=Run myscript

[Service]
Type=oneshot
ExecStart=/usr/local/bin/myscript.sh
```

### Управление

```bash
sudo systemctl enable --now mytimer.timer
systemctl list-timers
sudo journalctl -u mytimer
```

## Журнал systemd

```bash
# Очистить журнал
sudo journalctl --vacuum-size=100M

# Определить размер
journalctl --disk-usage

# Структура логов
journalctl --list-boots
```

## Шпаргалка

```bash
# Перезапустить NetworkManager
sudo systemctl restart NetworkManager

# Посмотреть почему сервис не запускается
sudo systemctl status myservice
sudo journalctl -u myservice

# Создать автозапуск
sudo systemctl enable myservice

# Заблокировать сервис
sudo systemctl mask unwanted-service
```
