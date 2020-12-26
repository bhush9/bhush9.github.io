---
layout: post
title:  "Device notifier porting progress"
date:   2013-09-05 11:00:00
tags: kde
comments: true
---

As a part of SoK project, I am currently porting [device notifier](http://userbase.kde.org/Plasma/DeviceNotifier) applet to Plasma2. Device notifier applet was already ported to QML by Viranch Mehta so it was somewhat easy task for me. In a Plasma2 port first task is to change versions of imports and some other modifications. Result was awesome, I got Device Notifier applet in working stage.

![Device Notifier port initially]({{ site.url }}/images/device-notifier-1.png)

After that I ported config.ui file to config.qml because in Plasma 2 config.ui files are no longer used. To port config.ui files you can have a look at the code given in plasma-framework/examples/applets/conditionalloader. As a sidenote all example DataEngines in the plasma-framework/examples/dataengines are now ported to use KF5.

Here is a configuration dialog which is ported to QML.

![Device Notifier configuration]({{ site.url }}/images/device-notifier-config.png)

But currently other options like Device actions, Removable devices are still missing.