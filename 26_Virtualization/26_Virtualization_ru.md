# Виртуализация

## KVM/QEMU

### Установка

```bash
sudo pacman -S qemu-full virt-manager libvirt dnsmasq

# Запустить libvirt
sudo systemctl enable --now libvirtd

# Добавить пользователя в группу
sudo usermod -aG libvirt $USER
```

### Проверка

```bash
# Проверить поддержку виртуализации
egrep -c '(vmx|svm)' /proc/cpuinfo

# KVM модуль
lsmod | grep kvm
```

## Virt-Manager

### Запуск

```bash
virt-manager
```

### Создание виртуальной машины

1. Файл → Новая виртуальная машина
2. Выбрать ISO
3. Настроить RAM, CPU, диск
4. Запустить

## Управление через CLI

```bash
# Список ВМ
virsh list --all

# Запустить
virsh start vm_name

# Остановить
virsh shutdown vm_name

# Удалить
virsh undefine vm_name --remove-all-storage

# Подключиться
virsh console vm_name

# Информация
virsh dominfo vm_name
```

## Snapshots

```bash
# Создать снапшот
virsh snapshot-create-as vm_name snapshot_name

# Список снапшотов
virsh snapshot-list vm_name

# Восстановить
virsh snapshot-revert vm_name snapshot_name

# Удалить
virsh snapshot-delete vm_name snapshot_name
```

## Образы

```bash
# Конвертировать
qemu-img convert -f raw -O qcow2 image.img image.qcow2

# Создать
qemu-img create -f qcow2 disk.qcow2 50G

# Информация
qemu-img info disk.qcow2

# Увеличить
qemu-img resize disk.qcow2 +50G
```

## Виртуальная сеть

```bash
# Список сетей
virsh net-list --all

# Запустить сеть
virsh net-start default

# Автозапуск
virsh net-autostart default

# Настройки сети
virsh net-info default
```

## Шпаргалка

```bash
# Список ВМ
virsh list --all

# Запустить ВМ
virsh start myvm

# Создать снапшот
virsh snapshot-create-as myvm snap1

# Создать диск
qemu-img create -f qcow2 disk.qcow2 50G
```
