# Arch-linux-install-tutorial
full-command to install the arch-linux 

__after you startup the os,by type these command can install the os successfully__ 
dhcpcd
cfdisk /dev/sda
mkfs.ext4 /dev/sda3
mkswap /dev/sda2
swapon /dev/sda2
mkfs.vfat /dev/sda1
mount /dev/sda3 /mnt
mkdir /mnt/boot
mount /dev/sda1 /mnt/boot
pacstrap /mnt vim grub grub-bios base base-devel mkinitcpio linux fcitx plasma-meta kde-applications-meta sddm fcitx fcitx-chewing dhcpcd networkmanager kcm-fcitx
genfstab -U /mnt >> /mnt/etc/fstab
arch-chroot /mnt
ln -sf /usr/share/zoneinfo/Asia/Taipei /etc/localtime
vim /etc/hostname
passwd
vim /etc/sudoers
mkinitcpio -p linux
grub-install /dev/sda
grub-mkconfig -o /boot/grub/grub.cfg
systemctl enable sddm
systemctl enable NetworkManager
exit
umount /mnt/boot
umount /mnt
reboot
