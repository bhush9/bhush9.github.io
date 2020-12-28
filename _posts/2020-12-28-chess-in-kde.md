---
layout: post
title:  "Chess and KDE"
date:   2020-12-28 20:40:00 +05:30
tags: 100DaysToOffload kde
---

## Chess players in KDE community

Some of us have started a KDE community chess players team on the lichess.org. Mostly as a place to find people who are interested in chess and occasionally playing various variants of chess

If you want to join, [KDE Chess Players on lichess](https://lichess.org/team/kde-chess-players)

## Knights animations

Personally I rarely use the knights, and instead use the online chess platforms like [Lichess](https://lichess.org) (which by the way is another great FOSS project). Recently I was made aware about the animations in the knights were quite distracting.

See following example video,

<video width="100%" controls>
    <source src="/media/20201228/knights-funky-animation.mp4" type="video/mp4"/>
</video>

I initially wanted to get rid of animation completely but I realised that the animation speed is configuration option instead of something hard-coded. I proposed [a patch to change default animation speed to instant](https://invent.kde.org/games/knights/-/merge_requests/3).

My next idea is to change the animation code to animate movement of single piece that is moving instead of the knights currently animating all of the pieces from center of board so that users who prefer animation get something sensible.

## Wishlist for knights

It would be quite nice if we had a support for the Lichess in the knights to be able to play online games. knights does support [FICS](https://freechess.org) already for playing online games. But it would be quite nice to be able to also use knights as the client/front-end for Lichess. It does support extensive [API](https://lichess.org/api) to interact with it.

I will try to look into this probably in future but IMO, web client of Lichess already works great.

Day #2 of the #100DaysToOffload series.
