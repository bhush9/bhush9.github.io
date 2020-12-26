---
layout: post
title:  "How do I test Plasma Mobile? (part 2)"
date:   2018-02-02 15:36:58 +05:30
tags: kde
comments: true
disqusfix: true
---

The [first part of this series](http://blog.bshah.in/2018/01/26/trying-out-plasma-mobile/) focused on testing Plasma Mobile on virtual machine and/or on a PC/laptop. In this second part we will focus on testing Plasma Mobile on actual mobile devices.

Currently there are two possible ways of testing Plasma Mobile on an actual mobile device,

- Using postmarketOS
- Installing Halium and a KDE neon-based rootfs

I will explain both methods briefly in this blog post. Note that some of these steps may involve getting device-specific sources and building them manually, This may require a intermediate knowledge of how to unlock the bootloader, flashing and restoring devices and basic knowledge about various UNIX/Linux commands.

## Using postmarketOS

[postmarketOS](https://postmarketos.org) is touch-optimized, pre-configured Alpine Linux-based distribution which offers Plasma Mobile as one choice of several available user interfaces.

[There is a list of the devices that  can run postmarketOS](https://wiki.postmarketos.org/wiki/Devices), and you can find [instructions on installing postmarketOS on your device at their wiki page](https://wiki.postmarketos.org/wiki/Installation_guide).

When you follow the instructions to install postmarketOS, remember to [select "plasma-mobile" as the user interface when asked](https://wiki.postmarketos.org/wiki/Installation_guide#User_interface):

```
Available user interfaces (5):
* none: No graphical environment
* hildon: (X11) Lightweight GTK+2 UI (optimized for single-touch touchscreens)
* luna: (Wayland) webOS UI, ported from the LuneOS project (Not working yet)
* plasma-mobile: (Wayland) Mobile variant of KDE Plasma, optimized for touchscreen
* weston: (Wayland) Reference compositor (demo, not a phone interface)
* xfce4: (X11) Lightweight GTK+2 desktop (stylus recommended)
User interface [weston]: plasma-mobile
```

An important thing to note about postmarketOS is that it also offers Plasma Mobile on devices running mainline kernel, for example on the [Sony Xperia Z2 tablet](https://wiki.postmarketos.org/wiki/Sony_Xperia_Z2_Tablet_(sony-castor-windy)), [Google Nexus 7 (2013)](https://wiki.postmarketos.org/wiki/Google_Nexus_7_2013_(asus-flo)), and [LG Nexus 5 (partially)](https://wiki.postmarketos.org/wiki/Google_Nexus_5_(lg-hammerhead)). More information about Plasma Mobile on postmarketOS project can be found at the [Plasma Mobile wiki entry](https://wiki.postmarketos.org/wiki/Plasma_Mobile).

Video below shows Plasma Mobile running on the Sony Xperia Z2 Tablet, which is running on mainline kernel instead of the pre-installed older kernel version.

<video controls>

    <source src="https://postmarketos.org/static/video/2017-12/plasma-castor.mp4" type="video/mp4"/>

</video>

However note that the postmarketOS project is still at very early stages of development and is not suitable for most end users yet.

## Installing Halium and a KDE neon-based rootfs

![Various devices running Plasma Mobile]({{ site.url }}/images/plasma-mobile-halium-devices.jpg)

[Halium](https://halium.org) provides the minimal android layer that allows a non-Android graphical environment to interact with the underlying Android kernel and access the hardware. The Plasma Mobile team provides a Neon-based rootfs which can be used along with the Halium builds. Currently [Halium has been ported to multiple devices](https://github.com/halium/projectmanagement/issues?q=is%3Aissue+is%3Aopen+label%3APorts), however, binary builds are not provided because most of them include binary blobs which we cannot redistribute them legally. Instead we provide a link to the source manifest and you can use that to build your own images. [Documentation on how to build and install Halium is available at the Halium website](http://docs.halium.org/en/latest/).

Plasma Mobile on Nexus 5 and Nexus 5X is using the Halium based images, binary images for those are distributed at [Plasma Mobile image server](http://images.plasma-mobile.org/halium/) as a reference for other porters and developers for easy testing. You can install on those devices using the flashtool available [on Github](https://github.com/plasma-phone-packaging/pm-flashtool/).


