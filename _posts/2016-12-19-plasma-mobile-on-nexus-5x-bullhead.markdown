---
layout: post
title:  "Plasma Mobile running on Nexus 5X (bullhead)"
date:   2016-12-19 14:30:00 +05:30
tags: kde
comments: true
disqusfix: true
---

Currently Plasma Mobile is supported by very small number of devices, for example Nexus 5, and One plus one. These devices uses Android 5.0 or CM12 as their base. Current libhybris upstream doesn't have support for the devices running Android 6.0 (Marshmallow), however there are two different forks of libhybris which are proposed to be merged into upstream libhybris and supports the Android 6.0,

- [https://github.com/libhybris/libhybris/pull/327](https://github.com/libhybris/libhybris/pull/327)
- [https://github.com/libhybris/libhybris/pull/328](https://github.com/libhybris/libhybris/pull/328)

This allows one to use Android 6.0 based binaries on normal Linux userspace and supports both armhf and aarch64 with some changes. I decided to try this on recent Nexus 5X device for which only Android 6.0 and higher version's binary blobs are available. With some changes in KWin, for example : [support for HWcomposer 1.4 and 1.5](https://phabricator.kde.org/D3686) and some changes in build infrastructure, it was possible to have Plasma working on Nexus 5X.

Image showing test_hwcomposer running from libhybris:

![test_hwcomposer running on Nexus 5X]({{ site.url }}/images/hwcomposer-bullhead.jpg)

Image showing Plasma Mobile running on Nexus 5X:

![Plasma on Nexus 5X]({{ site.url }}/images/plasma-mobile-bullhead.jpg)

As of now, just graphics and input are supported on Nexus 5X, however I've plan to work on Network, calling and other functionalities in upcoming weeks, which is required to have usable system. However this is good step in direction of having support for more devices, as this will open the possibilities of supporting newer devices, I will be happy to help if someone wants to port/run Plasma Mobile on their device, feel free to contact me over email bshah@kde.org or in #plasma channel on Freenode.

If you like work done by KDE community like this and want to support our work, please consider donating to our [Make the World a Better Place! - KDE End of Year 2016 Fundraising](https://www.kde.org/fundraisers/yearend2016/) campaign.

Happy Holidays!
