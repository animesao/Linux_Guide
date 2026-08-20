# Web Server (Nginx)

## Installation

```bash
sudo pacman -S nginx
sudo systemctl enable --now nginx
```

## Basic Commands

| Command | Description |
|---------|-------------|
| `sudo systemctl start nginx` | Start |
| `sudo systemctl stop nginx` | Stop |
| `sudo systemctl restart nginx` | Restart |
| `sudo nginx -t` | Test config |
| `sudo nginx -s reload` | Reload config |

## Configuration

### Main config `/etc/nginx/nginx.conf`

```nginx
events {
    worker_connections 1024;
}

http {
    include       mime.types;
    default_type  application/octet-stream;

    server {
        listen 80;
        server_name example.com;

        root /var/www/html;
        index index.html;

        location / {
            try_files $uri $uri/ =404;
        }
    }
}
```

### Locations

| File | Description |
|------|-------------|
| `/etc/nginx/nginx.conf` | Main config |
| `/etc/nginx/conf.d/*.conf` | Additional configs |
| `/etc/nginx/sites-available/` | Available sites |
| `/etc/nginx/sites-enabled/` | Enabled sites |
| `/var/log/nginx/` | Logs |

## Static Site

```bash
# Create directory
sudo mkdir -p /var/www/html

# Add index.html
echo "<h1>Hello Linux</h1>" | sudo tee /var/www/html/index.html

# Permissions
sudo chown -R http:http /var/www/html
```

## Virtual Hosts (Server Blocks)

```nginx
# /etc/nginx/sites-available/mysite.conf
server {
    listen 80;
    server_name mysite.local;

    root /var/www/mysite;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

```bash
# Enable
sudo ln -s /etc/nginx/sites-available/mysite.conf /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl restart nginx
```

## SSL (Let's Encrypt)

```bash
# Install certbot
sudo pacman -S certbot certbot-nginx

# Get certificate
sudo certbot --nginx -d example.com -d www.example.com

# Renew
sudo certbot renew

# Check
sudo certbot certificates
```

## PHP

```bash
# Install
sudo pacman -S php-fpm

# Enable
sudo systemctl enable --now php-fpm

# Add to nginx.conf:
location ~ \.php$ {
    fastcgi_pass unix:/run/php-fpm/php-fpm.sock;
    fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    include fastcgi_params;
}
```

## Reverse Proxy

```nginx
server {
    listen 80;
    server_name app.example.com;

    location / {
        proxy_pass http://localhost:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

## Quick Reference

```bash
# Test config
sudo nginx -t

# Restart
sudo systemctl restart nginx

# View logs
sudo tail -f /var/log/nginx/access.log

# Get SSL
sudo certbot --nginx -d example.com
```
