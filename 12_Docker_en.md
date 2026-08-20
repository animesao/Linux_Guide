# Docker

## Installation

```bash
sudo pacman -S docker docker-compose
sudo systemctl enable --now docker
sudo usermod -aG docker $USER
# Re-login
```

## Images

| Command | Description |
|---------|-------------|
| `docker pull image` | Download image |
| `docker images` | List images |
| `docker rmi image` | Delete image |
| `docker image prune` | Clean unused images |
| `docker build -t name .` | Build image |

## Containers

| Command | Description |
|---------|-------------|
| `docker run image` | Run container |
| `docker run -d image` | Run in background |
| `docker run -it image bash` | Run with terminal |
| `docker run -p 8080:80 image` | Port mapping |
| `docker run -v /host:/container image` | Mount directory |
| `docker run --name name image` | Run with name |
| `docker ps` | Running containers |
| `docker ps -a` | All containers |
| `docker stop name` | Stop |
| `docker start name` | Start |
| `docker restart name` | Restart |
| `docker rm name` | Remove |
| `docker logs name` | Logs |
| `docker logs -f name` | Follow logs |
| `docker exec -it name bash` | Enter container |
| `docker inspect name` | Detailed info |

## Docker Compose

### File docker-compose.yml

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

### Commands

| Command | Description |
|---------|-------------|
| `docker-compose up -d` | Start all services |
| `docker-compose down` | Stop all |
| `docker-compose ps` | Service status |
| `docker-compose logs` | Logs |
| `docker-compose exec service bash` | Enter service |
| `docker-compose pull` | Update images |
| `docker-compose restart` | Restart |

## Networking

```bash
# Create network
docker network create mynet

# Run in network
docker run --network mynet image

# List networks
docker network ls

# Connect container
docker network connect mynet container
```

## Useful Images

```bash
# Nginx (web server)
docker run -d -p 80:80 nginx

# PostgreSQL (database)
docker run -d -p 5432:5432 -e POSTGRES_PASSWORD=pass postgres

# Redis
docker run -d -p 6379:6379 redis

# Portainer (Docker GUI)
docker run -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock portainer/portainer
```

## Quick Reference

```bash
# Run Nginx
docker run -d --name web -p 80:80 nginx

# View logs
docker logs web

# Enter container
docker exec -it web bash

# Stop and remove
docker stop web && docker rm web

# Clean everything
docker system prune -a
```
