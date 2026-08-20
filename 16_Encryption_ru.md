# Шифрование

## GPG (GnuPG)

| Команда | Описание |
|---------|----------|
| `gpg --gen-key` | Сгенерировать ключ |
| `gpg --list-keys` | Список ключей |
| `gpg --list-secret-keys` | Список секретных ключей |
| `gpg --export -a "name"` | Экспортировать публичный ключ |
| `gpg --export-secret-keys -a "name"` | Экспортировать приватный ключ |
| `gpg --import key.gpg` | Импортировать ключ |
| `gpg --delete-key "name"` | Удалить ключ |
| `gpg --sign file` | Подписать файл |
| `gpg --verify file` | Проверить подпись |

### Шифрование файла

```bash
# Зашифровать
gpg -c file.txt

# Расшифровать
gpg file.txt.gpg

# Зашифровать для конкретного получателя
gpg -e -r "email@example.com" file.txt
```

## SSH-ключи

### Генерация

```bash
# Ed25519 (рекомендуется)
ssh-keygen -t ed25519 -C "email@example.com"

# RSA (legacy)
ssh-keygen -t rsa -b 4096 -C "email@example.com"
```

### Управление

```bash
# Копировать ключ на сервер
ssh-copy-id user@host

# Проверить подключение
ssh -T git@github.com

# Список ключей
ls ~/.ssh/

# ssh-agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

### Конфиг `~/.ssh/config`

```
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed2559

Host server
    HostName 192.168.1.100
    User myuser
    Port 22
```

## LUKS (шифрование дисков)

```bash
# Зашифровать раздел
sudo cryptsetup luksFormat /dev/sdXN

# Открыть зашифрованный раздел
sudo cryptsetup open /dev/sdXN myvolume

# Создать файловую систему
sudo mkfs.ext4 /dev/mapper/myvolume

# Смонтировать
sudo mount /dev/mapper/myvolume /mnt

# Закрыть раздел
sudo umount /mnt
sudo cryptsetup close myvolume
```

## age (современная замена GPG)

```bash
# Установка
sudo pacman -S age

# Генерация ключей
age-keygen -o key.txt

# Зашифровать
age -r age1public_key... -o file.txt.age file.txt

# Расшифровать
age -d -i key.txt -o file.txt file.txt.age
```

## OpenSSL

```bash
# Зашифровать файл
openssl enc -aes-256-cbc -salt -in file.txt -out file.enc

# Расшифровать
openssl enc -d -aes-256-cbc -in file.enc -out file.txt

# Сгенерировать ключ
openssl rand -base64 32

# Хэш пароля
openssl passwd -6 "password"
```

## Шпаргалка

```bash
# Генерация SSH-ключа
ssh-keygen -t ed25519

# Копировать ключ
ssh-copy-id user@server

# Зашифровать файл
gpg -c important.txt

# Расшифровать
gpg important.txt.gpg
```
