# Linux Guide

<p align="center">
  <img src="https://img.shields.io/badge/OS-Arch%20Linux-1793D1?style=for-the-badge&logo=archlinux&logoColor=white"/>
  <img src="https://img.shields.io/badge/Language-RU%20%7C%20EN-blue?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Files-62-green?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Topics-31-purple?style=for-the-badge"/>
</p>

<p align="center">
  Полная шпаргалка по Linux для новичков. 31 тема на двух языках.
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
| Настроить SSH сервер | [21 - SSH сервер](#21-ssh-сервер) |
| Запустить веб-сервер | [22 - Веб-сервер](#22-веб-сервер) |
| Работать с базами данных | [23 - Базы данных](#23-базы-данных) |
| Настроить окружение разработки | [24 - Разработка](#24-разработка) |
| Играть в игры на Linux | [25 - Игры](#25-игры-на-linux) |
| Создать виртуальную машину | [26 - Виртуализация](#26-виртуализация) |
| Установить Flatpak / Snap | [27 - Flatpak/Snap](#27-flatpak--snap) |
| Настроить общий доступ к файлам | [28 - Samba/NFS](#28-samba--nfs) |
| Подключить VPN | [29 - VPN](#29-vpn) |
| Настроить Btrfs / снапшоты | [30 - Btrfs](#30-btrfs--снапшоты) |
| Установить modern утилиты | [31 - Современные утилиты](#31-современные-утилиты) |

---

## Содержание

### 1. Основные команды
> Навигация, файлы, права доступа, поиск, редактирование, горячие клавиши

| [Russian](01_Basics/01_Basic_Commands_ru.md) | [English](01_Basics/01_Basic_Commands_en.md) |
|------------------------------------------------|------------------------------------------------|

### 2. Диски и монтирование
> lsblk, blkid, mount, fstab, swap, разделы, NTFS/ext4/exFAT

| [Russian](02_Disks/02_Disks_Mounting_ru.md) | [English](02_Disks/02_Disks_Mounting_en.md) |
|-----------------------------------------------|-----------------------------------------------|

### 3. Управление пакетами
> pacman, AUR, yay/paru, группы пакетов, кэш

| [Russian](03_Packages/03_Package_Management_ru.md) | [English](03_Packages/03_Package_Management_en.md) |
|------------------------------------------------------|------------------------------------------------------|

### 4. Информация о системе
> CPU, RAM, температура, железо, neofetch, uptime

| [Russian](04_System/04_System_Info_ru.md) | [English](04_System/04_System_Info_en.md) |
|---------------------------------------------|---------------------------------------------|

### 5. Сеть
> ip, NetworkManager, SSH, DNS, firewall, ping, wget

| [Russian](05_Network/05_Network_ru.md) | [English](05_Network/05_Network_en.md) |
|------------------------------------------|------------------------------------------|

### 6. Пользователи и группы
> adduser, usermod, sudo, passwd, группы, UID/GID

| [Russian](06_Users/06_Users_Permissions_ru.md) | [English](06_Users/06_Users_Permissions_en.md) |
|--------------------------------------------------|--------------------------------------------------|

### 7. Процессы
> top, htop, kill, systemd, фон, приоритеты, pgrep

| [Russian](07_Processes/07_Processes_ru.md) | [English](07_Processes/07_Processes_en.md) |
|----------------------------------------------|----------------------------------------------|

### 8. Текст и поиск
> grep, sed, awk, find, sort, uniq, regex, wc

| [Russian](08_Search/08_Text_Search_ru.md) | [English](08_Search/08_Text_Search_en.md) |
|---------------------------------------------|---------------------------------------------|

### 9. Полезные утилиты
> tar, zip, wget, curl, ffmpeg, tmux, rsync, скриншоты

| [Russian](09_Utils/09_Utilities_ru.md) | [English](09_Utils/09_Utilities_en.md) |
|------------------------------------------|------------------------------------------|

### 10. Systemd
> systemctl, journalctl, сервисы, таймеры, создание сервиса

| [Russian](10_Systemd/10_Systemd_ru.md) | [English](10_Systemd/10_Systemd_en.md) |
|------------------------------------------|------------------------------------------|

### 11. Cron
> crontab, расписание, at, anacron

| [Russian](11_Cron/11_Cron_ru.md) | [English](11_Cron/11_Cron_en.md) |
|------------------------------------|------------------------------------|

### 12. Docker
> контейнеры, образы, docker-compose, сети, порты

| [Russian](12_Docker/12_Docker_ru.md) | [English](12_Docker/12_Docker_en.md) |
|----------------------------------------|----------------------------------------|

### 13. Git
> init, commit, branch, merge, rebase, stash, теги, алиасы

| [Russian](13_Git/13_Git_ru.md) | [English](13_Git/13_Git_en.md) |
|----------------------------------|----------------------------------|

### 14. Shell скрипты
> переменные, условия, циклы, функции, аргументы, ошибки

| [Russian](14_Scripts/14_Shell_Scripts_ru.md) | [English](14_Scripts/14_Shell_Scripts_en.md) |
|------------------------------------------------|------------------------------------------------|

### 15. Логирование
> journalctl, /var/log, logrotate, настройка журнала

| [Russian](15_Logging/15_Logging_ru.md) | [English](15_Logging/15_Logging_en.md) |
|------------------------------------------|------------------------------------------|

### 16. Шифрование
> GPG, SSH-ключи, LUKS, age, OpenSSL

| [Russian](16_Encryption/16_Encryption_ru.md) | [English](16_Encryption/16_Encryption_en.md) |
|------------------------------------------------|------------------------------------------------|

### 17. Железо и драйверы
> GPU, звук, Bluetooth, принтеры, lspci, lsusb, модули

| [Russian](17_Hardware/17_Hardware_ru.md) | [English](17_Hardware/17_Hardware_en.md) |
|--------------------------------------------|--------------------------------------------|

### 18. Проблемы и отладка
> загрузка, сеть, диск, память, pacman, chroot, восстановление

| [Russian](18_Troubleshoot/18_Troubleshooting_ru.md) | [English](18_Troubleshoot/18_Troubleshooting_en.md) |
|-------------------------------------------------------|-------------------------------------------------------|

### 19. Wayland и X11
> sway, hyprland, xrandr, clipboard, скриншоты

| [Russian](19_Wayland/19_Wayland_X11_ru.md) | [English](19_Wayland/19_Wayland_X11_en.md) |
|----------------------------------------------|----------------------------------------------|

### 20. Arch Linux
> mkinitcpio, bootloader, pacman.conf, mirrorlist, AUR

| [Russian](20_Arch/20_Arch_Linux_ru.md) | [English](20_Arch/20_Arch_Linux_en.md) |
|------------------------------------------|------------------------------------------|

### 21. SSH сервер
> Настройка sshd, ключи, туннели, fail2ban

| [Russian](21_SSH_Server/21_SSH_Server_ru.md) | [English](21_SSH_Server/21_SSH_Server_en.md) |
|------------------------------------------------|------------------------------------------------|

### 22. Веб-сервер
> Nginx, SSL, Let's Encrypt, PHP, reverse proxy

| [Russian](22_WebServer/22_WebServer_ru.md) | [English](22_WebServer/22_WebServer_en.md) |
|----------------------------------------------|----------------------------------------------|

### 23. Базы данных
> PostgreSQL, MySQL/MariaDB, Redis, psql

| [Russian](23_Databases/23_Databases_ru.md) | [English](23_Databases/23_Databases_en.md) |
|----------------------------------------------|----------------------------------------------|

### 24. Разработка
> Python, Node.js, PHP, Rust, Go, компиляция

| [Russian](24_Development/24_Development_ru.md) | [English](24_Development/24_Development_en.md) |
|--------------------------------------------------|--------------------------------------------------|

### 25. Игры на Linux
> Steam, Proton, Lutris, Wine, MangoHud, Gamemode

| [Russian](25_Gaming/25_Gaming_ru.md) | [English](25_Gaming/25_Gaming_en.md) |
|----------------------------------------|----------------------------------------|

### 26. Виртуализация
> KVM, QEMU, Virt-Manager, снапшоты, образы

| [Russian](26_Virtualization/26_Virtualization_ru.md) | [English](26_Virtualization/26_Virtualization_en.md) |
|-------------------------------------------------------|-------------------------------------------------------|

### 27. Flatpak и Snap
> Flathub, Snap Store, установка, обновление, очистка

| [Russian](27_Flatpak_Snap/27_Flatpak_Snap_ru.md) | [English](27_Flatpak_Snap/27_Flatpak_Snap_en.md) |
|----------------------------------------------------|----------------------------------------------------|

### 28. Samba и NFS
> Общий доступ к файлам, Windows/Linux, сервер, клиент

| [Russian](28_Samba_NFS/28_Samba_NFS_ru.md) | [English](28_Samba_NFS/28_Samba_NFS_en.md) |
|----------------------------------------------|----------------------------------------------|

### 29. VPN
> WireGuard, OpenVPN, PPTP/L2TP, настройка

| [Russian](29_VPN/29_VPN_ru.md) | [English](29_VPN/29_VPN_en.md) |
|----------------------------------|----------------------------------|

### 30. Btrfs и снапшоты
> Файловая система, подvolюмы, Timeshift, сжатие

| [Russian](30_Btrfs/30_Btrfs_ru.md) | [English](30_Btrfs/30_Btrfs_en.md) |
|--------------------------------------|--------------------------------------|

### 31. Современные утилиты
> bat, eza, fd, ripgrep, fzf, zoxide, starship, dust, duf

| [Russian](31_Modern_Utils/31_Modern_Utils_ru.md) | [English](31_Modern_Utils/31_Modern_Utils_en.md) |
|----------------------------------------------------|----------------------------------------------------|

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

### Docker
```bash
docker ps                   # контейнеры
docker run -d -p 80:80 nginx # запустить
docker exec -it name bash   # войти
docker compose up -d        # compose
```

### Modern утилиты
```bash
bat file.txt        # красивый cat
eza -la             # красивый ls
fd "pattern"        # быстрый find
rg "pattern" .      # быстрый grep
find . | fzf        # fuzzy поиск
```

---

## Лицензия

MIT — используйте как хотите.
