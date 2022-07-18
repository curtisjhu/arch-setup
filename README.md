
# Installing Arch (for myself)

<br>

Boot from ISO image on USB stick.

### Keyboard
```
ls /usr/share/kdb/keymaps/**.*.maps.gz
loadkeys de-latin1
```

### Internet
1. Ethernet
2. Wifi (iwctl)
#. Mobile network (mmcli)
```
iwctl
> device list
> station [wlan0] scan
> station [wlan0] get-networks
> station [wlan0] connect

> station [wlan0] show
> station [wlan0] disconnect
> help
```
```
ping google.com
```

### Clock
```
timedatectl --help
timedatectl list-timezones
timedatectl set-timezones America/Los_Angeles
```

### Disk Partitioning

```
fdisk -l
```
Enter disk you want to partition
- Usually partition with /home, /swap, /root, or sometimes /boot
```
fdisk [/dev/sda]
> n %creates new partition
...
> d %delete partition
...
> w %save
```

#### Format Partition
- ext4 is the default Linux filesystem (when in doubt, choose ext4).
- swap is a dedicated partition that is used in place of RAM when RAM is used up. Instead of partitioning, you can simply create a swapfile in root directory.
- efi systems require a separate partition.

```
mkfs.ext4 [/dev/sda1] 		%root
mkswap [/dev/sda2] 			%swap
mkfs.fat -F 32 [/dev/sda3] 	%efi, if applicable
```

### Mount filesystems
```
mount [/dev/sda1] /mnt
mount --mkdir [/dev/sda3] /mnt/boot %efi
swapon [/dev/sda2] %swap
```

### Install/Configure
```
pacstrap /mnt base linux linux-firmware
```
```
genfstab -U /mnt >> /mnt/etc/fstab
arch-chroot /mnt
$ hwclock --systohc
```
```
$ locale-gen
$ echo "LANG=en_US.UTF-8" > /etc/locale.conf
$ echo "curtis" > /etc/hostname
$ echo "127.0.0.1 localhost curtis" >> /etc/hosts
$ echo '::1 localhost curtis' >> /etc/hosts
```

Configure a password
```
passwd
```

### Bootloader
```
pacman -S grub (efibootmgr)
grub-install /dev/sda
grub-mkconfig -o /boot/grub/grub.cfg
```

### User Privileges
```
pacman -S sudo
useradd -m curtis
passwd curtis
usermod -aG wheel,audio,video,storage curtis

```
```
su root
vim /etc/sudoers
```

### DE, DS, WM, DM
```
pacman -S xorg networkmanager
pacman -S lightdm lightdm-gtk-greeter

```
```
systemctl enable NetworkManager.service
systemctl enable lightdm.service
```

or
```
sudo git clone https://aur.archlinux.org/ly.git
cd ly
makepkg -si
systemctl enable ly.service
```

### Reboot
```
exit
unmount /mnt
reboot
// or [shutdown now]
```

