---
layout: post
title:  "How to emulate Plasma Mobile on your machine with qemu"
date:   2017-11-23 19:10:00 +05:30
categories: kde
comments: true
disqusfix: true
---

If you want to develop for Plasma Mobile, but you don't have a Mobile device, it is useful to emulate a Plasma Mobile on your desktop or laptop. Earlier this was not documented and has been asked multiple times on how to achieve this.


This blog post is intended to help install a Plasma Mobile on the qemu-x86.

* First of all create a qemu-image of 10GB size.

```
qemu-img create -f raw neon-unstable.img 10G
```

* Download the KDE Neon Dev edition (git unstable) ISO. [Link](https://files.kde.org/neon/images/neon-devedition-gitunstable/current/neon-devedition-gitunstable-current.iso)
* Start the qemu system with the downloaded the KDE Neon ISO.

```
qemu-system-x86_64 -cdrom /path/to/neon-devedition-gitunstable-current.iso -boot menu=on -drive file=/path/to/created/neon-unstable.img,format=raw -vga virtio -display sdl,gl=on -m 2G -enable-kvm
```

![KDE Neon startup](/images/kde-neon-startup.png)

* This will boot the KDE Neon system with Plasma Desktop. You will need to use Calameras to install the Plasma on the virtual machine.

![KDE Neon Installation](/images/kde-neon-install.png)

* Once installed, shutdown the virtual machine and restart the machine without ISO attached.

```
qemu-system-x86_64 -boot menu=on -drive file=/path/to/created/neon-unstable.img,format=raw -vga virtio -display sdl,gl=on -m 2G -enable-kvm
```

* In the virtual machine, open konsole and add the repository for Plasma Mobile.

```
curl http://neon.plasma-mobile.org:8080/Pangea%20CI.gpg.key | sudo apt-key add -
sudo add-apt-repository http://neon.plasma-mobile.org:8080
```

* Install the updates

```
sudo apt update && sudo apt upgrade
```

![KDE Neon install updates](/images/kde-neon-install-update.png)

* Install the Plasma Phone shell and configuration for Plasma Phone.

```
apt install plasma-phone-components plasma-phone-settings
```

* Logout from the Desktop Session and select the Plasma Mobile (Wayland) session.

![SDDM Plasma Mobile](/images/sddm-plasma-mobile.png)

* This steps will start Plasma Mobile session.

![Plasma Mobile in qemu](/images/plasma-mobile-qemu.png)

Please note that this steps are experimental at the moment, I am working on providing pre-built ISO images which will not require the KDE Neon developer edition ISO.
