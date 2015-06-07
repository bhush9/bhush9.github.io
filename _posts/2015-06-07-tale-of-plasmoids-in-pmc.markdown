---
layout: post
title:  "Tale of Plasmoids in Plasma Media Center"
date:   2015-06-07 16:57:59
categories: kde
comments: true
disqusfix: true
---

Hello Planet

This is first update of the my GSoC project TV optimized dashboard support in the Plasma Media Center. First let me tell you what this project is about

![What if Plasma Had just 7 inputs](/images/remote.png)

Exact usecase of Plasma Media Center is more or less watching your media files on your TV while sitting on the couch, and when we think of input devices for the TV first thing that comes to mind is Remote control. Any remote control will have minimum 7 button inputs

- Cardinal Controls (up/down/left/right)
- Select or OK
- Menu
- Back

Challenge in this project is to provide the full potential of Plasma to the users of the remote like input devices. Plasma being flexible can support this usecase by means of custom shell package and containment. My job during this summer is to work on containment and shell package to support this usecase.

####Progress

In the community bonding period I discussed the whole project with one of awesome member of Visual Design Group, Ken Vermette. Much to my surprise he said to me that he had one draft post with what-if-plasma-had-7-inputs scenario. After discussing various pros and cons of various design proposals I and Ken agreed upon using horizontal carousel like applet strip design.

![Mockup](/images/mockup-b.png)

With the great help from my mentor Marco Martin, I am currently working on the containment which will allow to load the plasmoids and navigate through them using the left and right keys. Below is short video of the progress.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Kfec_kUcDNA?rel=0&amp;controls=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

In upcoming days I plan to work on the Widget explorer and Widget configuration user interface. I will post more updates here soon. Stay tuned.
