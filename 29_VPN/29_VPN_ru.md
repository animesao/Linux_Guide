# VPN

## WireGuard

### Установка

```bash
sudo pacman -S wireguard-tools
```

### Настройка клиента

```bash
# Сгенерировать ключи
wg genkey | tee privatekey | wg pubkey > publickey

# Создать конфиг /etc/wireguard/wg0.conf
[Interface]
PrivateKey = <private_key>
Address = 10.0.0.2/24
DNS = 1.1.1.1

[Peer]
PublicKey = <server_public_key>
Endpoint = server_ip:51820
AllowedIPs = 0.0.0.0/0
```

### Управление

```bash
# Запустить
sudo wg-quick up wg0

# Остановить
sudo wg-quick down wg0

# Автозапуск
sudo systemctl enable wg-quick@wg0

# Статус
sudo wg show
```

## OpenVPN

### Установка

```bash
sudo pacman -S openvpn
```

### Подключение

```bash
# Подключиться
sudo openvpn client.ovpn

# В фоне
sudo openvpn --daemon --config client.ovpn

# Остановить
sudo killall openvpn
```

### Автозапуск

```bash
# systemd
sudo systemctl enable openvpn-client@client
```

## PPTP/L2TP

```bash
# NetworkManager
sudo pacman -S networkmanager-pptp networkmanager-l2tp

# Перезапустить
sudo systemctl restart NetworkManager
```

## Проверка

```bash
# Мой IP
curl ifconfig.me

# Проверить подключение
ping 8.8.8.8

# DNS
nslookup google.com

# Traceroute
traceroute google.com
```

## Шпаргалка

```bash
# WireGuard: запустить
sudo wg-quick up wg0

# WireGuard: остановить
sudo wg-quick down wg0

# WireGuard: автозапуск
sudo systemctl enable wg-quick@wg0

# OpenVPN: подключить
sudo openvpn client.ovpn

# Проверить IP
curl ifconfig.me
```
