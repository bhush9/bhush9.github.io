---
layout: post
title:  "Find your way to Plasma Mobile"
date:   2018-06-06 13:45:00 +05:30
tags: kde
comments: true
disqusfix: true
---

### [Find your own way](https://www.plasma-mobile.org/findyourway/) to help develop Plasma Mobile

The Plasma Mobile project was started by the KDE community with the goal of becoming a free, user-friendly, privacy-enabling and customizable platform for mobile devices. We are always on the look out for more contributors to help push Plasma Mobile forward. However contributions to Plasma Mobile has high entry barrier due to various reasons, among which are the lack of documentation and easily available open tasks for Plasma Mobile.

One of the goals KDE community has set itself is to [streamline the onboarding of new contributors](https://phabricator.kde.org/T7116). With this goal in mind, we intend to solve the issue of the high entry barrier for contributors that affects the Plasma Mobile project and, along with KDE Promo team, we have set up various tasks:

- [Grow the number of developers and community support for Plasma Mobile](https://phabricator.kde.org/T7770)
- [Grow Plasma Mobile: Collect data](https://phabricator.kde.org/T7771)
- [Grow Plasma Mobile: Goal: Onboarding of new contributors](https://phabricator.kde.org/T7790)

While working on one of tasks to collect data we [learned that users want an easy way to test Plasma Mobile](https://phabricator.kde.org/T7779) and, to meet this requirement, we worked on the [easily installable images](https://blog.bshah.in/2018/01/26/trying-out-plasma-mobile/) [which can be tested on either a virtual machine or on real hardware](https://blog.bshah.in/2018/02/02/trying-out-plasma-mobile-part-two/). Check out the two parts series we wrote about that. You can find out how to do this in [part 1](https://blog.bshah.in/2018/01/26/trying-out-plasma-mobile/) and [part 2](https://blog.bshah.in/2018/02/02/trying-out-plasma-mobile-part-two/) of our blog post on the subject.

Like the rest of the KDE community, Plasma Mobile is using Phabricator to track and manage the task list. You can find the following tasks on Phabricator:

- Plasma Mobile [project board](https://phabricator.kde.org/tag/plasma%3A_mobile/), which includes all tasks.
- Plasma Mobile [PM 1.0 milestone](https://phabricator.kde.org/project/profile/247/) which includes the tasks needed  to be done to get Plasma Mobile to a basic 1.0 state.
- Plasma Mobile [PM 2.0 milestone](https://phabricator.kde.org/project/view/248/) which builds upon the functionality provided in the 1.0 milestone.

We realised that for new contributors these tasks can be hard to find and difficult to navigate through. To help with this we created another task to help potential contributors [easily find the tasks they can work on](https://phabricator.kde.org/T8806). Thanks to Dimitris Kardarakos, we now have a web-page on plasma-mobile.org which provides a set of question-answer nodes and leaf nodes pointing to various phabricator tasks. This system is [based on the code](https://github.com/jdm/asknot) used by Mozilla to power similar website.

![Find your way webpage]({{ site.url }}/images/plasma-mobile-find-your-way.png)

You can navigate through various tasks and TODO items from [https://www.plasma-mobile.org/findyourway/](https://www.plasma-mobile.org/findyourway/).

In addition to make the tasks easy to reach, we have also worked on revamping the existing Phabricator tasks. See [T6942](https://phabricator.kde.org/T6942), for example, that asks that someone create a calendar app for Plasma Mobile. An earlier version of this task didn't contain much useful information on how such an application could be created. The task was edited to include more information on which libraries you can use, references, knowledge requirements and system requirements for developing and testing such an application.

![Task difference]({{ site.url }}/images/plasma-mobile-calender-task.png)

We hope this will make it easier for you to get involved in the Plasma Mobile project. In order to make it easier for you develop and test applications, we are also [working on the developer guide](https://community.kde.org/Plasma/Mobile/DevGuide). I will announce it here when the guide is completed (*spolier alert: easy to use docker images to test your applications*). You can send questions by contacting us on Matrix at [#plasmamobile:matrix.org](https://matrix.to/#/#plasmamobile:matrix.org) or over IRC at [irc://chat.freenode.net/#plasma](irc://chat.freenode.net/#plasma) or over email at [plasma-mobile@kde.org](mailto:plasma-mobile@kde.org). We will be happy to listen to your feedback.

Looking forward to your contributions!
