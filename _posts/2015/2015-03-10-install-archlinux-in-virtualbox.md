---
title: Archlinux in Virtualbox
excerpt: "Install Arch Linux in Virtualbox"
tags: [linux,archlinux]
categories: dev
comments: true
guid: urn:uuid:23a4e2e0-8619-4852-8d82-1a513e5704b0
---

Install Arch Linux in Virtualbox

[https://wiki.archlinux.org/index.php/Installation\_guide](https://wiki.archlinux.org/index.php/Installation_guide)

Pre-installation
---- 

### Partition the disks
~~~
$ fdisk /dev/sda
~~~

boot

~~~
> n
> return (default primary)
> return (default partition 1)
> return (default first sector)
> +250M
~~~

swap

~~~
> n
> return (default primary)
> return (default partition 2)
> return (default first sector)
> +2G
~~~

/

~~~
> n
> return (default primary)
> return (default partition 3)
> return (default first sector)
> +2G
> return
~~~

/home

~~~
> n
> p (make primary)
> return (default first sector)
> return (default last sector)
~~~

make /dev/sda1 bootable

~~~
> a
> 1
~~~

make /dev/sda1 to swap type partition

~~~
> t
> 2
> 82
~~~

write table to disk and exit fdisk

~~~
> w
~~~

### Format the partitions

format partitions

~~~
$ mkfs.ext4 /dev/sda1
$ mkfs.ext4 /dev/sda3
$ mkfs.ext4 /dev/sda4
~~~

make swap

	$ mkswap /dev/sda2

mount swap

	$ swapon /dev/sda2

### Mount the partitions

~~~
$ mount /dev/sda3 /mnt
$ cd /mnt
$ mkdir boot home
$ mount /dev/sda1 boot
$ mount /dev/sda4 home
$ cd /
~~~

Installation
---- 

### Select the mirrors

rankmirrors to make this faster (though it takes a while)

~~~
mv /etc/pacman.d/mirrorlist /etc/pacman.d/mirrorlist.orig
rankmirrors -n 6 /etc/pacman.d/mirrorlist.orig \>/etc/pacman.d/mirrorlist
pacman -Syy
~~~

### Install the base packages

~~~
# install base packages (take a coffee break if you have slow internet)
pacstrap /mnt base base-devel
~~~

### Configure the system

Generate an fstab file

	$ genfstab -p /mnt >> /mnt/etc/fstab

Change root into the new system

	$ arch-chroot /mnt

Set the hostname

	$ echo [archlinux] > /etc/hostname

Set the time zone

	$ ln -sf /usr/share/zoneinfo/Australia/Sydney /etc/localtime

uncomment the needed locales in `/etc/locale.gen`, then generate them with

	$ locale-gen

Set locale preferences in `/etc/locale.conf` and possibly `$HOME/.config/locale.conf`

	$ echo LANG=en_US.UTF-8 > /etc/locale.conf

Set the root password (root account ,not your account, we will create that later)

	$ passwd

### Install a bootloader

~~~
$ pacman -S grub-bios
$ grub-install /dev/sda
~~~

Create a new initial RAM disk

~~~
$ mkinitcpio -p linux
$ grub-mkconfig -o /boot/grub/grub.cfg
$ exit
~~~

### Unmount the partitions

~~~
$ umount /mnt/home
$ umount /mnt/boot
$ umout /mnt
$ reboot
~~~

Until not, we finish installing archlinux, then we are going to setup the system.

Post-installation
---- 

After reboot, you might not be able to connect to innternet, run command to get ip address

    $ dhcpcd

run it automatically when system starts

    $ systemctl enable dhcpcd

turn on multi lib to install 32bit applications

    $ vi /etc/pacman.conf

uncomment

~~~
[multilib](#)
Include = /etc/pacman.d/mirrorlist
~~~

update packages

~~~
$ pacman -Syy
$ pacman -Su
~~~

install x environment

    $ pacman -S xorg-server xorg-xinit xorg-server-utils

intall mesa for 3d

    $ pacman -S mesa

install virtualbox guest packages

~~~
$ pacman -S virtualbox-guest-utils
$ modprobe -a vboxguest vboxsf vboxvideo
~~~

create

	$ vi /etc/modules-load.d/virtualbox.conf

add

~~~
vboxguest
vboxsf
vboxvideo
~~~

	$ reboot



~~~
$ pacman -S xorg-twm xorg-xclock xterm
$ startx
~~~

create user to login

~~~
$ useradd -m -g users -G storage,power,wheel -s /bin/bash jma
$ passwd jma
$ visudo
~~~

allow user to run `sudo` command

find `Uncomment to allow members of group wheel to execute any command` and uncomment `%wheel ALL=(ALL) ALL`
