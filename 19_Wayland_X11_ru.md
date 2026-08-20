# Wayland и X11

## Какой протокол используется

```bash
# Проверить
echo $XDG_SESSION_TYPE

# Wayland
wayland

# X11
x11
```

## Wayland

### Композиторы

| Композитор | Описание |
|------------|----------|
| `sway` | i3 для Wayland |
| `hyprland` | Современный композитор |
| `kwin_wayland` | KDE |
| `mutter` | GNOME |

### Установка sway

```bash
sudo pacman -S sway waybar wofi wl-clipboard grim slurp
```

### Конфиг sway

Файл `~/.config/sway/config`:

```
# Модификатор
set $mod Mod4

# Запуск терминала
bindsym $mod+Return exec alacritty

# Закрыть окно
bindsym $mod+Shift+q kill

# Переключение
bindsym $mod+Left focus left
bindsym $mod+Right focus right
bindsym $mod+Up focus up
bindsym $mod+Down focus down

# Запуск
bindsym $mod+d exec wofi --show drun
```

### Утилиты

```bash
# Скриншот
grim -g "$(slurp)" screenshot.png

# Буфер обмена
wl-copy "text"
wl-paste

# Мониторы
swaymsg -t get_outputs
```

## X11

### Настройка

```bash
# Конфиг Xorg
/etc/X11/xorg.conf.d/

# Генерация конфига
sudo Xorg -configure
```

### Настройка разрешения

```bash
# Посмотреть разрешение
xrandr

# Установить разрешение
xrandr --output DP-1 --mode 1920x1080

# Частота обновления
xrandr --output DP-1 --mode 1920x1080 --rate 144
```

### xinit

```bash
# Запуск X
startx

# Конфиг ~/.xinitrc
exec sway
# или
exec i3
```

## Clipboard

```bash
# Wayland
wl-copy "text"
wl-paste

# X11
xclip -selection clipboard
xsel --clipboard

# Универсально
sudo pacman -S xclip
echo "text" | xclip -selection clipboard
```

## Режим совместимости

```bash
# Запуск X-приложения в Wayland
QT_QPA_PLATFORM=xcb program

# Через XWayland (автоматически)
# Большинство приложений работают
```

## Шпаргалка

```bash
# Проверить протокол
echo $XDG_SESSION_TYPE

# Wayland скриншот
grim -g "$(slurp)" screen.png

# X11 разрешение
xrandr

# Clipboard
wl-copy "hello"
wl-paste
```
