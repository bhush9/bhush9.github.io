---
layout: post
title:  "Plasma Mobile in Randa(aaaaaaaa)"
date:   2017-09-19 19:15:00 +05:30
tags: kde
comments: true
disqusfix: true
---

Last week I had a chance to attend the Randa meetings 2017, my plan was to work on the Plasma Mobile during the sprint, improve the state of current images. A few things changed over the course of the week:

### New shiny wallpaper and packages

Starting from 8 Sept, we started using the packages from [KDE Neon buildsystem](http://build.neon.kde.org) instead of building them on the [Plasma Mobile CI](http://mobile.neon.pangea.pub:8080), this provides few benefits,

- No need to separately build the common things like Qt5, KDE Frameworks, Plasma
- Always up-to-date packages, no need to manually re-trigger builds for common things

We also upgraded to newer version of Qt, Qt 5.9 from the older version of Qt 5.7.1, this aligns our stack with whatever KDE Neon dev unstable edition is using.

![Shiny Plasma]({{ site.url }}/images/pm-new-wallpaper.jpg)

### Rootfs for non-nexus Qualcomm devices

Non-nexus Qualcomm devices use a modified version of the hwcomposer.h which is not ABI compatible with the generic version of the android API headers, so for them the libhybris and kwin need to be separately built. Previously our CI infrastructure didn't support this workflow, however now we are able to create the rootfs for such devices. Below is an image of Plasma Mobile running on Xiomi Mi device.

![Plasma Mobile on CAF device]({{ site.url }}/images/pm-caf.jpg)

### Marble maps

At Randa, we had a chance to test the newer version of the Marble maps, which has much more improved performance when zooming out-in. We were able to happily search locate Randa in the Marble maps.

![Marble maps on Plasma Mobile]({{ site.url }}/images/pm-marble-maps.jpg)

### QML based mobile friendly "konsole"

Previously we were using Konsole from the KDE Applications as a terminal emulator, however Konsole user interface was not mobile-friendly, and it was not possible to e.g, tab complete the command, go through history, etc. At Randa Emmanuel Lepage Vallee pointed us to qmltermwidget, which powers the terminal application in Ubuntu Touch and Cool-retro-term application. Marco Martin was able to write a [simple QML application](https://github.com/notmart/qmltermwidget) around qmltermwidget which can replace Konsole in Plasma Mobile.

![QML based Terminal application]({{ site.url }}/images/pm-qmlkonsole.jpg)

### Kirigami based koko

During GSoC 2017 lot of work has been put to port the normal QtQuick based image viewer application Koko to kirigami2, you can follow the work of Student developer Atul Sharma on his [blog](http://atulsharma.me/). At the Randa Sprint, we were able to test this work on Plasma Mobile and it shows great improvements compared to the older version.

![Koko, image gallery application]({{ site.url }}/images/pm-koko.jpg)

### Improved window switching experience

Due to a bug in the Plasma Mobile shell, shell windows such as task switcher and shell itself were also appearing in the task switcher, as a result of that user was able to close the shell window which ultimately ends up crashing the plasmashell. We were able to fix this bug in the plasma-workspace and plasma-phone-components so that Plasma Mobile shell windows would not appear in the task switcher.

![Task switching]({{ site.url }}/images/pm-task-switching.jpg)

### Kube(!!!)

Yes, that is [Kube](https://kube.kde.org) in the first picture, we were able to run the Kube on the Plasma Mobile, it works in theory on Plasma Mobile, however the user interface is not mobile-friendly and needs various fixes to be usable on mobile. We will work with the Kube team to fix the issues and then test them on Plasma Mobile in the future.

### Conclusion

That is all for now, I would like to thank the all the donors who donated for the Randa Meetings 2017, and made it possible for me to travel to Randa, Switzerland.

If you liked the work done on Plasma Mobile during the Randa Sprint, please support us on [Randa 2017 fundraiser](https://www.kde.org/fundraisers/randameetings2017/) to make events like Randa possible in the future.
