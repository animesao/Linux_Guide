# Virtualization

## KVM/QEMU

### Installation

```bash
sudo pacman -S qemu-full virt-manager libvirt dnsmasq

# Start libvirt
sudo systemctl enable --now libvirtd

# Add user to group
sudo usermod -aG libvirt $USER
```

### Check

```bash
# Check virtualization support
egrep -c '(vmx|svm)' /proc/cpuinfo

# KVM module
lsmod | grep kvm
```

## Virt-Manager

### Launch

```bash
virt-manager
```

### Create VM

1. File → New Virtual Machine
2. Select ISO
3. Configure RAM, CPU, disk
4. Start

## CLI Management

```bash
# List VMs
virsh list --all

# Start
virsh start vm_name

# Stop
virsh shutdown vm_name

# Delete
virsh undefine vm_name --remove-all-storage

# Connect
virsh console vm_name

# Info
virsh dominfo vm_name
```

## Snapshots

```bash
# Create snapshot
virsh snapshot-create-as vm_name snapshot_name

# List snapshots
virsh snapshot-list vm_name

# Revert
virsh snapshot-revert vm_name snapshot_name

# Delete
virsh snapshot-delete vm_name snapshot_name
```

## Images

```bash
# Convert
qemu-img convert -f raw -O qcow2 image.img image.qcow2

# Create
qemu-img create -f qcow2 disk.qcow2 50G

# Info
qemu-img info disk.qcow2

# Resize
qemu-img resize disk.qcow2 +50G
```

## Virtual Network

```bash
# List networks
virsh net-list --all

# Start network
virsh net-start default

# Autostart
virsh net-autostart default

# Network info
virsh net-info default
```

## Quick Reference

```bash
# List VMs
virsh list --all

# Start VM
virsh start myvm

# Create snapshot
virsh snapshot-create-as myvm snap1

# Create disk
qemu-img create -f qcow2 disk.qcow2 50G
```
