# Базы данных

## PostgreSQL

### Установка

```bash
sudo pacman -S postgresql
sudo systemctl enable --now postgresql
```

### Настройка

```bash
# Инициализировать
sudo -u postgres initdb -D /var/lib/postgres/data

# Запустить
sudo systemctl start postgresql

# Войти
sudo -u postgres psql

# Создать пользователя
sudo -u postgres createuser -P myuser

# Создать базу
sudo -u postgres createdb mydb

# Дать права
sudo -u postgres psql -c "GRANT ALL PRIVILEGES ON DATABASE mydb TO myuser;"
```

### Команды psql

| Команда | Описание |
|---------|----------|
| `\l` | Список баз |
| `\c dbname` | Подключиться к базе |
| `\dt` | Список таблиц |
| `\d tablename` | Структура таблицы |
| `\du` | Список пользователей |
| `\q` | Выйти |

### Конфиг `/var/lib/postgres/data/postgresql.conf`

```bash
# Слушать все интерфейсы
listen_addresses = '*'

# Порт
port = 5432
```

### Конфиг `/var/lib/postgres/data/pg_hba.conf`

```
# Разрешить подключение
host    all    all    192.168.1.0/24    md5
```

## MySQL/MariaDB

### Установка

```bash
sudo pacman -S mariadb
sudo systemctl enable --now mariadb
```

### Настройка

```bash
# Безопасная установка
sudo mysql_secure_installation

# Войти
mysql -u root -p

# Создать базу
CREATE DATABASE mydb;

# Создать пользователя
CREATE USER 'myuser'@'localhost' IDENTIFIED BY 'password';

# Дать права
GRANT ALL PRIVILEGES ON mydb.* TO 'myuser'@'localhost';

# Применить
FLUSH PRIVILEGES;
```

## Redis

### Установка

```bash
sudo pacman -S redis
sudo systemctl enable --now redis
```

### Команды

```bash
# Подключиться
redis-cli

# Проверить
PING

# Установить значение
SET key value

# Получить значение
GET key

# Список ключей
KEYS *
```

## Утилиты

```bash
# pgAdmin (GUI для PostgreSQL)
sudo pacman -S pgadmin4

# DBeaver (универсальный клиент)
sudo pacman -S dbeaver

# sqlite3
sudo pacman -S sqlite
sqlite3 database.db
```

## Шпаргалка

```bash
# PostgreSQL
sudo -u postgres psql

# MySQL
mysql -u root -p

# Redis
redis-cli

# Создать базу PostgreSQL
sudo -u postgres createdb mydb

# PostgreSQL статус
sudo systemctl status postgresql
```
