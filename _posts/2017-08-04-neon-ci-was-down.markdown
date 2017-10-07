---
layout: post
title:  "Neon CI was down, Why?"
date:   2017-08-04 13:30:00 +05:30
categories: kde
comments: true
disqusfix: true
---

This post is public service announcement regarding the KDE Neon infrastructure.

Earlier we KDE neon developers decided that we should build the armhf and/or arm64 packages on [Neon CI](https://build.neon.kde.org) itself instead of the different Plasma Mobile specific [Jenkins Instance](http://mobile.neon.pangea.pub:8080). First step to make this happen was the adding ARM architecture in the KDE Neon [package archive](https://archive.neon.kde.org). We are using the [Aptly](https://www.aptly.info) for serving the packages.

Aptly however have a limitation that if you have started with publishing the empty repository, then you need to specify the complete architectures list initally and that list can't be updated after publishing. See quote from [Aptly docs](https://www.aptly.info/doc/aptly/publish/repo/),

> Empty local repos could be published as well (as placeholder, for subsequent updates using aptly publish update command). When publishing empty local repos it is important to specify complete architectures list (using -architectures flag), as it can’t be changed after publishing.

Due to this limitation, only solution we had was to drop and republish the repositories with new architectures added. I started working on this at 15:43:14 IST yesterday, following were the steps taken:

- Suspended neon CI
- Stopping the aptly service on the `racnoss.kde.org` server
- Create a staging public repository and symlink it to older path
- Take a backup of the old aptly db at `~/aptly/db`
- Restart the aptly service and run a script to drop and republish the public repositories

At this point, script failed with cryptic 404 error instantly however, upon inspection we realized that it was failing for old wily repos, which are unused since we are using the Ubuntu 16.04 xenial nowadays. Since we are not doing any builds of wily currently, script was modified to skip the published repositories of wily distribution. However next run of script failed with 404 API error again. Cause for this error turned out to be different, it was design flow in the aptly REST API which is exposed when the publish Prefix have `/` or `_` in it. To quote from [Aptly docs](https://www.aptly.info/doc/api/publish/),

> if publishing prefix contains slashes /, they should be replaced with underscores (_) and underscores should be replaced with double underscore (__).

At this point checking state of aptly revealed that out of 10 publishing end points we had just 3 publishing endpoints present, At this point we reverted to older db backup and fixed the script, this time execution of script was sucessful. However I wanted someone to verify that everything is in order before making the new published repositories public. So today after inspection of both old and new repositories I've made the change final and also KDE Neon Jenkins is now back in service, running builds.

#### For users

This change affects the KDE Neon [archive](https://archive.neon.kde.org). I've done my best to verify that everything is in order but still if you face any errors while doing `apt update` or `apt upgrade`, please let us know by commenting here or in #kde-neon IRC channel. I will keep backup of old aptly db and public repositories for 1 week and then will clean it if no complaints are received.

**Edit**: Update URL to Mobile CI and update the description of bug which we hit
