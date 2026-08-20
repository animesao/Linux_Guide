# Пользователи и группы

## Информация

| Команда | Описание |
|---------|----------|
| `whoami` | Текущий пользователь |
| `id` | UID, GID и группы |
| `who` | Кто.logged in |
| `w` | Кто logged in и что делает |
| `last` | История входов |
| `cat /etc/passwd` | Все пользователи |
| `cat /etc/group` | Все группы |

## Управление пользователями

| Команда | Описание |
|---------|----------|
| `sudo adduser name` | Создать пользователя (интерактивно) |
| `sudo useradd -m name` | Создать пользователя |
| `sudo useradd -m -G wheel name` | Создать с группой wheel |
| `sudo passwd name` | Задать пароль |
| `sudo usermod -aG group name` | Добавить в группу |
| `sudo userdel -r name` | Удалить пользователя |

## Управление группами

| Команда | Описание |
|---------|----------|
| `sudo groupadd name` | Создать группу |
| `sudo groupdel name` | Удалить группу |
| `groups` | Группы текущего пользователя |
| `getent group wheel` | Участники группы |

## sudo

### Добавить пользователя в wheel

```bash
sudo usermod -aG wheel username
```

### Проверить

```bash
groups username
```

### Настройка sudoers

```bash
sudo visudo
```

Добавить строку (для полного доступа):

```
username ALL=(ALL:ALL) ALL
```

## Смена пользователя

```bash
# Сменить пользователя
su - username

# Стать root
sudo -i
sudo su

# Выполнить команду от root
sudo command
```

## Пароли

```bash
# Сменить свой пароль
passwd

# Сменить пароль другому
sudo passwd username

# Заблокировать аккаунт
sudo passwd -l username

# Разблокировать
sudo passwd -u username
```

## Шпаргалка

```bash
# Создать пользователя
sudo adduser newuser
sudo usermod -aG wheel newuser

# Стать root
sudo -i

# Посмотреть группы
groups

# Сменить пароль
passwd
```
