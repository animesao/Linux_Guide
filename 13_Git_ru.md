# Git

## Настройка

```bash
git config --global user.name "Your Name"
git config --global user.email "email@example.com"
git config --global core.editor "vim"
```

## Основные команды

| Команда | Описание |
|---------|----------|
| `git init` | Инициализировать репозиторий |
| `git clone url` | Клонировать репозиторий |
| `git add file` | Добавить файл в staging |
| `git add .` | Добавить все файлы |
| `git commit -m "message"` | Закоммитить |
| `git push` | Отправить на удалённый |
| `git pull` | Получить с удалённого |
| `git status` | Статус |
| `git log` | История коммитов |
| `git log --oneline` | Сокращённая история |
| `git diff` | Различия |

## Ветки

| Команда | Описание |
|---------|----------|
| `git branch` | Список веток |
| `git branch name` | Создать ветку |
| `git checkout name` | Переключиться |
| `git checkout -b name` | Создать и переключиться |
| `git switch name` | Переключиться (новый способ) |
| `git switch -c name` | Создать и переключиться |
| `git branch -d name` | Удалить ветку |
| `git branch -D name` | Принудительно удалить |
| `git merge name` | Слить ветку |
| `git rebase name` | Rebase |

## Удалённые репозитории

| Команда | Описание |
|---------|----------|
| `git remote add origin url` | Добавить удалённый |
| `git remote -v` | Список удалённых |
| `git push -u origin main` | Отправить впервые |
| `git fetch` | Получить без слияния |
| `git pull --rebase` | Pull с rebase |

## Отмена изменений

```bash
# Отменить staging
git reset HEAD file

# Отменить коммит (сохранить изменения)
git reset --soft HEAD~1

# Отменить коммит (удалить изменения)
git reset --hard HEAD~1

# Отменить конкретный коммит
git revert commit_hash

# Отменить изменения в файле
git checkout -- file
```

## Stash

```bash
# Сохранить изменения
git stash

# Сохранить с именем
git stash push -m "description"

# Посмотреть stash
git stash list

# Применить stash
git stash apply

# Применить и удалить
git stash pop

# Удалить stash
git stash drop
```

## Теги

```bash
# Создать тег
git tag v1.0.0

# Создать тег с описанием
git tag -a v1.0.0 -m "Release 1.0.0"

# Отправить теги
git push --tags

# Список тегов
git tag
```

## Полезные алиасы

```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.lg "log --oneline --graph --all"
```

## Шпаргалка

```bash
# Быстрый коммит
git add . && git commit -m "update"

# Посмотреть историю
git log --oneline --graph

# Создать ветку и переключиться
git checkout -b feature

# Слить ветку
git merge feature

# Отправить
git push origin main
```
