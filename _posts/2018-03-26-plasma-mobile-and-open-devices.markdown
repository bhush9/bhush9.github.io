---
layout: post
title:  "Plasma Mobile on open devices"
date:   2018-03-26 10:06:58 +05:30
categories: kde
comments: true
disqusfix: true
---

Plasma Mobile reference images are based on [halium](https://halium.org), which uses the propietary binary blobs to make use of phone hardware. This requires the libhybris which allows us to use bionic based binary blobs in the traditional libc based environment. Halium based devices also use very old vendor-provided kernel trees, these vendor trees generally range from version 3.4 to 3.18, most of the kernel versions listed here are already marked as EOL on kernel.org. 

Greg KH addressed this issue in a 3.18.48 kernel [announcement email rant](http://lkml.iu.edu/hypermail/linux/kernel/1702.1/00296.html):

```
> Oh, if you are _stuck_ on 3.18 (/me eyes his new phone), well, I might
> have a plan for you, that first involves you yelling very loudly at your
> hardware vendor and refusing to buy from them again unless they cut this
> crap out. After you properly vent to them, drop me an email and let's
> see what we can come up with, you aren't in this sinking ship alone, and
> it's obvious your vendor isn't going to help out...
```

It's however very clear that yelling at device vendor hasn't really helped and we're still seeing the new devices arriving on the market shipping Linux kernel version 3.18. There are some very new phones in market which use Kernel version 4.4, however these devices are so expensive that it is generally not feasible for many people to buy them.

So, how do we solve this issue? Projects like [postmarketOS](https://www.postmarketos.org) tries to solve this issue by using only open source components provided by vendors and avoiding binary blobs, but generally this doesn't really result in usable system as it will not allow us to use Hardware Acceleration and other hardware features. Another solution is to use the mainline kernel, which is actively maintained and developed by the Linux Kernel community.

Little while after I started working on Plasma Mobile I stumbled upon the [Android running on Nexus 7 with mainline kernel](https://plus.google.com/111524780435806926688/posts/fkQ1BMjNNcn) and wondered what it would take to get Plasma Mobile running on the device which runs the mainline kernel and a fully free software stack. In the process, I learned about how to mainline and asked the folks in ##linux-msm and #freedreno channels for help. Thanks to @bamse, @agross, @robclark I managed to add [initial support for Nexus 5 board in the mainline kernel](https://www.spinics.net/lists/arm-kernel/msg520971.html). This was [merged into Linux kernel version 4.9](https://www.spinics.net/lists/arm-kernel/msg528588.html). However this didn't really support useful features other then serial console over headphone jack, power and volume buttons. After adding initial support for hammerhead in mainline kernel I was not able to continue the work due time constraints.

Similar to hammerhead, community member [opendata](https://github.com/opendata26), a contributor to postmarketOS project, very recently managed to run [Plasma Mobile on the Sony Xperia Z2 tablet](https://postmarketos.org/blog/2017/12/31/219-days-of-postmarketOS/#plasma-mobile). While the device came with a Linux kernel version 3.4 from the provider, @bamse managed to port 4.X Linux kernel version to that device. Recently I learned that community member [flto](https://github.com/flto/) has continued the work I started a while ago, and has been [more successful](https://github.com/flto/linux/wiki/hammerhead-upstream) in hardware support then I initially was.

This week I decided to provide a pre-built Plasma Mobile image which can work with the mainline kernel. Current Plasma Mobile images are based on KDE Neon, which uses Ubuntu 16.04 Xenial as an underlying base. Unfortunately the version of Mesa in Ubuntu's repos were too old. Thankfully, community member [JBBgameich](http://www.jbbgameich.tk) has been maintaining the apt repository for Debian buster which included packages for Plasma Mobile. After [some work to create a rootfs](https://github.com/debian-pm-tools/rootfs-builder/commits/mainline) I successfully managed to boot a Plasma Mobile image on the Nexus 5 running a mainline kernel with mesa and [freedreno graphics driver](https://github.com/freedreno/freedreno/wiki).

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/sXnbRAeiffo" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

Using the same image as me, opendata was also able to run Plasma Mobile on the Sony Xperia Z2 tablet. Below is snapshot of the Kinfocenter application showing the system information.

![castor kinfocenter](/images/plasma-mobile-castor.png)

Currently these images are mainly experimental and super-unstable, they aren't really ready for production at all. However it proves that Plasma Mobile is capable of running on devices which support the mainline Linux kernel and fully free software stack. This will ultimately be useful for all the new projects working on free and open mobiles, such as [Sony's Xperia open devices](https://developer.sony.com/develop/open-devices/), [Purism's Librem 5](https://puri.sm/shop/librem-5/), since Plasma Mobile is committed to providing fully free and open source software for every device.

Despite usual warning of it may eat your kittens, if you want to try it on your device which is supported by mainline kernel, please contact us on Matrix at #plasmamobile:matrix.org or over email at plasma-mobile@kde.org

<i>Thanks to KDE Plasma team, @JBBgameich, @opendata, @flto, @bamse, @robclark, @agross, postmarketOS community, Debian Qt/KDE team for making this possible</i>
