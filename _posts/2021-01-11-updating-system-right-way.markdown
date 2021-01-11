---
layout: post
title:  "Updating system right way"
date:   2021-01-11 20:25:00 +05:30
tags: 100DaysToOffload kde
---

I was ~~arguing~~ discussing earlier today with some community members what is best practice regarding the updating systems.

![XKCD argument](https://imgs.xkcd.com/comics/the_sake_of_argument.png)

There are two approaches to this,

- Updating system with software center provided by desktop/mobile environment like, GNOME software center, KDE Plasma Discover etc.
- Updating system with distributions command line tools, apt, pacman, zypper etc.

I personally advocate for first option instead of second and here are my reasons,

- Software centers abstract away the technical details of package manager that non-technical users do not need to know about, like repository, package.
- Most software centers will avoid forcing the "broken" setup, generally package managers allow to pass arguments like `--force` which may leave system in broken state
- Software centers provides the shutdown/suspend inhibition which prevents systems from going to sleep in middle of upgrades and leaving broken system
- At least KDE Plasma Discover and GNOME software center can do offline upgrades, that allows to boot system in minimal session just to upgrade and then reboot to working system

## But Bhushan....

### Command line is "True Linux experience™"

No it is not!

### How will user learn about Linux?

Users do not need to know about that, just like to get treated by doctor in hospital you don't need science degree, you don't have to teach everyone how Linux works. Remember that users exist outside of our typical "Linux user-space". If you are assuming that users of Linux need to know how command line works, we will never be able to go beyond 1% market-share we have in computing.

### GUI software center does not work

Report bug to upstream or distro's bug reporting system, and help developers fix it.

### I prefer command line tools still

<small>so do I!</small> Sure, but that does not mean you have to assume that every new user will be comfortable with the command line tools or terminal even.

Day #5 of the #100DaysToOffload series.
