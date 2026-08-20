# Shell скрипты

## Структура скрипта

```bash
#!/bin/bash

# Комментарий

echo "Hello, World!"
```

## Переменные

```bash
# Объявление
name="Linux"
age=25

# Использование
echo "OS: $name"
echo "Age: ${age}"

# Чтение ввода
read -p "Enter name: " username
echo "Hello, $username"

# Системные переменные
echo $HOME
echo $USER
echo $PWD
echo $PATH
```

## Арифметика

```bash
a=10
b=3

echo $((a + b))     # 13
echo $((a - b))     # 7
echo $((a * b))     # 30
echo $((a / b))     # 3
echo $((a % b))     # 1
echo $((a ** 2))    # 100

# Более сложные вычисления
echo "scale=2; 10/3" | bc
```

## Условия

```bash
# if/elif/else
if [ "$a" -gt "$b" ]; then
    echo "a больше"
elif [ "$a" -lt "$b" ]; then
    echo "a меньше"
else
    echo "равны"
fi

# Сравнение строк
if [ "$str1" = "$str2" ]; then
    echo "равны"
fi

# Проверка файла
if [ -f "file.txt" ]; then
    echo "файл существует"
fi

if [ -d "dir" ]; then
    echo "директория существует"
fi

# Проверка команды
if command -v git &> /dev/null; then
    echo "git установлен"
fi
```

### Операторы сравнения

| Оператор | Описание |
|----------|----------|
| `-eq` | Равно |
| `-ne` | Не равно |
| `-gt` | Больше |
| `-lt` | Меньше |
| `-ge` | Больше или равно |
| `-le` | Меньше или равно |
| `=` | Строки равны |
| `!=` | Строки не равны |
| `-f` | Файл существует |
| `-d` | Директория существует |
| `-z` | Строка пуста |
| `-n` | Строка не пуста |

## Циклы

```bash
# for
for i in 1 2 3 4 5; do
    echo "Number: $i"
done

# for с диапазоном
for i in {1..10}; do
    echo $i
done

# for (C-style)
for ((i=0; i<10; i++)); do
    echo $i
done

# while
while [ condition ]; do
    echo "loop"
    sleep 1
done

# until
until [ condition ]; do
    echo "waiting"
    sleep 1
done

# Бесконечный цикл
while true; do
    echo " forever"
    sleep 1
done
```

## Функции

```bash
# Простая функция
greet() {
    echo "Hello, $1!"
}

# Вызов
greet "World"

# Функция с возвратом
add() {
    echo $(( $1 + $2 ))
}

result=$(add 5 3)
echo "Sum: $result"
```

## Аргументы

```bash
#!/bin/bash

echo "Script name: $0"
echo "Arg 1: $1"
echo "Arg 2: $2"
echo "All args: $@"
echo "Number of args: $#"
```

## Обработка ошибок

```bash
#!/bin/bash

set -e  # Остановка при ошибке
set -u  # Ошибка при неопределённой переменной
set -o pipefail  # Ошибка в pipe

# Проверка команды
if ! command -v docker &> /dev/null; then
    echo "Docker не установлен"
    exit 1
fi
```

## Полезные паттерны

```bash
# Проверить существует ли файл
[ -f "$file" ] && echo "exists" || echo "not found"

# Запустить с sudo если нужно
[ $EUID -ne 0 ] && exec sudo "$0" "$@"

# Перейти в директорию скрипта
cd "$(dirname "$0")"

# Замерить время выполнения
time {
    # команды
}
```

## Шпаргалка

```bash
#!/bin/bash
set -euo pipefail

NAME="Linux"
echo "Hello, $NAME"

for i in {1..5}; do
    echo "Count: $i"
done

if [ -f "/etc/passwd" ]; then
    echo "File exists"
fi
```
