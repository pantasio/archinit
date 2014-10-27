archinit
========

sudo pacman –Syu

sudo pacman –S bash-completion

sudo pacman -S xorg-server xorg-xinit xorg-utils xorg-server-utils mesa

pacman -S xf86-video-intel

startx

pacman -S cinnamon

pacman –S net-tools

pacman -S network-manager-applet

ip link

systemctl stop dhcpcd@ens33.service

systemctl disable dhcpcd@ens33.service

systemctl stop dhcpcd.service

systemctl disable dhcpcd.service

pacman –S gdm

systemctl enable gdm

systemctl start gdm

https://wiki.archlinux.org/index.php/Maximizing_performance
Catalyst Install

- yaourt catalyst-test (as non root user)

- open another terminal (ctrl+alt+F2) log in as root

- ctl+alt+F1 (non root) install then follow instructions

- in root terminal

	add nomodeset to grub ; nano /etc/default/grub
	update grub ; grub-mkconfig -o /boot/grub/grub.cfg
	
	pacman -S acpid
	systemctl enable atieventsd
	systemctl start atieventsd

	systemctl enable catalyst-hook
	systemctl start catalyst-hook

	systemctl enable temp-links-catalyst
	systemctl start temp-links-catalyst

	pacman -S qt4 (for AMD Control Center GUI)
	exit root

- ctl+alt+F1 (non root)
- sudo aticonfig --initial
- sudo reboot


Reinstall GRUB2 with arch linux live cd / usb key

So I had to reinstall my Windows 8 in my dual boot system with Arch
Linux. After the reinstall I had the default boot manager of Windows
back in place of GRUB2.

My way to fix it, was to install on my USB key the current live CD of
archlinux Download here. Burn it to CD or copy it to your USB key with


dd bs=4M if=/path/to/archlinux.iso of=/dev/sdx
After the installing of the live CD to my USB key. I was restarting my
PC to boot from it. Afterwards I got the default arch Linux shell.

I was creating a root point for my root disk in /mnt/root/

mkdir /mnt/root/
Now I can mount the root partition to this point

mount /dev/sdXX /mnt/root
Now I had to change the root. This command also adds the necessary
folders like (proc, dev,…)

arch-chroot /mnt/root
I have a separate boot partition so I had to mount this also to my
chroot system

mount /boot
Regenerate the grub.cfg

grub-mkconfig -o /boot/grub/grub.cfg
So, it’s nearly done! I had only to install Grub back in the MBR

grub-install /dev/sdXX
Last not but least. Rebooted and it was working

