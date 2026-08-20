# Сеть

## Информация о сети

| Команда | Описание |
|---------|----------|
| `ip addr` | IP-адреса всех интерфейсов |
| `ip link` | Сетевые интерфейсы |
| `ip route` | Таблица маршрутизации |
| `hostname -I` | Локальный IP |
| `ss -tuln` | Открытые порты |
| `ss -tulpn` | Открытые порты с процессами |

## Подключение

| Команда | Описание |
|---------|----------|
| `ping google.com` | Проверить соединение |
| `ping -c 4 google.com` | 4 пинга и остановиться |
| `curl google.com` | HTTP-запрос |
| `wget url` | Скачать файл |
| `traceroute google.com` | Маршрут до сервера |
| `dig domain.com` | DNS-записи |
| `nslookup domain.com` | DNS-запрос |

## Настройка сети

### NetworkManager (рекомендуется)

```bash
# Статус
nmcli device status

# Подключиться к Wi-Fi
nmcli device wifi list
nmcli device wifi connect "SSID" password "PASSWORD"

# Отключиться
nmcli device disconnect wlan0

# Статическое IP
nmcli connection modify "name" ipv4.addresses 192.168.1.100/24
nmcli connection modify "name" ipv4.gateway 192.168.1.1
nmcli connection modify "name" ipv4.dns "8.8.8.8 8.8.4.4"
nmcli connection modify "name" ipv4.method manual
nmcli connection up "name"
```

###临时变化

```bash
# Поднять интерфейс
sudo ip link set wlan0 up

# DHCP
sudo dhclient wlan0

# Статический IP
sudo ip addr add 192.168.1.100/24 dev wlan0
sudo ip route add default via 192.168.1.1
```

## DNS

### Файл /etc/resolv.conf

```
nameserver 8.8.8.8
nameserver 8.8.4.4
nameserver 1.1.1.1
```

### Быстрая смена DNS

```bash
sudo echo "nameserver 8.8.8.8" > /etc/resolv.conf
```

## SSH

```bash
# Подключиться
ssh user@hostname

# Подключиться по порту
ssh -p 2222 user@hostname

# Копировать файл
scp file.txt user@hostname:/path/

# Копировать директорию
scp -r dir/ user@hostname:/path/

# Сгенерировать ключи
ssh-keygen -t ed25519

# Копировать ключ на сервер
ssh-copy-id user@hostname
```

## Firewall

```bash
# ufw (простой)
sudo pacman -S ufw
sudo ufw enable
sudo ufw allow ssh
sudo ufw allow 80/tcp
sudo ufw status

# iptables (продвинутый)
sudo iptables -L
```

## Шпаргалка

```bash
# Мой IP
ip addr show | grep "inet "

# Открытые порты
ss -tuln

# Пинг
ping -c 4 google.com

# Скачать файл
wget https://example.com/file.zip

# Подключиться по SSH
ssh user@192.168.1.100
```
