# Разработка

## Python

### Установка

```bash
sudo pacman -S python python-pip
```

### Виртуальное окружение

```bash
# Создать
python -m venv myenv

# Активировать
source myenv/bin/activate

# Деактивировать
deactivate

# Установить пакеты
pip install package_name

# Экспорт зависимостей
pip freeze > requirements.txt

# Установить из файла
pip install -r requirements.txt
```

## Node.js

### Установка

```bash
sudo pacman -S nodejs npm
```

### Управление версиями (nvm)

```bash
# Установить nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash

# Установить Node
nvm install --lts
nvm use --lts

# Переключать версии
nvm install 18
nvm use 18
```

### npm команды

| Команда | Описание |
|---------|----------|
| `npm init` | Инициализировать проект |
| `npm install package` | Установить пакет |
| `npm install` | Установить зависимости |
| `npm run script` | Запустить скрипт |
| `npm update` | Обновить пакеты |

## PHP

### Установка

```bash
sudo pacman -S php php-fpm

# Запустить
sudo systemctl enable --now php-fpm
```

### Composer

```bash
# Установить
sudo pacman -S composer

# Создать проект
composer create-project laravel/laravel myproject

# Установить пакет
composer require package/name
```

## Rust

### Установка

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# Обновить
rustup update

# Компилятор
rustc --version
```

### Cargo команды

| Команда | Описание |
|---------|----------|
| `cargo new project` | Создать проект |
| `cargo build` | Собрать |
| `cargo run` | Собрать и запустить |
| `cargo test` | Тесты |
| `cargo update` | Обновить зависимости |

## Go

### Установка

```bash
sudo pacman -S go
```

### Команды

```bash
# Модуль
go mod init github.com/user/project

# Зависимости
go mod tidy

# Собрать
go build

# Запустить
go run main.go
```

## Компиляция

```bash
# Make
make

# CMake
mkdir build && cd build
cmake ..
make

# Meson
meson setup build
cd build
ninja
```

## Шпаргалка

```bash
# Python venv
python -m venv myenv && source myenv/bin/activate

# Node.js проект
npm init -y

# Rust проект
cargo new myproject

# Go проект
go mod init myproject
```
