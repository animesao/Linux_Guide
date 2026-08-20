# Flatpak и Snap

## Flatpak

### Установка

```bash
sudo pacman -S flatpak
```

### Команды

| Команда | Описание |
|---------|----------|
| `flatpak install app` | Установить приложение |
| `flatpak uninstall app` | Удалить |
| `flatpak list` | Список установленных |
| `flatpak update` | Обновить всё |
| `flatpak search keyword` | Найти приложение |
| `flatpak run app` | Запустить |
| `flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo` | Добавить Flathub |

### Примеры

```bash
# Добавить Flathub
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo

# Установить Firefox
flatpak install flathub org.mozilla.firefox

# Установить VS Code
flatpak install flathub com.visualstudio.code

# Установить Discord
flatpak install flathub com.discordapp.Discord

# Запустить
flatpak run org.mozilla.firefox

# Обновить всё
flatpak update
```

### Очистка

```bash
# Удалить неиспользуемые runtime
flatpak uninstall --unused

# Очистить кэш
flatpak repair
```

## Snap

### Установка

```bash
# Установить snapd
sudo pacman -S snapd

# Запустить
sudo systemctl enable --now snapd.socket

# Символическая ссылка
sudo ln -s /var/lib/snapd/snap /snap
```

### Команды

| Команда | Описание |
|---------|----------|
| `sudo snap install app` | Установить |
| `sudo snap remove app` | Удалить |
| `snap list` | Список |
| `sudo snap refresh` | Обновить |
| `snap find keyword` | Найти |
| `snap run app` | Запустить |

### Примеры

```bash
# Установить Firefox
sudo snap install firefox

# Установить VS Code
sudo snap install code --classic

# Установить Telegram
sudo snap install telegram-desktop

# Список
snap list

# Обновить всё
sudo snap refresh
```

## Сравнение

| Критерий | Flatpak | Snap |
|----------|---------|------|
| Пакеты | Flathub | Snap Store |
| Размер | Больше | Больше |
| Запуск | Быстрее | Медленнее |
| Изоляция | Да | Да |
| Автообновление | Нет | Да |

## Шпаргалка

```bash
# Flatpak: добавить Flathub
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo

# Flatpak: установить
flatpak install flathub org.mozilla.firefox

# Snap: установить
sudo snap install firefox

# Flatpak: обновить
flatpak update

# Snap: обновить
sudo snap refresh
```
