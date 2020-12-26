---
layout: post
title:  "Plasma Mobile as Daily Driver on PinePhone"
date:   2019-12-20 23:10:00 +05:30
tags: kde
comments: true
disqusfix: true
---

Last week I was in Bluesystems GmbH meeting in Germany, almost 7000 km away from home. While one would hope that this journey is smooth, of-course this was not case for my journey. I missed my phone in first segment of journey (which now is on route to my home as I write). In 4 hours of layover I tried to retrieve my phone but unfortunately it was already with Lost and Found team and getting that would require me going through immigration etc. Thankfuly I had a LG Nexus 5X which I generally use to test out Plasma Mobile builds, In hurry I flashed LineageOS on it and downloaded some basic applications I needed on it. In second lag of journey I spent time copying some of required documents and files to mobile device.

Fast-forward 2 days, my Nexus 5X decided that it is time to give up. After turning off screen, it won't turn back on. I tried charging it for few hours but no luck. I did not need mobile while I was in meeting, since I was having meeting and stay at same place. I was able to communicate with my family and friends over telegram. But when I needed to travel back home, I realized while I can survive without mobile device, it won't be largely fun.

## Preparing PinePhone

While I had no android device with me, I had a PinePhone developer prototype[^1], which can run Plasma Mobile among others! So I decided to see if I can make use of Plasma Mobile while traveling back? My use-case was in general very limited,

- Minor web browsing
- Hotel check-in
- Boarding train and flights
- Searching for public transport options
- Communication

I generally don't use my SIM cards abroad due to high international roaming charges so I didn't need working calls yet. So with absolute minimal requirement in mind I started setting up my pinephone.

### Web browsing

Plasma Mobile have a Angelfish web browser, which is using QtWebengine and Kirigami user interface. Out of the box the QtWebengine doesn't work with Mali400-MP2 being used in the PinePhone, however internally chromium manages the workarounds specific to graphics drivers. One such workaround is available already for the Mali400, however it is tested only with binary driver released by Allwinner, and not opensource Lima driver. So we needed to adjust the workaround to match opensource lima driver as well.
```
--- qtwebengine-everywhere-src-5.13.2/src/3rdparty/chromium/gpu/config/gpu_driver_bug_list.json 2019-08-09 21:46:06.000000000 +0800
+++ qtwebengine-everywhere-src-5.13.2.new/src/3rdparty/chromium/gpu/config/gpu_driver_bug_list.json     2019-12-03 23:49:02.230915250 +0800
@@ -908,8 +908,7 @@
       "id": 108,
       "cr_bugs": [449150],
       "description": "Mali-4xx does not support GL_RGB format",
-      "gl_vendor": "ARM.*",
-      "gl_renderer": ".*Mali-4.*",
+      "gl_renderer": ".*Mali-*4.*",
       "features": [
         "disable_gl_rgb_format"
       ]

```
This patch allows one to browse web using angelfish.

### Hotel check-in and Boarding train/flights

I was staying in Frankfurt for one day since my flight was early morning next day. So I needed to check in the hotel and also board two trains to reach Frankfurt. While I had paper copy of the bookings with me, using them is boring! *wink*

I decided to use the [itinerary application](https://invent.kde.org/kde/itinerary) for checking in the hotel and traveling on trains. Itinerary allows you to import and manage various bookings and boarding passes. While I managed to import the booking for my hotel, I had trouble importing booking for train and my flight's boarding passes. Investigation of the issue showed that itinerary was not built in neon with zxing-cpp dependency. zxing-cpp allows to scan and decode various types of barcodes and QR codes; Which are commonly used in Flight and Train boarding passes.

[Adding zxing-cpp dependency](https://packaging.neon.kde.org/kde/kitinerary.git/commit/?h=Neon/unstable&id=2ba0e954405e46ab95166eda6c1d5630d2527b32) in kitinerary package solved issue and I was able to import all my boarding passes. After importing them I was able to use them at most places without any problem[^2].

### Searching for public transport options

I needed to search for public transportation while in Frankfurt. I used [ktrip application](https://invent.kde.org/kde/ktrip) to find my way around the Frankfurt, in general it is quite easy to use,

1. Enter your start point and end point
2. Enter the time you want to depart at
3. Find connections!

While I can make use of the maps at train station and bus station as well, Being able to get this information directly from your mobile device was quite useful.

### Communication

During travel I was able to connect with friends, family and colleagues using Telegram messanger, I was able to easily install it using Discover software center. Since I was on KDE Neon, which have it's own Qt packages I decided to use the version from flathub. While telegram itself worked flowlessly, I had minor annoying issue that if someone sends [animated sticker](https://telegram.org/blog/animated-stickers) in chat, my Telegram application would crash opening that chat. I haven't investigated issue further, but it could be bug in telegram or issue with graphics driver, it is hard to tell at moment. While I only wanted to use the Telegram, one can use Kaidan for XMPP and Spectral for Matrix chats as well.

## Conclusion

Overall it was much smoother experience to use the Plasma Mobile as a *daily driver*. I realized that while it is definitely not ready for the average user, there are variouse areas where we can improve most and make a impact.

- Working calls: This is absolute must for using daily driver. I hope that we can solve audio routing issues on Pinephone soon.
- Power management: Currently in case of Plasma Mobile, operating system is not optimized for this at all. It is definitely a new horizon for us and we can do lot there.
- User interface responsiveness: I realized that there are lot of places where we can improve the general responsiveness of user interface and application
- More applications: While my usecase was quite limited in terms of what I wanted to do with my phone, I am sure people have very different usecases of their phone and that includes lot more applications then we have currently.

While this blog post is focused on my usage of software on Pine64 PinePhone, If you are looking for hardware review, you can take a look at [post by Martijn Braam](https://tuxphones.com/yet-another-librem-5-and-pinephone-linux-smartphone-comparison/) comparing the Librem 5 and PinePhone hardware. That provides much more detail on hardware of PinePhone.

If you are excited about Linux smartphones and want to help us progressing Plasma Mobile forward, you can reach us at #plasmamobile:kde.org matrix room.

[^1]: I would like to thank Pine64 for sending Pinephone prototype to me.
[^2]: I had a minor trouble at first Etihad flight where they wanted to see boarding sequence number, which is not shown in the boarding pass page of itinerary. I have forwarded that bug to itinerary devs so that will be solved!
