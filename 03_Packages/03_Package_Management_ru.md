# Управление пакетами (pacman — Arch Linux)

## Основные команды

| Команда | Описание |
|---------|----------|
| `sudo pacman -Syu` | Обновить все пакеты |
| `sudo pacman -Syyu` | Принудительно обновить реестр и пакеты |
| `sudo pacman -S name` | Установить пакет |
| `sudo pacman -R name` | Удалить пакет |
| `sudo pacman -Rs name` | Удалить пакет и зависимости |
| `sudo pacman -Rns name` | Удалить пакет, зависимости и конфиги |
| `sudo pacman -Sc` | Очистить кэш пакетов |
| `sudo pacman -Scc` | Полностью очистить кэш |

## Поиск

| Команда | Описание |
|---------|----------|
| `pacman -Ss keyword` | Найти пакет по ключевому слову |
| `pacman -Qs keyword` | Найти среди установленных |
| `pacman -Qi name` | Информация об установленном пакете |
| `pacman -Ql name` | Список файлов пакета |
| `pacman -Qo /path/file` | Какому пакету принадлежит файл |
| `pacman -Qdt` | Пакеты-сироты (не нужны никому) |

## Группы пакетов

```bash
# Установить группу
sudo pacman -S gnome          # рабочий стол GNOME
sudo pacman -S base-devel     # инструменты сборки
sudo pacman -S xorg           # X Window System

# Посмотреть пакеты в группе
pacman -Sg gnome
```

## AUR (Arch User Repository)

### Установка AUR-помощника

```bash
# yay (рекомендуется)
sudo pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si

# paru
git clone https://aur.archlinux.org/paru.git
cd paru
makepkg -si
```

### Команды yay/paru

| Команда | Описание |
|---------|----------|
| `yay -S name` | Установить из AUR |
| `yay -R name` | Удалить пакет |
| `yay -Syu` | Обновить всё (включая AUR) |
| `yay -Ss keyword` | Искать в AUR |
| `yay -Qi name` | Информация о пакете |

## Полезные пакеты

```bash
# Системные
sudo pacman -S htop tree neofetch unzip

# Сеть
sudo pacman -S networkmanager network-manager-applet

# Мультимедиа
sudo pacman -S vlc mpv ffmpeg

# Разработка
sudo pacman -S git nodejs npm python

# Шрифты
sudo pacman -S ttf-liberation ttf-dejavu noto-fonts
```

## Шпаргалка

```bash
# Полное обновление системы
sudo pacman -Syu

# Установить пакет
sudo pacman -S name

# Удалить пакет с зависимостями
sudo pacman -Rns name

# Очистить кэш
sudo pacman -Sc

# Посмотреть занимаемое место
pacman -Qi | grep "Размер"
```
