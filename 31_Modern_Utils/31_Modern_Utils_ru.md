# Современные утилиты

## bat (улучшенный cat)

```bash
# Установка
sudo pacman -S bat

# Использование
bat file.txt

# С номерами строк
bat -n file.txt

# С подсветкой языка
bat -l python file.py

# В pager
bat -p file.txt
```

## exa/eza (улучшенный ls)

```bash
# Установка
sudo pacman -S eza

# Использование
eza

# С деталями
eza -la

# С деревом
eza --tree

# С иконками
eza --icons

# С цветами
eza -la --color=always
```

## fd (улучшенный find)

```bash
# Установка
sudo pacman -S fd

# Использование
fd pattern

# Поиск по имени
fd "*.txt"

# Поиск в директории
fd pattern /path

# По типу файла
fd -t f pattern
fd -t d pattern

# Игнорировать .gitignore
fd --no-ignore pattern
```

## ripgrep (улучшенный grep)

```bash
# Установка
sudo pacman -S ripgrep

# Использование
rg pattern

# Поиск в файле
rg pattern file.txt

# Рекурсивно
rg pattern /path

# С контекстом
rg -C 3 pattern

# С номерами строк
rg -n pattern

# По типу файла
rg -t py pattern
```

## fzf (fuzzy finder)

```bash
# Установка
sudo pacman -S fzf

# Использование
# Поиск файлов
find . | fzf

# Поиск в истории
history | fzf

# С предпросмотром
fzf --preview 'cat {}'

# Интеграция с vim
vim $(fzf)

# Интеграция с cd
cd $(find -type d | fzf)
```

## zoxide (улучшенный cd)

```bash
# Установка
sudo pacman -S zoxide

# Добавить в .bashrc
eval "$(zoxide init bash)"

# Использование
z pattern

# Интерактивно
zi
```

## starship (промпт)

```bash
# Установка
sudo pacman -S starship

# Добавить в .bashrc
eval "$(starship init bash)"
```

## dust (улучшенный du)

```bash
# Установка
sudo pacman -S dust

# Использование
dust

# В директории
dust /path

# С ограничением
dust -n 10
```

## duf (улучшенный df)

```bash
# Установка
sudo pacman -S duf

# Использование
duf

# Определённые диски
duf /dev/sda1
```

## procs (улучшенный ps)

```bash
# Установка
sudo pacman -S procs

# Использование
procs

# По имени
procs nginx

# Дерево
procs --tree
```

## Шпаргалка

```bash
# Установить все
sudo pacman -S bat eza fd ripgrep fzf zoxide starship dust duf procs

# Быстрый поиск
rg "pattern" .

# Найти файл
fd "name"

# Fuzzy поиск
find . | fzf

# Красивый ls
eza -la --icons

# Красивый cat
bat file.txt
```
