---
layout: post
title:  "CyanogenMod, LineageOS and Plasma Mobile"
late:   2016-12-28 17:60:00 +05:30
categories: kde
comments: true
disqusfix: true
---

We are at almost end of 2016, unfortunately 2016 also took away great project with it, Cyanogenmod. However there is fork named [LineageOS in pipeline](http://lineageos.org/Yes-this-is-us/). Given we [switched our android base to CyanogenMod earlier](http://blog.bshah.in/2016/05/02/plasma-mobile-new-base-system/), lots of people asked me how this will affect Plasma Mobile?

We used CyanogenMod source tree and kernel for generating minimal android system which is used in hammerhead port. All of them are [available on github](https://github.com/CyanogenMod) currently. However it is not clear that upto when it will be available and will receive updates given code review system (gerrit) for CyanogenMod is offline. At this point we have two options,

- Switch to LineageOS, given it is 1:1 fork of CyanogenMod currently it will not require much work.
- Switch to AOSP base, given we don't really use the "extra" things provided by CM on top of AOSP.

While option 2 might sound big work, it in fact is not. For instance, in Nexus 5X (bullhead) port, underlying system is AOSP based instead of the CyanogenMod to simplify the things. Personally I had low priority [task on phabricator](https://phabricator.kde.org/T4944) for longterm to switch to AOSP base, but based on current situation this will need to be done with higher priority than earlier. :-(

That's all for now, I hope this clarifies situation..
