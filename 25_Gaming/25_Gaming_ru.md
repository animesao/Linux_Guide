# Игры на Linux

## Steam

### Установка

```bash
# Включить multilib
sudo nano /etc/pacman.conf
[multilib]
Include = /etc/pacman.d/mirrorlist

sudo pacman -Syu

# Установить Steam
sudo pacman -S steam
```

### Настройка

1. Открыть Steam
2. Настройки → Совместимость
3. Включить "Включить Steam Play для всех продуктов"
4. Выбрать Proton

## Proton

### Версии Proton

| Версия | Описание |
|--------|----------|
| Proton Experimental | Самая новая |
| Proton 8.0 | Стабильная |
| Proton GE | Модифицированная (лучшая совместимость) |

### Установка Proton GE

```bash
# Установить protonup-qt
sudo pacman -S protonup-qt

# Или через yay
yay -S protonup-qt-bin

# Запустить и выбрать Proton GE
```

## Lutris

### Установка

```bash
sudo pacman -S lutris
```

### Использование

1. Открыть Lutris
2. "+" → Импортировать игру
3. Выбрать установщик (exe/setup)
4. Настроить Proton/Wine

## Wine

### Установка

```bash
sudo pacman -S wine
```

### Запуск .exe

```bash
wine game.exe
```

### Настройка

```bash
# Wine конфигурация
winecfg

# Установить библиотеки
winetricks
```

## Оптимизация

### Драйверы

```bash
# NVIDIA
sudo pacman -S nvidia nvidia-utils lib32-nvidia-utils

# AMD
sudo pacman -S mesa vulkan-radeon lib32-vulkan-radeon

# Intel
sudo pacman -S mesa vulkan-intel lib32-vulkan-intel
```

### Мониторинг

```bash
# MangoHud (FPS, температура)
sudo pacman -S mangohud

# Запуск с MangoHud
mangohud %command%

# В Steam: настройки → совместимость → ввести
MANGOHUD=1 %command%
```

### Gamemode

```bash
# Установить
sudo pacman -S gamemode lib32-gamemode

# В Steam: настройки → совместимость → ввести
gamemoderun %command%
```

## Проблемы

```bash
# Установить 32-битные библиотеки
sudo pacman -S lib32-mesa lib32-vulkan-radeon lib32-nvidia-utils

# Обновить кэш шрифтов
fc-cache -fv

# Проверить Vulkan
vulkaninfo
```

## Шпаргалка

```bash
# Установить Steam
sudo pacman -S steam

# Установить Lutris
sudo pacman -S lutris

# MangoHud
sudo pacman -S mangohud

# Gamemode
sudo pacman -S gamemode
```
