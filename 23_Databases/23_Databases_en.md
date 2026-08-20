# Databases

## PostgreSQL

### Installation

```bash
sudo pacman -S postgresql
sudo systemctl enable --now postgresql
```

### Setup

```bash
# Initialize
sudo -u postgres initdb -D /var/lib/postgres/data

# Start
sudo systemctl start postgresql

# Login
sudo -u postgres psql

# Create user
sudo -u postgres createuser -P myuser

# Create database
sudo -u postgres createdb mydb

# Grant permissions
sudo -u postgres psql -c "GRANT ALL PRIVILEGES ON DATABASE mydb TO myuser;"
```

### psql Commands

| Command | Description |
|---------|-------------|
| `\l` | List databases |
| `\c dbname` | Connect to database |
| `\dt` | List tables |
| `\d tablename` | Table structure |
| `\du` | List users |
| `\q` | Quit |

### Config `/var/lib/postgres/data/postgresql.conf`

```bash
# Listen all interfaces
listen_addresses = '*'

# Port
port = 5432
```

### Config `/var/lib/postgres/data/pg_hba.conf`

```
# Allow connection
host    all    all    192.168.1.0/24    md5
```

## MySQL/MariaDB

### Installation

```bash
sudo pacman -S mariadb
sudo systemctl enable --now mariadb
```

### Setup

```bash
# Secure installation
sudo mysql_secure_installation

# Login
mysql -u root -p

# Create database
CREATE DATABASE mydb;

# Create user
CREATE USER 'myuser'@'localhost' IDENTIFIED BY 'password';

# Grant permissions
GRANT ALL PRIVILEGES ON mydb.* TO 'myuser'@'localhost';

# Apply
FLUSH PRIVILEGES;
```

## Redis

### Installation

```bash
sudo pacman -S redis
sudo systemctl enable --now redis
```

### Commands

```bash
# Connect
redis-cli

# Check
PING

# Set value
SET key value

# Get value
GET key

# List keys
KEYS *
```

## Utilities

```bash
# pgAdmin (GUI for PostgreSQL)
sudo pacman -S pgadmin4

# DBeaver (universal client)
sudo pacman -S dbeaver

# sqlite3
sudo pacman -S sqlite
sqlite3 database.db
```

## Quick Reference

```bash
# PostgreSQL
sudo -u postgres psql

# MySQL
mysql -u root -p

# Redis
redis-cli

# Create PostgreSQL database
sudo -u postgres createdb mydb

# PostgreSQL status
sudo systemctl status postgresql
```
