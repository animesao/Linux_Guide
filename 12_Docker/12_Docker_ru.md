# Docker

## Установка

```bash
sudo pacman -S docker docker-compose
sudo systemctl enable --now docker
sudo usermod -aG docker $USER
# Перелогинься
```

## Образы

| Команда | Описание |
|---------|----------|
| `docker pull image` | Скачать образ |
| `docker images` | Список образов |
| `docker rmi image` | Удалить образ |
| `docker image prune` | Очистить неиспользуемые |
| `docker build -t name .` | Собрать образ |

## Контейнеры

| Команда | Описание |
|---------|----------|
| `docker run image` | Запустить контейнер |
| `docker run -d image` | Запустить в фоне |
| `docker run -it image bash` | Запустить с терминалом |
| `docker run -p 8080:80 image` | Проброс порта |
| `docker run -v /host:/container image` | Монтирование директории |
| `docker run --name name image` | Запустить с именем |
| `docker ps` | Запущенные контейнеры |
| `docker ps -a` | Все контейнеры |
| `docker stop name` | Остановить |
| `docker start name` | Запустить |
| `docker restart name` | Перезапустить |
| `docker rm name` | Удалить |
| `docker logs name` | Логи |
| `docker logs -f name` | Следить за логами |
| `docker exec -it name bash` | Войти в контейнер |
| `docker inspect name` | Подробная информация |

## Docker Compose

### Файл docker-compose.yml

```yaml
version: '3'
services:
  web:
    image: nginx:latest
    ports:
      - "80:80"
    volumes:
      - ./html:/usr/share/nginx/html
    restart: always

  db:
    image: postgres:15
    environment:
      POSTGRES_PASSWORD: password
      POSTGRES_DB: mydb
    volumes:
      - db_data:/var/lib/postgresql/data

volumes:
  db_data:
```

### Команды

| Команда | Описание |
|---------|----------|
| `docker-compose up -d` | Запустить все сервисы |
| `docker-compose down` | Остановить все |
| `docker-compose ps` | Статус сервисов |
| `docker-compose logs` | Логи |
| `docker-compose exec service bash` | Войти в сервис |
| `docker-compose pull` | Обновить образы |
| `docker-compose restart` | Перезапустить |

## Сеть

```bash
# Создать сеть
docker network create mynet

# Запустить в сети
docker run --network mynet image

# Список сетей
docker network ls

# Подключить контейнер
docker network connect mynet container
```

## Полезные образы

```bash
# Nginx (веб-сервер)
docker run -d -p 80:80 nginx

# PostgreSQL (БД)
docker run -d -p 5432:5432 -e POSTGRES_PASSWORD=pass postgres

# Redis
docker run -d -p 6379:6379 redis

# Portainer (GUI для Docker)
docker run -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock portainer/portainer
```

## Шпаргалка

```bash
# Запустить Nginx
docker run -d --name web -p 80:80 nginx

# Посмотреть логи
docker logs web

# Войти в контейнер
docker exec -it web bash

# Остановить и удалить
docker stop web && docker rm web

# Очистить всё
docker system prune -a
```
