# Cron и планировщики

## crontab

| Команда | Описание |
|---------|----------|
| `crontab -e` | Редактировать расписание |
| `crontab -l` | Показать расписание |
| `crontab -r` | Удалить расписание |
| `crontab -u user -l` | Расписание другого пользователя |

## Формат crontab

```
* * * * * command
│ │ │ │ │
│ │ │ │ └─ День недели (0-7, где 0 и 7 = воскресенье)
│ │ │ └─── Месяц (1-12)
│ │ └───── День месяца (1-31)
│ └─────── Час (0-23)
└───────── Минута (0-59)
```

## Примеры

```bash
# Каждый день в 3:00
0 3 * * * /usr/local/bin/backup.sh

# Каждые 5 минут
*/5 * * * * /usr/local/bin/check.sh

# Каждый понедельник в 9:00
0 9 * * 1 /usr/local/bin/report.sh

# Каждый час
0 * * * * /usr/local/bin/hourly.sh

# Первое число каждого месяца в полночь
0 0 1 * * /usr/local/bin/monthly.sh

# В будни каждые 30 минут
*/30 * * * 1-5 /usr/local/bin/workday.sh
```

## Специальные переменные

| Переменная | Значение |
|------------|----------|
| `@reboot` | При загрузке |
| `@daily` | Раз в день |
| `@weekly` | Раз в неделю |
| `@monthly` | Раз в месяц |
| `@yearly` | Раз в год |

```bash
# Выполнить при загрузке
@reboot /usr/local/bin/start.sh

# Раз в день
@daily /usr/local/bin/backup.sh
```

## Системные cron

```bash
# Директории
/etc/cron.d/          # Пользовательские задачи
/etc/cron.daily/      # Ежедневные задачи
/etc/cron.hourly/     # Ежечасные задачи
/etc/cron.weekly/     # Еженедельные задачи
/etc/cron.monthly/    # Ежемесячные задачи

# Файлы ограничения
/etc/cron.allow       # Кто может использовать cron
/etc/cron.deny        # Кто не может
```

## at (одноразовые задачи)

```bash
# Запланировать задачу
at now + 5 minutes
at> /usr/local/bin/script.sh
at> Ctrl+D

# Запланировать на время
echo "/usr/local/bin/script.sh" | at 14:00

# Посмотреть очередь
atq

# Удалить задачу
atrm job_number
```

## Anacron

```bash
# Файл /etc/anacrontab
# period  delay  command
1         5      cron.daily
7         25     cron.weekly
@monthly  45     cron.monthly
```

## Шпаргалка

```bash
# Открыть crontab
crontab -e

# Бекап каждого дня в 2:30
30 2 * * * tar -czf /backup/home-$(date +\%Y\%m\%d).tar.gz /home

# Каждые 10 минут проверять интернет
*/10 * * * * ping -c 1 google.com || notify-send "No internet"

# Посмотреть задачи
crontab -l
```
