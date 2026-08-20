# Network

## Network Information

| Command | Description |
|---------|-------------|
| `ip addr` | IP addresses of all interfaces |
| `ip link` | Network interfaces |
| `ip route` | Routing table |
| `hostname -I` | Local IP |
| `ss -tuln` | Open ports |
| `ss -tulpn` | Open ports with processes |

## Connectivity

| Command | Description |
|---------|-------------|
| `ping google.com` | Check connection |
| `ping -c 4 google.com` | 4 pings then stop |
| `curl google.com` | HTTP request |
| `wget url` | Download file |
| `traceroute google.com` | Route to server |
| `dig domain.com` | DNS records |
| `nslookup domain.com` | DNS query |

## Network Configuration

### NetworkManager (recommended)

```bash
# Status
nmcli device status

# Connect to Wi-Fi
nmcli device wifi list
nmcli device wifi connect "SSID" password "PASSWORD"

# Disconnect
nmcli device disconnect wlan0

# Static IP
nmcli connection modify "name" ipv4.addresses 192.168.1.100/24
nmcli connection modify "name" ipv4.gateway 192.168.1.1
nmcli connection modify "name" ipv4.dns "8.8.8.8 8.8.4.4"
nmcli connection modify "name" ipv4.method manual
nmcli connection up "name"
```

### Temporary

```bash
# Bring up interface
sudo ip link set wlan0 up

# DHCP
sudo dhclient wlan0

# Static IP
sudo ip addr add 192.168.1.100/24 dev wlan0
sudo ip route add default via 192.168.1.1
```

## DNS

### /etc/resolv.conf file

```
nameserver 8.8.8.8
nameserver 8.8.4.4
nameserver 1.1.1.1
```

### Quick DNS change

```bash
sudo echo "nameserver 8.8.8.8" > /etc/resolv.conf
```

## SSH

```bash
# Connect
ssh user@hostname

# Connect on custom port
ssh -p 2222 user@hostname

# Copy file
scp file.txt user@hostname:/path/

# Copy directory
scp -r dir/ user@hostname:/path/

# Generate keys
ssh-keygen -t ed25519

# Copy key to server
ssh-copy-id user@hostname
```

## Firewall

```bash
# ufw (simple)
sudo pacman -S ufw
sudo ufw enable
sudo ufw allow ssh
sudo ufw allow 80/tcp
sudo ufw status

# iptables (advanced)
sudo iptables -L
```

## Quick Reference

```bash
# My IP
ip addr show | grep "inet "

# Open ports
ss -tuln

# Ping
ping -c 4 google.com

# Download file
wget https://example.com/file.zip

# SSH connect
ssh user@192.168.1.100
```
