---
layout: post
title:  "Plasma Media Center at Plasma Sprint 2015"
date:   2015-02-19 17:12:51
categories: kde
comments: true
---

Hola gente,

So all _plasmoids_ are gathered in Blue Systems office in beautiful city of Barcelona, Spain for Plasma Sprint 2015. One of the points I wanted to discuss was future of Plasma Media Center. Plasma Media Center got ported to KDE frameworks 5 and Plasma 5 library during last GSoC and with the help of our great Visual Design Group we also revamped the user interface fro Plasma media center. We also have integrated it as Plasma Shell package so plasmashell can load it as shell package and also can switch to mediacenter shell pacage.

At sprint I demostrated the current state of PMC to rest of Plasma team and we discussed some points,

- We should release it with Plasma 5 (i.e eventually move it to kde/workspace and Plasma 5.3 will have plasma-mediacenter), That will be technical preview for Plasma Media Center.
- Focus on "Living room" experience, at moment it is more like application and not really a whole mediacenter solution
- Eventually provide integration between different type of systems and Plasma Media Center (Android, Plasma Active, KDE connect etc)
- Figure out alternatives for multimedia playing, at moment Plasma Media Center is not able to play stuffs on some distributions like kubuntu due to libav/gstreamer and stuff.
- Work on polishing user interface and workflow for Plasma Media Center
- Some of features that should be included in Plasma Media Center, like integrated applications with Plasma Media Center

I also worked on some of the functionality for Plasma Media Center that will be eventually merged or are merged,

- Integration for services that allows to search media like YouTube, Flickr etc
- Proper plugin system for Plasma Media Center, so that plugins like UPnP media server and client can be integrated into Plasma Media Center.
- Allowing user to log into Plasma Media Center session directly from the login manager, this required little change in both plasmashell and Plasma Media Center shell package, now Plasma Media Center ships xsession desktop file for Plasma Media center.

If you want to try current status of Plasma Media Center then you can build the master branch of the plasma-mediacenter repository or you can install the binary packages shipped by various distributions. For example,

- KUbuntu users can install it through KUbuntu CI ppa
- Opensuse users can use KDE:Unstable:Extra repository
- Archlinux users can install plasma-mediacenter-git package

For moving the Plasma Media Center to kde/workspace will require it to be moved to kdereview for review of the plasma-mediacenter code, I will be filing sysadmin ticket and will send to email to plasma-devel and kde-core-devel mailing list for that.

Thanks for reading! I will be looking forward to feedback from community about current state of Plasma Media Center.

Update: I have just requested move of plasma-mediacenter to kdereview from extragear and also sent a [mail](https://mail.kde.org/pipermail/plasma-devel/2015-February/039429.html) to plasma-devel/kde-core-devel

Adiós!
