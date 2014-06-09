---
layout: post
title:  "GSoC report #2 - Plasma mediacenter functional mode"
date:   2014-06-09 21:40:00
categories: kde
comments: true
---

Hello KDE community,

This is second update to my GSoC 2014 project. Previously I ported homescreen and mediabrowser part of the plasma-mediacenter. My next task is to port mediacontroller and mediaplayer components of the plasma-mediacenter. To port mediacontroller and mediaplayer I also wrote runtimeData class which acts as a bridge between libs and qmlcomponents.

So here is screenshot of the current state

![mediaplayer and mediacontroller](/images/mediacenter-player.png)

At the moment duration slider is broken.. But plasma-mediacenter on KF5 is progressing towards functional mode.

My next plan is to,

- Fix slider
- Port playlist components
- Add option to toggle plasmashell dashboard
- Use units provided by PlasmaCore instead of hardcoded values.

Thanks for reading! Stay tuned for more updates.
