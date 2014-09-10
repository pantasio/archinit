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

