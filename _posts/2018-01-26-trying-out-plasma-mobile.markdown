---
layout: post
title:  "How do I test Plasma Mobile? (part 1)"
date:   2018-01-26 12:00:00 +05:30
categories: kde
comments: true
disqusfix: true
---

Last week we asked the Free Software community what they wanted to do to help us move forward with Plasma Mobile. These were the results from the poll on Twitter:

![Poll on twitter](/images/kde-plasma-mobile-twitter-poll.png)

And this was what the poll on Google+ looked like:

![Poll on Google+](/images/kde-plasma-mobile-googleplus-poll.png)

As you can see, the results were similar with least 44% poll participants wanting to test Plasma Mobile on their device, and/or as a virtual machine, or on real machine. Testing this on virtual machine was quite a hack earlier as explained in a previous [blog post](/2017/11/23/emulate-plasma-mobile/). We had no dedicated ISO image for Plasma Mobile, to test the Plasma Mobile one had to install KDE Neon developer edition and then run a few commands to convert it to a Plasma Mobile installation.

But, this week, by popular demand, we are providing an x86_64 based ISO images you can download from [Plasma Mobile images server](http://images.plasma-mobile.org/iso/).

### How to test

You can download the latest ISO and boot in either Virtual Machine or boot it on real machine.

#### QEMU/KVM

![Plasma Mobile on qemu](/images/qemu-plasma-mobile-iso.png)

#### VirtualBox

![Plasma Mobile on VirtualBox](/images/virtualbox-plasma-mobile.png)

#### On actual device

![Plasma Mobile on Dell laptop](/images/plasma-mobile-dell-laptop.png)

### Things to try

- Add a widget to the desktop

![Add widgets dialog](/images/plasma-mobile-add-widgets.png)

- Download and install an app from Discover Software Center

![Plasma Discover](/images/plasma-mobile-discover.png)

- Read comics in Peruse

![Peruse](/images/plasma-mobile-peruse.png)

- Test Kaidan, the XMPP client 

![Kaidan](/images/plasma-mobile-kaidan.png)

#### Disclaimer

This software is Alpha! Use it at your own risk. This software is not recommended for use in production and many core functionalities will probably not work. This version is intended for testing some features and for preview only. Plasma Mobile is not yet at a level where it can substitute the operating system currently running on your mobile phone, but with your help, we will get there.

### How to send us feedback

You can reach us on plasma-mobile@kde.org mailing list, or #plasma IRC channel on Freenode, or #plasmamobile:matrix.org matrix room, or on https://t.me/plasmamobile telegram group.

Thank you for helping us test Plasma Mobile.

*2nd part of this series will focus on testing Plasma Mobile on actual mobile devices instead of virtual machine or PC/laptop*
