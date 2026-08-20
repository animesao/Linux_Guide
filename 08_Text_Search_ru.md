# Текст и поиск

## Поиск в файлах

| Команда | Описание |
|---------|----------|
| `grep "text" file` | Найти текст в файле |
| `grep -r "text" /path` | Рекурсивный поиск |
| `grep -i "text" file` | Поиск без учёта регистра |
| `grep -n "text" file` | Показать номера строк |
| `grep -c "text" file` | Подсчитать совпадения |
| `grep -v "text" file` | Исключить совпадения |
| `grep -A 3 "text" file` | 3 строки после совпадения |
| `grep -B 3 "text" file` | 3 строки до совпадения |

## Поиск с помощью find

```bash
# Найти файлы по имени
find /path -name "*.txt"

# Найти директории
find /path -type d -name "name"

# Найти по размеру
find /path -size +100M

# Найти по дате
find /path -mtime -7

# Найти и выполнить команду
find /path -name "*.log" -exec rm {} \;
```

## Регулярные выражения

| Паттерн | Описание |
|---------|----------|
| `.` | Любой символ |
| `*` | 0 или более |
| `+` | 1 или более |
| `?` | 0 или 1 |
| `[abc]` | Один из символов |
| `[^abc]` | Не один из символов |
| `^` | Начало строки |
| `$` | Конец строки |
| `\b` | Граница слова |

## sed (редактирование)

```bash
# Замена текста
sed 's/old/new/g' file

# Замена в файле (in-place)
sed -i 's/old/new/g' file

# Удалить строку
sed '/pattern/d' file

# Вставить строку
sed '3i\new line' file

# Показать строки 5-10
sed -n '5,10p' file
```

## awk (обработка текста)

```bash
# Вывести первый столбец
awk '{print $1}' file

# Вывести столбцы
awk '{print $1, $3}' file

# С разделителем
awk -F: '{print $1}' /etc/passwd

# Условие
awk '$3 > 100' file

# Подсчёт
awk '{sum += $1} END {print sum}' file
```

## sort и uniq

```bash
# Сортировка
sort file

# Сортировка чисел
sort -n file

# Уникальные строки
sort file | uniq

# Подсчёт повторений
sort file | uniq -c

# Сортировка по количеству
sort file | uniq -c | sort -rn
```

## wc (подсчёт)

```bash
# Строки
wc -l file

# Слова
wc -w file

# Символы
wc -c file
```

## Шпаргалка

```bash
# Найти IP-адреса в логе
grep -oE "[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+" log.txt

# Заменить текст в файле
sed -i 's/old_text/new_text/g' file.txt

# Вывести уникальные IP
grep -oE "[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+" log.txt | sort | uniq

# Подсчитать количество строк
wc -l file.txt

# Найти файлы больше 100MB
find / -size +100M -type f
```
