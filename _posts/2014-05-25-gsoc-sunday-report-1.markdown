---
layout: post
title:  "GSoC Sunday report #1 : Plasma mediacenter running on KF5/Qt5"
date:   2014-05-25 20:00:00
categories: kde
comments: true
---

Hello planet! This is first report for my GSoC project porting plasma mediacenter to Qt5/KF5 and Implementing shell package.

So far I have,

* With help from sebas ported away plugin loading code from deprecated methods and macros
* Ported Plasma mediacenter welcome screen and media browser to QtQuick 2.0 and Plasna Next components.
* Cleaned source code of autotests and ported away from deprecated methods

Now enough words,

Lets checkout some screenshots..

![Mediacenter welcome screen](/images/mediawelcome.png)

![Mediacenter photos browsing](/images/mediabrowser-photos.png)

![Mediacenter local file browsing](/images/mediabrowser-browsing.png)

![Mediacenter youtube browsing](/images/mediabrowser-youtube.png)
Apparently I hit [bug 334767 in KIO::file_copy](https://bugs.kde.org/334767) so thumbnails are not working for online backends.. This is best screenshot I was able to get.. :D

So that's it for today.. Next week I have my exams so I will skip next report. Thanks for reading..
