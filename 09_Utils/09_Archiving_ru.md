# Архивация (zip)

## Установка

```bash
sudo pacman -S zip unzip
```

## Создание архива

| Команда | Описание |
|---------|----------|
| `zip archive.zip file` | Заархивировать файл |
| `zip archive.zip file1 file2` | Несколько файлов |
| `zip -r archive.zip dir/` | Заархивировать директорию |
| `zip -r archive.zip dir/ -x "*.log"` | Исключить файлы |
| `zip -e archive.zip file` | С паролем |

### Примеры

```bash
# Заархивировать один файл
zip backup.zip config.txt

# Заархивировать несколько файлов
zip backup.zip file1.txt file2.txt file3.txt

# Заархивировать всю папку
zip -r project.zip myproject/

# Заархивировать с исключениями
zip -r archive.zip folder/ -x "*.tmp" -x "*.cache"

# Заархивировать с паролем
zip -e secret.zip private.txt
```

## Просмотр архива

```bash
# Список файлов в архиве
unzip -l archive.zip

# Проверить архив
zip -T archive.zip
```

## Распаковка

| Команда | Описание |
|---------|----------|
| `unzip archive.zip` | Распаковать в текущую директорию |
| `unzip archive.zip -d /path` | Распаковать в указанную директорию |
| `unzip -o archive.zip` | Перезаписать без вопросов |
| `unzip -n archive.zip` | Не перезаписывать существующие |
| `unzip -l archive.zip` | Посмотреть содержимое |
| `unzip -t archive.zip` | Проверить архив |

### Примеры

```bash
# Распаковать в текущую папку
unzip archive.zip

# Распаковать в конкретную папку
unzip archive.zip -d /home/user/extracted/

# Перезаписать все файлы
unzip -o archive.zip

# Распаковать только конкретный файл
unzip archive.zip file.txt

# Распаковать с wildcard
unzip archive.zip "*.txt"
```

## Обновление архива

```bash
# Добавить файл в архив
zip archive.zip newfile.txt

# Обновить файл в архиве
zip -u archive.zip file.txt

# Удалить файл из архива
zip -d archive.zip file.txt
```

## Другие форматы

### tar.gz

```bash
# Создать
tar -czf archive.tar.gz dir/

# Распаковать
tar -xzf archive.tar.gz

# Просмотреть
tar -tzf archive.tar.gz
```

### tar.bz2

```bash
# Создать
tar -cjf archive.tar.bz2 dir/

# Распаковать
tar -xjf archive.tar.bz2
```

### tar.xz

```bash
# Создать
tar -cJf archive.tar.xz dir/

# Распаковать
tar -xJf archive.tar.xz
```

### 7z

```bash
# Установка
sudo pacman -S p7zip

# Создать
7z a archive.7z dir/

# Распаковать
7z x archive.7z

# Просмотреть
7z l archive.7z
```

## Шпаргалка

```bash
# Быстро заархивировать папку
zip -r backup.zip myproject/

# Быстро распаковать
unzip archive.zip

# Распаковать в папку
unzip archive.zip -d /tmp/extracted/

# Посмотреть что внутри
unzip -l archive.zip
```
