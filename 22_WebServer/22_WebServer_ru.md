# Веб-сервер (Nginx)

## Установка

```bash
sudo pacman -S nginx
sudo systemctl enable --now nginx
```

## Основные команды

| Команда | Описание |
|---------|----------|
| `sudo systemctl start nginx` | Запустить |
| `sudo systemctl stop nginx` | Остановить |
| `sudo systemctl restart nginx` | Перезапустить |
| `sudo nginx -t` | Проверить конфиг |
| `sudo nginx -s reload` | Перезагрузить конфиг |

## Конфигурация

### Основной конфиг `/etc/nginx/nginx.conf`

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

### Серверы

| Файл | Описание |
|------|----------|
| `/etc/nginx/nginx.conf` | Основной конфиг |
| `/etc/nginx/conf.d/*.conf` | Дополнительные конфиги |
| `/etc/nginx/sites-available/` | Доступные сайты |
| `/etc/nginx/sites-enabled/` | Активные сайты |
| `/var/log/nginx/` | Логи |

## Статический сайт

```bash
# Создать директорию
sudo mkdir -p /var/www/html

# Добавить index.html
echo "<h1>Hello Linux</h1>" | sudo tee /var/www/html/index.html

# Права
sudo chown -R http:http /var/www/html
```

## Домены (Server Blocks)

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
# Активировать
sudo ln -s /etc/nginx/sites-available/mysite.conf /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl restart nginx
```

## SSL (Let's Encrypt)

```bash
# Установить certbot
sudo pacman -S certbot certbot-nginx

# Получить сертификат
sudo certbot --nginx -d example.com -d www.example.com

# Обновить
sudo certbot renew

# Проверить
sudo certbot certificates
```

## PHP

```bash
# Установить
sudo pacman -S php-fpm

# Настроить
sudo systemctl enable --now php-fpm

# В nginx.conf добавить:
location ~ \.php$ {
    fastcgi_pass unix:/run/php-fpm/php-fpm.sock;
    fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    include fastcgi_params;
}
```

## Proxy (обратный прокси)

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

## Шпаргалка

```bash
# Проверить конфиг
sudo nginx -t

# Перезапустить
sudo systemctl restart nginx

# Посмотреть логи
sudo tail -f /var/log/nginx/access.log

# Получить SSL
sudo certbot --nginx -d example.com
```
