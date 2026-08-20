# Полезные утилиты

## Архивация

| Команда | Описание |
|---------|----------|
| `tar -czf archive.tar.gz dir/` | Создать .tar.gz |
| `tar -xzf archive.tar.gz` | Распаковать .tar.gz |
| `tar -cjf archive.tar.bz2 dir/` | Создать .tar.bz2 |
| `tar -xjf archive.tar.bz2` | Распаковать .tar.bz2 |
| `unzip archive.zip` | Распаковать .zip |
| `zip -r archive.zip dir/` | Создать .zip |

## Скачивание

| Команда | Описание |
|---------|----------|
| `wget url` | Скачать файл |
| `wget -c url` | Продолжить скачивание |
| `curl -O url` | Скачать файл |
| `curl url -o file` | Скачать с именем |

## Конвертация

```bash
# Кодировка текста
iconv -f FROM -t TO file

# Кодировка видео
ffmpeg -i input.mp4 output.avi

# Кодировка аудио
ffmpeg -i input.mp3 output.flac

# Изменить размер изображения
convert input.jpg -resize 800x600 output.jpg
```

## Мониторинг

| Команда | Описание |
|---------|----------|
| `htop` | Мониторинг процессов |
| `btop` | Красивый монитор |
| `iotop` | Мониторинг дисков |
| `nload` | Мониторинг сети |
| `glances` | Всё в одном |
| `dstat` | Статистика системы |

## Сравнение файлов

```bash
# Сравнить два файла
diff file1 file2

# Побочный diff
diff -y file1 file2

# Игнорировать пробелы
diff -b file1 file2

# Сравнить директории
diff -r dir1 dir2

# Сравнить файлы (vimdiff)
vimdiff file1 file2
```

## Бэкапы

```bash
# Рsync (резервное копирование)
rsync -av source/ dest/

# С удалённого сервера
rsync -avz user@host:/path/ /local/path/

# С exceptions
rsync -av --exclude='*.log' source/ dest/
```

## Скриншоты

```bash
# Скриншот (нужен scrot)
scrot screenshot.png

# С задержкой
scrot -d 5 screenshot.png

# Область экрана
scrot -s screenshot.png

# flameshot (GUI)
flameshot gui
```

## Терминал

| Команда | Описание |
|---------|----------|
| `tmux` | Мультиплексор терминала |
| `screen` | Эмуляция терминала |
| `script session.log` | Запись сессии |
| `clear` | Очистить экран |

### tmux основы

```bash
# Создать сессию
tmux

# Отсоединиться
Ctrl+B, D

# Присоединиться
tmux attach

# Новое окно
Ctrl+B, C

# Переключение
Ctrl+B, 0-9
```

## Автодополнение

```bash
# Включить автодополнение
source /usr/share/bash-completion/bash_completion

# Добавить в .bashrc
echo 'source /usr/share/bash-completion/bash_completion' >> ~/.bashrc
```

## Шпаргалка

```bash
# Создать бэкап
tar -czf backup.tar.gz /important/dir/

# Скачать файл
wget https://example.com/file.zip

# Просмотреть архив
tar -tzf archive.tar.gz

# Распаковать архив
tar -xzf archive.tar.gz

# Записать сессию терминала
script session.log
```
