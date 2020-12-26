---
layout: post
title:  "Season off, code on!"
date:   2014-01-01 11:21:00
tags: kde 
comments: true
---

Hello planet! Happy New Year 2014! With the year 2013 Season of KDE has come to an end. This was great experience for me. Under guidance of Sebastian Kügler (sebas), I ported some of the DataEngines to KDE Frameworks 5 and libplasma2, Some applets to Plasma2 and QML2 and also killed some bugs.

List of things that I ported to Plasma2 includes Icon (Generic Icon), Device notifier, ksgrd module from libksysguard, Activity bar and much more. I got to know many things about opensource world.

## Patience

Okay that's first rule of life, Keep patience. When you ask a question or ping someone on IRC, just stick to IRC, don't disappear or panic! If you don't get reply in expected time that doesn't mean that you are being ignored. You will get reply for sure. Just wait!

## Double check whatever you do

When you work on some opensource project and you have commit access to that project, it doesn't mean you can commit anything. If you are going to commit something without someone reviewing, please make sure that commit will not break build on CI system. Keep eye on Jenkins. During my SoK once I commited some changes that were not ready to commit and result was broken build of kde-workspace on Jenkins, I fixed it after 30 minutes and 5 commits. :(

## Stick to the plan

That's what movies tell us! (Right?) Sometimes in opensource world it is not recommanded to do work which is out of plan. I started to port some of applets in kdeplasma-addons during the end of SoK but then I realized porting stuffs from kdeplasma-addons was out of scope to meet the requirements of Plasma 2 release schedule. It's not that you are forbidden to do stuffs out of plan but its better if you stick to the plan.

That's what I learnt during SoK. I plan to make my contributions to KDE this year also in spair time. Sebastian Kügler and everyone else from Plasma team, thanks again for mentoring me through this season.
