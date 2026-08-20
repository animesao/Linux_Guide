# Linux Guide

<p align="center">
  <img src="https://img.shields.io/badge/OS-Arch%20Linux-1793D1?style=for-the-badge&logo=archlinux&logoColor=white"/>
  <img src="https://img.shields.io/badge/Language-RU%20%7C%20EN-blue?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Files-40-green?style=for-the-badge"/>
</p>

<p align="center">
  Полная шпаргалка по Linux для новичков. Каждая тема на двух языках.
</p>

---

## Быстрый старт

| Что нужно сделать | Где смотреть |
|--------------------|--------------|
| Начать использовать терминал | [01 - Основные команды](#1-основные-команды) |
| Смонтировать диск / USB | [02 - Диски и монтирование](#2-диски-и-монтирование) |
| Установить программу | [03 - Управление пакетами](#3-управление-пакетами) |
| Узнать информацию о системе | [04 - Информация о системе](#4-информация-о-системе) |
| Настроить сеть / Wi-Fi | [05 - Сеть](#5-сеть) |
| Создать пользователя | [06 - Пользователи и группы](#6-пользователи-и-группы) |
| Убить зависший процесс | [07 - Процессы](#7-процессы) |
| Найти текст в файлах | [08 - Текст и поиск](#8-текст-и-поиск) |
| Скачать файл / создать архив | [09 - Полезные утилиты](#9-полезные-утилиты) |
| Настроить автозапуск сервиса | [10 - Systemd](#10-systemd) |
| Запланировать задачу по времени | [11 - Cron](#11-cron) |
| Запустить контейнер | [12 - Docker](#12-docker) |
| Работать с Git | [13 - Git](#13-git) |
| Написать скрипт | [14 - Shell скрипты](#14-shell-скрипты) |
| Посмотреть логи | [15 - Логирование](#15-логирование) |
| Зашифровать файл / SSH-ключи | [16 - Шифрование](#16-шифрование) |
| Узнать какое железо | [17 - Железо и драйверы](#17-железо-и-драйверы) |
| Исправить проблему | [18 - Отладка](#18-проблемы-и-отладка) |
| Настроить Wayland / X11 | [19 - Wayland/X11](#19-wayland-x11) |
| Специфика Arch Linux | [20 - Arch Linux](#20-arch-linux) |

---

## Содержание

### 1. Основные команды
> Навигация, файлы, права доступа, поиск, редактирование, горячие клавиши

| [Russian](01_Basic_Commands_ru.md) | [English](01_Basic_Commands_en.md) |
|-------------------------------------|-------------------------------------|

### 2. Диски и монтирование
> lsblk, blkid, mount, fstab, swap, разделы, NTFS/ext4/exFAT

| [Russian](02_Disks_Mounting_ru.md) | [English](02_Disks_Mounting_en.md) |
|--------------------------------------|--------------------------------------|

### 3. Управление пакетами
> pacman, AUR, yay/paru, группы пакетов, кэш

| [Russian](03_Package_Management_ru.md) | [English](03_Package_Management_en.md) |
|------------------------------------------|------------------------------------------|

### 4. Информация о системе
> CPU, RAM, температура, железо, neofetch, uptime

| [Russian](04_System_Info_ru.md) | [English](04_System_Info_en.md) |
|----------------------------------|----------------------------------|

### 5. Сеть
> ip, NetworkManager, SSH, DNS, firewall, ping, wget

| [Russian](05_Network_ru.md) | [English](05_Network_en.md) |
|------------------------------|------------------------------|

### 6. Пользователи и группы
> adduser, usermod, sudo, passwd, группы, UID/GID

| [Russian](06_Users_Permissions_ru.md) | [English](06_Users_Permissions_en.md) |
|-----------------------------------------|-----------------------------------------|

### 7. Процессы
> top, htop, kill, systemd, фон, приоритеты, pgrep

| [Russian](07_Processes_ru.md) | [English](07_Processes_en.md) |
|--------------------------------|--------------------------------|

### 8. Текст и поиск
> grep, sed, awk, find, sort, uniq, regex, wc

| [Russian](08_Text_Search_ru.md) | [English](08_Text_Search_en.md) |
|----------------------------------|----------------------------------|

### 9. Полезные утилиты
> tar, zip, wget, curl, ffmpeg, tmux, rsync, скриншоты

| [Russian](09_Utilities_ru.md) | [English](09_Utilities_en.md) |
|--------------------------------|--------------------------------|

### 10. Systemd
> systemctl, journalctl, сервисы, таймеры, создание сервиса

| [Russian](10_Systemd_ru.md) | [English](10_Systemd_en.md) |
|------------------------------|------------------------------|

### 11. Cron
> crontab, расписание, at, anacron

| [Russian](11_Cron_ru.md) | [English](11_Cron_en.md) |
|----------------------------|----------------------------|

### 12. Docker
> контейнеры, образы, docker-compose, сети, порты

| [Russian](12_Docker_ru.md) | [English](12_Docker_en.md) |
|------------------------------|------------------------------|

### 13. Git
> init, commit, branch, merge, rebase, stash, теги, алиасы

| [Russian](13_Git_ru.md) | [English](13_Git_en.md) |
|---------------------------|---------------------------|

### 14. Shell скрипты
> переменные, условия, циклы, функции, аргументы, ошибки

| [Russian](14_Shell_Scripts_ru.md) | [English](14_Shell_Scripts_en.md) |
|-------------------------------------|-------------------------------------|

### 15. Логирование
> journalctl, /var/log, logrotate, настройка журнала

| [Russian](15_Logging_ru.md) | [English](15_Logging_en.md) |
|-------------------------------|-------------------------------|

### 16. Шифрование
> GPG, SSH-ключи, LUKS, age, OpenSSL

| [Russian](16_Encryption_ru.md) | [English](16_Encryption_en.md) |
|----------------------------------|----------------------------------|

### 17. Железо и драйверы
> GPU, звук, Bluetooth, принтеры, lspci, lsusb, модули

| [Russian](17_Hardware_ru.md) | [English](17_Hardware_en.md) |
|-------------------------------|-------------------------------|

### 18. Проблемы и отладка
> загрузка, сеть, диск, память, pacman, chroot, восстановление

| [Russian](18_Troubleshooting_ru.md) | [English](18_Troubleshooting_en.md) |
|---------------------------------------|---------------------------------------|

### 19. Wayland и X11
> sway, hyprland, xrandr, clipboard, скриншоты

| [Russian](19_Wayland_X11_ru.md) | [English](19_Wayland_X11_en.md) |
|-----------------------------------|-----------------------------------|

### 20. Arch Linux
> mkinitcpio, bootloader, pacman.conf, mirrorlist, AUR

| [Russian](20_Arch_Linux_ru.md) | [English](20_Arch_Linux_en.md) |
|----------------------------------|----------------------------------|

---

## Быстрая навигация по командам

### Файлы и директории
```bash
ls -la              # все файлы с деталями
cd /path            # перейти
cp -r dir1 dir2     # копировать
rm -rf dir          # удалить
find / -name "*.txt" # найти
```

### Диски
```bash
lsblk -f            # все диски
sudo mount /dev/sdXN /mnt  # смонтировать
df -h               # место на диске
sudo blkid          # UUID разделов
```

### Система
```bash
sudo pacman -Syu    # обновить
htop                # процессы
free -h             # RAM
systemctl status x  # сервис
journalctl -u x     # логи
```

### Сеть
```bash
ip addr             # мой IP
ping google.com     # проверка
ssh user@host       # подключение
nmcli device wifi connect "SSID" password "pass"
```

### Git
```bash
git add . && git commit -m "msg"
git push
git pull
git checkout -b feature
```

---

## Лицензия

MIT — используйте как хотите.
# Linux_Guide
