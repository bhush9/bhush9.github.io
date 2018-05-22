---
layout: post
title:  "Screenlocker integration in KWin Wayland"
date:   2015-11-17 20:30:00
categories: kde
comments: true
disqusfix: true
---

Since last few weeks I was working on the Lockscreen integration with KWin Wayland session, this is most important bit of the Plasma on Wayland session. Currently in X11 lockscreen is managed by ksmserver (KDE's session manager). It suffers from various security problems which are mentioned on [blog post](http://blog.martin-graesslin.com/blog/2015/01/why-screen-lockers-on-x11-cannot-be-secure/) by Martin Gräßlin. This blog post also mentions that in Wayland lockscreen functionality should be moved in kwin_wayland, so that compositor is aware that screen is locked, what windows are owned by greeter, and what should get input events.

To provide screenlocker integration in kwin_wayland, KWin needs to link to kscreenlocker library. Which was being built as static library in plasma-workspace. To avoid dependency loop kscreenlocker was split into different [repository](https://quickgit.kde.org/?p=kscreenlocker.git) to which ksmserver in plasma-workspace and kwin_wayland can depend upon. Next, kwin_wayland was adjusted to start KSldApp (stands for KScreenlocker Daemon Application). As a result, we had beautiful lockscreen on wayland session!

![screenshot]({{ site.url }}/images/lockscreen.png)

However, this was not really secure.. one can just Alt+Tab the screenlocker. oops!

![Thoug shal not pass]({{ site.url }}/images/memescreenlocker.jpg)

Now it was time for adding security constraints to KWin, so security promised earlier is available. Security constraints are,

- When screen is locked, allow only lockscreen/greeter windows to be shown
- When screen is locked no other clients/windows should be able to get input events
- Allow only on-screen input methods like maliit to be shown on lockscreen
- Do not pass any events to KWin effects or any other clients

For this kwin_wayland needs to know which windows are provided by lockscreen or greeter. For this KSldApp passed the client connection created by it to kwin_wayland. This way kwin can identify the greeter windows to apply various security restrictions. kwin_wayland have InputRedirection class which handles getting input events from the input devices and passes it to various clients, effects or applications based upon their priority. InputRedirection was adjusted to pass keyboard events to just lockscreen and mouse events to lockscreen as well as input methods.

However, things that are not secured/tested are :

- Touch events
- Global shortcuts for screenlocker
- Fallback/emergency screen not yet working

Also currently lockscreen on wayland is not unit tested. I plan to work on this in upcoming days.

This secured screen locker architecture for Plasma on Wayland session will be available for Plasma 5.5 release cycle. This also fixes 11 year old bugs like [keyboard/mouse grabs prevent screenlocker from starting](https://bugs.kde.org/show_bug.cgi?id=78871). Overall its very nice improvement to Plasma Desktop.

Enjoy!
