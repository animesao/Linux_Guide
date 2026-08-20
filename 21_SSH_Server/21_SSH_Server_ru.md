# SSH Сервер

## Установка

```bash
sudo pacman -S openssh
sudo systemctl enable --now sshd
```

## Настройка

### Конфиг `/etc/ssh/sshd_config`

```bash
# Порт
Port 22

# Запретить вход root
PermitRootLogin no

# Только по ключам (рекомендуется)
PasswordAuthentication no
PubkeyAuthentication yes

# Пользователи
AllowUsers myuser

# Шифрование
KexAlgorithms curve25519-sha256
Ciphers chacha20-poly1305@openssh.com
MACs hmac-sha2-512-etm@openssh.com
```

### Применить изменения

```bash
sudo systemctl restart sshd
```

## Ключи

### Генерация

```bash
# На клиенте
ssh-keygen -t ed25519 -C "email@example.com"

# Копировать на сервер
ssh-copy-id -p 22 user@server
```

### Автоматическое подключение

Файл `~/.ssh/config`:

```
Host server
    HostName 192.168.1.100
    User myuser
    Port 22
    IdentityFile ~/.ssh/id_ed25519
```

## Портфолио (Agent Forwarding)

```bash
# Запустить агент
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Подключиться с агентом
ssh -A user@server

# Или в конфиге
Host server
    ForwardAgent yes
```

## Туннели

```bash
# Локальный порт → удалённый сервер
ssh -L 8080:localhost:80 user@server

# Удалённый порт → локальный
ssh -R 8080:localhost:80 user@server

# SOCKS прокси
ssh -D 1080 user@server
```

## Проверка

```bash
# Статус
sudo systemctl status sshd

# Логи
sudo journalctl -u sshd

# Тест подключения
ssh -v user@server
```

## Безопасность

```bash
# Fail2ban (защита от брутфорса)
sudo pacman -S fail2ban
sudo systemctl enable --now fail2ban

# Конфиг /etc/fail2ban/jail.local
[sshd]
enabled = true
port = 22
maxretry = 3
bantime = 3600
```

## Шпаргалка

```bash
# Сгенерировать ключ
ssh-keygen -t ed25519

# Скопировать на сервер
ssh-copy-id user@server

# Подключиться
ssh user@server

# Проверить sshd
sudo systemctl status sshd
```
