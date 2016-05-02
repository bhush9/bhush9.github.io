---
layout: post
title:  "Plasma Mobile : New base system"
date:   2016-05-02 11:20:00 +05:30
categories: kde
comments: true
disqusfix: true
---

Last Akademy, the Plasma team revealed the first prototype of the new Plasma Mobile. Plasma Mobile is designed to work on any existing operating system stack, and so far, our reference images were based on Ubuntu Touch. Ubuntu Touch runs the Android system inside an LXC container to make use of Android Hardware Abstraction Layer, binary drivers and other proprietary services required to make use of hardware. To create our reference image, we used to fetch the Ubuntu Touch rootfs, remove Unity/Mir packages and install KF5, kwin_wayland, plasma and other applications on top of it.

Our initial Ubuntu Touch base was Ubuntu 15.04. Eventually, our image started to diverge from the Ubuntu Touch base. For example, we upgraded [libhybris to upstream version](https://blog.martin-graesslin.com/blog/2015/11/upgrading-libhybris/) because libhybris available in Ubuntu archive diverged too much from upstream to be useful in our context. We also had to upgrade to a newer Qt version, and we also needed to upgrade the base system to Ubuntu 16.04 (Xenial Xerus) because we did not have the resources for managing different branches for packaging the latest git KF5/Plasma for 15.04.

To simplify things further, we wanted to experiment if we can get our own operating system stack that can run on mobile devices. After we gathered and analyzed our requirements, we came up with the following base system architecture,

- Cyanogenmod/AOSP based android system
- Ubuntu/Neon system inside chroot or container

This new setup can bring some nice advantages for us,

- Easier to run Plasma Mobile stack with any operating system
- Theoretically possible to run Plasma on every device supported by Cyanogenmod
- Control over android stack for Plasma

There are various solutions available to run the Linux system on the Android base inside the chroot. For example, [Linux Deploy android application](https://play.google.com/store/apps/details?id=ru.meefik.linuxdeploy&hl=en). However they require a complete android system, and support only [VNC viewer](https://play.google.com/store/apps/details?id=com.realvnc.viewer.android&hl=en) or similar solutions for GUI. Since we wanted to run full KWin/Wayland session that would not work for us. Eventually I came across [LXC for android](https://lists.linuxcontainers.org/pipermail/lxc-users/2013-December/005952.html). This allows one to run Linux system inside the container on Android.

LXC requires various kernel features enabled to run containers, I needed to enable them in the Cyanognenmod [kernel for Nexus 5](https://github.com/CyanogenMod/android_kernel_lge_hammerhead). After various fixes here and there, I got a console working for Ubuntu system:

```
root@hammerhead:/data/lxc/lxc # lxc-start -n system -F
 * Setting up X socket directories...
    ...done.

Ubuntu Xenial Xerus (development branch) ubuntu-phablet console

ubuntu-phablet login: phablet
Last login: Wed May 12 08:39:00 UTC 1971 on lxc/console
Welcome to Ubuntu Xenial Xerus (development branch) (GNU/Linux 3.4.0-cyanogenmod-g15e5a99-dirty armv7l)

 * Documentation:  https://help.ubuntu.com/
```

Next thing to do in the line was to run the libhybris tests inside the container, this worked as expected after bind mounting /system and /vendor inside the container.

![Test hwcomposer running](/images/test_hwcomposer.jpg)

After that, we attempted to run kwin_wayland, to our surprise this didn't work as expected, and all Qt applications crashed with,

```
WARNING: QApplication was not created in the main() thread.
Segmentation fault
```

After researching a lot we got to know that Ubuntu Touch ships some [patches in bionic](https://code-review.phablet.ubuntu.com/gitweb?p=aosp/platform/bionic.git;a=shortlog;h=refs/heads/phablet-4.4.2_r1) to fix this issue. After applying those patches on bionic, KWin showed fancy lockscreen on phone.

![Oh its gorgeous](/images/pm-newstack.jpg)

Input, however didn't work as expected, as kwin failed to register session to logind inside container. KWin requires logind to open the input devices and get input events through its libinput backend. Martin Gräßlin investigated the problem and came up with solution which fetched the XDG_SESSION_ID variable and run TakeControl on that logind session, that in-addition to working input on new phone system, allows to [start KWin/Wayland on another tty](https://blog.martin-graesslin.com/blog/2016/04/starting-kwinwayland-on-another-virtual-terminal/).

There are several problems with this new stack, and currently I am working on fixing those issues and having 1:1 feature parity with current Ubuntu Touch based setup. Currently there is no easy way to install a zip file to flash this new base, it requires installing stripped-down Cyanogenmod ROM, installing lxc from daily builds and putting Plasma Mobile rootfs in the right place. This is currently documented at [KDE community wiki](http://community.kde.org/Plasma/Mobile/CyanogenmodBase/). In upcoming weeks I will be working on deployable image which you can directly flash to your device.
