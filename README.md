# raspberrypi-usb-boot

- Fresh install Raspberry Pi OS 64-bit on SD
- Update

```sh
sudo apt update
sudo apt full-upgrade
```
- Change status from critical to stable and update firmware
```sh
sudo nano /etc/default/rpi-eeprom-update
sudo rpi-eeprom-update -d -a
```

- Set USB boot through raspi-config

- Mount SSD
```sh
sudo mkdir /mnt/target
sudo mount /dev/sda2 /mnt/target/
sudo mount /dev/sda1 /mnt/target/boot/
```

- Point root to /dev/sda2, i.e. `root=/dev/sda2`
```sh
sudo nano /mnt/target/boot/cmdline.txt
```

- Check if fstab points to the right boot and root

```sh
sudo nano /mnt/target/etc/fstab
```

```
/dev/sda1       /boot      vfat          defaults                     0       2
/dev/sda2      /              ext4         defaults,noatime       0       2
```

- Power down and remove SD card
- Boot from USB :)
- We advise to use Rufus to flash the SSD via Windows (enable MBR partition scheme)
