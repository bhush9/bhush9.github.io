---
layout: post
title:  "What Makes Plasma Mobile"
date:   2017-11-24 21:10:00 +05:30
categories: kde
comments: true
disqusfix: true
---

*This post-series explains how Plasma Mobile is built and distributed. The first post of this series will give a high-level overview over parts that create a Plasma Mobile system.* 

### Introduction 

In order to run Plasma Mobile on a device that is so far only supported by Android, the following parts are used:

- boot.img (contains a kernel and minimal initrd) 
- Halium system.img (contains the Android binary blobs) 
- Plasma Mobile rootfs 

Out of this 3 parts, boot.img and system.img need to be compiled for each device seperately and they cannot be reused as-is on different devices. The rootfs can be used on different subsets of devices. We currently provide two types of rootfs, 

- Generic rootfs 
- CAF rootfs (CodeAurora Forum rootfs)

Generic rootfs is used on the mainly Nexus and other non-qualcomm devices, and CAF rootfs is used on Qualcomm devices which are using kernel and binary blobs provided on CodeAurora Forum. For this blog post I will focus on the Plasma Mobile rootfs, and what is included in it. 

### Plasma Mobile rootfs 

A Plasma Mobile rootfs includes following parts, 

- init system 
- Logind/consolekit 
- Libinput 
- DRM/HWcomposer/Framebuffer for graphics 
- Wayland 
- Qt5 (5.7.1 minimum, 5.9 recommended) 
- Login manager with wayland session support (SDDM for example) 
- Ofono, Telepathy (optional, provides phone call functionalities) 
- Plasma phone components 
- Kirigami components 
- Various applications 

Any distribution packaging this can act as a base system for Plasma Mobile. Packaging these parts along with plasma-phone-components ensures a working Plasma Mobile system. Nowadays, most modern distributions provide these parts and should be able to package and run Plasma Mobile. You can find a list of the repositories at : https://community.kde.org/Plasma/Mobile/Code 

In my next posts I will go into more details of individual parts of Plasma Mobile and how they are working on a Plasma Mobile-powered phone. Stay tuned!
