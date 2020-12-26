---
layout: post
title:  "Plasma Mobile at Plasma Sprint Valencia"
date:   2019-07-22 12:50:00 +05:30
tags: kde
comments: true
disqusfix: true
---

In June month we gathered in Slimbook's offices to work on Plasma. Along with Plasma developers, we were also joined by KDE Usability and Productivity team.

During the sprint I mostly worked to create up-to-date image for Plasma Mobile, as from last few weeks Plasma Mobile image was quite out-of-date and needed update.

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/JxNlApC1tB4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Some of the bugfixes we did includes,

- Workaround for potentially broken Qt 5.12.3, using basic render loop instead of threaded.
- [Fix for the regression in Window placement, sizing](https://phabricator.kde.org/D22054) (Thanks to Aleix and David for help on this)
- Fixing WiFI settings on mobile

Apart from Plasma Mobile, I worked on general Plasma bugfixes as well,

- [Behavior change in plasma-framework PluginLoader to fix behavior of X-KDE-ParentApp entries](https://phabricator.kde.org/D22049)
- [Fix for regression of the double locksceen in Plasma session](https://phabricator.kde.org/D22021)

If you want to know overall progress made in the Plasma + Usability & Productivity sprint, then you can take a look at [dot story](https://dot.kde.org/2019/07/04/plasma-usability-productivity-sprint-valencia-spain) for more detailed sprint report.

Thanks to [Slimbook](https://slimbook.es/en/) for hosting us and [KDE e.V.](https://ev.kde.org) for sponsoring my travel!

Also, I am going to Akademy 2019, and talking with Marco Martin about [Plasma on embedded devices](https://conf.kde.org/en/akademy2019/public/events/109).

![I am going to Akademy 2k19](https://cdn.kde.org/akademy/2019/imgoing/Akademy2019BannerBoscoVerticale.png)
