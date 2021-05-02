# rpi-initramfs
initramfs update scripts for raspberry pi.

Scripts will automatically create and remove initramfs when kernel is updated. It will also update /boot/config.txt appropriately.

## Prerequisites
File /boot/config.txt should contain initramfs entry for currently installed kernel. For example:
```
initramfs initrd.img-5.4.51-v8+ followkernel
```

## Instalation:
Copy both folders info /etc/kernel/.

## How it works
Scripts will be called after kernel is removed and after kernel is instaled. 

Post removal script will remove old initramfs file and will comment out initramfs entry in config.txt. It will check if removed kernel is the same type as running one. For example:
- on RPi 4 in 64 bit mode, it will only act for kernel8.img
- on RPi 4 in 32 bit mode, it will only act for kernel7l.img
- on RPi 3 it will only act for kernel7.img

Post instalation script will create initramfs file and restore initramfs entry in config.txt with apropriet version number.
