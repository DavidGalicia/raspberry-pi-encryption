# Raspberry Pi Encryption Build Script
Creates a bootable SD card for an Raspberry Pi 5 with an encrypted root filesystem from an .img file in the current directory.
The filesystem is decrypted using a connected USB key drive when the Raspberry Pi 5 boots.
Tested images: 2025-12-04-raspios-trixie-arm64.img

# How to create a USB key drive:
Use `lsblk -d` to list parent devices and locate your USB drive. If your USB drive is `sdb` then
```
fdisk /dev/sdb # create a DOS MBR with a single primary partition (Id=83, Type=Linux)
lsblk # show all devices. should list sdb1
mkfs.ext4 -L KEY /dev/sdb1
 ```
You can now copy the Encryption key created by the script to the USB drive.
