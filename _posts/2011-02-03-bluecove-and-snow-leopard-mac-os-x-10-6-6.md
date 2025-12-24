---
layout: post
title: BlueCove and Snow Leopard (Mac OS X 10.6.6)
categories:
- Spencer ex San Diego
---

BlueCove is an implementation of [JSR-82](http://www.jsr82.com/jsr-82-basics/) (aka JSR082 aka JSR82; can you tell I'm trying to get this post to be pretty googleable?), which is the Java API for Bluetooth. It's pretty necessary to have something like this if you're trying to use Java to control Bluetooth in any sort of application. In particular, I'm using it for [WiiRemoteJ](http://code.google.com/p/bochovj/wiki/WiiRemoteJ), a handler for Wii remotes.

Okay, so, there's plenty of information on the webs about getting BlueCove to work under various flavors of Linux, but I googled and googled until my googler was sore trying to find a solution for Mac OS X 10.6. Finally I figured it out, with the tangential help of [this somewhat unrelated thread](http://lejos.sourceforge.net/forum/viewtopic.php?p=8383&sid=aa70046a4f7f183acd283340aef2a06b).

The error I was getting looked something like this:
`Native Library bluecove not available
java.lang.IllegalStateException: Bluetooth failed to initialize. There is probably a problem with your local Bluetooth stack or API.
 at [stack data]
Caused by: javax.bluetooth.BluetoothStateException: BlueCove library bluecove not available`
My googling indicated that this error message on Macs usually happens when you're on a 64-bit processor, because BlueCove doesn't support the 64-bit architecture. Well, my MacBook is 32-bit, so I'm like, that can't possibly be the problem.

... OR COULD IT????

It turns out that even if you don't have a 64-bit processor, if you're running Snow Leopard, you have both the 32- and the 64-bit JREs installed on your system. (I know, right? I mean, why wouldn't you autodetect which architecture you have, and only install the 64-bit JRE if it would actually be useful?) So all you have to do to fix the problem is open up your Java preferences and tell it to give the 32-bit JRE priority over the 64-bit JRE.

Here's a picture. All you have to do is drag the 32-bit above the 64-bit.
[![Java preferences window.](http://sbagleysd.wordpress.com/wp-content/uploads/2011/02/java.png?w=300 "java")](http://sbagleysd.wordpress.com/wp-content/uploads/2011/02/java.png)

I hope that this post has the Google-juice and that it helps someone figure this stupid thing out.
