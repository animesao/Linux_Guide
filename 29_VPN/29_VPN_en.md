# VPN

## WireGuard

### Installation

```bash
sudo pacman -S wireguard-tools
```

### Client Setup

```bash
# Generate keys
wg genkey | tee privatekey | wg pubkey > publickey

# Create config /etc/wireguard/wg0.conf
[Interface]
PrivateKey = <private_key>
Address = 10.0.0.2/24
DNS = 1.1.1.1

[Peer]
PublicKey = <server_public_key>
Endpoint = server_ip:51820
AllowedIPs = 0.0.0.0/0
```

### Management

```bash
# Start
sudo wg-quick up wg0

# Stop
sudo wg-quick down wg0

# Autostart
sudo systemctl enable wg-quick@wg0

# Status
sudo wg show
```

## OpenVPN

### Installation

```bash
sudo pacman -S openvpn
```

### Connect

```bash
# Connect
sudo openvpn client.ovpn

# In background
sudo openvpn --daemon --config client.ovpn

# Stop
sudo killall openvpn
```

### Autostart

```bash
# systemd
sudo systemctl enable openvpn-client@client
```

## PPTP/L2TP

```bash
# NetworkManager
sudo pacman -S networkmanager-pptp networkmanager-l2tp

# Restart
sudo systemctl restart NetworkManager
```

## Testing

```bash
# My IP
curl ifconfig.me

# Check connection
ping 8.8.8.8

# DNS
nslookup google.com

# Traceroute
traceroute google.com
```

## Quick Reference

```bash
# WireGuard: start
sudo wg-quick up wg0

# WireGuard: stop
sudo wg-quick down wg0

# WireGuard: autostart
sudo systemctl enable wg-quick@wg0

# OpenVPN: connect
sudo openvpn client.ovpn

# Check IP
curl ifconfig.me
```
