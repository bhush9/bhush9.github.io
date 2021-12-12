---
layout: post
title:  "TLP has unintended side effects on Mobile devices"
date:   2021-12-12 11:20:00 +05:30
tags: 100DaysToOffload kde pinephone
---

We often get a complaint that Plasma Mobile is laggy. Today I wanted to debug it, one of the best way to debug this is to check if something is making use of system resources when it should not.

Running top on Manjaro Plasma Mobile dev images, I found that tlp is consuming 10-20% CPU constantly.

```
9099 root      20   0    5928   4568   2560 R   8.2   0.1   0:00.25 tlp
```

`tlp` is a daemon to "Optimize Linux Laptop Battery Life" [website](https://linrunner.de/tlp/)

One of first thing I did was to disable it and restart system. To my surprise it did not help and tlp was there in process-list anyway.

I decided to go with more brute approach and masked the `tlp.service`.

```
[bshah@manjaro-arm ~]$ systemctl cat tlp
# Unit tlp.service is masked.
[bshah@manjaro-arm ~]$ systemctl status tlp
○ tlp.service
     Loaded: masked (Reason: Unit tlp.service is masked.)
     Active: inactive (dead)
```

Restarting again and tlp was there in top again,

```
[bshah@manjaro-arm ~]$ ps -ef | grep tlp
root       10163    7861  8 10:12 ?        00:00:00 /bin/sh /usr/bin/tlp auto
```

This made it obvious that tlp is not being started by the systemd, but something else is starting it,

Looking at parent processes of tlp revealed it to be udevd

```
[bshah@manjaro-arm ~]$ ps -ef | grep 7861
root        7861    2280  0 10:10 ?        00:00:00 /usr/lib/systemd/systemd-udevd
root       11305    7861  0 10:12 ?        00:00:00 /bin/sh /usr/bin/tlp auto
bshah      11325    8878  0 10:12 ttyS0    00:00:00 grep 7861
```

Some more grep revealed that following rule is responsible for triggering tlp constantly,

```
[bshah@manjaro-arm ~]$ cat /lib/udev/rules.d/85-tlp.rules 
...
# handle change of power source ac/bat, ignore input device batteries
ACTION=="change", SUBSYSTEM=="power_supply", KERNEL!="hidpp_battery*", RUN+="/usr/bin/tlp auto"
```

This is Particularly bad because it is being triggered on every change event on the power_supply udev device and AXP20P driver sends this event on every charge/discharge:

```
UDEV  [2780.904234] change   /devices/platform/soc/1f03400.rsb/sunxi-rsb-3a3/axp20x-battery-power-supply/power_supply/axp20x-battery (power_supply)
KERNEL[2782.693116] change   /devices/platform/soc/1f03400.rsb/sunxi-rsb-3a3/axp20x-battery-power-supply/power_supply/axp20x-battery (power_supply)
```

This ultimately means that on every charge/discharge, it will call tlp, which will consume CPU for some reason, and then cycle continues.

I like to call it "Automatic battery discharging machine" :D

TLDR: Distributions please uninstall `tlp` from your PinePhone and possibly also other phone images, instead of saving battery it will consume it more.

Day #8 of the #100DaysToOffload series.
