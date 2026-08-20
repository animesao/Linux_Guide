# Development

## Python

### Installation

```bash
sudo pacman -S python python-pip
```

### Virtual Environment

```bash
# Create
python -m venv myenv

# Activate
source myenv/bin/activate

# Deactivate
deactivate

# Install packages
pip install package_name

# Export dependencies
pip freeze > requirements.txt

# Install from file
pip install -r requirements.txt
```

## Node.js

### Installation

```bash
sudo pacman -S nodejs npm
```

### Version Management (nvm)

```bash
# Install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash

# Install Node
nvm install --lts
nvm use --lts

# Switch versions
nvm install 18
nvm use 18
```

### npm Commands

| Command | Description |
|---------|-------------|
| `npm init` | Initialize project |
| `npm install package` | Install package |
| `npm install` | Install dependencies |
| `npm run script` | Run script |
| `npm update` | Update packages |

## PHP

### Installation

```bash
sudo pacman -S php php-fpm

# Start
sudo systemctl enable --now php-fpm
```

### Composer

```bash
# Install
sudo pacman -S composer

# Create project
composer create-project laravel/laravel myproject

# Install package
composer require package/name
```

## Rust

### Installation

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# Update
rustup update

# Compiler
rustc --version
```

### Cargo Commands

| Command | Description |
|---------|-------------|
| `cargo new project` | Create project |
| `cargo build` | Build |
| `cargo run` | Build and run |
| `cargo test` | Tests |
| `cargo update` | Update dependencies |

## Go

### Installation

```bash
sudo pacman -S go
```

### Commands

```bash
# Module
go mod init github.com/user/project

# Dependencies
go mod tidy

# Build
go build

# Run
go run main.go
```

## Compilation

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

## Quick Reference

```bash
# Python venv
python -m venv myenv && source myenv/bin/activate

# Node.js project
npm init -y

# Rust project
cargo new myproject

# Go project
go mod init myproject
```
